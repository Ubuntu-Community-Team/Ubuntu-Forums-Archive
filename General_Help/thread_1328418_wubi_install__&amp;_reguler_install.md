---
title: "wubi install  &amp; reguler install"
date: 2009-11-16
forum: General Help
---

### Post by trixman on 2009-11-16
a freind of mine just installed unbuntu via the wubi method, was wondering on the installl in windows it asked for the disk size she chose 30 gig of space does that mean all she can use is 30gig while in ubuntu.

and the wubi install on her dell desktop went great she installed 9.10


thanks

---

### Post by HappyFeet on 2009-11-16
> **trixman said:**
> does that mean all she can use is 30gig while in ubuntu.


Yes.

---

### Post by trixman on 2009-11-16
> **HappyFeet said:**
> Yes.

can you make it bigger if you want later on

---

### Post by HappyFeet on 2009-11-16
> **trixman said:**
> can you make it bigger if you want later on

If that's the case, I recommend doing a real dual boot. Performance will be much better. Let's be real here, as wubi is *OK* for trying it out, but nothing beats a real install. Just my .02

---

### Post by craig10x on 2009-11-16
I initally did a Wubi of 8.10 on my new Toshiba Laptop....once i realized how nice Linux and Ubuntu is, i waited about 2 months into 9.04 (to give them a chance to smooth most of the "bugs" out) and then did a real install...in fact, decided at that point to not even "dual boot"  but just wipe out Windows and go 100% Ubuntu ;)

Yeah...unfortunately, that is as big as you can make Wubi  (30 gb).....it's really best to use as a way of determining if you like Ubuntu and then if you do, the next step is to do either a "dual boot" install with Windows or just go 100% with Ubuntu...depending on your needs and desires....

Frankly, though...i don't miss Windows at all... :)

---

### Post by solwic on 2009-11-16
> **HappyFeet said:**
> If that's the case, I recommend doing a real dual boot. Performance will be much better. Let's be real here, as wubi is *OK* for trying it out, but nothing beats a real install. Just my .02

My .02, as well.  +1

---

### Post by running_rabbit07 on 2009-11-16
I first installed via Wubi. The very next day, I uninstalled it and ran the LiveCD and set up the real dual boot. I can't remember that one evening with Wubi, but it must have been good.

---

### Post by rahilm on 2009-11-16
> **HappyFeet said:**
> If that's the case, I recommend doing a real dual boot. Performance will be much better. Let's be real here, as wubi is *OK* for trying it out, but nothing beats a real install. Just my .02


i agree...wubii install is jut for trying out.
i used wubii when i was new to ubuntu with a mere 4GB install..then 8GB for half a month...
after that i did a real install and been using that since then...
its nice...really nice....recommended...it works faster and you can later expand your partition or even delete windows etc ec

---

### Post by trixman on 2009-11-17
> **HappyFeet said:**
> If that's the case, I recommend doing a real dual boot. Performance will be much better. Let's be real here, as wubi is *OK* for trying it out, but nothing beats a real install. Just my .02

how do you do a dual boot

---

### Post by armandh on 2009-11-17
here is where it gets tricky

the process may involve reducing your existing partition.
unless you add another drive or have unpartitioned space.

as an example my wife's vista laptop
I used vista's disk utilities to reduce the vista partition and then from the live disk install selected "largest unpartitioned space"

installed as expected including swap.

the disk's master boot record is changed to start grub [in the new partition] and it gives one a choice of the new ubuntu or the existing OS.

you may also use Ubuntu's install partition choices to modify the existing partition. here I suggest finding a tutorial.

some seriously fragmented window partitions are a problem
always back up needed stuff when making HD changes

---

### Post by trixman on 2009-11-17
> **armandh said:**
> here is where it gets tricky

the process may involve reducing your existing partition.
unless you add another drive or have unpartitioned space.

as an example my wife's vista laptop
I used vista's disk utilities to reduce the vista partition and then from the live disk install selected "largest unpartitioned space"

installed as expected including swap.

the disk's master boot record is changed to start grub [in the new partition] and it gives one a choice of the new ubuntu or the existing OS.

you may also use Ubuntu's install partition choices to modify the existing partition. here I suggest finding a tutorial.

some seriously fragmented window partitions are a problem
always back up needed stuff when making HD changes

what about a external  hard drive

---

