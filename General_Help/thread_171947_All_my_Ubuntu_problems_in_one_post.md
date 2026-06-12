---
title: "All my Ubuntu problems in one post"
date: 2006-05-07
forum: General Help
---

### Post by Goonie on 2006-05-07
Ok here it is. I decided to summarize all my Ubuntu problems in one post. I would really appreciate if you guys can start me on my way on any of them.

1. My network card is always inactive on boot even though it shouldn't. I have to enable it manually.  This probably has something to do with the "Deconfiguring network interfaces - Fail" message during shutdown

2. I cannot get Webmin to work. When I put [https://127.0.0.1:10000](https://127.0.0.1:10000) in firefox nothing happens, the connection times out. I have no clue what's wrong there. All I've read on Webmin problems are related to login problems but at least they get a login screen. 

3. I can't ping my localhost. Pinging 127.0.0.1 times out. The hosts file has a valid entry for this ip. This problem is probably connected to problem number 2.

4. I'm trying to find a simple gui tool to set up a pptp vpn connection. I tried to get pptpconfic but the repository that was suggested on the project homepage wasn't valid. (I tried installing webmin + webmin pptp client for that same reason but see problem 2)

5. I'm running VMWare Player and set up a Win XP virtual machine but I set the "partition" too small and now it's full. I'd like to know if there is a simple way to resize the virtual drive.

6. My CD drive works funny but works fine in the WinXP virtual machine in VMWare. See this thread for more info [http://www.ubuntuforums.org/showthread.php?t=163591](http://www.ubuntuforums.org/showthread.php?t=163591)

There... that's it for now, hope to hear from you guys.

Goonie

---

### Post by Computeruser on 2006-05-07
Re: Point 5:
Are you running VMware or VMware Player? You cannot build a machine in the Player. With respect to making the XP machine larger, I don't think you can. You can add a virtual drive to the machine and use that for data storage. IIRC, someone succeeded in making the virtual machine larger, but it was difficult and risky. I have never attempted it.

---

### Post by Goonie on 2006-05-07
I'm running VMWare Player and I only need 1 GB more to let the Windows + Office run smoothly. I don't really need any space for storage since the files are all stored on a shared directory in Ubuntu. The problem  is just that the Windows is complaining about low disk space and that it needs more space to run properly. Who would have guessed that only installing the OS and a pretty stripped down version of Office would eat up 4GB :(

Oh well, I guess I can go through the setup process again and allow for 5-6GB this time.

Goonie

---

### Post by az on 2006-05-07
[QUOTE=Goonie]Ok here it is. I decided to summarize all my Ubuntu problems in one post. I would really appreciate if you guys can start me on my way on any of them.

1. My network card is always inactive on boot even though it shouldn't. I have to enable it manually.  This probably has something to do with the "Deconfiguring network interfaces - Fail" message during shutdown[/QUOTE]

What network card is it.  Post your dmesg as a txt attachment

run
dmesg
in a terminal and cut and paste....

[QUOTE=Goonie]2. I cannot get Webmin to work. When I put [https://127.0.0.1:10000](https://127.0.0.1:10000) in firefox nothing happens, the connection times out. I have no clue what's wrong there. All I've read on Webmin problems are related to login problems but at least they get a login screen. [/QUOTE]

You installed webmin from the repos?  
[https://wiki.ubuntu.com/WebminWithoutARootAccount?highlight=%28webmin%29](https://wiki.ubuntu.com/WebminWithoutARootAccount?highlight=%28webmin%29)


[QUOTE=Goonie]3. I can't ping my localhost. Pinging 127.0.0.1 times out. The hosts file has a valid entry for this ip. This problem is probably connected to problem number 2.[/QUOTE]

Post ifconfig

---

### Post by Computeruser on 2006-05-07
[QUOTE=Goonie]I'm running VMWare Player <snip>
Oh well, I guess I can go through the setup process again and allow for 5-6GB this time.
Goonie[/QUOTE]

If you check the documentation, you can set the disk up with a large limit and the disk will only get as big as it needs to. I routinely set up disks at 10 or 12 Gb to ensure I have expansion room. Please don't do all the work again and only allow another 2 Gb.

And I should check again: Any VMware Player I have used cannot create a machine. How do you create your virtual machines?

A pro pos of nothing else, do-nothing SuSE and Fedora machines are as big or bigger than XP. Thankfully, Ubuntu is nicely smaller even when all common software is installed. New features cost space, I guess.

---

### Post by Goonie on 2006-05-08
The network card is Intel 2200BG. Dmesg output is attached to this post

Regarding building virtual machines in player I followed a friends how-to. It's in icelandic but you might get the idea if you look at the code entries. There are also links in his how-to to other sites.

[http://gthb.org/vmware-player-a-ubuntu/](http://gthb.org/vmware-player-a-ubuntu/)

I'm gonna check out that webmin solution as soon as I get the chance.

Thx 
Guys

---

### Post by Computeruser on 2006-05-08
You apparently used VMware Builder which appears to be a third party product. VMware Workstation is cheap enough now that I just use it. It was one of the guys on the VMware Builder page that succeeded in enlarging a virtual disk if I remember correctly. That page, however, proves what I was trying to get at. You cannot with VMware Player alone create a Virtual Machine.

---

### Post by Goonie on 2006-05-09
Ok guys here's an update

I've given up on the idea of resizing the virtual drive, going to buy the Workstation and start over as soon as I fix my latest problem (see below)

I solved the problem with my network card not being activated on boot as well as my webmin problem. I noticed that lo wasn't up either so I did "ifconfig lo up" and there we go pinging localhost works and connecting to webmin as well. In webmin I found a networking module that listed all network devices activated on boot and webmin returned an error which made me realize there was a typo in /etc/networking/interfaces at the very beginning of the file. This typo was the cause of no interfaces loading at boot..... :$ Kinda silly, I know.

But here is my latest problem. My hard drive is full... So I bought a larger one and ghosted my drive onto the larger one. I had a dual boot setup with Win XP Pro and Ubuntu. When I put the new drive in the machine hangs before Grub loads and I see a message saying "GRUB" and a blinking cursor. I've tried various ways to write over the MBR again using a Live CD but to no avail. This is a problem I need to solve. Do you know the best way to move a dual boot system onto a larger drive without rendering Grub useless and beyond repair?

Thx
Goonie

---

### Post by BrokeBody on 2006-05-09
[QUOTE=Goonie]
6. My CD drive works funny but works fine in the WinXP virtual machine in VMWare.[/QUOTE]

Enter
```
sudo hdparm /dev/hda
sudo hdparm /dev/hdc
sudo hdparm /dev/hdd
```
and tell me what the console has listed to you.

---

### Post by Goonie on 2006-05-11
Here is the output from hdparm

```
root@goonielap:/home/goonie# hdparm /dev/hda

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 117210240, start = 0
root@goonielap:/home/goonie# hdparm /dev/hdc

/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
root@goonielap:/home/goonie#
```

---

### Post by dashnak on 2006-05-11
Seems your CD drive doesn't have DMA acceleration enabled, that makes it slow and possibly funny-behaving...
Try this:
```
sudo hdparm -d1 /dev/hdc
``` If you want to make it permanent add these lines to the end of /etc/hdparm.conf
```
/dev/hdc {
dma = on
}
``` Well, maybe it won't lead to the kind of funny behavior you described, but it is still useful...

---

### Post by BrokeBody on 2006-05-11
That's what I wanted to say. ;)

---

### Post by Goonie on 2006-05-11
thx guys

dma is now on but I can't remember where I put those cds that worked funny in ubuntu. Will try and find them and test with the new settings and let you know :)

Goonie

---

### Post by BrokeBody on 2006-05-11
Is DMA on when you restart your system?

---

### Post by Goonie on 2006-05-12
Yes. I edited hdparm.conf and dma is on. Haven't tested the drive fully to see if it still acts funny but I'll try that when I get off work.

Goonie

---

### Post by Goonie on 2006-05-12
Yes. The CD drive works great with DMA enabled. I love simple solutions like this. 

Thx guys

Goonie

---

