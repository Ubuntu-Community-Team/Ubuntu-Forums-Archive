---
title: "Access Ubuntu machine from a Windows machine accross network"
date: 2011-12-09
forum: General Help
---

### Post by thomo2710 on 2011-12-09
Hi all,

I have a complete Windows (sorry) network apart from 1 Ubuntu 11.04 desktop edition machine that i am using for monitoring (Nagios)

I need my nagios cfg files backed up to my Windows server every night.

I cant use my backup softwares Linux Agent as it does not support 11.04 yet and the installer fails.

I am thinking of using robocopy on the windows backup server to pull the files off the Ubuntu machine so they are put onto tape later on that night.

How can i access the Ubuntu machine from Windows please?

As you can see im primarily a Windows user so Linux knowledge is in its infant stage!

Cheers

---

### Post by lykwydchykyn on 2011-12-09
Lot of options here:

 - You could mount a windows share (on the back up server or some other server being backed up) from the Ubuntu machine, then script ubuntu to copy files to it every night.

 - Or install samba on the Ubuntu machine and share out the directory with the config files.

 - Or install ftp on the Ubuntu machine and script windows to grab the files over ftp

There are probably other options too, but those would be the most common approaches when working with windows.

---