### Post by CaKiwi on 2009-11-17
With a wubi install, you can access the rest of the disk by going to the /host partition.

---

### Post by armandh on 2009-11-18
> **trixman said:**
> what about a external  hard drive

an external HD is a good deal on a MOBO with a bios that will allow a boot from the usb first.

simply unplug your regular HD when setting up Ubuntu to avoid any mistakes.

my mini9 and 2 micro atx MOBOs will boot from an external HD when it is pluged in. 

have not tried external SATA but it would depend on the bios's ability to select the boot drive.

PS with dual boot one can access other partitions

---

### Post by trixman on 2009-11-18
> **armandh said:**
> an external HD is a good deal on a MOBO with a bios that will allow a boot from the usb first.

simply unplug your regular HD when setting up Ubuntu to avoid any mistakes.

my mini9 and 2 micro atx MOBOs will boot from an external HD when it is pluged in. 

have not tried external SATA but it would depend on the bios's ability to select the boot drive.

PS with dual boot one can access other partitions

ok thanks so if i buy a external hard drive to be used with my regular machine i cant use a usb connection to my pc to hook up the drive and then install linux on the new drive.

sorry i am new to this stuff:p

---

### Post by armandh on 2009-11-18
> **trixman said:**
> ok thanks so if i buy a external hard drive to be used with my regular machine i cant use a usb connection to my pc to hook up the drive and then install linux on the new drive.

sorry i am new to this stuff:p

if the BIOS on your computer permits booting from a usb devise

B4 you spend you may want to make a boodable memory stick to test it out.

---

### Post by fluffman86 on 2009-11-18
I *DO NOT* recommend booting off of USB.  It's really slow, and a lot can go wrong.

Here's a quick howto I just wrote for someone else with a similar question.  When you get to the partitioning part, instead of deleting a partition (as you probably only have a C drive), you'll want to edit your C drive and shrink it down.  Make sure that Uninstall that 30gb file that Wubi is on, too, under Add/Remove Programs.  I would also recommend running ccleaner on windows to free up some additional space, and then defragment as well.  It will make the whole process go quicker and smoother.

> **fluffman86 said:**
> It won't run quicker if it's the ONLY os, but it will run quicker with a full install instead of the Wubi install.  Here's what I would recommend: 

1. Uninstall Ubuntu from Programs and Settings under your Control Panel, and make sure that nothing else is stored on your D drive.  This will ERASE your D drive!

2. Download 9.10 from Ubuntu.com, and burn it to CD like you did with Jaunty.

3. Reboot your computer with the CD in the drive.  If it starts to boot into windows again, then Reboot again.  This time, look for options while your computer is booting.  On Dells, you see "Press F12 for Boot Options" and "Press F2 for BIOS".  You want to look for something like boot options so you can boot from CD, or if that's not available, then go into the BIOS and set your system to boot from CD.

4. When the Ubuntu logo comes up, press Enter to select "Try Ubuntu without any change to your computer" or something like that.

5. Make sure everything works.  Wireless probably won't work straight away, but you want to make sure you can play some of the sound in Places > Home > Examples.  If you've already been using Wubi, then this probably won't be an issue.

6. Go back to the Desktop and select Install.  Follow the prompts, and when it gets to the partitioning screen it will have a few options.  Choose "Manual"

7. In the manual partitioning screen, You will see either 2 hard drives or 2 partitions.  One will be the size of your D drive, and it should show up as being empty.  Ubuntu will call it either /dev/sdb or /dev/sda2.  Click on it, then choose "Delete.

8. Click on the freshly created Free Space, and choose Add.  This will be a primary partition, 1024 megabytes, and next to Use as select "Swap"

9. If the remaining free space is 40 GB or more, then create a new partition that's about 10 GB, this time choosing Ext4, and next to mount point choose "/".  Then Create another partition with the remaining space, again as Ext4, and Mount it to /home.

If the total size of D is LESS THAN 40 GB, just create the "/" and the swap, and home will automatically go inside of that.

10. Continue with the install, answer any of the questions, and eventually you'll be asked to reboot (after about 30 minutes to an hour of installing).  When you reboot you'll have a faster Ubuntu machine, and it will automatically boot into Ubuntu.  To boot Vista, you may need to hold down shift right after your computer powers on, and select it from the Grub menu. 

If you have any questions, just ask!

---

