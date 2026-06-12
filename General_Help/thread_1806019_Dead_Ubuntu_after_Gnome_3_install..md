---
title: "Dead Ubuntu after Gnome 3 install."
date: 2011-07-17
forum: General Help
---

### Post by emjotbin on 2011-07-17
After upgrading to 11.04 I did not like Unity. I found procedures to switch to Gnome 3 and, without reading reports about problems with it, I followed one. When it called to reboot I get good purple then blink then purple with word “… UBUNTU..” then black screen with some misaligned messages about batteries and last one about CUPS. And this screen is a dead end. 
I found advices to remove “gnome-accessibility-theme” and install standard theme. My problem is that my only system is plain Unix without network from “recovery mode”. I tried to ifconfig but I don’t know how to get WiFi to start on this Dell laptop. I remember I spend a lot of time to get right drivers for my first Ubuntu. I have no way to remember what I did to have it working.
My question is: how to switch back to Unity (and wait for fixed Gnome 3) or how to fix Gnome 3 from “recovery mode”?
(I would like to avoid install from scratch because I don’t remember what I did to install all drivers to have functional Ubuntu).

---

### Post by wildmanne39 on 2011-07-17
Hi, here is a link for fixing your problem but it may not work in my opinion the best option is to reinstall.
[http://ubuntuforums.org/showthread.php?t=1742343](http://ubuntuforums.org/showthread.php?t=1742343)

---

### Post by raja.genupula on 2011-07-17
> **wildmanne39 said:**
> Hi, here is a link for fixing your problem but it may not work in my opinion the best option is to reinstall.
[http://ubuntuforums.org/showthread.php?t=1742343](http://ubuntuforums.org/showthread.php?t=1742343)



hey wildman
what happen to gnome 3 . i think this is 2nd time .

---

### Post by emjotbin on 2011-07-17
[FONT=Times New Roman]Thanks for the good thread. I knew this one. Problem is that my only interface is “recovery mode” without network. “[COLOR=black]sudo add-apt-repository” in one of the steps in this thread requires internet access that is not available in my case.[/COLOR][/FONT]

---

### Post by wildmanne39 on 2011-07-17
> **emjotbin said:**
> [FONT=Times New Roman]Thanks for the good thread. I knew this one. Problem is that my only interface is “recovery mode” without network. “[COLOR=black]sudo add-apt-repository” in one of the steps in this thread requires internet access that is not available in my case.[/COLOR][/FONT]Hi, I hate to say it then but your best bet is to reinstall.

---

### Post by emjotbin on 2011-07-17
I fixed it and did not have to reinstall.
I wired my laptop to router with old Ethernet cable. When I boot up to Recovery Mode and selected "Drop to Root With Networking" I was on line. I selected root to avoid "Permission denied". Now I was able to install ppa-purge:
sudo apt-get install ppa-purge
next step was to removing Gnome 3:
sudo ppa-purge ppa:gnome3-team/gnome3
I saw thousand of lines of output. I made a picture of the screen when it stopped asking to confirm operation twice. After about 15 minutes the purge process was reported done. I rebooted and.... get Unity back!

---

### Post by wildmanne39 on 2011-07-17
> **emjotbin said:**
> I fixed it and did not have to reinstall.
I wired my laptop to router with old Ethernet cable. When I boot up to Recovery Mode and selected "Drop to Root With Networking" I was on line. I selected root to avoid "Permission denied". Now I was able to install ppa-purge:
sudo apt-get install ppa-purge
next step was to removing Gnome 3:
sudo ppa-purge ppa:gnome3-team/gnome3
I saw thousand of lines of output. I made a picture of the screen when it stopped asking to confirm operation twice. After about 15 minutes the purge process was reported done. I rebooted and.... get Unity back!Hi, I am glad you was able to get online and fix your problem.

---

