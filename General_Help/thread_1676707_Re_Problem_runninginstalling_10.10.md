---
title: "Re: Problem running/installing 10.10"
date: 2011-01-27
forum: General Help
---

### Post by Ivaylo Nedqlkow on 2011-01-27
Hi I have the following problem, 
I want to install ubunto with windos 7. 
I already have installed windows7, with wubi trying to put ubunto,
I parted with Disk mangedment, which is embedded in windows7,
a new partition which is 10 db. And there want to put ubunto. 
and so to make two operating system.
When I began to install ubunto during installation shows me this error

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=182106&stc=1&d=1296157618[/IMG]

---

### Post by s.fox on 2011-01-27
Please do not hijack other threads. Thank you.

Moved to separate thread.

---

### Post by Rubi1200 on 2011-01-28
Hi and welcome to the forums Ivaylo Nedqlkow :-)

Wubi is something that is installed **inside** Windows.

If you are looking to create a dual-boot system, this is probably the wrong way to go about it.

You can install Wubi but this is what you need to do.

First, you need to install with administrator rights.

Second, you can choose to install to the partition you want, but some of the files must remain on the C drive or you will have problems.

Third, if you install successfully you need to lock the grub-pc and grub-common packages in order to prevent issues that currently affect Wubi from causing problems.

In the Wubi Guide, there is more information and links to relevant pages.
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

If you would rather set up a proper dual-boot we can also help, but 10GB is not enough for that.

---

