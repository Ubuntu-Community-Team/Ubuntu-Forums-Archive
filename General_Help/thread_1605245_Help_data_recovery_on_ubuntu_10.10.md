---
title: "Help data recovery on ubuntu 10.10"
date: 2010-10-25
forum: General Help
---

### Post by toufiqueimam on 2010-10-25
Hi, I am Toufique a home (non geek) user from Bangladesh. I am using ubuntu from 9.10. Recently I have installed v 10.10. I wanted my pc to look like mac. So i have downloaded machabuntu theme from sourceforge. But when i started to install it, it deleted all contents of my /home folder! My documents,music etc folders are empty.but it did not install any mac theme.even it deleted my default themes. I Used 290gb ext4 partition as my home folder. My all data were in my home folder. After a day it is not booting also.(tells i have a serious problem in /home). So Is there any way to get my data back? I don't know how to use testdisk. I  usually post my solutions in [http://forum.linux.org.bd](http://forum.linux.org.bd) but they were not able to solve it and reffered my here.

---

### Post by toufiqueimam on 2010-10-26
i am waiting for the solution. Please help me

---

### Post by gunsten on 2010-10-26
I dont have a solution for you, but I googled and found two hits that might be of interrest:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

[http://ubuntuforums.org/showthread.php?t=417761](http://ubuntuforums.org/showthread.php?t=417761)


But first of all I'd tell you not to use the computer, if the lost files are very important to you. When deleting a file, what you actually do is telling the system that the memory space is available. By using the computer you risk that the information actually gets overwritten. And when that happens the information is actually lost permanently.

Also, I would like to add that it sounds risky to reconstruct deleted files on a file system in use. So it would be important to be sure that just the files you actually want to rescue gets reconstructed. So what I mean is that before you do anything, be sure that you know how the software, or method, really do.

I hope you will get more qualified help with this - a real bummer to lose files like that. You reminded me that I should really backup the home folder regularly.

Good luck!

---

### Post by Presence on 2010-10-26
Photorec/testdisk might be your only free option. If the files are missing, make sure you don't put any more files on the hard drive. If you haven't, most of the data should still be recoverable.

Here's how to use Photorec:
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

Try using RIPLinux, it comes with photorec. (Don't try to install anything on the HDD until you get your files back):
[http://www.tux.org/pub/people/kent-robotti/looplinux/rip/](http://www.tux.org/pub/people/kent-robotti/looplinux/rip/)

---

### Post by iluminameluna on 2011-11-06
N.B.: the manual shows: ```
sudo testdisk-6.11-2/linux/testdisk_static
``` but actually, w/ version 6.11-2 (the version as of this post) can be run w/ a simple:

```
sudo testdisk
``` at the command prompt

At least w/ Linux & it's distros. Which assumes you have admin privileges, of course.

---

### Post by Rubi1200 on 2011-11-06
Thread closed.

Reason: necromancy.

Thanks for participating.

---

