---
title: "questions about installing ubuntu"
date: 2011-02-27
forum: General Help
---

### Post by soraxd on 2011-02-27
right now i have ubuntu installed inside of my windows 7, i gave it a 30 gb allowance. i like ubuntu so much i want to make it my main os, and have windows 7 as my secondary. what my plan was, was to install a fresh version of windows 7, install ubuntu again inside windows 7, and try and use easyBCD to make ubuntu my main os. but now im wondering, ext4 is faster right? so i should actually make a partition, and install the two OS separably, right? or doesnt ext4 make a difference? also will i be able to share files thru the two os? or will i have to add my pictures ect to both os to view them? how should i go about doing this, thanks!

---

### Post by Smart Viking on 2011-02-27
There are very many advantages to installing ubuntu seperately, I recommend that you do that. ext does make a difference.

---

### Post by soraxd on 2011-02-27
if i were going to do that, i would install windows, then use a program like paragon partition manager to make a large partition formatted to ext4, and install ubuntu on it. 
will i be able to share files between the two os?

---

### Post by oldfred on 2011-02-27
HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Even the desiger of wubi expects you to go to separate partitions.
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

Running one system inside another's is not the most reliable way. If it fine for testing, but if you really want to use it a lot then it is time to convert. 

Once you have copied your data, you should be be able to uninstall from windows.

Shrink windows using windows MMC, but do not create additional partitions.

Use gparted to create partitions for Ubuntu.

Shared NTFS partition 
[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Some examples of installs and issues:
Issues on dual boot in same drive:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!
Installs:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Ok, I gave you too much to absorb in one post. Please ask if you have any questions.

---

### Post by wiggly81 on 2011-02-27
Windows will NOT see the ext3/4 partition used by Ubuntu unless u install 3rd party software, however Ubuntu will see and have access to windows partition

---

### Post by soraxd on 2011-02-27
alright wow, that IS alot to take in.. so everyone is in agreeance  ext4 is the fastest way to go right? wouldnt i have to install windows first if i want the linux partition to be ext4? i want the option at start up to be unbuntu tho, where it says 'select an OS or else the first OS will start up in 5 seconds', i want the first one to be unbutu, can i set that later with easyBCD? or another program?

---

### Post by helosk on 2011-02-27
so I'm tremendously excited to install Ubuntu on my PC - very tired of having to hunt for programs - buying them and having them not work...

that being said - I'm having a lot of trouble installing Ubuntu on my system.

I keep getting the error msg "there is no disk in the drive. Please insert a disk into drive /device/harddisk5/dr5."

I have no idea what this means...

any help?

---

### Post by Mark Phelps on 2011-02-28
> **helosk said:**
> so I'm tremendously excited to install Ubuntu on my PC - very tired of having to hunt for programs - buying them and having them not work...

Please don't hijack this thread with your problems.  The op is not done with this thread yet, and trying to keep responses to theme separate from responses to you is only going to get confusing.

Please open your own thread to deal with your problems.

Thanks

---

### Post by Mark Phelps on 2011-02-28
> **soraxd said:**
> alright wow, that IS alot to take in.. so everyone is in agreeance  ext4 is the fastest way to go right? 
It's not just a matter of speed. While Ext4 is likely to be faster, I doubt you would really see any speed difference.
> wouldnt i have to install windows first if i want the linux partition to be ext4?
You don't HAVE to install Windows first, but it's generally better that way because Linux will detect Windows and not the other way around.
> i want the option at start up to be unbuntu tho, where it says 'select an OS or else the first OS will start up in 5 seconds', i want the first one to be unbutu, can i set that later with easyBCD? or another program?
Your questions on using EasyBCD are best directed to the EasyBCD support forum at NeoSmart Technologies.  Folks around here will most generally tell you NOT to use EasyBCD but to use GRUB2 instead.

---

