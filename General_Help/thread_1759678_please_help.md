---
title: "please help"
date: 2011-05-16
forum: General Help
---

### Post by jayson.w on 2011-05-16
i installed ubuntu 11.04 using wubi now i want to get rid of windows how do i do this?

---

### Post by gsmanners on 2011-05-16
I'm pretty sure the only way is to back up everything you've done in Ubuntu, then just reinstall with the normal installer. Just make absolutely sure you want to do that, first.

---

### Post by seawolf167 on 2011-05-16
Follow the instructions contained in [this post ]("http://ubuntuforums.org/showthread.php?t=1519354")to migrate your wubi install to it's own dedicated partition (scroll down for the automated script).

I highly suggest backing up with [Clonezilla ]("http://www.clonezilla.org")before you get started.

---

### Post by jayson.w on 2011-05-16
thank for the info i will do that as soon as i figure out this whole partition prob im having

---

### Post by seawolf167 on 2011-05-17
What kind of partition problem?

---

### Post by jayson.w on 2011-05-18
when i looked up how to partion it says to right click on free space and create partition.....i dont have free space. i dont want windows....maybe a very lil partition of windows would be ok...

---

### Post by seawolf167 on 2011-05-18
If you want to keep your Windows partition (and [dual boot]("https://help.ubuntu.com/community/WindowsDualBoot")), you should boot into windows then use the Windows partition editor to resize that partition (right click "my computer", select "manage", then go to disk management). You'll want to shrink the partition so you have the amount of free space you want.

If you want to remove Windows entirely you can either boot off a live cd or boot into your Ubuntu install and use GParted (System -> Administration -> GParted) to delete Window's NTFS partition.

Once you have free space from either of the above steps, you can create a new partition by doing almost the exact same thing - boot off a LiveCD, fire up GParted, then resize your existing Ubuntu partition or create a new one.

Note that Wubi installs reside inside Windows as a virtual partition, you'll need to move this to it's own dedicated partition before you completely remove the Windows NTFS partition else it will be deleted along with Windows.

I highly suggest backing up before you start, I like [Clonezilla]("http://www.clonezilla.org")

---

### Post by jayson.w on 2011-05-18
ok i understand that ubuntu install with wubi is in the windows ntfs partition and i need to move it to its own partition ...my question is how do i go about doing so? also i am very thankful for all of your help thus far...most ppl wont deal with a noob like myself lol

---

### Post by jayson.w on 2011-05-18
also i see you are running 10.04...i install 11.04 is there different commands?   i dont see system anywhere

---

### Post by seawolf167 on 2011-05-18
> **jayson.w said:**
> ok i understand that ubuntu install with wubi is in the windows ntfs partition and i need to move it to its own partition ...my question is how do i go about doing so? also i am very thankful for all of your help thus far...most ppl wont deal with a noob like myself lol

Follow the instructions in the link I posted earlier for how to move wubi to it's own partition. As for creating the partition itself, use my previous post for how to resize your current partition to make free space. System is under the upper-right icon in 11.04, it is probably easier just to hit [ALT][F2] to open the run dialog box then type in "GParted" to open the program.

---

### Post by brunog on 2011-05-18
Hi seawolf167,
I am having an issue with clonezilla.
I can make the USB drive using tuxboot.
It only boots up to clonezilla in my new PC, but when I try it on my old PC (Pentium4 - where I need to make the clone) it just gives me a "boot error" and does not go further to clonezilla

Any advice?
Thanks

---

### Post by seawolf167 on 2011-05-18
> **brunog said:**
> Hi seawolf167,
I am having an issue with clonezilla.
I can make the USB drive using tuxboot.
It only boots up to clonezilla in my new PC, but when I try it on my old PC (Pentium4 - where I need to make the clone) it just gives me a "boot error" and does not go further to clonezilla

Any advice?
Thanks

Assuming you are booting off a USB image, if your old computer doesn't support usb booting or doesn't have it turned on in BIOS it won't be able to boot and you'll have to use a cd. If it is support and turned on and you get the message, try using the Clonezilla safe graphics settings. You should try a cd just to make sure it works.

If the above doesn't solve the problem please open a new thread so others can see and respond to your question.

---

### Post by jayson.w on 2011-05-19
thank you so much for your help. got it all done and am now running  great.

---

### Post by seawolf167 on 2011-05-19
Nice :) glad you got it working!

---

