---
title: "Removing dual boot with Mint"
date: 2012-02-14
forum: General Help
---

### Post by Shenarah on 2012-02-14
Hi

I have a PC on which Mint was installed as a dual boot option with Ubuntu. The Mint installation didn't work properly and hangs on the logon screen. How can I get rid of it and the dual boot option and revert back to Ubuntu only?

Thanks

---

### Post by forrestcupp on 2012-02-14
Well, you need to back up all of your data before you do anything. What you have to do is pretty risky.

I would create an Ubuntu Live bootable USB stick and boot to it. Make sure you don't mount any drives, and open GParted to delete your Mint partition and resize the Ubuntu partition to use that space. Pretty dangerous, so make sure you back up, and make sure you know which partitions you're dealing with.

After you've done that, you'll have to restore GRUB. [Here's a good How-to](http://www.howopensource.com/2011/08/reinstall-recover-grub-from-ubuntu-live-cd-usb/) that explains how to install a program called "boot repair" from your Live USB. It's a graphical program that repairs GRUB for you.

Or you could just reinstall Ubuntu and tell it to use the whole disk. :)

---

### Post by garvinrick4 on 2012-02-14
Post a screen shot of "gparted" here using paperclip (attachments) so as users can see
what your partition scheme looks like and can give you a answer to your Thread. Have 
added and removed many installs with out problems but as stated before me always back
up your personals first. 
If you want to make sure Ubuntu has control of grub boot into Ubuntu and:
```
sudo grub-install /dev/sda
```
```
sudo update-grub
```


that will handle any boot issues removing a different partition.

---

### Post by Shenarah on 2012-02-15
Is there a way to scrub the Mint but keep the partition for use as a srorage are in Ubuntu, then have the PC boot straight into Ubuntu without the boot menu?

---

### Post by garvinrick4 on 2012-02-15
> **Shenarah said:**
> Is there a way to scrub the Mint but keep the partition for use as a srorage are in Ubuntu, then have the PC boot straight into Ubuntu without the boot menu? Yes

Take the screenshot of gparted and post so know what to tell you to do. Is quite simple really.

---

### Post by Shenarah on 2012-02-16
Here is my screenshot.

---

### Post by forrestcupp on 2012-02-16
> **Shenarah said:**
> Here is my screenshot.

First, you need to figure out which partition is Ubuntu and which is Mint. It's either sda1 or sda6. If you open up System Monitor from Ubuntu and click the File Systems tab, whichever one is mounted as root '/' should be Ubuntu.

---

### Post by Shenarah on 2012-02-16
It says it's /sda6

---

### Post by Shenarah on 2012-02-16
/sda1 has the Mint that went wrong.

---

### Post by garvinrick4 on 2012-02-16
If it were me I would start over and do it up right use gparted to make partitions. (Back up all personal files then just copy to new /home being made.)

1. Get rid of both swaps (right click on them and delete:
Hit green apply arrow to apply command
2. right click on both sda1 and sda6 and delete.
Hit green apply arrow.
3. Make a new partition scheme all should be unallocated space
Right click on unallocated and select new. 
Make first a 10 gig partition.
Right click on unallocated again.
Make second all space but about 5 gig or so. (gparted will assign sda#'s itself)
Right click on 5 gig or so unallocated and make swap.
4. Install Ubuntu and use "something else" when installing.   (something else is like doing install manually) Not hard to do at all.
Make sda1 the 10 gig your / and format to ext4 (double click on sda1)
Make sda5 the large partition /home and ext4 format (double click on sda5)
Make sda6 the swap. (double click on sda6)
Grub on bottom should say going into sda
Now hit apply to make it happen 
5. Now you can reinstall at any time into sda1 your file system or / without having
    anything to do with your /home at all.
6. If you ever want to put in a second install you just choose home sda5 again without
    formating and can use same /home. Same thing for 3rd, 4th and so on and on.
7. You have a good looking partition scheme now.

---

### Post by forrestcupp on 2012-02-16
Just keep in mind that garvinrick4's solution means you're wiping everything out and starting over, so make sure you back up your personal files if you do that.

I don't know that you really need to go to that extreme, though. I'd probably boot into a LiveCD or USB and open GParted, or use the GParted Live CD, and modify the partitions. I'd delete sda1 and one of the swap partitions and move things around to where you can grow sda6 into the unallocated space. That way you can keep your current Ubuntu installation.

The only thing is, you might have to restore Grub after doing that. No matter what, back up all of your personal stuff.

---

### Post by garvinrick4 on 2012-02-16
Here is my partition scheme with each operating system sharing same /home in sda8
so anytime I want to do a fresh install of a operating system I do not bother the /home at
all. To install and update your packages and install your applications does not take that
long a few hours or so. I did the 5 linux installs all in an evening that is in my screenshot.
I like multiple installs which many do. Really just according to what you want to do. Making
your partitions in Live Cd using "gparted" and installing or using what you have. I prefer
this is only reason I got involved in Thread, do what you are comfortable with.
 Click on thumbnail for example of multiple install using same /home and just one swap is
all that is needed. If you want any more help just ask, enjoy your Ubuntu Linux.

---

### Post by forrestcupp on 2012-02-17
> **garvinrick4 said:**
> Here is my partition scheme with each operating system sharing same /home in sda8
so anytime I want to do a fresh install of a operating system I do not bother the /home at
all.

Wow! That's crazy. I'm a minimalist when it comes to partitions.Everyone has their preferences. I can see the point in having a separate /home partition, though. Although, you even have to pay attention to that when you do a clean install of a version upgrade and you don't necessarily want some of the system settings to carry over.

---

### Post by Shenarah on 2012-02-18
Well I ended up starting from scratch. Seemed the easier option. Thanks for all your help peeps.

---

