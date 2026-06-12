---
title: "remastering a system?"
date: 2011-12-29
forum: General Help
---

### Post by zero2xiii on 2011-12-29
Hay all,

First off, I have no idea where to post this question. So moderators, please move the thread if its in the wrong section.

Now off to the questioning:
I have installed a ubuntu 11.04 inside a virtual machine to create a new live DVD from that includes some software for people who want to try ubuntu but does not have the internet to install the packages and stuff to get a working ubuntu system.

I am using relinux for the remastering. Now there are a few questions.

First off:
I want to include some "How to" videos for the distro. For example setting up the email client and the basic workings of the system etc etc. Where can this be placed and linked so that it will apear on the live desktop (and if possible on the installed desktop aswell) like the "example content"?. I want to place it in /etc/skel but I am afraid it will be duplicated everytime a new user is created on the system.

Secondly:
The current ISO file is about 1.6gig, after adding the videos is will increase to well over 2gig. (maybe even over 3 gig). Will this impact the performance of the system, due to the squashfs being so huge?

I will add more questions as I go along, but those are the 2 biggest ones at the moment.

Thanks in advance

---

### Post by BC59 on 2011-12-29
I use Remastersys for things like that. And it's copying everything you have on the System. So if you have a folder with videos on the desktop, the new system installed, will have the same exactly folder on desktop.

---

### Post by zero2xiii on 2011-12-30
Hay,

I dont find remastersys in the repros and according to net sources it is discontinued. However it seems that relinux is just a frontend for it.

Now I am having difficulties generating the ISO file. It generates the filessystem.squashfs and the md5 sum. But generating the ISO file fails with no errors.

How do you remaster your system for distrobution, and where do you get remastersys?

Cherz

---

### Post by BC59 on 2011-12-30
Links to install and how to Remastersys:
[http://www.remastersys.com/repository/ubuntu-testing/](http://www.remastersys.com/repository/ubuntu-testing/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys) (out of date)

---

### Post by zero2xiii on 2011-12-30
Hay,

I have fiewed those in my research. And as stated earlier. Relinux is just a front for it. I found my initial problem (after extensive diging in the script and MAN pages of all the programs used.) I found that my volume name was more than 32chars, not trigering an error, just exiting. However, now when I boot the ISO file in a vmware pc, it goes to busybox and gives error:

> (initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: No such device
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

What causes this error? The ISO file is 1.2gig, and the md5 sum matches on all steps of the generation with the expected md5.

---

### Post by zero2xiii on 2011-12-30
After "fullclean"ing the relinux setup. It compiled and ran successfully.

Still want to know where I can place the videos so they dont copy  themselfs everytime a new user is made?

Thanks

---

### Post by Derek Karpinski on 2011-12-30
Why don't you put the videos in /usr/share/doc or something like that, then symlink to the desktop for each new user.

---

### Post by zero2xiii on 2011-12-31
> **Derek Karpinski said:**
> Why don't you put the videos in /usr/share/doc or something like that, then symlink to the desktop for each new user.

Yea that might work.

If I create /etc/skel/Desktop and put a symlink there, will it appear on the desktop of every new user created? Aswell as the Live user?

Thanks

---

### Post by Derek Karpinski on 2011-12-31
> **zero2xiii said:**
> Yea that might work.

If I create /etc/skel/Desktop and put a symlink there, will it appear on the desktop of every new user created? Aswell as the Live user?

Thanks

Better than creating /etc/skel/Desktop, look at how Ubuntu creates that stupid Examples folder on each new users desktop.

They create an 'examples.desktop' file in /etc/skel.  Inside that .desktop file is a link to /usr/share/example-content

---

