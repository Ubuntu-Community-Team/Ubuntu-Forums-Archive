---
title: "Accidentally deleted dpkg, can't update"
date: 2010-06-23
forum: General Help
---

### Post by rizameister on 2010-06-23
i have accidentally deleted **dpkg**, so i have this error in **Synatic** when trying to update

[IMG]http://img691.imageshack.us/img691/8715/screenshot04f.png[/IMG]


**or through terminal, showing this error**:

root@XXXXXX:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  fglrx
The following NEW packages will be installed:
  fglrx
0 upgraded, 1 newly installed, 0 to remove and 39 not upgraded.
2 not fully installed or removed.
Need to get 0B/29.2MB of archives.
After this operation, 100MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Could not exec dpkg!
E: Sub-process /usr/bin/dpkg returned an error code (100)

**How to get original dpkg? and where to copy?**

---

### Post by Noz3001 on 2010-06-23
Can you not compile and install from source?

---

### Post by Leppie on 2010-06-23
download the package from this page: [http://packages.ubuntu.com/lucid/dpkg](http://packages.ubuntu.com/lucid/dpkg)
hopefully gdebi still works for you, just launch the package from your browser.

---

### Post by gzarkadas on 2010-06-23
From the liveCD (if I remember well) or from [http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/](http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/) (just make sure you select the correct version for your distro).

Since you don't have dpkg anymore you cannot use dpkg to install the .deb file (its the chicken and egg problem :)). So you will have to use `ar' to unpack the .deb archive (debian packages are `ar' type archives). 

See `man ar' for details - it may also be the case that you will be able to unpack it from inside the gnome gui (don't know since I have never needed that). Then copy dpkg -since you just deleted this file, there is no need to touch config files etc- in /usr/bin/ . 

Use `chmod 750 /usr/bin/dpkg' afterwards to set the right permissions for the executable.

---

### Post by sisco311 on 2010-06-23
Assuming that you are using Ubuntu 10.04. Download the package:
```
mkdir /tmp/dpkg
cd /tmp/dpkg
```

for 32bit:
```
wget http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.15.5.6ubuntu4_i386.deb
```

for 64bit:
```
wget http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.15.5.6ubuntu4_amd64.deb
```

Extract the archive:
```
ar x dpkg*.deb data.tar.gz
tar xfvz data.tar.gz ./usr/bin/dpkg
```

Copy the binary to /usr/bin:

```
sudo cp ./usr/bin/dpkg /usr/bin/
```

Now try to reinstall dpkg:
```

sudo apt-get update
sudo apt-get install --reinstall dpkg
```

---

### Post by rizameister on 2010-06-23
> **sisco311 said:**
> Assuming that you are using Ubuntu 10.04. Download the package:
```
mkdir /tmp/dpkg
cd /tmp/dpkg
```

for 32bit:
```
wget http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.15.5.6ubuntu4_i386.deb
```

for 64bit:
```
wget http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.15.5.6ubuntu4_amd64.deb
```

Extract the archive:
```
ar x dpkg*.deb data.tar.gz
tar xfvz data.tar.gz ./usr/bin/dpkg
```

Copy the binary to /usr/bin:

```
sudo cp ./usr/bin/dpkg /usr/bin/
```

Now try to reinstall dpkg:
```

sudo apt-get update
sudo apt-get install --reinstall dpkg
```

Thank you all! It is working!
sisco 311 You're **God**!

---

### Post by sisco311 on 2010-06-23
You're welcome!


Please mark this thread as [SOLVED].

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" Menu and then "Mark this thread as Solved".

Thanks.

---

### Post by nic168 on 2011-06-07
Hi Sisco311,

I need help as I know nothing about using Terminal and handling .deb files. I actually face exactly same problem in this thread. Are you able to SSH into my iphone if I give you my Wifi ip address?

Hope you can help me.

Thank you in advance.

Nicholas.

---

### Post by sisco311 on 2011-06-07
> **nic168 said:**
> Hi Sisco311,

I need help as I know nothing about using Terminal and handling .deb files. I actually face exactly same problem in this thread. Are you able to SSH into my iphone if I give you my Wifi ip address?

Hope you can help me.

Thank you in advance.

Nicholas.

Hi nic168 and welcome to the forums!

You can do the same thing via the GUI.

You have to download **dpkg_1.16.0~ubuntu8_i386.deb** from [http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/](http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/)

Then open your file manager and navigate to the directory where the file was downloaded. Right click on the file and select *Extract here*. The file will be extracted in a new directory: dpkg_1.16.0~ubuntu8_i386.

Now open your file manager as root, press Alt+F2 and run:
```
gksu nautilus
``` 

Navigate to the dpkg_1.16.0~ubuntu8_i386/usr/bin directory and copy the **dpkg** file in the /usr/bin directory. Close the file manager.

Open Synaptic package manager, search for the dpkg package and reinstall it.

HTH

---

