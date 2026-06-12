---
title: "How to install other desktops"
date: 2011-11-29
forum: General Help
---

### Post by rng on 2011-11-29
I am running ubuntu 10.04LTS and very happy with it. Though gnome is very good, I want to try other desktops especially xfce and lubuntu desktop. Can I install these 2 desktops on the existing gnome version and have a choice at startup as to which desktop to start?

Thanks for your help.

---

### Post by Megaptera on 2011-11-29
Good xfce tutorial: [http://www.psychocats.net/ubuntu/xfce](http://www.psychocats.net/ubuntu/xfce)

---

### Post by Frogs Hair on 2011-11-29
The site linked above has instructions for Kubuntu as well . I can't find much information about Lubuntu on 10.04 though .

---

### Post by holycow131415 on 2011-11-29
lubuntu uses lxde.

[http://linuxhub.net/2010/04/install-lxde-light-weight-desktop-manager-on-ubuntu-10-04/](http://linuxhub.net/2010/04/install-lxde-light-weight-desktop-manager-on-ubuntu-10-04/)

---

### Post by rng on 2011-11-29
Thank you all. I will try to install these and let you know my experience.

---

### Post by digithal on 2011-11-29
You don't have to make a new installation of Xubuntu or Lubuntu if you want to test different environments.
To install LXDE, just type in terminal:
```
sudo apt-get install lxde
```
or to install XFCE:
```
sudo apt-get install xfce4
```
Then select the session you want to start from your login manager.

---

### Post by bluexrider on 2011-11-29
> **digithal said:**
> You don't have to make a new installation of Xubuntu or Lubuntu if you want to test different environments.
To install LXDE, just type in terminal:
```
sudo apt-get install lxde
```or to install XFCE:
```
sudo apt-get install xfce4
```Then select the session you want to start from your login manager.

If you decide to do either one of these then all you have to do to change the desktop is to log out then choose which desktop you want to log into.

Caution: Installing additional desktops also adds the software to the OS. You will have a multitude of duplicate entries in your menu. Different terminal choices and different burning software. etc.

---

### Post by rng on 2011-11-29
I can't believe it is that simple. I just issue those commands, allow them to finish and reboot. And I should have a menu to choose the desktop! So I don't need to go through those links. I will try one of these commands first, say lxde.

Currently, I login straight to gnome desktop. How would I get login manager at startup?

---

### Post by bluexrider on 2011-11-29
> **rng said:**
> I can't believe it is that simple. I just issue those commands, allow them to finish and reboot. And I should have a menu to choose the desktop! So I don't need to go through those links. I will try one of these commands first, say lxde.

Currently, I login straight to gnome desktop. How would I get login manager at startup?


You DO NOT have to REBOOT Simply log out, choose the desktop from the drop-down menu and log in.

---

### Post by digithal on 2011-11-29
At the bottom of your [login screen]("http://www.linux-mag.com/s/i/articles/7740/lucid-logon.jpg") there is a Session list. Simply select LXDE and then login with your username and password.
And yes, there is no need to reboot the machine. Just logout.

---

### Post by Paddy Landau on 2011-11-29
Alternatively, you can install Xubuntu's desktop (using XFCE) or Lubuntu's desktop (using LXDE).```
sudo apt-get install xubuntu-desktop
sudo apt-get install lubuntu-desktop
```Or you can do it from Synaptic or the Ubuntu Software Centre.
Or just click the [Xubuntu desktop]("apt:xubuntu-desktop") and [Lubuntu desktop]("apt:lubuntu-desktop") links.

But...

Please remember [post=11498674]bluexrider's caution[/post].

---

### Post by rng on 2011-11-29
Thanks for your posts. Is there any difference in following 2 commands or do they have same effect any of them can be used:

sudo apt-get install lxdeor 
sudo apt-get install lubuntu-desktop

And approximately how much space would lxde and xfce4 would take on disk? 
Edit: I checked from synaptic package manager: lxde would download 78 mb and xfce4 only 27mb. But I thought lxde was supposed to be lighter?

---

### Post by Paddy Landau on 2011-11-30
> **rng said:**
> Thanks for your posts. Is there any difference in following 2 commands or do they have same effect any of them can be used:

sudo apt-get install lxde [or]
sudo apt-get install lubuntu-desktop
The latter one specifically installs the Lubuntu desktop, whereas the former does not.

> **rng said:**
> I checked from synaptic package manager: lxde would download 78 mb and xfce4 only 27mb. But I thought lxde was supposed to be lighter?
Yes, it is lighter -- when it runs. I cannot comment on what you would download; it may be that there is some overlap between XFCE and what is already installed, so some items may be already installed. But that's a guess. The important thing is that LXDE is lighter on the hardware.

Because you are installing LXDE or XFCE over Gnome, in neither case will you get the plain versions, but they should be good enough.

---

### Post by rng on 2011-11-30
> The latter one specifically installs the Lubuntu desktop, whereas the former does not.I am sorry but what is the difference between installing lxde and lubuntu-desktop? Will I not get lxde desktop if I install lxde?

I have actually installed 'lxde' and 'xfce4' meta-packages from synaptic and I got their desktops. But it changed the mounting of my fat32 partition so that I can no more execute files from that partition. Any help in this regard will also be appreciated. Thanks.

---

### Post by Paddy Landau on 2011-11-30
> **rng said:**
> I am sorry but what is the difference between installing lxde and lubuntu-desktop? Will I not get lxde desktop if I install lxde?
I'm sorry, I don't know the details. The Lubuntu desktop is LXDE, but with certain customisation. That's all I know.

> **rng said:**
> ... it changed the mounting of my fat32 partition so that I can no more execute files from that partition.
You have a FAT32 partition? That is unusual.

Please post the contents of [FONT=Fixedsys]/etc/fstab[/FONT] (between [FONT=Fixedsys][noparse]```
[/noparse][/FONT] and [FONT=Fixedsys][noparse]
```[/noparse][/FONT] to make it easy to read, please).

---

### Post by rng on 2011-11-30
There is no entry for this fat32 partition in /etc/fstab file. I used to mount it from 'Places' item on top menu bar and used to execute bash script files on that partition. Now I can open the partition but files are not executable anymore and I cannot change that because the command 'sudo chmod +x filename.sh' does not work (it finishes without any message or error notice, but does not change any file permission). Any clues why this has happened and how I can revert back to the original situation?

---

### Post by Paddy Landau on 2011-11-30
FAT32 and NTFS both do not support the level of permissions that Linux has.

By default, Linux does not permit execution of programs from FAT32 or NTFS because of that lack of control. There is a way to tell Linux to override that security restriction. If you mount the partition from /etc/fstab, you can add the *exec* option. I don't know how to override the restriction when automatically mounting using Nautilus.

---

