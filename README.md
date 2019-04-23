### golang_setup
Possible issues:  
> [Failed to compile in Ubuntu 16.04](https://github.com/moovweb/gvm/issues/197)  

```
mkdir golang
mkdir golang/3rdpkg
mkdir golang/own
cd golang
wget https://github.com/golang/go/archive/go1.4.3.tar.gz
wget https://github.com/golang/go/archive/go1.6.tar.gz
tar -xvf go1.4.3.tar.gz
tar -xvf go1.6.tar.gz

echo "export golang=${HOME}/golang" >> ~/.bashrc
echo "export GOROOT=${golang}/go" >> ~/.bashrc
echo "export GOROOT_BOOTSTRAP=${golang}/go-bootstrap" >> ~/.bashrc
echo "export GOPATH=${golang}/3rdpkg:${GOROOT}:${golang}/own" >> ~/.bashrc
echo "export PATH=${GOROOT}/bin:${PATH}" >> ~/.bashrc

unlink go
ln -s go-go1.4.3 go
. ~/.bashrc
cd go/src
./all.bash

cd ${golang}
unlink go-bootstrap
unlink go
ln -s go-go1.6 go
ln -s go-go1.4.3 go-bootstrap
cd ${GOROOT}/src
./all.bash
go version
```
