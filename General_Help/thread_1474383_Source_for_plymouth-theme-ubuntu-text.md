---
title: "Source for plymouth-theme-ubuntu-text"
date: 2010-05-06
forum: General Help
---

### Post by doixanh on 2010-05-06
I'm using the CLI only. So when I boot up, the plymouth plugin "ubuntu-text" is loaded. I want to modify the plugin. 

Where can I get the source for that plugin? I looked in the repo and its binary is here [http://packages.ubuntu.com/lucid/plymouth-theme-ubuntu-text](http://packages.ubuntu.com/lucid/plymouth-theme-ubuntu-text) I could find the source for Ubuntu plymouth  but there isn't source for ubuntu-text inside it.

Any help is appreciated.

---

### Post by ankspo71 on 2010-05-06
Hi,
Source files should be available for every open source package in Ubuntu, but we have to ask for it. I prefer to do that by command line.

1.) Open a terminal and type:
```
cd Desktop
apt-get source plymouth-theme-ubuntu-text
```

2.) I'm using Kubuntu 10.04 and it gave me an error that "dpkg-dev" was not installed. If you get the error too, Open a terminal and type the code below, then go back and repeat step 1.
```
sudo apt-get install dpkg-dev
```

Edited:
Oops, I just noticed you said command line only. So you can ignore 'open the terminal' parts :p

---

### Post by doixanh on 2010-05-06
Got it, thank you so much :D

---

