---
title: "GRUB can't write to MBR?"
date: 2011-09-24
forum: General Help
---

### Post by xioSlayer on 2011-09-24
Trying to dual boot windows 7 and Ubuntu Server.

windows 7 was already installed.

I install ubuntu and resize the partition, and its all working fine until I get most of the way through the install. Then it tries to install GRUB and says

```
unable to install GRUB, fatal error.
```

Then the system won't boot windows or linux...
[B]
What can I do to fix this?[/B]




i tried to follow [this guide]("http://ailoo.net/2008/07/reinstall-grub-using-a-linux-live-cd/"), but when I go to install GRUB, it says ERROR: cannot write to /dev/sda

---

### Post by garvinrick4 on 2011-09-24
Get your Windows dvd and see if windows bootloader will install in the mbr of your drive. I doubt it but give it a try. 
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 

Just to check if any bootloader will go in the mbr or your drive.
Or if running chkdsk will look at the first sectors I do not know as to repair.
Anyway that is where to start, if grub2 will not install, will not install, look for
other avenues to repair those first sectors of your drive, if possible.

---

### Post by Blasphemist on 2011-09-24
This may help. How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 11.10) [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Leppie on 2011-09-24
try the [Super Grub2 disk]("http://www.supergrubdisk.org/super-grub2-disk/")

---

### Post by xioSlayer on 2011-09-24
Thank you.  I will try these solutions.



> **garvinrick4 said:**
> Get your Windows dvd and see if windows bootloader will install in the mbr of your drive. I doubt it but give it a try. 
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 

Just to check if any bootloader will go in the mbr or your drive.
Or if running chkdsk will look at the first sectors I do not know as to repair.
Anyway that is where to start, if grub2 will not install, will not install, look for
other avenues to repair those first sectors of your drive, if possible.

What would it mean if windows wouldn't write to the MBR either?  Since windows was functioning doesn't that mean it was capable of writing to it?  It is a 10 year  old drive... ](*,)

I ran chkdisk on it not too long ago and it didn't report any errors.

---

### Post by garvinrick4 on 2011-09-24
> What would it mean if windows wouldn't write to the MBR either?
Grub is placed in the mbr (master boot record) of the drive which is in the first sectors
of the drive. I am just wondering if gone bad. So seeing if able to put Windows grub back in.

---

### Post by xioSlayer on 2011-09-25
> **garvinrick4 said:**
> Grub is placed in the mbr (master boot record) of the drive which is in the first sectors
of the drive. I am just wondering if gone bad. So seeing if able to put Windows grub back in.

Using this I was able to make windows boot again.

```

bootrec.exe /fixboot
bootrec.exe /fixmbr

```

So that means it succesfully wrote to the MBR?   i'm going to try to install ubuntu server  then I will run these commands from ubuntu live CD:

```
First you need to find out what your drives are called. You can do this by going to a terminal and typing:

sudo fdisk -l

From that you need to find the device name of your Ubuntu drive, something like &#8220;/dev/sda5&#8243;.
So, still in the terminal, type:


sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5

And then, to reinstall the grub:

sudo grub-install --root-directory=/media/sda5 /dev/sda

Push enter and you&#8217;re done! Of course you need to replace &#8220;/dev/sda5&#8243; and &#8220;/dev/sda&#8221; with what you found in the fdisk output.
```

---

### Post by mcduck on 2011-09-25
You should also check your BIOS settings in case boot sector virus protection is enabled... That option prevents any changes in MBR, so you'll need to disable it when installing a new OS.

---

### Post by xioSlayer on 2011-09-25
> **mcduck said:**
> You should also check your BIOS settings in case boot sector virus protection is enabled... That option prevents any changes in MBR, so you'll need to disable it when installing a new OS.

its a xfx 650i ultra motherboard, and I can't find any options similar to that.   However, this exact system was able to install grub with a different motherboard...

any other things with the motherboard that I can check?

---

### Post by pkg9991 on 2011-09-25
from the recovery mode of Ubuntu the Grub can be fixed as well

---

### Post by garvinrick4 on 2011-09-25
@xioslayer
 Sunday morning here and been out of House and just got back online did all work out?

---

### Post by xioSlayer on 2011-09-26
> **garvinrick4 said:**
> @xioslayer
 Sunday morning here and been out of House and just got back online did all work out?


No this is like the 20th time i've installed windows 7/ubuntu server :[

I keep trying different solutions from what i find on the net, such as disconnecting all the drives except the one I'm trying to dual boot on.  Still not working.  I even put the other motherboard back in since i was able to install grub with it on this exact system just a week ago.

So as long as my HDD didn't break in the last week, and chkdisk passes fine, this exact system should be capable and I have no idea whats stopping it.  

I was certain that when I put in the other motherboard that it would be bound to work, but I was wrong.

---

### Post by garvinrick4 on 2011-09-26
If you run 
```
sudo fdisk -l
```Lower case L

It will give you a list of drives and their partitions.
Drive sda with its partitions
Drive sdb with its partitions
Drive sdc with its partitions
And so on and on.
All you have to do at install is place grub in the corresponding drive in which you install
your Ubuntu.
You install Ubuntu on a partition in sda you install grub on sda.
You install Ubuntu on a partition in sdb you install grub on sdb
The grub is installed in that particular drives mbr (master boot record) (first few sectors or drive)
and it looks for the boot files in the install of Ubuntu and boots. Done as simple as that.

Every type of installer always asks you where you want to install grub!!

