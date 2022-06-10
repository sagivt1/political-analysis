# Political Analysis


# Requirements
* python 2.6 or newer
* Go (Go 1.15 for all operating systems) 
* GIT
* Gpu Drivers
* bzip2
* gcc-4.6.3 or newer

# Requirements Packages and Modules
* numpy & scipy
* TensorFlow
* pickle
* sklearn
* json
* pandas
* transformers
* requests
* fasttext

# Installation and Configuration
**It is recomended to create new virtual environment**  
Follow the steps to setup the environment for the project  

## 1. Create environment for the project (python, PuTTY, Jupyterlab)

#### Install PuTTY and connect to the server
Download [PuTTY](https://www.putty.org/) and install.  
Insert server ip to Host Name.  
Add key to Connection->SSH->Auth Private key file for authentication.   
#### For Jupiter
Go to Connection->SSH->Tunnel set ***port = 8000***, ***destination = localhost:8888***  
If 8000 is used by another process, select a different, unused port number.  
8888 is the port that Jupyter Notebook is running on.  
Save the new connection and connect to server.

#### Install python packages and development tools:
```bash
sudo apt update
sudo apt -y upgrade
```
#### Check the version of Python 3:
```bash
python3 -V
```
#### Install pip
```bash
sudo apt install -y python3-pip
```
#### Run
```bash
sudo apt install build-essential libssl-dev libffi-dev python-dev
```

#### Setting Up a Virtual Environment
```bash
sudo apt install -y python3-venv
mkdir environments
cd environments
python3 -m venv my_env
```

### Activating the virtual environment
```bash
source my_env/bin/activate
```

### Install and run Jupyter lab
#### Install Jupyter  
```bash
pip install jupyterlab
```
#### activate virtual environment  
```
source ~/environments/my_env/bin/activate
```

### Start Jupyter
```
jupyter-lab
```
Enter the address [http://localhost:8000](http://localhost:8000/lab) to your browser.  
Enter the token/password from the output of the server.   
***Example***
>[I 2022-06-10 10:53:05.246 ServerApp] jupyterlab | extension was successfully loaded.  
>[I 2022-06-10 10:53:05.246 ServerApp] Serving notebooks from local directory: /home/politicalanalysis  
>[I 2022-06-10 10:53:05.246 ServerApp] Jupyter Server 1.13.1 is running at:  
>[I 2022-06-10 10:53:05.246 ServerApp] http://localhost:8888/lab?token=123456789123456789132456789    
>[I 2022-06-10 10:53:05.246 ServerApp]  or http://127.0.0.1:8888/lab?token=123456789123456789132456789  
>[I 2022-06-10 10:53:05.247 ServerApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).  

    
## 2. Install Git, Go and yap onlp
### Install Git
```
apt-get install git 
```
### Install Go
```
wget https://dl.google.com/go/go1.13.5.linux-amd64.tar.gz
```
```
sudo tar -C /usr/local/ -xzf go1.13.5.linux-amd64.tar.gz
``` 
### Download and Set Yap onlp
>The following instructions are for Linux but similarly this can be done on Windows and MacOS.  
>  
>    Make sure you have Go and Git installed and on the command PATH.  
>    Setup a Go environment:  
>        Create a directory (usually per workspace/project) mkdir yapproj; cd yapproj  
>        Set $GOPATH environment variable to your workspace: export GOPATH=path/to/yapproj    
>        In the workspace directory create the src subdirectory: mkdir src  
>        cd into the src directory cd src  
>    Clone the repository in the src folder of the workspace git clone https://github.com/OnlpLab/yap.git  
>    Unzip the models and build the application:    
>>   $ cd yap  
>>   $ bunzip2 data/*.bz2  
>>   $ go get .  
>>   $ go build .  
>>   $ ./yap  
>>   ./yap - invoke yap as a standalone app or as an api server  
>>     
>>   Commands:  
>>   
>>       api         start api server
>>       dep         runs dependency training/parsing
>>       hebma       run lexicon-based morphological analyzer on raw input
>>       joint       runs joint morpho-syntactic training and parsing
>>       ma          run data-driven morphological analyzer on raw input
>>       malearn     generate a data-driven morphological analysis dictionary for a set of files
>>       md          runs standalone morphological disambiguation training and parsing
>>   
>>   Use "./yap help <command>" for more information about a command
>>

### Running YAP as a RESTful API server
Go to the yap main folder and use the command to start the server:
```
./yap api
```

## 3.FastText

### install gcc
```
sudo apt update
sudo apt install build-essential
sudo apt-get install manpages-dev
```
### validate  
```
gcc --version
```
***First time loading fasttext will take some because the model will need to be download.***

### Using Fasttext
```
import fasttext  
import fasttext.util  
ft = fasttext.load_model('cc.en.300.bin')  
ft.get_nearest_neighbors('hello')  
```

## 3. Download and Loading Hebert
### Download HeBert
```
git lfs install
git clone https://huggingface.co/avichr/heBERT
```
### Lodaing HeBert
```
from transformers import AutoTokenizer, AutoModelForMaskedLM
tokenizer = AutoTokenizer.from_pretrained("avichr/heBERT")
model = AutoModelForMaskedLM.from_pretrained("avichr/heBERT")
```

## 4.Nvidia Driver
[Download](https://developer.nvidia.com/cuda-downloads)

## 5. Python packages
```
pip install pandas
pip install numpy
pip install scikit-learn
pip install scipy
pip install tensorflow
pip install pickle-mixin
pip install transformers
pip install requests
pip install fasttext
```

## More resources
https://jupyter.org/install  
https://github.com/avichaychriqui/HeBERT  
https://huggingface.co/bert-base-multilingual-cased  
https://go.dev/doc/install  
https://www.digitalocean.com/community/tutorials/how-to-install-run-connect-to-jupyter-notebook-on-remote-server  
[https://nlp.biu.ac.il/~rtsarfaty/onlp](https://github.com/OnlpLab)  



