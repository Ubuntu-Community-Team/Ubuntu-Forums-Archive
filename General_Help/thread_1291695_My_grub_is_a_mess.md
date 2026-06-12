---
title: "My grub is a mess"
date: 2009-10-15
forum: General Help
---

### Post by DonDodge on 2009-10-15
My grub is a mess and I want to clean it up. I have all these items but I'm unsure on how to safely get rid of the unwanted (unneeded) lines:

Ubuntu 7.10, kernel 2.6.22-14-386
Ubuntu 7.10, kernel 2.6.22-14-386 (recovery mode)
Ubuntu 7.10, kernel 2.6.22-14-generic
Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
Ubuntu 7.10, memtest86+
Other operating systems
Microsoft Windows XP Home Edition
Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/hda3)
Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/hda3)
Ubuntu 7.10, memtest86+ (on /dev/hda3)

My valid Ubuntu installation is the first line (Ubuntu 7.10, kernel 2.6.22-14-386). 
The line for the next installation (Ubuntu 7.10, kernel 2.6.22-14-generic) refers to an old and broken install.
The final installation (Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/hda3)) no longer exists.

Can I just delete the unwanted choices from the menu.lst file or do I need to comment them out?

Another thing I want to accomplish is change my default so that my computer boots directly to the "Microsoft Windows XP Home Edition" on (hd0,0) after a 3 second timeout. How do I make it boot straight to the "other" OS

Currently I have it set with a disabled timeout and must make my OS choice by "prompt".

Thank you for helping the ignorant.
Don

---

### Post by PrePenguin on 2009-10-15
> **DonDodge said:**
> My grub is a mess and I want to clean it up. I have all these items but I'm unsure on how to safely get rid of the unwanted (unneeded) lines:
 
Ubuntu 7.10, kernel 2.6.22-14-386
Ubuntu 7.10, kernel 2.6.22-14-386 (recovery mode)
Ubuntu 7.10, kernel 2.6.22-14-generic
Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
Ubuntu 7.10, memtest86+
Other operating systems
Microsoft Windows XP Home Edition
Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/hda3)
Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/hda3)
Ubuntu 7.10, memtest86+ (on /dev/hda3)
 
My valid Ubuntu installation is the first line (Ubuntu 7.10, kernel 2.6.22-14-386). 
The line for the next installation (Ubuntu 7.10, kernel 2.6.22-14-generic) refers to an old and broken install.
The final installation (Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/hda3)) no longer exists.
 
Can I just delete the unwanted choices from the menu.lst file or do I need to comment them out?
 
Another thing I want to accomplish is change my default so that my computer boots directly to the "Microsoft Windows XP Home Edition" on (hd0,0) after a 3 second timeout. How do I make it boot straight to the "other" OS
 
Currently I have it set with a disabled timeout and must make my OS choice by "prompt".
 
Thank you for helping the ignorant.
Don
   
 
 Yep just delete what u dont want in there.

---

### Post by jeremyswalker on 2009-10-15
Personally, I would comment out your unwanted entries, rather than delete them. Then, your change is easliy reversible if need be. Or you could make a backup of your menu.lst and just delete the unwanted entries.

If you got rid of all your entries except for the 1st, 2nd, and Windows, you could make Windows default after three seconds by adding:
```
default 2
timeout 3
```
somewhere toward the top of the file.

---

### Post by DonDodge on 2009-10-15
This is too weird. I ran ```
gksudo gedit /boot/grub/menu.lst
``` and commented out all the unwanted lines, saved the file, rebooted and there they were.

I did it again but this time I deleted the lines, saved the file, rebooted and all the lines are still there in the boot menu. 

When I verify the changes in /boot/grub/menu.lst, the lines are gone. I don't understand how this can happen. I should now be seeing:

```
Ubuntu 7.10, kernel 2.6.22-14-386
Ubuntu 7.10, kernel 2.6.22-14-386 (recovery mode)
Ubuntu 7.10, memtest86+
Other operating systems:
Microsoft Windows XP Home Edition

```

because that's all there is. I deleted all the other stuff.

Edit: Apparently I'm lost and my grub is running off another menu.lst file that lives somewhere else. I removed my "prompt" command and reactivated a 3 second timeout and the grub menu hasn't changed in the sightest. It still sits there, offering me a choice of all the original systems and waits for me to choose which OS I want to use.

