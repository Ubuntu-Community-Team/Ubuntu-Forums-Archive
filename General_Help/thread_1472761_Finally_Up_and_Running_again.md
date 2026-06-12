---
title: "Finally Up and Running again"
date: 2010-05-04
forum: General Help
---

### Post by grnorris on 2010-05-04
Usually I don't have much issue when it comes to updating things with Ubuntu but, this Upgrade to 10.04 really got me.  First I realized that due to intermediate Internet connection I'd have to install via CD.  This was of course no biggie since I wanted to have a copy of the disk anyway but, little did I realize that in order to upgrade you need to use the alternate CD (a little better documentation would've been nice).  So, I tried installing via the main 64 bit CD and what I ended up with was a partially upgraded system (not good).  Additionally this partial update killed my wireless card (the only way I can connect 99.9999999999% of the time-no exaggeration).  That too wasn't too much of a problem since I could just reboot into windows (7) and download the CD from there, and I did and I installed completely off-line.  The problem is that when grub 2 came up I wasn't quite sure on the configuration  so I followed it's advice and installed everywhere (or at least to all my local partitions).  Again, a bad idea for now I couldn't load windows and my wireless internet was screwed because the Upgraded Ubuntu doesn't support Atheros cards (which really got me because I simply loved 9.1 which was the first I tried that did have support, 8.1 did not).  So now I was completely SOL until just a few moments ago, here's what I did (or at least what I did that I think actually solved the problem instead of just making worse):

First off I needed internet so I got my friend Jose to use his computer as an intermediary between mine and the internet.

Second I needed to fix Windows so I followed a link and found that I need to do this:

#sudo apt-get install testdisk#
#sudo testdisk /dev/sda#

(Somewhere below I had to choose advanced)
proceed
Intel
select windows partition /dev/sda2     NOTE:  It was actually sda1, the win7 loader
choose boot
BackupBS
Y to confirm

Note:  I actually did a hell of a lot more than that because I followed at least 20 different solutions but, this is the one that actually worked, also I'm afraid I don't have the link for that solution anymore-it was on another computer.

So the next thing I had to fix was my wireless.  By this point I had connected to Jose's computer so I was able to just follow this:

[http://www.mail-archive.com/fedora-list@redhat.com/msg59546.html](http://www.mail-archive.com/fedora-list@redhat.com/msg59546.html)

It's a little confusing to find the appropriate download link but once you do just follow the instructions (remembering to reboot afterward).  Also you might need to delete your wireless configuration and create a new one (via the Graphical User Interface).

So, my next step is when I actually have enough time on the net (probably tomorrow) to download all the updates for programs that became unusable during the upgrade.

---

### Post by grnorris on 2010-05-06
Thought I'd update this thread (I can see a few people have read it and I am linking to it so I'm hoping this has proved useful to someone).

I just finished installing all the apps that were deleted (here's how):

open synaptic, select 'Status', select 'Not installed (residual config)'  find the apps you know you want (some may be obsolete) and just reinstall them-Internet required).

I was also having issues with my notification area the thread I used to fix it (or at least this seems to have worked) is below:
[http://ubuntuforums.org/showthread.php?p=9249849#post9249849](http://ubuntuforums.org/showthread.php?p=9249849#post9249849)

---

