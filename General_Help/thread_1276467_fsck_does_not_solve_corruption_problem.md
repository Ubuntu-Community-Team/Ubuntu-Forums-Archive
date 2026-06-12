---
title: "fsck does not solve corruption problem"
date: 2009-09-27
forum: General Help
---

### Post by snacht on 2009-09-27
Summary: 
I have a few corrupt files. When I run fsck I see there are errors but they don't get fixed. How do I fix them?


Details:
A corrupt file is ~/Pictures/2009-08-29/P1000945.JPG. 
I know this because rsync fails on this file and also because when "dd  if=Pictures/2009-08-29/P1000945.JPG" fails with i/o error.

I then do 
sudo touch /forcefsck
sudo shutdown -r -F now
to force an fsck on boot. I see a lot of errors go by, but after the succesfull boot, the problem remains.

the log files at /var/log/fsck do not contain any usefull info.
Running fsck manually via the the boot cd with the -r option to fix interactively just returns:
[FONT="Fixedsys"]/dev/sda4: clean, 564912/5960304 files, 14240616/23870581 blocks[/FONT]
sooooo.

is fsck not the right tool? Where can I change the options fsck uses when it runs automatically at boot time? How can I can change the log level of fsck for the boot time run? Is fsck actually the tool being used or is it another tool? 
Any help is welcome.
Thanks,
Stefaan

---