---

### Post by DonDodge on 2009-10-15
Oh jeez, I got a mess. My computer is indeed running off a different and hidden menu.lst file. This apparently happened when I used Acronis to clone my old IDE main drive to a new 1 TB SATA earlier this year. I never got rid of the XP and Ubuntu on the IDE disk.

Even though I could edit my menu.lst file in my running Ubuntu installation (and see the changes), my grub is running off the menu.lst file that is not a part of the running Ubuntu file system.

What I did was boot to the CD so I could view the Ubuntu installations on both disks and edited the menu.lst file on /media/disk. I got the line changes to stick but it still didn't work right because of timeout and prompt. Next try I booted to CD and edited the file on media/disk-1 and changed the timeout and prompt commands. Now it does what I expect it to as far as waiting for a prompt and showing the proper operating systems.

Problem now is I don't really know which file is actually running my grub. I suppose the next thing to do is disable the IDE drive and see what happens. Dang, messing with the grub scares me bad.

---

### Post by DonDodge on 2009-10-15
Okay, I confirmed it and the mess I found is certainly not what I was expecting when I began this silly grub-cleaning project. My grub is running off menu.lst that lives on my old IDE drive. Not the menu.lst file that lives on the new SATA drive.

The only way I can get my computer to use the grub on the new SATA drive (cloned installation) is disable the IDE controller. If I delete (rm) the menu.lst file on the old IDE drive, my computer won't boot unless I disable the IDE controller.

Not so much a problem at the moment since everything works even though I'm running Ubuntu off the old IDE and XP off the new SATA but here's the rub. If I lose the physical IDE drive, which is old and beginning to show signs of failure, I'm afraid I will lose the whole computer or will have to replace all of my (4) IDE drives with SATA drives and leave the IDE controller permanently disabled.

So.... can anyone please tell me how to transfer control of this system to the menu.lst file that lives in the Ubuntu partition of the SATA drive rather than the menu.lst file that lives in the Ubuntu partition on the old IDE drive?

---

### Post by jeremyswalker on 2009-10-15
Ok, I believe the following will fix your setup. I have done this before, but it's been quite awhile. I've researched a little on the subject, as well. So far, everything I've read seems to confirm my thinking. I don't remember if you can drop to a grub shell on an installed system, so you may need to use a LiveCD. (It's not on my system, but I'm using Karmic and not the same grub as you.)

