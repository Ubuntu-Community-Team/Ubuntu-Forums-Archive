---
title: "Nautilus Cannot Handle Locations"
date: 2010-03-04
forum: General Help
---

### Post by linuxus95 on 2010-03-04
Hello, and big thanks for all replies. I am running Karmic, fully updated etc, but I have a very weird problem. At one time, probably after an update, I noticed that the only thing that showed up in the "Connect to Server" menu was the Custom Location option. Also, if I try opening my local network, I get the message "Nautilus cannot handle network locations." Same with SSH, when I type ssh:// or sftp:// into nautilus, I get the reply that "Nautilus cannot handle ssh locations." Basically, nautilus is unable to use any protocol like ssh, ftp, network, or anything. As I said before, when opening the Connect to Server dialog under Places, the only connection option shows is custom location, even though the drop down menu used to be full of possible ways to connect, like ftp, ssh, windows share etc. I also noticed Nautilus acts weird when i insert an audio disc, it tells me that "this type of disc cannot be mounted." I could not find a solution to this anywhere on the internet, so I am posting this thread (hopefully in the right place):p. I have no idea what is going on, and don't feel like re-installing just because of this, I think, small bug. Again, will be grateful for any replies!

---

### Post by not2comply on 2010-03-04
Same thing happen to me, using Karmic Koala on Dell Studio XPS 8000. I can't access web disk on remote host. The only thing I could do with nautilus is exploring local disk ( with root access of course ), other than that... none worked.

And I found something on bug list [here]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/185756") . Is it fixed in 9.10?

Thanx in advance

---

### Post by linuxus95 on 2010-03-05
Thanks for confirming, mounting other filesystems with root privileges also worked for me. I checked out the bug report, but it seems to be targeted at Hardy users and I did not find a solution there, that's why I initially posted this thread. Let me know if you find out something else!:popcorn:

---

### Post by not2comply on 2010-03-06
I'm in a dead end with nautilus. so i use konqueror to access my remote host. ;)

---

### Post by peal on 2010-03-28
I ran into this problem after upgrading to Lucid Lynx. After some googleing it seems like it is related to gvfs. I checked out synaptic an saw that I was missing:
gvfs-backends - userspace virtual filesystem - backends
gvfs-bin - userspace virtual filesystem - binaries
gvfs-fuse - userspace virtual filesystem - fuse server

So I installed them and now everything is working again.

Hope this helps.

---

### Post by linuxus95 on 2010-03-29
Wow thanks! I checked Synaptic and just got those packages installed in Karmic too. Fixed all after reboot. Anyways, thanks for the solution! Perhaps you should upgrade the "Drapper Drake" distro in your signature?;)

---

### Post by dcompiled on 2010-11-18
I just recently installed some updates and a few hours later my system locked up.  After rebooting nautilus can no longer open samba drives, sftp connections or anything other than local.  I checked to see what was installed and the gvfs-bin package was missing so I installed it and rebooted again.  This had no effect.  Does anyone else know why this might have stopped working and what I can do to fix it?  Im using ubuntu 10.10 64 bit.

---

### Post by johnbyrne on 2010-12-08
Thanks guys! I just installed the gvfs modules mentioned above and it solved all my problems!

BTW, I'm running Meerkat on an AMD 64 Dell Laptop.

Thanks again!

---

### Post by Didge on 2010-12-16
I have this problem too with 10.10 64bit. It is driving me nuts!!

---

