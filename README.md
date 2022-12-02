# Inery
Inery Master Node
Component Recommended Requirement 

CPU Intel Core i7-8700 Hexa-Core

RAM 64 GB DDR4 RAM

Storage 2 x 1 TB NVMe SSD Connection 

1 Gbit/s port

## *Update Package*

```
sudo apt-get update && sudo apt install git && sudo apt install screen
```

Update Tools

```
sudo apt-get install -y make bzip2 automake libbz2-dev libssl-dev doxygen graphviz libgmp3-dev \
autotools-dev libicu-dev python2.7 python2.7-dev python3 python3-dev \
autoconf libtool curl zlib1g-dev sudo ruby libusb-1.0-0-dev \
libcurl4-gnutls-dev pkg-config patch llvm-7-dev clang-7 vim-common jq libncurses5
```

## Edit Firewall Port

```
ufw allow 22 && ufw allow 8888 && ufw allow 9010 && ufw enable -y
```

## Installing Nodes

Clone Inery Nodes data from github


```
git clone https://github.com/inery-blockchain/inery-node
```

## Go to inery setup folder


```
cd inery-node/inery.setup
```

## change app permission

```
chmod +x ine.py
```

## export path to local os environment for inery binaries

```
./ine.py --export
```

##refresh path variable

```
cd; source .bashrc; cd -
```

## Edit the configuration

```
sudo nano tools/config.json
```

"MASTER_ACCOUNT":
{
    "NAME": "AccountName",
    "PUBLIC_KEY": "PublicKey",
    "PRIVATE_KEY": "PrivateKey",
    "PEER_ADDRESS": "IP:9010",
    "HTTP_ADDRESS": "0.0.0.0:8888",
    "HOST_ADDRESS": "0.0.0.0:9010"
}

AccountName ganti Account Name kalian di dashboard
Public Key dan Private Key juga kalian replace yang di dashboard
IP di PEER_ADDRESS ganti pake IP Private kalo yang pake azure kalau yang pake cantabo masukin IP Public

## Screen Master Node

```
screen -S master

./ine.py --master
```

NOTE! HARUS SETELAH SYNCRON

## Create Wallet 


```
cd;  cline wallet create --file defaultWallet.txt
```

## If your wallet has password, you need to unlock it first

```
cline wallet unlock --password YOUR_WALLET_PASSWORD
```

## import key 

```
cline wallet import --private-key MASTER_PRIVATE_KEY
```

change MASTER_PRIVATE_KEY dengan private kalian

## Register as producer by executing command:

```
cline system regproducer ACCOUNT_NAME ACCOUNT_PUBLIC_KEY 0.0.0.0:9010
```

## Approve your account as producer by executing command:

```
cline system makeprod approve ACCOUNT_NAME ACCOUNT_NAME
```

Cek di explore -> https://explorer.inery.io/



## OPTIONAL

## Remove node (uninstall) go to 

```
inery.setup/inery.node/ and execute ./stop.sh script
```

## Untuk melanjutkan protokol blockchain, jalankan 

```
start.sh script
```

## Untuk menghapus blockchain dengan semua data dari mesin lokal, buka 

```
inery.setup/inery.node/ and execute ./clean.sh script
```
