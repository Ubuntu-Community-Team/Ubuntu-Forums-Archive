---
title: "How do you make a copy of your system?"
date: 2010-01-30
forum: General Help
---

### Post by jacatone on 2010-01-30
I'm running Ubuntu 9.10. I'd really like to make an image of my entire system in the event of a mishap. I've found from experience that anything can happen with Linux and then you're into another reinstall. Anyone know of a good program or process? Thanks.

---

### Post by tgalati4 on 2010-01-30
Put in another drive the same size or larger.

Enumerate your drives (hint:  write them down)

In a terminal:

sudo fdisk -l

Presuming that your primary boot drive is /dev/sda and the second drive you put in is /dev/sdb:

sudo cp /dev/sda /dev/sdb

It might take a while.

I prefer to just back up /home to a flash drive and make a list of changes that you make to the system.  For instance, every time you make a change to /etc configuration file, make a copy of in your /Projects/config folder.  That way your customizations get backed up as well.  You could do a backup of /etc as well, but the intent is not a system restore, but capturing your customizations to apply to a new install.

I can load Ubuntu in 15-20 minutes.  That's normally quicker than a complete image restore.

---

### Post by tom.swartz07 on 2010-01-30
> **jacatone said:**
> I'm running Ubuntu 9.10. I'd really like to make an image of my entire system in the event of a mishap. I've found from experience that anything can happen with Linux and then you're into another reinstall. Anyone know of a good program or process? Thanks.

Quite a few people here, im sure, will recommend simple backup. Its a program that you just set and forget- it takes care of everything.


The best method I could tell you is, grab a list of installed apps from synaptic- when you open synaptic package manager, you could use the menu (file-save markings) to save all of the packages you have installed. Note that it saves it to ROOT's desktop, not your own- you need to specify that. 


Other than that, just make sure that you keep that file in a safe place and back up your home folder often.


Both of them could be easily copied to a USB key- i just got a little tiny thumbnail sized drive that holds 4gb- more than enough for all of that.

If you need more space, you could always use dropbox- its an online storage and backup program- you get 2gb for free. It seamlessly backs up your data- just pop a file in the folder and its safe. Dropbox will even 'clone' files onto another computer- useful if you have a Dual-Boot setup and dont want to shuffle files around by hand.
Hit the link in my signature to try it out!


Hope this helps!

---

### Post by tom.swartz07 on 2010-01-30
> **tgalati4 said:**
> Put in another drive the same size or larger.

Enumerate your drives (hint:  write them down)

In a terminal:

sudo fdisk -l

Presuming that your primary boot drive is /dev/sda and the second drive you put in is /dev/sdb:

sudo cp /dev/sda /dev/sdb

It might take a while.


NOTE: that method might overwrite data on the target drive- use that with caution

---

### Post by kaibob on 2010-01-30
There are a number of ways to do what you want but clonezilla is probably the most popular imaging program. Don't be put off by the cluttered interface--just accept the defaults when in doubt. Clonezilla is run from a live CD and the image file is typically saved to an external hard drive. I have been using clonezilla for about a year and have found it to be very reliable.

[http://clonezilla.org/](http://clonezilla.org/)

BTW, be sure to use the Ubuntu-based version. It work's best with ext4.

---

### Post by cenzorrll on 2010-01-30
i prefer making a compressed file that i just need to uncompress if something bad happens.  the basic steps are in my signature, tried and true and you don't need any special programs (besides tar, which is installed by default by every distro i've ever seen)

---

### Post by Ordes on 2010-01-30
Remastersys...

it lets u create a liveISO of your runnig os, including all packages that u installed. You can also choose if u want to include /home or not. Which i never do. As its on a separate partition, much to big for a liveISO, and i have a separate backup for it.

In case your system goes down all u need is the system ISO anyways. Load it up. reinstall with all your packages. Copy your home and u have your system back in 10min....

---

### Post by garvinrick4 on 2010-01-30
i agree with kaibob I tried a few and I liked Clonezilla. I used a version marked Karmic
and made an image of my drive to an external. Have Windows 7/Karmic/Lucid and it
made an image of each partition. Can select to restore any or all. Like any software dealing
with your drive as long as you stay focused it worked like a charm. It is a live CD so nothing
is mounted. Price is right. Free. I do enjoy having an image much more than a back-up.
 Though I always keep my Home backed up all the time. My Bookmarks for Firefox and Chromium also. There is a setting in Synaptic to mark all your installed and backup. I have
tried quite a few styles just in case. Nice to have the Image though.

---