Then when you get into UBuntu you:
```
sudo update-grub
```That will initiate a package called "os-prober" to go out and find other operating systems
and put them in grub as a menu entry as to boot from.

Windows grub only boots Windows does not have a "os-prober" to go out and find other operating systems as to boot them.

---

### Post by Blasphemist on 2011-09-26
So lets try something new. The boot-repair cd, or boot-repair installed on the live cd, will produce a boot info summary with lots of good information. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

There must be something odd going on and this information should let us see what it is.

---

### Post by Blasphemist on 2011-09-26
Didn't see the previous post. That information may be enough. If gavinricks process doesn't fix it, go for boot-repair.

---

### Post by xioSlayer on 2011-09-26
Ok, oddly it wouldn't work with a single SATA drive.  Then i tried the two SATA drives in opposite order.  This time the grub passed install.   Then I restarted the system and windows booted up...

so I changed the HDD boot device priority to the storage drive (not the OS drive), and it let me into GRUB.

And now it "gave up waiting for root device." and suggests changing rootdelay.

Then takes me to a (initramfs) prompt.

Why would grub have installed on the storage drive?  shouldn't it automatically be on the OS drive?  It doesn't give me an option to choose during install.  (ubuntu 11.04 server).

---

### Post by garvinrick4 on 2011-09-26
```
sudo fdisk -l
```Lower case L
Find your ubuntu install.
If it say sda5, this is what I will use, [COLOR=Red]use your own[/COLOR].
In a terminal one at a time.
```
sudo mount /dev/[COLOR=Red]sda5 [/COLOR] /mnt
sudo grub-install --root-directory=/mnt /dev/[COLOR=Red]sda[/COLOR]
sudo umount /mnt
sudo reboot
Boot into ubuntu
```sudo update-grub
To put windows in as a menu entry.
Notick in grub-install I put it in sda if your Ubuntu install is on a partitionin sdb drive in output of fdisk -l then you would change that to sdb.
```
sudo mount /dev/[COLOR=Red]sdb5[/COLOR] /mnt
sudo grub-install --root-directory=/mnt /dev/[COLOR=Red]sdb[/COLOR]
sudo umount /mnt
sudo reboot
```grub=bootloader (if at install you see where do you want to put  bootloader that is grub.) All installers ask where do you want it  placed.

---

### Post by xioSlayer on 2011-09-26
> **garvinrick4 said:**
> ```
sudo fdisk -l
```Lower case L
Find your ubuntu install.
If it say sda5, this is what I will use, [COLOR=Red]use your own[/COLOR].
In a terminal one at a time.
```
sudo mount /dev/[COLOR=Red]sda5 [/COLOR] /mnt
sudo grub-install --root-directory=/mnt /dev/[COLOR=Red]sda[/COLOR]
sudo umount /mnt
sudo reboot
Boot into ubuntu
```sudo update-grub
To put windows in as a menu entry.
Notick in grub-install I put it in sda if your Ubuntu install is on a partitionin sdb drive in output of fdisk -l then you would change that to sdb.
```
sudo mount /dev/[COLOR=Red]sdb5[/COLOR] /mnt
sudo grub-install --root-directory=/mnt /dev/[COLOR=Red]sdb[/COLOR]
sudo umount /mnt
sudo reboot
```grub=bootloader (if at install you see where do you want to put  bootloader that is grub.) All installers ask where do you want it  placed.

Ok i will try these again.  When it asks about installing GRUB it says Yes or No then installs it on its own.  I can't select where to install it as far as i can see.

---

### Post by xioSlayer on 2011-09-27
I noticed something strange.

Using Super GRUB 2, I cannot boot into linux... I get status: {drdy error}
error: {UNC}
configured for UDMA/133

Could this have something to do with it?  

[http://ubuntuforums.org/archive/index.php/t-1034762.html]("http://ubuntuforums.org/archive/index.php/t-1034762.html")

At this link this person has the exact same error and they fixed it with a command part way down the page.  Where exactly would I enter that command?

---

### Post by garvinrick4 on 2011-09-27
> **xioSlayer said:**
> I noticed something strange.

Using Super GRUB 2, I cannot boot into linux... I get status: {drdy error}
error: {UNC}
configured for UDMA/133

Could this have something to do with it?  

[http://ubuntuforums.org/archive/index.php/t-1034762.html](http://ubuntuforums.org/archive/index.php/t-1034762.html)

At this link this person has the exact same error and they fixed it with a command part way down the page.  Where exactly would I enter that command?
I have never used Super grub2 and so do not have any practical experience to go with so I will bump this up to the start of Forum for you as to see if you can find a user with Super Grub2 experience.

---

### Post by dFlyer on 2011-09-27
Just a question. Why dual boot windows (what ever version) and a server version of linux. A server should be on it's on computer.

---

### Post by xioSlayer on 2011-09-27
> **dFlyer said:**
> Just a question. Why dual boot windows (what ever version) and a server version of linux. A server should be on it's on computer.

I wouldn't mind Ubuntu non-server but it has the same issue :[

Its just a spare desktop PC I have that i'd like to install linux on.  Server version seemed appropriate for reduced overhead because I also run a game server off of the pc from time to time.

This problem isn't isolated to the boot issues I suppose, since using the Super GRUB 2 disk didn't allow me to boot into linux even though it detected it as a choice.  It just threw those errors i mentioned and brought me to the "(initramfs)" prompt.
[B]
EDIT: It would appear that my primary hard drive was bad, and I'm trying the install again on the storage drive.[/B]

---

