---
title: "Installed but failes to boot up"
date: 2011-01-22
forum: General Help
---

### Post by Be'lakor Fan on 2011-01-22
Installed Ubuntu via WUBI, It said it installed and to reboot PC, Reboots fine with option for windows 7 or ubuntu, Click ubuntu and the process starts then a list starts scrolling and it stops at  [0.894739] [<FFFFFFFF8100aee0>] ? kernel_thread_helper+0x0/0x10  and does nothing, Turn laptop off by holding power button down, starts up in windows 7 x64 fine. What have I done wrong ?

Thanks in advance 

System Model:TOSHIBA Satellite Pro L510 PSLGXA-002002 - Operating System:Windows 7 Home Premium (x64) (build 7600)

---

### Post by Rubi1200 on 2011-01-22
Hi and welcome forums :)

Which version of Wubi did you try and install?

Can you boot Windows normally?

---

### Post by Be'lakor Fan on 2011-01-23
I assume it's the latest version of WUBI as I only just downloaded it. 

At start up it shows me Windows 7 and below that it shows Ubuntu, Boot into Windows 7 is smooth quick and clean, but trying to boot into Ubuntu works fine at first, screen changes color to a very deep red/maron with a little white box at the bottom of the screen that last's a few seconds before the screen goes black and there is all this scripts? on the screen and hangs at   [0.894739] [<FFFFFFFF8100aee0>] ? kernel_thread_helper+0x0/0x10

---

### Post by Rubi1200 on 2011-01-23
Two questions:

1. what graphics card do you have installed?

2. did you, by chance, click on the Skip button during installation of Wubi/Ubuntu?

---

### Post by bcbc on 2011-01-23
Here's a detailed how to install on this machine. [http://ubuntuforums.org/showthread.php?t=1612648](http://ubuntuforums.org/showthread.php?t=1612648)

It says that 10.10 is required. If you downloaded wubi from [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer) then you have 10.04.1. So you will need to get 10.10 from here [http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/)

To override startup options when installing with Wubi see here [http://ubuntuforums.org/showpost.php?p=10089820&postcount=8](http://ubuntuforums.org/showpost.php?p=10089820&postcount=8)

---

### Post by shabaaz on 2011-01-23
hi there,
i also have a very similar problem 
i have been using ubuntu 10.10 without any problems for quiet some time now.
(i have only ubuntu installed,no other os is present on the laptop hard disk)
what's happening now is-it is not booting-it says INIT PROCESS NOT FOUND
and just stays there-please help-have got lots of important data on my disk.

---

### Post by bcbc on 2011-01-23
@Shabaaz,
please create a separate thread for for your problem here [http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326) (What you can try is: when you boot hold down the SHIFT key and try a previous kernel or recovery mode.) In your new thread give as much information as you can.

---

### Post by aldee96 on 2011-01-23
Hey there, i think this is your problem. you are installing wubi in the extended partition. extended partition are not to be bootable, that's why you can choose ubuntu but unable to boot it. you should check it.

check wich partition is primary partition, if you find it. install wubi in it. and welcome to the ubuntu

---

