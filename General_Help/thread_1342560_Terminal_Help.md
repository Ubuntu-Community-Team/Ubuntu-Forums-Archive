---
title: "Terminal Help"
date: 2009-11-30
forum: General Help
---

### Post by Dizzane on 2009-11-30
Hi ummmmm, I am  very new to  (Ubunto 9.10) Linux and I just installed it onto my Laptop which is a "HP intel Centrino2" 2GB 120GB HD" with 2 Partitions Windows Vista and (Ubuntu 9.10) Linux

Okay my issue is that I cannot run anything in my Terminal and I searched the internet high and low looking for sources to solve my issue and I cannot seem to find one here is and example

> devon@devon-laptop:~$ sudo apt-get install vlc
[sudo] password for devon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package vlc
> devon@devon-laptop:~$ sudo apt-get install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager
So can anyone please help me out cause I am lost and confused at the same time?

---

### Post by yo2boy on 2009-11-30
Do you have the universe repositories enabled in Software Sources?

---

### Post by Locutus_of_Borg on 2009-11-30
sudo apt-get update

---

### Post by wesleybailey on 2009-11-30
You need to enable the universe repository, in order to download vlc.

Click Ubuntu logo button -> Ubuntu Software Control Center
Click Edit -> Software Sources
Put a check beside universe, and multiverse
and then click close

---

### Post by Dizzane on 2009-11-30
@yo2boy: Yes

@locutus_of_borg: This method did not work

@wesleybailey: Yes
[]("http://ubuntuforums.org/member.php?u=370318")

---

### Post by wesleybailey on 2009-11-30
So were you able to install vlc, once you enabled the universe repositories?

---

