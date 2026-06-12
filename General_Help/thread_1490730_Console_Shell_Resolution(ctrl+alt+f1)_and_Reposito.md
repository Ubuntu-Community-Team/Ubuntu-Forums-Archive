---
title: "Console Shell Resolution(ctrl+alt+f1) and Repositories issue"
date: 2010-05-22
forum: General Help
---

### Post by DuoWing on 2010-05-22
Hey, I'm new to Ubuntu. I had installed 9.04, but never used it much. Installed 10.04 64-bit the other day and I really like it. Anyway I've been searching and can't seem to find an answer to this, or at least one that seems to work. I'm trying to change the resolution of the shell console or whatever it's technical name is, the one when you hit ctrl+alt+f1. When I was running the live CD and upon first install it all ran fine, the text was alot smaller and I liked it better, plus it was nicer when shutting down as the text is rather large. This seemed to happen after installing NVIDIA drivers. The console isn't unusable, but doesn't look that good. 

I got the Nvidia 195.36.24-64bit drivers from Nvidia's site and got them installed. I had installed the drivers through the Ubuntu Hardware Driver manager, they were version 173 I see there's a newer version. I installed version 173 but it was having issues loading the additional graphics effects well and so I installed the driver from Nvidia's site and that seems to have worked well.

I'm running a Dell Inspiron 1440 Laptop, NVIDIA GeForce 8400M GS card. Intel Core 2 Duo 2.4 GHz Processor with 4gb of Ram. I'm running a dual boot of Windows 7 64-bit and Ubuntu 10.04 64-bit.

I had no problem customizing grub and getting that to run in 1024x768 resolution, adding an image, etc. I ran the vbeinfo command in grub and shows the highest resolution I can go to is 1440x900x32. I'm running that for Ubuntu's GUI.

I used the I think GFXPAYLOAD option in /etc/default/grub and changed my resolution, that didn't help. I used a command to change the text size in the shell console, it looked better, but still was off. I tried adding in the VGA=0x165 , VGA=868, etc and other numbers for the bootloader in Grub and that seems to make no change. This isn't a huge issue, just one that I'd like to figure out how to change. Any advice would be appreciated.

One thing that I remembered about while typing this is whenever I go to update the list for synaptic package manager it'll keep checking and say it's checking 116 packages and once it gets to about 114 out of 116 it'll give me an error:
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DEFailed to fetch [http://linux.dropbox.com/ubuntu/dists/lucid/Release.gpg](http://linux.dropbox.com/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'linux.dropbox.com:http' (-5 - No address associated with hostname)
Some index files failed to download, they have been ignored, or old ones used instead.

I'll search around, I don't know if this is really an issue or not. I'm assuming some packages and stuff no longer exist and it just can't update them? Since I'm still new to this OS, as I said I'm unsure if this is really an issue. Thanks for any and help guys.

Love the OS so far.
Thanks guys!

---

### Post by jangirke on 2011-05-12
Try here: [http://ubuntuforums.org/showthread.php?t=215566](http://ubuntuforums.org/showthread.php?t=215566)

---

