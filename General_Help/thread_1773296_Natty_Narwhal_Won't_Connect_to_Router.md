---
title: "Natty Narwhal Won't Connect to Router"
date: 2011-06-01
forum: General Help
---

### Post by Alecazam3568 on 2011-06-01
I need some serious help! All day I've been trying but I can't figure it out! (I'm not so savvy with Ubuntu but I know the basics.)

I have Ubuntu 11.04 Natty and when I started it the first time it wasn't connected to the Internet. I refreshed and did the basic stuff. But it wasn't so simple. I went to Network Tools and Natty didn't recognize my router. I am NOT connected through Ethernet either. I can't do/can't afford to do an ethernet hookup. I don't want to spend my time running a cable to the floor below my CPU. 

Anyway, I have a Broadcom 4306 Network Controller.

I am currently using my Windows to post. Also, I can't get drivers from Synaptic or anything (that includes NDISwrapper). Please help! Can I use Windows drivers without downloading NDISwrapper??? I'm so confused and starting to think this is hopeless. Even worse: I don't have a disk for installing Ubuntu, I downloaded online alongside Windows with Wubi. O_O

I want to get this fixed so please help. Again, my network controller is a Broadcom 4306.

Thanks in advance! :KS

~~Alecazam

---

### Post by grahammechanical on 2011-06-01
Here is a link to the trouble shooting guide. I am sure that there is information on what to do if you cannot get an ethernet connection to the Internet.

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Regards.

---

### Post by linuxinstalledfromhdd on 2011-06-01
Interesting. 

It's too bad you simply can't take your computer down the next floor and hook it just for like a couple of minutes to their router with a hardwire short ethernet cable.  You just download ndiswrapper in synaptic package manager, install it, and bring it back up stairs.  Then you can fool with the windows drivers from the manufacture's web site. And instal it that way pretty easily. We can walk you through it if you can get it to that point. I don't know of any other way that is going to allow it to work. Go try that. Standing by.:D

---

### Post by bcbc on 2011-06-01
You can install ndiswrapper if you want.... it's a little involved...
1. Go to terminal (CTRL+ALT+t)
2. mount the desktop CD iso ( [TAB] means press the tab key )
```
sudo mount -o loop /host/ubuntu/install/.fuse[TAB] /mnt
```
(the end result will look like this):  ```
sudo mount -o loop /host/ubuntu/install/.fuse_hidden0000000400000001 /mnt
```
3. Install ndiswrapper
```
sudo dpkg -i /mnt/pool/main/n/ndiswrapper/*.deb
sudo dpkg -i /mnt/pool/main/n/ndisgtk/*.deb
```
4. Unmount and exit terminal
```
sudo umount /mnt
exit
```
5. If you're using Unity hit the Windows key, then enter "Windows Wireless Drivers" and run it. Otherwise, click on System, Administration, Windows Wireless Drivers.
6. Point it towards your windows (XP) .INF file
7. Wait a bit, and it should light up your Network manager

---

### Post by Alecazam3568 on 2011-06-02
I don't have .inf drivers. I followed your commands and most of them  worked. I now have ndiswrapper! :D but But my drivers are all .sys  extensions. Can I use .sys driver extensions?

---

### Post by bcbc on 2011-06-02
> **Alecazam3568 said:**
> I don't have .inf drivers. I followed your commands and most of them  worked. I now have ndiswrapper! :D but But my drivers are all .sys  extensions. Can I use .sys driver extensions?

You need both the .inf and the .sys in the directory. It has to match the architecture of your install e.g. 32 or 64 bit. I believe you need the XP version of the driver. You should be able to download them from somewhere.

But check out this link to setting up broadcom 43xx cards. Maybe you don't need ndiswrapper: [http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

---

### Post by Alecazam3568 on 2011-06-02
Thanks :) I figured that out like right after i typed my previous post. Thanks though. I can probably get the XP version from Microsoft for free and thanks for the thread link :D

---

### Post by bcbc on 2011-06-02
You're welcome :)
Good luck! (And post back here when you get it sorted for others that might need help; or if you run into other problems)

---

### Post by Alecazam3568 on 2011-06-02
Ok, I'll post the results of the XP driver when i get to my computer (i'm on my ipod) tomorrow night :)

---

### Post by Alecazam3568 on 2011-06-03
I can't find a driver download anywhere even on dell.com! let alone for windows XP!

---

### Post by bcbc on 2011-06-03
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access)

That link shows where to get the b43-fwcutter off the desktop CD. Mount it in the same way you did to get ndiswrapper.

You also need to download some other files from windows; if you save them in the ubuntu directory - then you can retrieve them from the /host/ubuntu/... from Wubi.

Here's another reference that might help: [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

---

### Post by Alecazam3568 on 2011-06-03
Wait, I've found the driver and by some random stupid mistake, I got the driver to install properly on Natty. I had "BCMWL6.inf.txt" and I took off the .txt extension because otherwise Ubuntu would not accept it. Accidentally turning the .inf into literally binary, I put it in NDISwrapper and the driver was installed.

Now I have one more question: What do I do now? It's still not detecting my router. Where do I look for that? 

Also I'm sorry if I'm wasting your time in any way, it's just that Ubuntu refuses to cooperate sometimes, and I'm sort of new to Linux.

---

### Post by bcbc on 2011-06-03
> **Alecazam3568 said:**
> Wait, I've found the driver and by some random stupid mistake, I got the driver to install properly on Natty. I had "BCMWL6.inf.txt" and I took off the .txt extension because otherwise Ubuntu would not accept it. Accidentally turning the .inf into literally binary, I put it in NDISwrapper and the driver was installed.

Now I have one more question: What do I do now? It's still not detecting my router. Where do I look for that? 

Also I'm sorry if I'm wasting your time in any way, it's just that Ubuntu refuses to cooperate sometimes, and I'm sort of new to Linux.

On the one computer that I used ndiswrapper, I found that it didn't support wpa (only wep), but I could still see it. so probably there is some setup problem.

Follow this ndiswrapper troubleshooting guide to make sure it's setup correctly: [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

---

### Post by Alecazam3568 on 2011-06-04
My key is a WEP so no problem there... i may be looking in the wrong place for my router. Where should I look?System>Administration>Network Tools. Is that right? I'm used to Windows where there's just a list of connections to choose from.

EDIT: My mistake! I have the driver installed, the hardware is accepted, the software is accepted. But it says I am missing the firmware! Where do I get that?

---

### Post by bcbc on 2011-06-05
> **Alecazam3568 said:**
> My key is a WEP so no problem there... i may be looking in the wrong place for my router. Where should I look?System>Administration>Network Tools. Is that right? I'm used to Windows where there's just a list of connections to choose from.

EDIT: My mistake! I have the driver installed, the hardware is accepted, the software is accepted. But it says I am missing the firmware! Where do I get that?

What's the output from "ndiswrapper -l"? I don't think it makes sense to update the firmware on a working product. It's a good idea to post all the output you are getting to give an idea of what you've tried and what the exceptions are.

You might also have better luck in the networking & wireless subforum for expertise in this area. You can click on "Report abuse" and ask a forum moderator to move it for you.

---

