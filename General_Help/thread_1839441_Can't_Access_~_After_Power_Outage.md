---
title: "Can't Access ~ After Power Outage"
date: 2011-09-05
forum: General Help
---

### Post by Xiode on 2011-09-05
So I just woke up to a power outage and realized that I had my computer on the wrong power strip (the one without surge protection) *facepalm*  

The only thing that seems to not be working is that I can't access ~/ itself (ls, Nautilus, etc..).  I can, however, access subdirectories of ~/. Further, I've run fsck on all 3 of my partitions, and it states that my mount point for ~/ is clean.

Partitions:
[LIST]
[*]/  <- /dev/sda1
[*]/swp  <- /dev/sda2
[*]/home  <- /dev/sda3
[/LIST]

I've run fsck multiple times (sudo touch /forcefsck, sudo shutdown -Fr, GRUB Error Recovery, etc..).  I've also run two SMART diagnostics on my hard drive (all but the longer in-depth), and it seems to think that my HDD is healthy.

Also, if this provides any insight, sometimes a brief "ls ~/" right after start-up works, but then within 30-60 seconds it no longer does.  Apart from being able to access that folder specifically, everything seems to work fine.  Further, like I said, subdirectories of ~/ are accessible.

**Edit:** It seems I'm even able to access files within ~/ (eg: .vimrc), just can't list the contents of the directory itself?

Any ideas would be appreciated!

---

### Post by SecretCode on 2011-09-05
I'm guessing permissions on ~ itself.

What's the output of 
```
df ~
```
```
ls -la ~
```
```
sudo ls -la ~
```

Including error messages if any. If ls lists files then I guess you don't have a problem; if it doesn't but sudo ls does, then post the output as far as the . and .. lines.

I get:
```
$ sudo ls -la ~
ls: cannot access /home/joe/.gvfs: Permission denied
total 87796
drwxr-xr-x 87 joe  joe       4096 2011-09-04 22:39 .
drwxr-xr-x  5 root root      4096 2010-10-31 18:47 ..

```

---

### Post by Ad1217 on 2011-09-05
were you editing anything before the power outage?

---

### Post by Xiode on 2011-09-05
> **Ad1217 said:**
> were you editing anything before the power outage?

No, I was just sitting in a subdirectory of ~/ in the terminal, and apart from that only had open Chrome and the built-in PDF viewer.

**Output from *df ~*:**
```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3            267765480  68965408 185198332  28% /home
```

**Output from *ls -la*:**
Nothing, just sits there and blocks.

**Output from *sudo ls -la*:**
```
simmons@udesktop:~$ sudo ls -la ~
[sudo] password for simmons: 
ls: cannot access /home/simmons/.gvfs: Permission denied
total 612
drwxr-xr-x 81 simmons simmons  4096 2011-09-05 15:28 .
drwxr-xr-x  5 root    root     4096 2010-10-07 05:15 ..
.. the rest of the directory
```

---

### Post by Xiode on 2011-09-05
What exactly does that mean, that I can access it using *sudo* but not normally?  I am an administrator and had no problems before the outage.

---

### Post by SecretCode on 2011-09-06
I was hoping the permissions would show an error but you have r w and x for your username (iirc x is required on directories to list their contents). It looks normal.

However, the fact that sudo works suggests there's nothing wrong with the filesystem and that the problem is something to do with your account. On the other hand, I don't know why ls hangs rather than reporting an error. Or why it sometimes works straight after booting.

Can you create a second user account and see if the problem occurs with that too?

---

### Post by fdrake on 2011-09-06
have you try to check for disk errors? use a bootable live cd/usb and do:

```
sudo su
umount /dev/sda3
fsck -y /dev/sda3
```

after fixing possible errors try to changes the permissions of the file and see if it works.

---

