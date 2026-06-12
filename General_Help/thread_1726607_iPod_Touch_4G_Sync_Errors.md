---
title: "iPod Touch 4G Sync Errors"
date: 2011-04-11
forum: General Help
---

### Post by gr34t3st on 2011-04-11
So here is the situation: Just restored my iPod Touch 4G to factory settings and updated to the newest iOS version, 4.3.1. I attempted to sync my music library with the iPod but have had no success.

My default music player is Banshee. When I first synced with Banshee, I was getting an error that told me my iPod did not support the .m4a files. Obviously, that is wrong. These files were all on my iPod at one time too. When I used Rhythmbox or GtkPod, I get the same errors. I also had trouble with my iPod disconnecting almost as if there was a short in the cable.

I found a half-solution by following the instructions [here]("http://www.webupd8.org/2010/12/get-ios4-mountsync-working-in-ubuntu.html"). This fixed my connecting issue but it didn't fix the sync problems. 

After installing that fix, Banshee now crashes altogether after syncing for a few seconds. Rhythmbox and GtkPod give me the same errors as before. Right now, I'm sitting with a $300 paperweight. I could really use some help...

Thanks

---

### Post by vanadium on 2011-05-19
Everybody is very silent about this. I guess at present it won't work. Stay away from this device, and it it is out of your control, it will be a matter of getting a windows machine.
I am in you situation now. Our house is free of Windows or Apple, but I fear no much longer. My first attempt will be an install of Windows XP and iTunes in Virtualbox (with the USB extension).

---

### Post by tmette on 2011-05-19
I'm kind of in the same situation.  I'm still dual-booting Win7 so I still use it for my iPod needs.  Hopefully 11.10 comes with better support for the Touch 4G?

---

### Post by jyoticse804 on 2011-05-19
I am also facing the same type of problem & trying to recover. I have got enough help from
[http://www.webupd8.org/2010/12/get-ios4-mountsync-working-in-ubuntu.html](http://www.webupd8.org/2010/12/get-ios4-mountsync-working-in-ubuntu.html)

but need more..

---

### Post by alessandro0blanco on 2011-05-22
I got my iPod Touch 4G with iOS 4.3.1 to sync with banshee in ubuntu 10.10!
The steps to follow are these:

[LIST]
[*]Follow [this]("http://cogizio.org/operating-systems/ubuntu/3089") guide
[*]Install the latest version of libimobiledevice: 1.1.0 (to do this you should add the _natty _pmcenery ppa to your repositories)
[*]Install the 0.7.95 version of libgpod (select package libgpod4, the go to packages >> force version and select this version. Do this for libgpod-common too)
[/LIST]
I tried with ubuntu 11.04 but I couldn't install the 0.7.95 version of libgpod, so I failed with natty. But someone could teach me too how to do this.

Ask for more details!

---

