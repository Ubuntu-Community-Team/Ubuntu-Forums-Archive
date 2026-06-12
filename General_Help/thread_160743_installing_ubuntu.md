---
title: "installing ubuntu"
date: 2006-04-15
forum: General Help
---

### Post by bobanshirl on 2006-04-15
I am running win xp pro and I have the install disc for ubuntu.I have also created a UBCD4WIN recovery disc.What I need to know is if I put the Ubuntu disc in and install it will I lose my Win xp and if I do can I recover it with the recovery disc.In an ideal world I would like to be able to use both of the systems but am not sure how to go about it.At the moment I have the hard drive divided up C:,D:,E:,AND H: they are all NTFS and the C: is shown as Active Primary,D: & E: are shown as None Logical,and H:is shown as None Primary.I have got win xp on the E:The reason I have these different drives is that I was playing around with a partitioning program and I set up these, I suppose they are partitions,just to see what happened.The trouble is I dont really understand the technical jargon ie active,logical,primary etc if someone out there can understand all of this and explain to me in plain english then I would be forever grateful.Thanks a lot.Bob in Verwood Dorset England

---

### Post by DJ Scribblinni on 2006-04-15
Heres one quick guide to start your reading into being able to dual boot your windows and ubuntu.  [http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")
You already have a lot of partitions, 4 of them.  During the install process you'll be able to select new ways to partition the hard drive to your liking.  This guide shows his partitioning steps and what he creates during the install process.  You will have to reformat one or two of your partitions; Linux needs to be either on a ext2, or ext3 format (I'm not sure what the difference is).  And if you want to have the ability to easily share information between windows and linux, it is best to create (or reformat) a partition as fat32.  Linux doesn't have the greatest ability to write to NTFS.  

Here's a guide that helps explain the primary, logical, and extended partion labels. [ http://www.pcguide.com/ref/hdd/file/struct_Partitions.htm]("http://www.pcguide.com/ref/hdd/file/struct_Partitions.htm")


I hope that will help start you off.  Good Luck

---

### Post by Afief on 2006-04-15
sorry i don't really understand most of this old partitioning stuff either. i just don't look and hope it'll fade away somehow.

you can use both winXP and Ubuntu, and it's pretty easy.

put in the install CD, press enter on the terminal window that runs the installer(unless you have a weird computer or a laptop that needs special options.) I don't remember the exact sequence but most of it just trivial, read the text and answer the questions.
when it asks about paritioning do it manually, remove one of your NTFS partitions that you don't need(not E, it contains XP, not C because i think XP like 98 saves some stuff there, but i might be wrong.) it would also be good if you save 200 MB and create a SWAP parition(filesystem->SWAP.)

tell the system to mount your new parition(not the swap) as "/"(root). now there are much more filesystems(ext2/3, reiser, JFX,XFS....) than you used to have in xp(NTFS and FAT32) personally i used ext3, jfs and reiserFS, for the start i think normal ext3 will be good, but if you need the pc to perform tasks that are storage critical tasks(encoding DVDs to MPEG4? web server?) you might want to read some more about the different systems.

Summary
that's about all you really need: just remove one partition, make a new one, mount it as root, install on it. 

PS: it is known that ubuntu mounts windows paritions with ROOT permission when it installs, it's kinda annoying for new users, so this is something to do after you install
[http://www.ubuntuforums.org/showthread.php?t=155473](http://www.ubuntuforums.org/showthread.php?t=155473)

PPS: unlike windows linux is free, that means the devs can't pay Sony, Frauhenhaus or any other company that holds a patent. that's why they DON'T come with MP3, DivX, DVD support. it's easily solved through this page: [https://wiki.ubuntu.com/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29](https://wiki.ubuntu.com/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29)
summary of the page: After modifying your repositories(first thing explained in the link) open a terminal and type this:
sudo apt-get install  gstreamer0.8-mad gstreamer0.8-plugins  gstreamer0.8-plugins-multiverse  gstreamer0.8-ffmpeg mozilla-mplayer

this will install the basic stuff you need, you can get more details on the page i gave you(i'm just a noob myself, can't write you a script to do it all automaticly)

---

