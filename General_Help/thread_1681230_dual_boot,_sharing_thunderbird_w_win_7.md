---
title: "dual boot, sharing thunderbird w/ win 7"
date: 2011-02-03
forum: General Help
---

### Post by georgec32 on 2011-02-03
Hi all,

I have a dual-boot system on a laptop and wanted to share firefox and thunderbird between the two OSs (Win 7 and Ubuntu 10.10) so, following a posting on the forum, I partitioned a drive & formatted it as fat32, then put my mozilla stuff on that partition.  It worked good, I share email and browser between Ubuntu and Win7, but I have two problems I cannot seem to resolve.  

1) I have to manually mount the shared drive in order for firefox or thunderbird to work in ubuntu.  WHen I try to auto-mount, either by editing fstab OR by using the mount manager, it doesn't work .. thunderbird and firefox act as if they cannot see the drive, even tho I can see it with the 'mounted' symbol next to it etc.  I can re-do the profiles in both T-bird and Ffox to point to the mounted drive and it works ONLY for that session .. as soon as I log out of Ubuntu & come back in, it no longer works even tho the partition is still clearly mounted.

2) I use the lightning calendar add-on, but in ubuntu, the calendar shows up but nothing is on it and I can't change views etc.  It works fine in windows.  If I re-install t-bird in Ubuntu WITHOUT sharing the windows profile, it works fine.  

Any ideas on how to fix either of these?

thanks in advance
george c

---

### Post by Habitual on 2011-02-03
As usual, the first Google Hit:
[http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux](http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux)

---

### Post by georgec32 on 2011-02-03
two things:

1) I DID a google search (as I said in my post, I followed instructions in a post on how to do this).  I read thru about 5-6 links on how to do this.

2) it doesn't seem to work quite right.  It works fine, except if I automount the fat32 partition ... if I do that, it stops working correctly.  If I manually mount the fat32 directory in linux, it works just fine

thanks for the reply tho .. I'll read all that stuff again & see if I'm missing something in translating it to the other way (win first, linux added)


george c

---

### Post by georgec32 on 2011-02-04
OK I found a post that solved my problem .. I had to tweak the permissions as well as auto-mounting the partition.  The solution was at:  [http://www.uluga.ubuntuforums.org/showthread.php?t=1430112](http://www.uluga.ubuntuforums.org/showthread.php?t=1430112)

My thanks to **Habitual** who took the time to respond to my original post .. 



george c

---

