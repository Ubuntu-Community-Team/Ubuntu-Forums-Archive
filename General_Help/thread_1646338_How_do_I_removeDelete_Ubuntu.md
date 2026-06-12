---
title: "How do I remove/Delete Ubuntu"
date: 2010-12-15
forum: General Help
---

### Post by RuinRoad on 2010-12-15
Hello there,

I was running windows XP and then my computer crash and blue screened.

I gave it too my friend to fix because I'm not too tech savvy, He fixed it and installed ubuntu 10.10.

I don't want Ubuntu because of school reasons and I would like to play World of Warcraft without major graphical issues (Note: I played world of warcraft before on the computer and it ran smooth on XP)

Well I have windows XP and windows 7 and I want to know how to remove Ubuntu so I can install a windows OS...

Any help would greatly help me.

Thanks...

I will provide any info you want...! :p


Info:

Ubuntu 10.10
Kernel Linux 2.6.35-22-generic
GNOME 2.32.0

---

### Post by WorMzy on 2010-12-15
Just boot a LiveCD, use gparted (System -> Administration -> Partition Manager) to delete the partitions, then reboot into the Windows installer.

---

### Post by Habeouscorpus on 2010-12-15
Just Pop in a Windows disk and boot from it. Go through the directions of installing, and choose the option to reformat and install. BACK UP ALL YOUR FILES FIRST. FOR THE LOVE OF GOD, BACK THINGS UP.

There are lots of tutorials for installing windows online. :) Sorry you weren't happy with Ubuntu... But if you install Wine, you can still run WoW!

---

### Post by RuinRoad on 2010-12-15
> **Habeouscorpus said:**
> Just Pop in a Windows disk and boot from it. Go through the directions of installing, and choose the option to reformat and install. BACK UP ALL YOUR FILES FIRST. FOR THE LOVE OF GOD, BACK THINGS UP.

There are lots of tutorials for installing windows online. :) Sorry you weren't happy with Ubuntu... But if you install Wine, you can still run WoW!
[SIZE=5]
[SIZE=4]Alright so I ran into some major error...[/SIZE][/SIZE]


take a look.

[SIZE=5]When I try to run the installation through wine I get this:[/SIZE]
[IMG]http://i.imgur.com/uzfwT.png[/IMG]
[SIZE=5]
Then I try to run it through crossover games:[/SIZE]
[IMG]http://i.imgur.com/NAFcf.png[/IMG]
[IMG]http://i.imgur.com/Az6Rg.png[/IMG]

[SIZE=6]And this is the error?![/SIZE]

[IMG]http://i.imgur.com/tq2GL.png[/IMG]

---

### Post by WorMzy on 2010-12-15
Boot from the CD, don't run it inside Ubuntu.

---

### Post by wilee-nilee on 2010-12-15
Please use the screen shot utility rather then the prtsc key, this will make it a .jpg you can attach rather then the way it looks.

If you want to remove Ubuntu we should really confirm how it was installed. So far the assumptions are a partitioned dual boot.

---

### Post by RuinRoad on 2010-12-15
> **WorMzy said:**
> Boot from the CD, don't run it inside Ubuntu.


This is a stupid question, Forgive me for this.

When I'm loading I press F12.

What Do I do from there?

---

### Post by Habeouscorpus on 2010-12-15
In other words, insert the disk. Power off the computer. Then, during start up, the screen will come up saying, "F(Whatever) for Setup" Press it quick, or you may miss it! (if you miss, just try again) Then, select BIOS settings, if available. A screen should come up asking which medium to boot from. Select your CD drive with your arrow keys and hit enter. Then, it'll say, "Press any key to boot from disk...." Press a key. From there, you will be guided through windows install.

---

### Post by WorMzy on 2010-12-15
> **RuinRoad said:**
> This is a stupid question, Forgive me for this.

When I'm loading I press F12.

What Do I do from there?

I don't know, I can't see your screen. ;)

what options does it give you?

---

### Post by RuinRoad on 2010-12-15
> **Habeouscorpus said:**
> In other words, insert the disk. Power off the computer. Then, during start up, the screen will come up saying, "F(Whatever) for Setup" Press it quick, or you may miss it! (if you miss, just try again) Then, select BIOS settings, if available. A screen should come up asking which medium to boot from. Select your CD drive with your arrow keys and hit enter. Then, it'll say, "Press any key to boot from disk...." Press a key. From there, you will be guided through windows install.


