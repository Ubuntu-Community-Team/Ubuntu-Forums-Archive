---
title: "fsck failed run e2fsck"
date: 2006-02-18
forum: General Help
---

### Post by Red Knuckles on 2006-02-18
After installing Suse on /dev/hda2 when I try to boot into Ubuntu [/dev/hda3] I get the following error:

Checking all file systems. Bad magic number in superblock while trying to open /dev/hda2
/dev/hda2

This superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid and it really contains an ext2 filesystem [and not swap or ufs or something else], then the superblock is corrupt, and you might try running e2fsck with an alternate superblock: e2fsck -b 8193 <device>

fsck failed. Please repair manually.

Control -D will exit from this shell and continue system startup.

I suspect the problem is that /dev/hda2 isn't an ext2 filesystem it's a reiserfs filesystem [Suse 10.0oss]. At any rate how do I correct this error???:confused:  I ran sudo e2fsck -b 8193 /dev/hda2 to no effect. How do I find other superblocks to try???

---

### Post by cilynx on 2006-02-18
You need to install the reiserfs tools.  Specifically, you need 'reiserfsck'.

You can't e2fsck a non ext2 filesystem.

---

### Post by Red Knuckles on 2006-02-18
[QUOTE=cilynx]You need to install the reiserfs tools.  Specifically, you need 'reiserfsck'.

You can't e2fsck a non ext2 filesystem.[/QUOTE]

In Synaptic I ran search>reiserfs tolls and I got:

reiserfsprogs
progreiserfs

reiserfsprog was installed and I can run e2fsck but I get the exact same error message. I removed reiserfsprog and installed progreiserfs and got the same exact result. Synaptic will only allow one or the other program not both. What's next??? When I used Synaptic to search for reiserfsfsck it didn't find anything.

---

### Post by Red Knuckles on 2006-02-18
[QUOTE=Red Knuckles]In Synaptic I ran search>reiserfs tolls and I got:

reiserfsprogs
progreiserfs

reiserfsprog was installed and I can run e2fsck but I get the exact same error message. I removed reiserfsprog and installed progreiserfs and got the same exact result. Synaptic will only allow one or the other program not both. What's next??? When I used Synaptic to search for reiserfsfsck it didn't find anything.[/QUOTE]

For what it's worth several repositories are not working just now, don't know why...

---

### Post by cilynx on 2006-02-18
Either one of the reiserfs packages should be fine.  The problem is which filesystem checker to use on which filesystem.

e2fsck == ext2 filesystem check

reiserfsck == reiser filesystem check

See if you can run 'reiserfsck' where you were doing 'e2fsck'

Being that it's autodetecting as ext2, you may have an improper entry in your /etc/fstab.  The filesystem type needs to be reiserfs, not ext2

Good Luck

---

### Post by Red Knuckles on 2006-02-18
[QUOTE=cilynx]Either one of the reiserfs packages should be fine.  The problem is which filesystem checker to use on which filesystem.

e2fsck == ext2 filesystem check

reiserfsck == reiser filesystem check

See if you can run 'reiserfsck' where you were doing 'e2fsck'

Being that it's autodetecting as ext2, you may have an improper entry in your /etc/fstab.  The filesystem type needs to be reiserfs, not ext2

Good Luck[/QUOTE]

Thanks, I am able to run reiserfsck and did --check 1st. It found 3 bad nodes or something and prompted me to run with option --rebuild tree which is running now. Will repost after checking results. Learned something.

---

### Post by Red Knuckles on 2006-02-18
Also in /etc/fstab /dev/hda2 was listed under<type> as ext3 which I changed to reiserfs. As I said will report back after testing. In gparted /dev/hda2 was listed as reiserfs but not in /etc/fstab which is why I made that change.

---

### Post by cilynx on 2006-02-18
Sounds good.  Gparted actually reads the info from the partition.  Fstab is just a user-editable text file that tells the system how to mount and check volumes.

---

### Post by Red Knuckles on 2006-02-18
[QUOTE=cilynx]Sounds good.  Gparted actually reads the info from the partition.  Fstab is just a user-editable text file that tells the system how to mount and check volumes.[/QUOTE]

AWESOME!!! I was able to boot into Suse which I couldn't when I started this thread. AND was able to boot into Ubuntu without the error message.\\:D/
The error message when booting into Ubuntu started when I installed Suse 3 days ago. Then today I did something in Suse [Stopping something in the terminal when I shouldn't have] that locked me out of Suse till I learned how to deal with this. This Forum is the BEST I've used [Started out in Linux in Fedora 10 months ago and have used Ubuntu, Mandriva and Suse]. NO forum I've used responds faster.:-D

---

### Post by cilynx on 2006-02-18
Glad to hear you got it working.  I know one thing that makes the Ubuntu forums so quick to respond is that they have a very nice thread tracking setup as well as the ability to "show unanswered posts".  Welcome to the mix...

---

