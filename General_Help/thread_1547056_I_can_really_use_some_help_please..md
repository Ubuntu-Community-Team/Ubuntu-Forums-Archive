---
title: "I can really use some help please."
date: 2010-08-06
forum: General Help
---

### Post by ScottoMacD on 2010-08-06
Here is a quick rundown.

I am running Ubuntu 9.10 Karmic Koala.

Last night I had an update to do. Nothing out of the ordinary. This one however was fairly large. 27-28 MB.

At the end of the update I was asked to reboot. I was writing and email and wanted to finish so I clicked restart later.

After my email I went to shut down and we had a power failure (whole neighborhood) before it was finished shutting down.

When the power came back and I tried to reboot I go nothing. The initial Ubuntu logo shows then nothing.
When I hit esc. I get the following:
(Mounting/dev/disk/by-uuid/fc21dbcb-3722-4540-8e85-d5227c7137cbon/root failed: invalid arguement
Mounting/sys on/root/sys failed: no such file or directory
Mounting/dev on/root/dev failed: no such file or directory
Mounting/sys on/root/sys failed:
mounting/proc on/root/proc failed )

(Target file system doesn't have /sbin/init
No int found.
Try passing init=bootorg??)

There may be a couple of typos there I wrote it down fast on a piece of paper. I 'm sure you get the jist.

I tried putting in the 9.04  disk I have to see if I can get some sort of recovery. For some reason all the f keys except f1 do nothing.

I could really use some help here.
Is there anything I can do?
Or should I just download 10.4 and bite the bullet and reinstall?

Any help would be greatly appreciated.

---

### Post by mikewhatever on 2010-08-06
Can you boot from the 9.04 cd and post the output of the following command:
```
sudo fdisk -l
```
Hopefully, a simple file system check will solve the problem.
PS: What are the f keys for?

---

### Post by utilitytrack on 2010-08-06
Try install new system

---

### Post by ScottoMacD on 2010-08-06
> **mikewhatever said:**
> Can you boot from the 9.04 cd and post the output of the following command:
```
sudo fdisk -l
```Hopefully, a simple file system check will solve the problem.
PS: What are the f keys for?


The F Keys are on the bottom of the 9.04 cd when the install options are given
You can see it here. under the language choices.
[http://www.pronetworks.org/forums/ubuntu-9-04-installation-screenshots-t108880.html](http://www.pronetworks.org/forums/ubuntu-9-04-installation-screenshots-t108880.html)

I will try both suggestions this evening when I get home. unfortunately I have left the house and can't try until then.

I really appreciate the quick responses.

---

### Post by elliotn on 2010-08-06
Also try fsck

---

### Post by ScottoMacD on 2010-08-06
> **mikewhatever said:**
> Can you boot from the 9.04 cd and post the output of the following command:
```
sudo fdisk -l
```Hopefully, a simple file system check will solve the problem.
PS: What are the f keys for?


Ok Here is what I have. I am running off of the live cd right now:
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
102 heads, 51 sectors/track, 187768 cylinders
Units = cylinders of 5202 * 512 = 2663424 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       53936   140287510+   7  HPFS/NTFS
/dev/sda2           53937      187768   348097032    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa53da53d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9327    74919096   83  Linux
/dev/sdb2            9328        9729     3229065    f  W95 Ext'd (LBA)
/dev/sdb5            9328        9729     3229033+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

I hope this helps. I am completely in way over my head right now

---

### Post by mikewhatever on 2010-08-06
Thanks for the output. Before proceeding, how come you have Karmic installed, but only have the cd for Jaunty? Upgrade? I am asking because Karmic and Jaunty use different file systems by default. I you upgraded from Jaunty to Karmic, the file system should be the same and it's ok to run the check from the Jaunty cd. However, if you, at some point, did a clean install of Karmic, checking its file system from the Jaunty cd might not work.
From the same live cd, try running the following command:
```
sudo e2fsck -yv /dev/sdb1
```

---

### Post by ScottoMacD on 2010-08-06
> **mikewhatever said:**
> Thanks for the output. Before proceeding, how come you have Karmic installed, but only have the cd for Jaunty? Upgrade? I am asking because Karmic and Jaunty use different file systems by default. I you upgraded from Jaunty to Karmic, the file system should be the same and it's ok to run the check from the Jaunty cd. However, if you, at some point, did a clean install of Karmic, checking its file system from the Jaunty cd might not work.
From the same live cd, try running the following command:
```
sudo e2fsck -yv /dev/sdb1
```

Yes it was an upgrade from Jaunty.
I tried the  code and got the following:
ubuntu@ubuntu:~$ sudo e2fsck -yv /dev/sdb1
e2fsck 1.41.4 (27-Jan-2009)
/dev/sdb1: recovering journal
/dev/sdb1: Attempt to read block from filesystem resulted in short read while reading block 9338761

JBD: Failed to read block at offset 32102
e2fsck: Input/output error while recovering ext3 journal of /dev/sdb1

I am guessing that this is a much larger issue than I originally thought.

If there is no way to fix this particular issue and I will have to download and install that.
I am wondering if there is a way to back up my emails. They aren't that important and not a big loss but it would be nice to have them.

---

### Post by mikewhatever on 2010-08-07
Several suggestions I can think of:
1. Wait for a better file system expert then myself to help you.;)
2. Ask the mods to change the thread title to something meaningful and related to the actual problem. (Use the report button)

---

### Post by jmfal on 2010-08-07
I had similar problem last night.

Restart pc get into boot menu, select recovery mode press enter

SELECT: TRY TO FIX BROKEN PACKAGES  hit enter

stay at your monitor as it will type out info and may ask you if you want to continue, when it does  hit y then enter.

will ask for username enter username, then password then there will be a blinking cursor: type in  startx  press enter. login screen should appear or the screen with the options: resume normal boot
                                try to fix broken packages
                                the others I forgot,sorry

select: resume normal boot  press enter  should be ready to go

I don`t think it is a problem with the power outage,I think it was a bad update, been cruising the forum today and seen at least four or five ops with the same problem, best of luck , hope this helps out

---

### Post by utilitytrack on 2010-08-07
> **ScottoMacD said:**
> 
After my email I went to shut down and we had a power failure (whole neighborhood) before it was finished shutting down.


Please say where you live and how many times was power failures in your area. All of it looks like hardware failure, try replace PSU unit.

---

### Post by ScottoMacD on 2010-08-07
OK.

Well I'm back up.

How I am not too sure???
I booted into Windows to printout these pages and a couple of others I found because I cannot print from the Live CD.
After printing I was rebooting into Ubuntu holding down shift to get into recovery mode after as one paper suggested and the system booted?

I am assuming that it was the FSCK that we tried before but I really have no clue.

I am planning on upgrading to 10.04 today. I figure that will fix any lingering problems if any remain.

Thanks very much everyone for all the help and your patience as well. It is truly appreciated. 

Have a great day.

---

### Post by mikewhatever on 2010-08-07
Whatever lingering problem you might have, upgrading is not supposed to fix file system errors. Good luck anyway.;)

---

### Post by ScottoMacD on 2010-08-07
> **mikewhatever said:**
> Whatever lingering problem you might have, upgrading is not supposed to fix file system errors. Good luck anyway.;)

Thanks for the info Mike. I did not know that.

I upgraded to 10.04. It went smoothly and quite fast.

I had to remove and reinstall a couple of things which I expected and then I put the window boxes back on the right side where they belong. Why they moved them to the left is beyond me.

After all that I restarted and ubuntu said that there were errors to fix on the bootup. It  did a check and from that point on everything has been great.

Thanks again to everyone for everything.

---