I don't have that, See I tried that already... There is no Boot from CD but I have the disk in...? . Also number 1 is Normal.


[IMG]http://imgur.com/eip10l.jpg[/IMG]



[QUOTE=branscombe_richmond]also, never use a computer again for the rest of your life.[/QUOTE]

Alright man, I am formaly Admitting that I don't not a lot about computers... And you still have to  be a ***?
Because to me I thought that I would come on a help form to ask for help...

---

### Post by Habeouscorpus on 2010-12-15
Flames on the side of your face! Lordy, people are rude. 

Number four should work!

---

### Post by RuinRoad on 2010-12-15
> **Habeouscorpus said:**
> Flames on the side of your face! Lordy, people are rude. 

Number four should work!


Heh, I tried that one; It just booted normal ubuntu... :P

Let me go try again...

---

### Post by RuinRoad on 2010-12-15
> **RuinRoad said:**
> Heh, I tried that one; It just booted normal ubuntu... :P

Let me go try again...


Still not working, It just boots ubuntu as normal!

---

### Post by The Thunder Chimp on 2010-12-15
Do you have windows already installed on the computer? If not, just wipe your drive with a CD or usb (maybe the CD thing will work with a linux cd). From there, slide in the windows disk and it should go for windows installation on its own.

(Tell me if you need to know how to wipe your linux partition)

---

### Post by Habeouscorpus on 2010-12-15
Do you actually have a windows disk in the drive?

---

### Post by izz.y on 2010-12-15
When you see the scree, change the "1" to "4", to boot from the CD. You need to load the CD, and completely bypass Ubuntu, that is why you choose the IDE CD Rom drive option. This will load the windows installer, this is an Ubuntu forum so I can't/will not tell you how to install windows, you'll have to contact the legendary Microsoft for that, other than that, during the XP installation you will be given asked which partition to install XP on, delete all the partitions, create a new partition that is the same size as the drive, and install windows to that. This will also delete Ubuntu.

---

### Post by WorMzy on 2010-12-15
As said, option four is the option you need. But you should see a prompt afterwards saying something like "Press any key to boot from CD", at which point you need to press a key, otherwise it will boot from your hard disk instead (which Ubuntu is installed on).

Of course, I assume that the Windows CD you're using is legitimate? If it is an illegal copy then it may not work as expected.

I'd also like to point out that, if you haven't deleted the partitions as I mentioned earlier, then there is a chance that the Windows installer will fail because it cannot read your harddrive; there seems to be some problems with the Windows installer and drives formatted entirely as Linux filesystems.

---

### Post by RuinRoad on 2010-12-15
Okay, Well I have the Ubuntu LiveCD or what ever it's called ( The installation USB thing) and I'm gona try to uninstall ubuntu from there... Any tips?:KS

---

### Post by The Thunder Chimp on 2010-12-15
If you've managed to boot from the USB or CD, then you want to go to System > Administration > GParted Partition Editor. From there, just unmount every partition that are from the hard drive, right-click on them and click delete. Once it's done, click apply, and it will wipe everything for you. DON'T DO THIS IF YOU HAVE ANYTHING YOU WANT TO KEEP ON YOUR DRIVE!! (such as a windows partition or something)

---

### Post by RuinRoad on 2010-12-15
> **The Thunder Chimp said:**
> If you've managed to boot from the USB or CD, then you want to go to System > Administration > GParted Partition Editor. From there, just unmount every partition that are from the hard drive, right-click on them and click delete. Once it's done, click apply, and it will wipe everything for you. DON'T DO THIS IF YOU HAVE ANYTHING YOU WANT TO KEEP ON YOUR DRIVE!! (such as a windows partition or something)


Alright so when I booted from the USB it went to the.

TRY ubuntu and the INSTALL ubuntu menu...?


Also I have nothing I want. Just world of warcraft but I can reinstall that :P...

---

### Post by alem189 on 2010-12-16
"Try" is the right option.

---

### Post by The Thunder Chimp on 2010-12-21
Yep, go for "try".

---

