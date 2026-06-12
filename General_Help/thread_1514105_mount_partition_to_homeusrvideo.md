---
title: "mount partition to /home/usr/video"
date: 2010-06-20
forum: General Help
---

### Post by hoffmaster on 2010-06-20
Hi Linux community,

I am new to linux, after many years of windows.

I have created a 75g partition on a hard drive that I would like all videos to be accessible to all users of the computer.  I understand that I can mount to /home/**user**/video but I cant find a method to make **user** the current user that is logged on.

With that I will explain what I am trying to do.

I have built up a PC that I want to use as a place to download movies and music.  I then want to create a uPNP server to share the media over my LAN.  I vaguely understand what I am talking about and I think Vuze is the best program to meet all these needs.

Its not a huge issue because there is only a single user that will ever be using this PC but if this is possible it will help me greatly when I migrate my main PC to Ubuntu.

I am using Ubuntu 10.4 and I am not afraid to play on the command line.

---

### Post by colorlessprism on 2010-06-20
you might have more luck mounting the partition somewhere like "/mnt/media" and using symlinks at /home/<user>/video. you will have to play around with permissions to get it to all work. i use this method for my media files to avoid having to copy them over when i reinstall.

---

### Post by ajgreeny on 2010-06-20
I agree with colorlessprism that it will be easier to make links from each user to a separate partition mounted at /mnt in the root filesystem.

I do a similar thing with the home partition of my ubuntu 10.04.  I mount the ubuntu separate /home partition in /mnt of other distros, and then link the data folders of ubuntu's home to those same named data folders in the other distro's home folders.  I make sure the folder in /mnt is read/write enabled to the user logged on at any one time by using chmod.

---

### Post by hoffmaster on 2010-06-21
Wonderful!!!

---

