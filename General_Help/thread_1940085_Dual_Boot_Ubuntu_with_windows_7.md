---
title: "Dual Boot Ubuntu with windows 7"
date: 2012-03-13
forum: General Help
---

### Post by Possum93 on 2012-03-13
I have a system with three hard drives and four operating systems Win 7, Ubuntu 11.04, Ubuntu 11.10 and Fedora 16. I have a 1TB, 500GB, and an 80GB so I have plenty of room I want to add Ubuntu 10.10 on the free space that I have but when I try to do that I get the message No root file system is defined the order of my os's is 1. win Boot 2. Win 7, 3. free space, 4. container, 5. Fedora 16, 6. free space this is all on the 500GB drive. On the 80GB drive I have Ubuntu 11.04 entire drive. On the 1TB drive I have storage drive 1 212GB, Ubuntu 11.10 212GB, storage drive 2,367GB and last is 210GB Bitlocker drive storage when I start the install it wants to install to sda3 which looks like the 500GB drive free space is this correct and should I go ahead with it.

---

### Post by grahammechanical on 2012-03-13
well, you should know what you are doing when it comes to partitioning and installing what with having all those OS, but sometimes we forget what we already know. Such as selecting the partition to install to but not giving that partition a mount point of /

It think that is what that message is referring to.

Regards.

---

### Post by Mark Phelps on 2012-03-13
My general advice whenever installing a Linux distro in a PC in which a Windows OS is already installed is to disconnect the Windows OS drives BEFORE the installation.

But, I'm having a real hard time picturing your drive and partition setup.

Please boot into one of your existing Ubuntu installs, open a terminal, and enter "sudo fdisk -lu" (lowercase L, not a one) -- and post the results back here.  That will give us some info on your drives and their partitioning.

---

### Post by oldfred on 2012-03-13
For those with multiple installs and/or multiple drives, I like boot info script. While we use it to see what may be wrong with an install, it also is a good way to document system and know which boot loader is installed to which drive. You do not have to be an expert at reviewing it to see that it have useful info on your system.

I run it before & after every system change. In a worst case crash it has the detail you might need to rebuild a partition table and know what is/was where.

New test/git version has some fixes:

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```
If you need instructions the current version is here:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

