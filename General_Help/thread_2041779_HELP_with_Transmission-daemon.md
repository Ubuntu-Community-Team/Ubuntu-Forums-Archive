---
title: "HELP with Transmission-daemon"
date: 2012-08-13
forum: General Help
---

### Post by CocoMonGo on 2012-08-13
Hi all I really need help with Transmission-daemon 2.61 which I have installed with my Ubuntu 12.04 server. When I have added the torrent it fails to proceed further then 4mb giving the error:

```
Error: Permission denied (/home/user/Downloads/Torrents/ubuntu-12.04-desktop-amd64.iso)
```I have searched Google and Ubuntuforums for potential solution and nothing have solve my issue. The following is the process I used to install and setup Transmission-daemon:

```

sudo add-apt-repository ppa:transmissionbt/ppa
sudo apt-get update sudo apt-get install transmission-cli transmission-common transmission-daemon
sudo cd /home/user/Downloads
sudo mkdir Torrents
sudo cd Torrents
sudo mkdir Incomplete
 
sudo usermod -a -G debian-transmission user
sudo chgrp -R debian-transmission /home/user/Downloads/Torrents
sudo chmod -R 775 /home/user/Downloads/Torrents
sudo service transmission-daemon stop
```I then opened and changed the following lines via

```
 sudo nano /etc/transmission-daemon/settings.json
``````
    "blocklist-enabled": true,
    "blocklist-url": "http://list.iblocklist.com/?list=bt_level1&fileformat=p2p&arch$
    "cache-size-mb": 4,
    "download-dir": "/home/user/Downloads/Torrents",
    "encryption": 2,
    "incomplete-dir": "/home/user/Downloads/Torrents/Incomplete",
    "peer-port": xxxx,
    "rpc-enabled": true,
    "rpc-password": "xxx",
    "rpc-port": 9091,
    "rpc-url": "/transmission/",
    "rpc-username": "user",
    "rpc-whitelist": "192.168.1.*",
    "rpc-whitelist-enabled": true,
    "umask": 2,

```When that didn't work I tried:

```
sudo usermod --append --groups debian-transmission user
sudo chown -R debian-transmission:debian-transmission /home/user/Downloads/Torrents/
sudo chmod 777 /home/user/Downloads/Torrents/
sudo chmod 777 /home/user/Downloads/Torrents/Incomplete

```Later I tried to check the folder permissions
```
sudo ls -la /home/user/Downloads/Torrents
```and got the following code

```
drwxrwxrwx+ 3 debian-transmission debian-transmission 4096 Aug 13 21:42 .
drwxrwxrwx+ 4 user                root                4096 Aug 13 22:05 ..
drwxrwxrwx+ 2 debian-transmission debian-transmission 4096 Aug 13 21:42 Incomplete

```Help please! I have been cracking my head about this for weeks already without solution.

---

### Post by sanderj on 2012-08-13
Does the 12.04's default Transmission-daemon version (2.51) work for you?


And do you specifically need Transmission-daemon version 2.61?

---

### Post by CocoMonGo on 2012-08-13
Nope the original Transmission 2.51 did not work initially before I added the TransmissionBT ppa to get the latest version 2.61. I was getting the same issues with both version. 

Before going further best that I add that that Transmission-gtk works without issue (I have xubuntu-desktop installed but it is usually not running). I am running the server headless using PuTTy and the server is booted to CLI.

---

### Post by sanderj on 2012-08-14
> **CocoMonGo said:**
> Nope the original Transmission 2.51 did not work initially before I added the TransmissionBT ppa to get the latest version 2.61. I was getting the same issues with both version. 

Before going further best that I add that that Transmission-gtk works without issue (I have xubuntu-desktop installed but it is usually not running). I am running the server headless using PuTTy and the server is booted to CLI.

Some remarks:

1) '/home/user/' is not really what you have used, have you?
2) I've a headless Ubuntu 11.10 user running transmission as a daemon. I can't remember exactly how I configured it, but just with the default transmission version and no complex setup stuff
3) because of all the stuff you've done, it's unclear to me what is going on and I find it hard to help.

---

### Post by CocoMonGo on 2012-08-14
> **sanderj said:**
> Some remarks:

1) '/home/user/' is not really what you have used, have you?
2) I've a headless Ubuntu 11.10 user running transmission as a daemon. I can't remember exactly how I configured it, but just with the default transmission version and no complex setup stuff
3) because of all the stuff you've done, it's unclear to me what is going on and I find it hard to help.

To answer your question;
1. No "user" is not exactly what I am using right now but I have ensured the proper user name was used in all instances.
2. With the default transmission-daemon setting it would have saved my files to "[FONT=&quot]/var/lib/transmission-daemon/downloads". However since I am only accessing the server via SAMBA [/FONT]I need to open and connect another "SAMBA Drive/Folder" on the server and clients - which I do not intend to since I already have 2-3 sharing SAMBA folders already.

I am having an assumption that it is a folder permission issue right now but am not too sure how to proceed.

---

### Post by CocoMonGo on 2012-08-17
I found out that "drwxrwxrwx+" means there is an ACL additional requirements there. I have managed to remove the "+" from the premission requirements of the folders but Transmission-daemon still refuses to download the to set folder. I even compared the new folder's permission requirements to the default folder (/var/lib/transmission-daemon/downloads) and from what I see they are the same. There is no issue downloading to the default folder though. 

Anybody can advise what I might be doing wrong?

---

