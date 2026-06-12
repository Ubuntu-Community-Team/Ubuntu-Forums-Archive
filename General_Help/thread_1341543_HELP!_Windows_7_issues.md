---
title: "HELP! Windows 7 issues"
date: 2009-11-29
forum: General Help
---

### Post by SlashHeist on 2009-11-29
Hey all I have a Asus U50a laptop and I tried to install Ubuntu on it.

I used the windows disk management tool and shrunk my hard drive into two partitions. Then i used Ubuntu cd to boot and install to my free space. Ubuntu worked but a few things like wireless and wired internet wouldnt work. So i decided i didnt want Ubuntu and would just stick with Windows. 

I tried getting rid of the partition that ubuntu was on but it wouldnt work. it would only boot into ubuntu. now everytime i boot i get a loading grub stage 1.5 then error 22. 

what do i do?!?!?!

i tried using the recovery cd my comp came with but it just goes through the process then when i boot i get the same error. 

any help would be much appreciated. i just want windows 7 back thats all. no ubuntu.

---

### Post by mjwilson1313 on 2009-11-29
did you try using the ubuntu live cd  to boot with to get to the ubuntu os

---

### Post by Leppie on 2009-11-29
If you can get to a recovery console with the recovery disk, run fdisk /mbr
that should recover the master boot record and erase grub.
otherwise there's boot images with fdisk for download on the net.

---

### Post by wilee-nilee on 2009-11-29
Did you restart the W7 set up to make sure it was intact before installing Ubuntu.

---

### Post by SlashHeist on 2009-11-29
> **Leppie said:**
> If you can get to a recovery console with the recovery disk, run fdisk /mbr
that should recover the master boot record and erase grub.
otherwise there's boot images with fdisk for download on the net.

Ok so I got to where you were and did fixed the mbr. 

Now I can boot into Windows. I used the recovery CD my comp came and followed the instructions. When I put the driver and utilities CD in to install all the components it says they all failed. So I have a very basic Windows 7 with jack **** on it and I can even go online cause the LAN drivers werent updated. 

Man wtf did I do? lol

If my question is unanswerable thats ok. I was just hoping there is something I could do. Damn microsoft for not giving out OS cds anymore.

---

### Post by john newbuntu on 2009-11-29
Now, assuming that you have your recovery CD in your computer, it appears that your computer seems to be looking at the hard drive first for booting instead of your CD. So you need to go into your BIOS and change the order in which devices are looked at during startup.  You need to change the BIOS to boot from CD-ROM first. To enter BIOS, you my have to press the del or F2 key as soon as your computer boots (varies from computer to computer). For more help, look at:
[http://www.hiren.info/pages/bios-boot-cdrom](http://www.hiren.info/pages/bios-boot-cdrom)
Once you get your computer to read from your recovery disk, you may have options to fix startup (such as restoring MBR etc)

---

### Post by SlashHeist on 2009-11-30
Ok so to make sure things are clear since they might not be I am just gonna recap.

I installed ubuntu on a separate partition and it worked i booted up and everything. after that though I couldnt boot into windows, so i tried fixing that but couldnt figure out how. so i thought i would just delete the ubuntu partition but grub stayed and was messing with my start up process. after tinkering around and what not i found a download for a windows 7 64bit recovery cd so i tried that. i was able to get into a system recovery command prompt. i used bootrec.exe /fixmbr and bootrec.exe /fixboot and that enabled me to get rid of grub and boot from my windows disk. 

now i have windows 7 installed again but it is bare bones. and none of my laptops drivers are installed. when i insert the drivers cd i get a install screen for all the drivers for asus and what not. when i hit start it just goes through everyone really fast and they all say fail. i believe this is the problem (duh) but i dont know how to get the drivers installed. 

Honestly after reading what I wrote I sound like a complete fool that doesn't know anything. But I am pretty decent with comps, as well don't feel bad if you can't help me. Im not even sure whats wrong or how to explain it.

---

### Post by wilee-nilee on 2009-11-30
If the computer came with W7 there should be a recovery partition. If you installed it how did you do it? Were the drivers ever installed?

---

### Post by u.b.u.n.t.u on 2009-11-30
Check this out if it helps:

1. Windows 7 re boot
Control Panel\All Control Panel Items\Administrative Tools\System Configuration\Boot

2. Windows 7 re HDD partitions
Control Panel\All Control Panel Items\Administrative Tools\Computer Management\Storage\Disk Management

---

### Post by bpalone on 2009-11-30
Did you install the drivers as Administrator?  It seems that I have read somewhere that most all programs and especially drivers have to be installed as Administrator. I don't have 7 and won't have it, but I do read about M$ stuff.

Hope this helps.

---

### Post by SlashHeist on 2009-11-30
> **u.b.u.n.t.u said:**
> Check this out if it helps:

1. Windows 7 re boot
Control Panel\All Control Panel Items\Administrative Tools\System Configuration\Boot

2. Windows 7 re HDD partitions
Control Panel\All Control Panel Items\Administrative Tools\Computer Management\Storage\Disk Management

Ok so after looking around I found the problem and got everything squared away. Windows 7 is up and running. System Preparation Tool 3.1.4 starts up every time I boot though. Asking if I want to go into System Audit mode or System Out Of The Box Experience (OOBE).

Any ideas what that is doing? Or how to turn it off?

---

### Post by u.b.u.n.t.u on 2009-11-30
> **SlashHeist said:**
> Ok so after looking around I found the problem and got everything squared away. Windows 7 is up and running. System Preparation Tool 3.1.4 starts up every time I boot though. Asking if I want to go into System Audit mode or System Out Of The Box Experience (OOBE).

Any ideas what that is doing? Or how to turn it off?

Is this helpful?

[http://support.gateway.com/s/issues/2-2437815421.shtml](http://support.gateway.com/s/issues/2-2437815421.shtml)

---

### Post by SlashHeist on 2009-11-30
> **u.b.u.n.t.u said:**
> Is this helpful?

[http://support.gateway.com/s/issues/2-2437815421.shtml](http://support.gateway.com/s/issues/2-2437815421.shtml)

Yeah. Thank you much dude. You helped a lot.

---