******Please ensure you have some comprehension as to what I am guiding you to do here. This will reinstall the Grub bootloader. Please read through this guide** --> [https://help.ubuntu.com/community/GrubHowto]("https://help.ubuntu.com/community/GrubHowto").********

The following assumes your SATA drive is the second hard drive, and that the Ubuntu boot partition is the first partition of that drive.
This will drop you to a grub shell.
```
sudo grub
```
In the grub shell, enter:
```
root (hd1,0)
setup (hd1)
quit
```
You will have to ensure that "(hd1,0)" is your Ubuntu boot partition.

I checked myself against the following guide: [GrubHowto]("https://help.ubuntu.com/community/GrubHowto")

---

### Post by DonDodge on 2009-10-15
Thank you for helping me jeremyswalker. I am so far over my head here it's ridiculous.

My SATA drive is actually Disk 2 in XP Disk Management and it's (hd2) /dev/sda in the /boot/grub/device.map. This makes sense as I think those are equal.

Gparted calls the IDE drive /dev/hda with the Ubuntu at
hda4 Extended
hda5 Ext
hda6 Swap
XP is at hda1

Gparted calls the SATA drive /dev/sda with Ubuntu at
sda3 Extended
sda5 Ext
sda6 Swap
XP is at sda1

In both cases, the XP partitions have the boot flag. (This info was all collected when booted to the LiveCD)

Running df  /boot from the hda1 Ubuntu installation gives me groot=(hd0,4) which seems equal to hda5

I still have a lot of studying to do but if I'm reading you correctly, at the grub shell I should enter
```
root (hd2,0)
setup (hd2)
quit
```
and this will properly reinstall my grub to the SATA drive from the IDE drive?

My friend, this some scary stuff but I'm glad I stumbled across this problem now during some routine maintenance rather than later when I swapped out a dying IDE drive and found I lost my computer.

---

### Post by jeremyswalker on 2009-10-15
"root (hd*,*)" needs to point at the Ubuntu partition where you want to maintain your menu.lst. So, it looks to me like it would be (hd2,4). Of course, this is assuming it is on drive (hd2). It seems strange to me that it would be that, though (assuming you only have two internal drives). With two drives, it seems to me that they should be called (hd0) and (hd1).

---

### Post by DonDodge on 2009-10-15
I have two internal IDE drives. Last March I added the SATA. I thought I was being really cool by using Acronis to clone my main IDE drive over to the new SATA. I thought it worked like a champ. Haha.

If this command of root(hd2,4) doesn't work as planned, is it  recoverable or am I screwed?

---

### Post by jeremyswalker on 2009-10-15
As long as you have a LiveCD, it is recoverable. Just boot from the LiveCD and try again.

---

### Post by DonDodge on 2009-10-15
Thanks! I'll probably give it a try tomorrow afternoon. I'll let you know how it goes.

---

### Post by oldfred on 2009-10-16
Back to your original question when you get it booting correctly modify menu.lst so you can make windows first just by moving it to the top above the automagic area, then you then can adjust the timeout:

Everyone always seems to put the windows stanza at the bottom below the end of the automagic area. But you can also put it above the automagic area and it will be first. This is in the middle somewhere in menu.lst

# Put static boot stanzas [COLOR=Red]before and/or[/COLOR] after AUTOMAGIC KERNEL LIST
[COLOR=DarkRed]Put windows stanza here[/COLOR]
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

---

### Post by DonDodge on 2009-10-16
I ran the grub commands and have good news and bad news. 

The good news is I didn't goof anything up.

The bad news is I achieved no results at all even though grub reported a success.

```
grub> find /boot/grub/stage1  
(hd0,4) 
(hd2,4)
grub> root (hd2,4)
grub> setup (hd2)
Checking if "/boot/grub/stage1" exists... yes 
Checking if "/boot/grub/stage2" exists... yes 
Checking if "/boot/grub/e2fs_stage1_5" exists... yes 
Running "embed /boot/grub/e2fs_stage1_5 (hd2)"...  17 sectors are embedded. succeeded 
Running "install /boot/grub/stage1 (hd2) (hd2)1+17 p
 (hd2,4)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
```

The thing is still running the Ubuntu on the IDE drive and I verified grub is using the menu.lst file on the IDE drive.
No new grub files were written into either Ubuntu installation.

I wonder what I have to do to get this to take? Maybe I should  physically disconnect (unplug) the IDE drive and try this again?

Edit: I think what I'll do is disconnect all of my IDE hard drives, boot to the LiveCD and then run the grub commands. This way there should be no confusion as to what is what and where is where. And hopefully move the SATA drive to the first drive in the system.

---

### Post by jeremyswalker on 2009-10-16
I'm really at a loss. That should have worked, if you are positive (hd2) is the SATA drive.

My only question about removing the IDE drives before installing grub is how grub will recognize the drives once you reconnect them. As in: Will it bump your SATA drive back to its previous assignment, thus screwing up the configuration?

---

### Post by DonDodge on 2009-10-16
I don't know. It seems risky but I need to figure this out. The IDE drive is giving me warning flags in the manufacturer's diagnostic program and if I don't get this sorted before it fails, I'm screwed. 

Maybe I can rearrange the master/slave config on the IDE drives and get some success that way.

---

### Post by DonDodge on 2009-10-16
Okay, I'm coming to the conclusion this just isn't gonna work right with the IDE drives in the system.

After fully fixing the grub on the SATA as a single drive installation, I get:

With the IDE drives out of the system (and a little editing of the boot command line and later in the menu.lst) I have perfect function from the SATA for both XP and Ubuntu.

Adding in the IDE drives bumps the SATA back out of hd0 position and goofs everything up. There seems to be no way to hold the SATA as hd0.

Adding the non-bootable no-OS #2 IDE (slave) drive in the system I get grub error 22.

Adding the #1 IDE (primary) drive in the system boots the old IDE Ubuntu installation no matter what boot commands I insert.

Funny thing is, the grub always calls for the XP on (hd0,0) but it always boots the install on (hd2,0)  unless I change the boot order in the bios. And no matter how I try to wrangle it, grub always boots the Ubuntu on (hd2,4). No way can I get the SATA Ubuntu to boot if the IDE is in the system

I suppose my obvious solution is live with it the way it is now unless and until I dump the IDE drives and replace them with another SATA as a secondary drive. At least I have the thing dialed in to the point where I know all I have to do is unplug the IDE drives and I'm back in business on the SATA. I just won't be able to do much in the way of productive work in Ubuntu since the only way I can even see files in the SATA Ubuntu installation is boot to the LiveCD.

The only possible solution I see beyond this to make it all compatible is format the primary IDE drive and try to kill the MBR on that drive. Something in there is ruining my party. But then I have to rebuild the booting of the SATA and try to make it work right from the third position (hd2). I'm afraid all that will get me is a dead computer if I keep the IDE drives

Man, this has been very frustrating but quite educational.

---

### Post by oldfred on 2009-10-16
I believe your version supports the change Ubuntu did to use UUID's. I know back then I had some of the same issues with booting pata & sata drives and I solved most of them by changing to use UUID.

to see your uuids in a terminal (leave terminal open so you can copy uuid)

```
blkid
```in menu.lst change the root entry

root (hdx,y)   #look at blkid for sda entry and enter uuid  as below

uuid  somelongnumber


typical entry but for 9.04, I used this back for older version also - do not copy just to show full entry.
title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        c00546bd-fa9c-4562-9785-5661da528114
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=c00546bd-fa9c-4562-9785-5661da528114 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

remember sda1 is (hd0,0), sda2 is (hd0,1) etc Grub counts from zero.

---

### Post by DonDodge on 2009-10-16
Thanks oldfred but I gave it up. I guess you could say I lost the battle but won the war. Now I have it set up so all I have to do is disconnect the IDE drives and run on the SATA as hd0 with no problems and my system is out of danger. I ordered in a new 640 GB SATA as a backup drive. Even though I still have warranty on at least one of the old IDE drives, I'm gonna dump them. I imagine the new SATA drive will fall right in place when I install it.

Not exactly the solution I was looking for but it works for me... and thanks for your help in rewriting the grub. It's much appreciated.

---

### Post by Don1500 on 2009-10-16
Drives are too cheap these days to futz with them too much. After you XFER the data you were obviously trying hard to keep, wipe that drive and see if it works. (If you wern't trying to save data you could have wiped it yesterday.)

---

### Post by DonDodge on 2009-10-16
Hi Don,

I'm not worried about losing data. I do constant image and batch backups to various media including external drives that live in a fireproof safe in my office. 

What drives me nuts is stuff that doesn't work like I think it ought to. But you're right, this stuff is too cheap to futz around with too much.

---

### Post by falconindy on 2009-10-16
The problem (as I see it) is that your BIOS is loading IDE before SATA. hd0 is seen first with GRUB and it loads, with no regard for anything else. Have you checked the boot order in the BIOS? You might also try unflagging hd0 as a bootable drive (from GParted).

---

### Post by DonDodge on 2009-10-16
Yes, the bios is definitely loading IDE before SATA but changing the boot order and even making the IDE drives non-bootable does not fix the problem. It will still load the Ubuntu on the IDE drive. The only way to make the SATA go to the hd0 position and the only way to run the SATA Ubuntu installation is physically disconnect the IDE drives or disable the IDE controller.

Edit: I'm pretty sure the weirdness with this computer is due to the fact the SATA installation was cloned from the IDE installation. Either drive by itself works just fine but you know what they say about cloning anything. It don't always work out just right

---

### Post by stinger30au on 2009-10-16
> **DonDodge said:**
> My grub is a mess and I want to clean it up. 


my little grab was a mess last night too

my youngest son is just 2 and he made a mess with his dinner, anyone would have thought he had never seen food in his life

shoved his head in the bowl like a dog and chewed and licked and wound up with food every where

hes a grub

back to your regular programming

---

### Post by DonDodge on 2009-10-23
Before I installed the new SATA backup drive, I wrote zeros to the IDE drive to wipe it. This allowed the proper menu.lst file to run the grub. XP worked just fine but Ubuntu would load and lock up. Removing the IDE drives solved that problem and everything worked. Installing the new SATA drive worked exactly as expected. No problems at all.

I also cleaned and rearranged my messy grub so now it does what I want it to do

Bottom line here is if you use Acronis TrueImage to clone a drive that contains a grub, you probably won't get the results you expect.

I thank you all for your help with this.

---

