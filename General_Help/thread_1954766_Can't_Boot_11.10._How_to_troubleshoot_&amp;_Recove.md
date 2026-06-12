---
title: "Can't Boot 11.10. How to troubleshoot &amp; Recover?"
date: 2012-04-08
forum: General Help
---

### Post by kendoori on 2012-04-08
Am running 11.10 64-bit with Gnome-shell. Something happened late Friday whereby my machine never gets to the login screen. I do get to an Ubuntu splash logo, after that I get a text screen that it hangs on.

[IMG]https://lh6.googleusercontent.com/-Zjo0wF4eaQ4/T4HaHoCEAUI/AAAAAAAAALg/uAv2iK71wdw/s855/IMG_20120408_143243.jpg[/IMG]

The screen is referring to issues with mounting various network resources, including VMWare and also some references to my NAS that are in fstab.

I can get to the GRUB menu and into recovery console. If I try to do a file system check, I run into a similar error screen that I see when trying to boot normally. I am able to login with the CLI. Once at the CLI I can ping the Internet.

A possible clue here is that during my last good session I made some mods to the /etc/hosts file to reference another system which I'm connecting to with Synergy. Not sure this caused the problem as I logged in via CLI and modded the host file to remove the entry I'd made, to no avail. I also commented out the entries in my fstab that mount my NAS drives. This had no impact either.

I don't believe I have hardware issues as I'm able to boot properly with a Live USB and connect to my network/Internet.

A few more tidbits. I have regular Dejadups backups on my NAS. I have a good Clonezilla whole drive image which is 4-6 weeks old.. My home is encrypted.

I thought I'd try blowing away my hosts file via live USB, but when I mounted the hard drive everything was read-only and I couldn't figure out how to replace it.

Would love some sober advice on how to attack this.

---

### Post by Paddy Landau on 2012-04-09
I cannot say why this is happening to your computer, but you do seem to be having specific results with your hosts file.

My hosts file looks like this:
```
127.0.0.1    localhost
127.0.1.1    *computername*

# The following lines are desirable for IPv6 capable hosts
::1    ip6-localhost ip6-loopback
fe00::0    ip6-localnet
ff00::0    ip6-mcastprefix
ff02::1    ip6-allnodes
ff02::2    ip6-allrouters
```Replace *computername* with the name of your computer (it should be the same as in [FONT=Lucida Console]/etc/hostname[/FONT]). See if putting that in [FONT=Lucida Console]/etc/hosts[/FONT] helps.

---

### Post by kendoori on 2012-04-09
Turns out that the machine's root was out of disk space. The hosts thing had nothing to do with it. Somehow stuff had accumulate deep in the trash at root and home levels. Once I cleared that out, the machine booted properly. I'm running Gnome-shell and the trash can is NOT so obvious...

---

### Post by Paddy Landau on 2012-04-09
So weird. Thanks for letting us know.

---

