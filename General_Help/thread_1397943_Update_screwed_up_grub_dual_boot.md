---
title: "Update screwed up grub dual boot"
date: 2010-02-03
forum: General Help
---

### Post by 999alfred on 2010-02-03
On my hard disk I have ubuntu 9.10 (/dev/sda6) and Slackware 13 (/dev/hda1). Since Ubunutu was installed second, it replaced Slackware's lilo with grub. Anyway I modified grub and got Slackware 13 booting also, I has been this way for a couple of months. 

Tonight slackware would not boot, it kernel panic'ed. Complained about no device /dev/sda1 and listed possible devices, /dev/hda1 (What it is supposed to be) being one of them. What the heck, what changed???

A quick check of /boot/grub.cfg first showed that the las cahnged date was 2010-1-30. What? I have not touched grub.cfg since the Ubuntu 9.10 install. But, I remember that about that date I did a system update.

Plus, there were four Slackware menuentries, and I remember only one. Strange.

Anyway I changed Slackware's grub menu entry to root=/dev/hda1 and rebooted. Now it complained about no known file system, Slackware 13 is ext4. Here is the Slackware menuentry:
menuentry "Slackware Linux (Slackware 13.0.0.0.0) (on /dev/sda1)" {
        insmod ext2
        set root=(hd0,1)
        search --no-floppy --fs-uuid --set 0fc0487a-5cae-497d-9d3b-b5e7ecebe561
        linux /boot/vmlinuz-generic-2.6.29.6 root=/dev/hda1
}

Where'd the 'insmod ext2' come from.\? Slack has always been ext4. Plus I know I did not put all of those 0's on the Slackware 13.0.0.0.0.

So, what did the update change to cause this?
How do I get grub to boot Slack's ext4 file system?
Like I said, it booted perfectly until after the update.

tj

---

### Post by Ledus on 2010-02-03
Same happened to me and I got no help...

My  only option was to format the hard drive

---

### Post by 999alfred on 2010-02-03
Further info,
A bunch of files in /boot/grub have 2010-1-03 dates. a lot of .mod files, It looks like the whole directory got changed. And scew'ed my booting up.

(A ubuntu conspiracy to destroy all other distros? Enquiring minds want to know :-))

tj

---

### Post by meierfra. on 2010-02-03
> Where'd the 'insmod ext2' come from.\?

Grub uses the ext2 module for ext2, ext3 and ext4.  So that is perfectly normal.

> Plus I know I did not put all of those 0's on the Slackware 13.0.0.0.0.

That's probably the exact version of Slackware you are using.  Anyway, the  title is just for looks, and does not play any role in the booting.


> Complained about no device /dev/sda1
That's  weird. Your "grub.cfg" uses "root=/dev/hda1". To get a better picture of your set-up, please follow these [instruction]("http://bootinfoscript.sourceforge.net/") to run the boot info script and post the "RESULTS.txt"

---

### Post by meierfra. on 2010-02-03
> Same happened to me and I got no help...

Ledus: I looked up your old post.  Your problem seems quite different. Also you should use  more descriptive titles:  "singal over range!"   does  not  reveal any information about the nature of your problem.   If your thread  does not receive any attention, feel   free to bump your thread once every 24  hours.

---

### Post by meierfra. on 2010-02-03
>  I have not touched grub.cfg since the Ubuntu 9.10 install 

Did you  edit "grub.cfg" yourself when you installed Ubuntu?  
(edit: Sorry, just noticed that you answered that question in your first post)
grub.cfg is not  supposed  to be edited.  grub.cfg gets completely  rewritten during kernel updates and all  manual changes will be lost.

---

### Post by 999alfred on 2010-02-03
> **meierfra. said:**
> 
That's  weird. Your "grub.cfg" uses "root=/dev/hda1". To get a better picture of your set-up, please follow these [instruction]("http://bootinfoscript.sourceforge.net/") to run the boot info script and post the "RESULTS.txt"

Find RESULTS,txt attached.

tj

---

### Post by Psychodox on 2010-02-04
> **999alfred said:**
> (A ubuntu conspiracy to destroy all other distros? Enquiring minds want to know :-))

tj

OH man..:shock: gave me a feeling of using win... mi.. win... I'm going to bed now

---

### Post by meierfra. on 2010-02-04
Where  does seems to be a problem with Grub2 and  slackware.

