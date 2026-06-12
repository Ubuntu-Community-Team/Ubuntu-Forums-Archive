---
title: "errno 5 input/output error when trying to install ubuntu 10.04"
date: 2010-05-02
forum: General Help
---

### Post by crumpetrules on 2010-05-02
The title is pretty self explanatory, I was just wondering how to overcome this error, if I can...

---

### Post by 3rdalbum on 2010-05-02
Input/Output error means that one of the discs/disks being used is damaged.

When you put in the CD and it shows you the screen with a little picture of a keyboard and a cutout person at the bottom, hit a key on your keyboard. At the menu that appears, use the "Check CD for defects" option.

If this checks out okay, then your hard disk might have bad blocks. You can run a live session from the Ubuntu CD and use the System > Administration > Disk Utility program to test your hard disk.

If the CD is damaged, then try burning it again at a slower speed, such as 8x. You should also try making sure that you downloaded the ISO fully, by checking the MD5sum of the ISO file (there are various HOWTOs on the web, I don't use Windows so I can't help you check it on Windows).

If the hard disk is damaged then there's not much you can do except replace it.

---

### Post by ChrisG_UK on 2010-05-02
I hit the same problem with Ubuntu 10.04. Tried all the solutions, many times, no luck. This seems to affect so many people, there must be a bug here. 

Xubuntu 10.04 installed first time, I think that vindicates my hardware.

It's also difficult to have confidence in an installer that just cr*ps out with "errno 5". Frankly, it's a bit amateurish. At least if it told us the filename, and whether it was reading or writing it, we would have something to go on instead of having to try a whole bunch of random solutions.

No need to reply, I'll stick with Xubuntu for now.

---

### Post by rnerwein on 2010-05-02
hi
on my sons box the same behavior (on my box with the same CD no problem )
his drive is: ATAPI / TSSTcorp.
 MD5sum is ok.
i burned a new CD - same behavior. but after some tries it works.
his box is equiped with an intel i3 cpu and have 8GB mem.

ciao

---

### Post by n.l.o on 2010-05-02
+1 here on a brand new ThinkPad T410, with 7200 disk.

stops at 23% and Errno 5.
will try above...

---

### Post by dino99 on 2010-05-02
less problem with usb stick if you can boot with (unetbootin)

---

### Post by n.l.o on 2010-05-03
I guess my problem was using my mobile broadband connection to download the iso. the MD5sum was not correct, twice...

Anyway, got to work, downloaded et voila, works like a charm.

Thank you for the help!

---

### Post by csw840915 on 2010-05-07
Hi there, I read through the posts and got to the last part that you say you fixed your problem but you say et,, what does et mean?? What did you do to fix your md5 check. Thanks.

---

### Post by n.l.o on 2010-05-09
Hi,

I mean that I got to my workplace, that is another network/internet connection which is a bit more stable/reliable than my mobile broadband connection.

I just downloaded it as I did before, and it worked.
The MD5sum was correct.

Good Luck!

Cheers

---

### Post by azeezp on 2010-06-10
Still same problem with 10.04. Tried in two PCs. Only difference is the percentage at which this error appears is different....
No luck so far.. Looks like a serious bug..

---

### Post by n.l.o on 2010-06-11
> **azeezp said:**
> Still same problem with 10.04. Tried in two PCs. Only difference is the percentage at which this error appears is different....
No luck so far.. Looks like a serious bug..

Did you check your md5sums before burning cd/usb?
If not, check that as a first step.

Cheers

EDIT:
The second step would be to check the cd/usb for defects at the liveCD boot menu, there you choose 'Check disc for defects'. (info, see: [https://help.ubuntu.com/community/BootOptions]("https://help.ubuntu.com/community/BootOptions") )

---

### Post by azeezp on 2010-06-18
Hi all,
SOLVED..
After 2 weeks of research, trying to install in 4 PCs, and after wasting 4 CDs burning again and again, this is how i solved the problem: 

1. Downloaded 10.04 iso once again
2. downloaded "Universal USB Installer" from [http://www.pendrivelinux.com](http://www.pendrivelinux.com)
3. created a usb bootable disk in my pen drive
4. installed ubuntu from the USB 

and lo! the beauty of ubuntu 10.04 is back to my PC.

I dont know which one solved- Re downloading or usb booting. That experiment next week...

Cheers

---

### Post by azeezp on 2010-07-03
I downloaded new ISO image, and it is working when burnt to CD.
So possible problem was in the first iso image.

---

