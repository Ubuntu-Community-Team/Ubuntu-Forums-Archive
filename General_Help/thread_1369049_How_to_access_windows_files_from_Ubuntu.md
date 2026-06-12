---
title: "How to access windows files from Ubuntu?"
date: 2009-12-31
forum: General Help
---

### Post by sgwebb on 2009-12-31
When using the live CD, I was able to mount and access my windows HD and edit my files from Ubuntu from places>> I would see my Windows XP HD, and my USB HD. 

I have now installed Ubuntu, but can not find those files, or how to even get to them, in older versions of SUSE (I used many years ago) it used to put a direct link on the desktop, I am wondering if I can not find it because I chose the easy install option of Ubuntu to install it like a windows program..?

---

### Post by manco on 2009-12-31
Which version of Ubuntu are you running?

I believe your Windows partition should be visible under "Places"

One of the HDD's is your Ubuntu partition and the other is your Windows partition.

---

### Post by SeaJayEmm on 2009-12-31
Boot up windows, go to my computer, highlight the C: drive right click and select share.

---

### Post by kestrel1 on 2009-12-31
It should be found under places. Once you click on it it will be mounted for you.

---

### Post by ahayzen on 2009-12-31
Sometimes the Windows drives don't appear under places and you have to go to
Places > Computer > Windows Drive

Also if you install NTFS Configuration Tool (from the Ubuntu software centre). Run the program (System > Admin > NTFS Configuration tool) if you tick the boxes then the windows drive should auto mount and appear in an icon on the desktop and under places when you boot.

---

### Post by MelDJ on 2009-12-31
if you are using wubi, it will be in /host

---

### Post by Morbius1 on 2009-12-31
> I am wondering if I can not find it because I chose the easy install option of Ubuntu to install it like a windows program..?     If you mean you installed Ubuntu within windows then I think you mean Wubi. If so try looking at the following folders in Ubuntu:

/host
/media

I may have misunderstood your description.

[COLOR=Blue]Sorry, Posted at the same time [/COLOR]

---

### Post by JSeymour on 2009-12-31
I don't know if there's a point-n-drool way to do it, but the command-line way would be to bring up a partition application, such as qtparted, identify the NTFS partition (be **careful** of what buttons you push!), and manually issue the mount command from an xterm.  Say your NTFS partition is /dev/sda2 (that's where it is on my laptop), open a terminal and try:

mount /dev/sda2 /mnt

Your MS-Win filesystem should appear in /mnt

/mnt is kind of a general-purpose mount point, so if you want something more permanent, you could create a new mount-point wherever you want and then put the appropriate line in /etc/fstab

Search here or Google for "NTFS fstab entry" or the like for hints.

Jim

---

### Post by NovaWasp on 2009-12-31
How'd you install Ubuntu.
 
If you selected the "Use Entire Disk" option, those files are gone.
 
Shutdown immediately.
 
Use a live CD to run photorec
 
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
 
You will probably get some of them back.
 
Use AmoK Exif Sorter to reorganize any jpegs it finds (assuming that they still have intact Exif tags).  Use and ID3 tag organizer to fix the music.  The rest you'll have to sift through and rename yourself.
 
hope this helps.

---

### Post by sgwebb on 2009-12-31
Thanks everyone, there are a lot of good suggestions I am going to try here.. but let me first post some responses to the questions, I have gotten..


1. Version of Ubuntu = 9.10
2. How was it installed..?
I used the option to install as a windows program, I gave it 50GB of space, 
my computer now dual boots.. to either Windows XP, or Ubuntu..

---

### Post by sgwebb on 2009-12-31
OK I found it .. thanks Morbius it was in /host, I figured it had something to do with the way I installed it because it was in the places drop-down with the livecd. 

Thanks again!

---

### Post by sgwebb on 2009-12-31
Thanks also to MelDJ, who mentioned it first.. I read the posts from the bottom up.. :-)

---

