---
title: "Pianobar still isn't working. (10.10)"
date: 2011-07-16
forum: General Help
---

### Post by Comrade7 on 2011-07-16
Alright so I've done the whole [http://packages.ubuntu.com/natty/pianobar](http://packages.ubuntu.com/natty/pianobar)
and I still get this "(i) Login... Error: Protocol incompatible. Please upgrade libpiano.
"
Should I be running the download with something other than the default software center?

---

### Post by mazato on 2011-07-18
the keys are outdated on that version, you should download from the developer's site if you are confortable complilling it, just run sudo make install and voilá !
[http://6xq.net/projects/pianobar/](http://6xq.net/projects/pianobar/)

---

### Post by Comrade7 on 2011-07-19
oh man I don't know how to do that yet lol

---

### Post by alexhayes on 2012-05-02
Try this script:

```

#!/bin/bash

#this is a script designed to install the latest version of pianobar
echo 'moving to downloads folder'
cd ~/Downloads

echo 'downloading pianobar source'
wget http://github.com/PromyLOPh/pianobar/tarball/master

echo 'renaming to compress file'
mv master pianobar.tar.gz

echo 'extracting tarball'
tar -xvf pianobar.tar.gz

echo 'renaming ugly tarball'
mv Promy* pianobar-install-files

echo 'entering source directories'
cd pianobar-install-files

echo 'installing dependencies'
sudo apt-get install libao-dev libgnutls-dev libfaad-dev libmad0-dev libjson0-dev

echo 'compiling'
make clean && make

echo 'installing'
sudo make install

echo 'cleaning up leftover files'
cd ~/Downloads
rm pianobar.tar.gz && rm -rf pianobar-install-files

if [ -f ~/.config/pianobar/config ]; then
    echo "pianobar already configured"
else
    echo 'writing configuration file'
    cd ~/.config
    mkdir pianobar
    cd pianobar
    echo 'Enter your pandora username and then press enter:'
    read pUser
    echo 'Enter your pandora password and then press enter:'
    read pPass
    echo 'user = ' $pUser > config
    echo 'password = ' $pPass >> config
fi

```

Copy this text into a file. Save it as filename.sh in your home folder. Open up a terminal and type 'sudo chmod +x filename.sh'. Then './filename.sh'. Follow the prompts.

---

