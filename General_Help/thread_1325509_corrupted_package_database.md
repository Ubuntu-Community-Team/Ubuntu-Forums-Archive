---
title: "corrupted package database"
date: 2009-11-13
forum: General Help
---

### Post by fethio on 2009-11-13
dpkg, apt-get, synaptic don't work!

I was busy cloning my hard drive, as my old drive was suffering from bad blocks detected after the karmic upgrade. I followed a neat tutorial in  [http://forums.linuxmint.com/viewtopic.php?t=3969]("http://forums.linuxmint.com/viewtopic.php?t=3969") which guided me through the process. Everything went nearly flawless. All my data was transferred.

However, I noticed that after I backed up all my data, I had removed four packages related with the annoying ubuntuone package using apt-get. The /var/lib/dpkg/status file changed during the process... The packages removed were: ubuntuone-client, ubuntuone-client-gnome, python-ubuntuone-client, and python-ubuntuone-storageprot.

Another thing happened when I plugged the new drive in, the swap was not recognized. I somehow managed to bring it up without swap, but the data in swap was lost (where /var/lib/dpkg/status was also lost I think)

Thus, after a couple of reboots, fsck fixed the filesystem by attaching lost inodes and stuff. The file /var/lib/dpkg/status could not be found, and I copied it over from the old drive, but it was not consistent with the package state as I had updated the package state after I backed up my data.

**Now, I have the** ubuntuone package **installed in my system, but when I run synaptic it shows up as NOT installed.**

And when I try re-installing it this is what I get:
```
dpkg: parse error, in file '/var/lib/dpkg/available' near line 0:
 newline in field name `1'
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: parse error, in file '/var/lib/dpkg/available' near line 0:
 newline in field name `1'

```

Guidance is appreciated...

---

### Post by seeker5528 on 2009-11-13
From the command line do:

```
sudo dpkg --clear-avail && sudo apt-get update
```

Later, Seeker

---

### Post by fethio on 2009-11-13
Took care of the problem.

Following those two magical lines of code, I could first reinstall and then completely remove the four annoying packages.

Thanks and praises...

---

### Post by seeker5528 on 2009-11-13
Unless you got to it pretty quickly before I edited the post, while I was researching the use of '&&' it should have been one line. ;)

You should be able to change the prefix of the thread to [SOLVED] then, under thread tools there is a link to mark the thread as solved.

Later, Seeker

---

### Post by fethio on 2009-11-15
Done...

Yes, I did the two line version before you edited your reply :)

---