Do you remember how you edited grub.cfg  when you installed Ubuntu?  

> Now it complained about no known file system, 
Can you post the exact error message?  Is it a message from Grub or from the kernel?


According to this [thread]("http://www.linuxquestions.org/questions/slackware-14/issue-booting-slackware-13-with-grub-773467/?highlight=slackware+grub2")  the last two entries on the Grub menu (the huge kernel) should work. Did your try those?   But if you want  to boot with the regular kernel you will have to create the initrd.gz file.

---

### Post by 999alfred on 2010-02-04
OPk, here we go.
Tried the last two entries as you suggested, i.e. root=/dev/sda1.

VFS: Cannot open root device "sda1" or unknown-block(0-0)
Please append a correct "root=" boot option; here are the available partitions:
0300    29316672 hda driver: ide-gd
  0301     14868126 hda1
  0302            1 hda2
  0305       465853 hda5
  0306     13341919 hda6
  0307       634536 hda7
1600     4194302 hdc driver: ide-cdrom
Kernel panic - not syncing: VFS: Unable to mount root fs on unknwon-block(0,0)

First entry, i.e. root=/dev/hda1
List of all partitions:
<same as above>
No filesystem could mount root, tried romfs
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (3,1)
Notice no "cannot open root device" error message.

This is the generic straight off of the Slack dvd kernel that has never required a initrd. I looked at the above mentioned thread briefly and will look at it in depth when time allows.

Is what I am seeing is that grub2 is going to require an initrd?

And no, I cannot remember exactly what I changed in grub after the 9.10 install to get Slackware to boot. that was four months ago. But, it seems it was a cut/paste of Ubuntu menuentry. Changing set root=(hd0,6) to (hd0,1) and root=/dev/sda1 to hda1.

Tonight I may get wild and on a another spare drive repeat the Slackware install, then install 9.10 modifying grub.cfg to get them both booting as before and save grub.cfg.  The do the 9.10 update, and if it happens again, compare the two grub.cfg files. The system it is on is a spare "play around with, don't care if I break it test system" anyway. If it wasn't for my "gotta find the answer" trait, I'd boot off of Slack dvd, using hda1 as root, modify lilo to include 9.10 on hda5 and forget about grub.

The worry some thing is, this seems to be a regularly occurring problem concerning grub2.

tj

---

### Post by meierfra. on 2010-02-04
> VFS: Cannot open root device "sda1" or unknown-block(0-0)
Try the last two entries, but change "sda1" to "hda1".

---

### Post by oldfred on 2010-02-04
After a little googling it seems that if you want to boot the generic kernel you have to create initrd.
[http://forums.scotsnewsletter.com/index.php?showtopic=31419](http://forums.scotsnewsletter.com/index.php?showtopic=31419)

You supposedly can boot the huge kernel ok. 

Alnother link:
[http://www.linuxquestions.org/questions/slackware-14/issue-booting-slackware-13-with-grub-773467/page2.html](http://www.linuxquestions.org/questions/slackware-14/issue-booting-slackware-13-with-grub-773467/page2.html)

---

### Post by 999alfred on 2010-02-04
Ok, now for the dirty low down truth. The problem was two fold:
1. ubuntu update redoing grub.cfg.
2. head up my ... well, you get the picture. 

First, when the update rebuilt grub.cfg it went to the Slackware /boot and got ALL the possible  kernels, generic, generic-smp, huge and huge-smp. Whereas I only had one kernel in my original grub.cfg.
Also, it changed the root=/dev/hda1 to /dev/sda1. Which cause the first error.

Second, I kept trying to boot off of the first Slack entry, which was generic. That was the head up ... well you get the picture. As generic does not have ext4 compiled in, so unrecognized fs, duh. Plus, I had not changed the OTHER entries that would have worked to hda1, duh.

I realized my mistakes while half asleep at work today.

Anyway changing sda1 to hda1 fixed the problem WHEN you booted the correct Slack kernel.

Took sometime, but as usual I learned a lot more then I knew before by troubleshooting the problem.

Thanks to meierfra for your kind help.

tj

---

### Post by meierfra. on 2010-02-05
> Anyway changing sda1 to hda1 fixed the problem WHEN you booted the correct Slack kernel.

Just be aware that "grub.cfg" will be overwritten again during the next Ubuntu kernel or Grub update. Let me know if your are interested in a  more permanent solution.

---

