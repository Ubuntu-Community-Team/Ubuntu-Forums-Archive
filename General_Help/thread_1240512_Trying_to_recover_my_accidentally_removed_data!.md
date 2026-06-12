---
title: "Trying to recover my accidentally removed data!"
date: 2009-08-14
forum: General Help
---

### Post by s3a on 2009-08-14
I have Debian Lenny on my hard drive and accidentally did sudo rm -rf * while I was in the home directory and removed all my (important) data!

To try to solve this problem, I loaded Ubuntu 9.04 and did sudo apt-get install scalpel as suggested here: [http://www.addictivetips.com/ubuntu-linux-tips/how-to-recover-deleted-filesdata-in-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-recover-deleted-filesdata-in-ubuntu-linux/) . I uncommented the parts of the /etc/scalpel/scalpel.conf text file so that it recovers the file types I want it to recover.

_Here is my issue:_

[I]ubuntu@ubuntu:~$ sudo scalpel /dev/sda6 -o output /media/disk/save_me
Scalpel version 1.60
Written by Golden G. Richard III, based on Foremost 0.69.
ERROR: You have attempted to use a non-empty output directory. In order
       to maintain forensic soundness, this is not allowed.
Aborting.[/I]

I thought the issue was that I was recovering data of my home partition into a directory within that same partition. So then I brought a completely empty (ntfs) hard drive and got the same issue:

[I]ubuntu@ubuntu:~$ sudo scalpel /dev/sda6 -o output /media/disk-1
Scalpel version 1.60
Written by Golden G. Richard III, based on Foremost 0.69.
ERROR: You have attempted to use a non-empty output directory. In order
       to maintain forensic soundness, this is not allowed.
Aborting.[/I]

Please help me recover my (very important) data!

Any help would be GREATLY appreciated!
Thanks in advance!

---

### Post by soapBAR2 on 2009-08-14
It's possible the first directory you tried was not empty, and that the NTFS drive had that frustrating automatically-created hidden thumbs.db in it. According to scalpel's manpage, you can output to a non-existent directory and it will create one. So, delete /mnt/disk/save_me (rmdir /mnt/disk/save_me) and try again.

---

### Post by s3a on 2009-08-14
Unfortunately, I get the same issue on both hard drives :(. 

Edit: Formatting the ntfs drive to ext3 and then removing the lost+found folder did it.

---

### Post by s3a on 2009-08-14
The recovery is hours from being complete but I noticed that this program does not recover what you don't ask it to recover (unless I am mistaken but then why would it ask you to choose what to uncomment out of the text file?). So then how do I recover my xournal files (.xoj) for example?

---

### Post by soapBAR2 on 2009-08-14
> **s3a said:**
> The recovery is hours from being complete but I noticed that this program does not recover what you don't ask it to recover (unless I am mistaken but then why would it ask you to choose what to uncomment out of the text file?). So then how do I recover my xournal files (.xoj) for example?

I'm not familiar with scalpel, but I'd be astonished if it didn't support wildcards. 

[http://en.wikipedia.org/wiki/Glob_(programming](http://en.wikipedia.org/wiki/Glob_(programming))

Here's your main wildcard characters.

---

### Post by s3a on 2009-08-14
What are wildcards? Your link seems lead to nowhere useful.

---

