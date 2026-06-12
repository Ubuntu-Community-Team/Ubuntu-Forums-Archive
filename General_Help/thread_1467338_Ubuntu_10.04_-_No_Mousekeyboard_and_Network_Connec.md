---
title: "Ubuntu 10.04 - No Mouse/keyboard and Network Connection"
date: 2010-04-30
forum: General Help
---

### Post by RedNight on 2010-04-30
I've done an ubuntu's fresh install, and, once I pass the login screen, my mouse and/or my keyboard just get paralyzed. 

With an USB mouse, this happens too. To apparently solve this issue, I just unplugged it and plug it again. Weird thing.

Then, since I installed 10.04, I just cannot connect to my home network. Every time I login, it seems connected but, never reach a website. I've tried

```
sudo ifconfig eth0 down && sudo if config eth0 up
ping www.google.com
```

and then, I got an exclamation mark on network's icon.


I've tried already to upgrade from 9.10 to 10.04 and I got the same issues.

I'll give you some more infos that might be useful:

```
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 645xx (rev 51)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:09.0 Communication controller: Conexant Systems, Inc. Device 10b4 (rev 89)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)


```


Can you help me up?

Nowadays, without an internet connection, no one live, right? 

I am seriously considering to back to 9.10...

Cheers from Portugal.

---

### Post by nanog on 2010-04-30
sounds like a driver problem.
chroot in (see my sig) and post errors you see in /var/log -- specifically syslog/dmesg/Xorg.

---

### Post by cogier on 2010-04-30
I have been trying to install 10.04 on a Dell laptop that had 9.10 and the install just stopped!

I am now trying the Alternative CD and so far this is looking good. Have a look here. [http://releases.ubuntu.com/lucid/]("http://releases.ubuntu.com/lucid/")

It may help.

---

### Post by RedNight on 2010-04-30
> **nanog said:**
> sounds like a driver problem.
chroot in (see my sig) and post errors you see in /var/log -- specifically syslog/dmesg/Xorg.

Chroot in???

---

### Post by nanog on 2010-04-30
[http://ubuntuforums.org/showpost.php?p=8628383](http://ubuntuforums.org/showpost.php?p=8628383)

---

### Post by RedNight on 2010-04-30
> **nanog said:**
> [http://ubuntuforums.org/showpost.php?p=8628383](http://ubuntuforums.org/showpost.php?p=8628383)

I'll try. ;)

---

### Post by WormiS on 2010-04-30
i have the same problem, my ps/2 keyboard and mouse get paralyzed if i try to press any key...
usb mouse work fine, but is not a solution.
any fix??

---

### Post by RedNight on 2010-04-30
> **RedNight said:**
> I'll try. ;)

I couldn't chroot /media/lucid



Any suggestion?

---

### Post by RedNight on 2010-04-30
> **cogier said:**
> I have been trying to install 10.04 on a Dell laptop that had 9.10 and the install just stopped!

I am now trying the Alternative CD and so far this is looking good. Have a look here. [http://releases.ubuntu.com/lucid/]("http://releases.ubuntu.com/lucid/")

It may help.

Does it keep looking good? :D

I'll take my chances with your suggestion...

---

### Post by WormiS on 2010-04-30
> **cogier said:**
> I have been trying to install 10.04 on a Dell laptop that had 9.10 and the install just stopped!

I am now trying the Alternative CD and so far this is looking good. Have a look here. [http://releases.ubuntu.com/lucid/]("http://releases.ubuntu.com/lucid/")

It may help.

nope.... it doesnt work... :(
my mouse and keyboard get paralyzed again....

any other solution?

---

### Post by CharlesA on 2010-04-30
> **RedNight said:**
> I couldn't chroot /media/lucid



Any suggestion?

What was the error, if any?

---

### Post by TartanPhoenix on 2010-05-01
I am getting the same situation: USB mouse and PS/2 Keyboard... either one works and the other doesn't or they both freeze after the login screen.
 
Any one found a solution?

---

### Post by cogier on 2010-05-01
Earlier I said that a new install with 10.04 on a Dell Latitude D505 would not work. I tried the Alternative CD, that didn't work either. I installed 9.10, updated it and then tried to upgrade.

Each of the above fail when the installs restart the computer, there is a little bit of disc activity then a bootup coloured screen, then it just stops dead.:(

---

### Post by spiz78 on 2010-05-02
Hello,

I have the same problem with a Dell D505. No way to install Ubuntu 10.04 :(
Seems a graphic issue, but is not possible to solve it.
Ubuntu 9.10 works fine.

Any suggestion?

Thanks

Spiz

---

### Post by jagland on 2010-05-02
hi cogier,spiz78.

See here managed to get my d505 working :) - [http://ubuntuforums.org/showpost.php?p=9219366&postcount=8](http://ubuntuforums.org/showpost.php?p=9219366&postcount=8)

---

### Post by WormiS on 2010-05-02
no way to solve it.
i tred to upgrade my 9.10, install a clean 10.04 using the alternative and normal iso, update my 10.04 kernel to 2.6.34, whats nanog said about "chroot in"...
but keyboard still freezing.



my keyboard works for a small time, sometimes i can write a single word like my password and then my mouse and keyboard get stuck.
:/


p.d sorry for my bad english :D

---

### Post by Meghnaad on 2010-05-03
I was able to sort this problem out
on my DELL Inspiron Desktop (for usb k/b and mouse)
check this:

> [http://blog.ichinmay.com/2010/05/03/ubuntu-10-04-upgrade-from-9-10-usb-keyboard-mouse-problem/](http://blog.ichinmay.com/2010/05/03/ubuntu-10-04-upgrade-from-9-10-usb-keyboard-mouse-problem/)


I am not sure if this is going to work for you
Please let me know if it works (even if it doesn't)

---

### Post by RedNight on 2010-05-04
I have already discovered what was freezing my PC and network connections.

I added to Grub list "noapic" and everything gone solved. 

Let's test the 10.04!:D

---

### Post by ytsionis on 2011-08-13
The SOLUTION  is [COLOR=Lime][HERE]("http://maarten.hondelink.com/index.php/No_Keyboard/mouse_when_upgrading_from_9.04_to_10.04_%28linux_Mint_7_upto_9%29")[/COLOR]

stop wasting your time 

i upgrade  to 10.04 and facing no mouse/keyboard after some googling found the right source...i hope this work for u too...;)

---

