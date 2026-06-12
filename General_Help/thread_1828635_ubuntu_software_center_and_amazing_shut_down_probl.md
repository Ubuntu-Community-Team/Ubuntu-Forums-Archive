---
title: "ubuntu software center and amazing shut down problem."
date: 2011-08-19
forum: General Help
---

### Post by vikash_chandola on 2011-08-19
**When we install software in xubuntu using software center, where are they saved. I mean where is their location. I need their set up files so that i can install them on different ubuntu machine without using internet.**
To know what's happening in my mind read it.

Recently i am using xubuntu 11.04 and want to switch from xubuntu to ubuntu 11.04. I have installed xubuntu using wubi so i need to unistall it before i install ubuntu with wubi. But there is a problem in uninstalling. I have installed some softwares of size around ~200MB in Xubuntu using software centre. I want to save them in different part of my hard drive before uninstalling the old xubuntu. If i directly uninstall it then all softwares will be deleted and i will lost them. I want to use those softwares in ubuntu.

** ERROR WITH SHUT DOWN**
When i boot ubuntu 11.04 from USB it seems different than it is mentioned in [download page of ubuntu](http://www.ubuntu.com/download/ubuntu/download). There were 5 to 6 options try ubuntu (live run), install ubuntu, memory test etc. when i continue with try ubuntu it loads in a live system in a minute then i found that it is not looking as I found gnome 3 in some youtube videos. when i shut down it does not close itself i require to press CPU button so that it closes. All the computers at the stage where a lot of text is written on screen and at last it is wriiten system halted[4522.52] (I write numbers randomly). Does their any problem. Last error i mention is also with running xubuntu 11.04. 

I will highly thank full it you help in any of the topic.
vikash chandola.

---

### Post by CrusaderAD on 2011-08-19
Your best best is to not try messing with the current installation. Find a .deb install package for the software you want, download it and just drop it on what ever machine you want that doesn't have an internet connection. You may run into some dependency problems though, but this is probably much less head ache than what you're trying to do.

---

### Post by vikash_chandola on 2011-08-19
> **CerealCypher said:**
> Your best best is to not try messing with the current installation. Find a .deb install package for the software you want, download it and just drop it on what ever machine you want that doesn't have an internet connection. You may run into some dependency problems though, but this is probably much less head ache than what you're trying to do.

Ok do you know anything about second problem of **shut down**. 
my ubuntu 11.04 is using gnome 2.4... so i think visual effects are working fine.
**thanks for our valuable reply** in future i will download software with .rpm and .deb extension

---

### Post by oldos2er on 2011-08-19
Package files are saved in /var/cache/apt/archives

Ubuntu 11.04 uses Gnome 2.x, not Gnome 3; however Ubuntu 11.10 which will be released in a couple months will use Gnome 3.

---

### Post by wyomingsour on 2011-08-20
I have ubuntu 10.04.  Mostly it has worked great, but the last few times I have installed software using the ubuntu software center, the software has not shown up anywhere in applications and I don't know how to find or start it.

---

### Post by Basher101 on 2011-08-20
some programs are run isnide the terminal via commands specifically for those programs.

---

### Post by wyomingsour on 2011-08-21
Thanks.  How does one find out what the commands are?

---

### Post by CatKiller on 2011-08-21
/var/cache/apt/archives

The ACPI implementation of your motherboard's BIOS is buggy. There might be a setting you can tweak to make it behave better, but there probably isn't.

---

