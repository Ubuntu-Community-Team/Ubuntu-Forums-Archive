---
title: "Partitions question, related to Windows &lt;-&gt; Ubuntu."
date: 2010-12-03
forum: General Help
---

### Post by awkwarddev on 2010-12-03
Hallow folks, I recently want to install Ubuntu, but also keep my Windows instalation in case of anything. I have a 160 Gb HDD, so I use one disk for all my needs, I want to know if I select the current partition of 160 GB and cut from it 80 GB, does this will overwrite the whole partition and delete everything in it, crushing it into two partitions, or it will simply cut the selected 80 GB and make a new partition, saving the old partition? 

And incase it will erase the partition and crush it into two partitions that are empty, is it enough reliable to just install Ubuntu alongside the Windows instalation partition?

---

### Post by oldfred on 2010-12-03
The question is how much data do you have in your windows partition. NTFS partition need about 30% free or they start to slow down and eventually will stop. If you shrink your windows will you still have free space?

If XP you can use gparted to shrink it, If Vista or Win7 you need to use the windows tools in MMC to shrink the windows partition. Do not create any Linux partitions in windows as it does not even know about Linux..

Resize windows partition info:
[https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows](https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows)

Dual Boot Win7 & Ubuntu
[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu)

Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

---

### Post by awkwarddev on 2010-12-03
Currently my windows uses 50 GB space from the whole 152 GB HDD, which is nearly 95 GB free, and I want to cut from this partition 80 GB space to fill it with Linux instalation, am I able to do this from the Linux installer or I should follow your instructions above, and yes I'm on Windows XP.

---

### Post by oldfred on 2010-12-03
It is my understanding that you now can do it all from manual install. (You could only do limited things before). But I like to control what partitions are where & their sizes in advance. Then I use manual install just to choose which partition for / (root) & its format. 

For the amount of space for Ubuntu:
Ubuntu's standard install is just / & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended.

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

