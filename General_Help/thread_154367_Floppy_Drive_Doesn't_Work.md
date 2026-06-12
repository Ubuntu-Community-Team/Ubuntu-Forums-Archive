---
title: "Floppy Drive Doesn't Work"
date: 2006-04-02
forum: General Help
---

### Post by GordonFreeman83 on 2006-04-02
Hi all, 

Could anybody help me get the floppy drive in Breezy working? It won't mount. The  how-to doesn't help, because I already have the latest pmount, and my /etc/fstab already looks the way it says it should.

And no issues with permissions. This is the only user on the system, in the sudoers group, permissions to use cd floppy etc.

Never mind Windows, I could easily mount a floppy from a Windows machine in a 90's version of BSD Unix!!! What is going on with this, no-one has an answer? I love ubuntu but this just doesn't make sense.

Please can anybody help? It's the only thing that doesn't work.

---

### Post by atlas95 on 2006-04-03
[QUOTE=GordonFreeman83]Hi all, 

Could anybody help me get the floppy drive in Breezy working? It won't mount. The  how-to doesn't help, because I already have the latest pmount, and my /etc/fstab already looks the way it says it should.

And no issues with permissions. This is the only user on the system, in the sudoers group, permissions to use cd floppy etc.

Never mind Windows, I could easily mount a floppy from a Windows machine in a 90's version of BSD Unix!!! What is going on with this, no-one has an answer? I love ubuntu but this just doesn't make sense.

Please can anybody help? It's the only thing that doesn't work.[/QUOTE]
Me too it's desn't work !

---

### Post by dmizer on 2006-04-03
first of all, what command are you using to mount the floppy?

should be:
```
mount /dev/fd0
```
or something very similar.

---

### Post by hajk on 2006-04-03
The original post obviously makes a lot of sense to GordonFreeman83, but -- frankly -- not to me. I don't know which "howto" he means, what he thinks the "latest" pmount package is, and by what authority he believes that /etc/fstab already looks the way it "should" look. Same goes for permissions, with which there are "no issues". He seems to know a lot, yet he can't mount a floppy.

I don't know that much, but a floppy now mounts fine on my machine (after initial failure). ;)

Please provide some details on pmount version, /etc/fstab and the output from 
"ls -lr /media/floppy*" -- then may be I can help you get it right.

---

### Post by agemon on 2007-09-03
I have the same problem (at least the part where the floppy doesn't mount :) )
when I try `sudo mount /dev/fd0 /media/floppy0`, the led lights up but it says 'mount: /dev/fd0 is not a valid block device'

i've googled the problem and found `dmesg | grep -i floppy`, but on my system it says:
[   25.906231] Floppy drive(s): fd0 is 1.44M
[   25.943042] PM: Adding info for platform:floppy.0

`less /var/log/messages | grep -i floppy` prints (if it is of any help):
Sep  3 00:46:27 mypc kernel: [   36.578535] Floppy drive(s): fd0 is 1.44M
Sep  3 08:55:03 mypc kernel: [   26.215589] Floppy drive(s): fd0 is 1.44M
Sep  3 11:05:08 mypc kernel: [   26.700946] Floppy drive(s): fd0 is 1.44M
Sep  3 11:22:12 mypc kernel: [   25.906231] Floppy drive(s): fd0 is 1.44M

I should mention that, when I compiled the kernel, i didn't had a floppy drive and i can't recall if i installed or not modules for it :(
PS: `ls -lr /media/floppy*` reads: 
lrwxrwxrwx 1 root root    7 2007-08-18 04:01 /media/floppy -> floppy0

/media/floppy0:
total 0

---

### Post by happybrick on 2007-09-03
I have the same problem.

I followed the instructions in this "how to" [http://ubuntuforums.org/showthread.php?t=3687](http://ubuntuforums.org/showthread.php?t=3687)
but to no avail.

fstab entry is:
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

dmesg | grep -i floppy output is:
[   30.132937] Floppy drive(s): fd0 is 1.44M

Error message when mounting via GUI or sudo mount /dev/fd0 command is:
mount: /dev/fd0 is not a valid block device

Floppy works fine in Windows.

Any help much appreciated.

---

