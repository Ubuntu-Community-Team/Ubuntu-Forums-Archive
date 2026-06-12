---
title: "&quot;File System&quot; Free Space: 2.7 MB"
date: 2009-10-07
forum: General Help
---

### Post by cadefy on 2009-10-07
Hi all, I was wondering why my File System is only 2.7 MB free? I also use Vista on this drive and when I went to install Ubuntu, I let it set up all for me automatically, when I used Vista I had C:\ which is 40gb (Vista Installation drive) then D:\ as my 180gb storage space, when I come to Ubuntu why can't I download anything? it tells me I have no space and that my File System has only 2mb free space?

How can I fix this?

Thanks :)

---

### Post by drs305 on 2009-10-07
cadefy,

Welcome to ubuntu. I would guess you chose "side by side" with Windows in Partitioning Step 4. There is a bug in the program that chooses a 2.5GB partition if you don't move the slider. This partition is unfortunately too small to operate Ubuntu. The bug is being fixed in Karmic but they have decided not to release a new ISO for earlier versions.

You can check with this command. Open a terminal with Applications, Accessories, Terminal. Then run this:
```

df -h

```

The minimum recommended size for an Ubuntu partition is 8GB.

If the / partition is about 2.5GB and / shows about 95% full, you will have to repeat the installation (selecting a larger partition with the slider at the bottom of the page in Step 4) or resize your Ubuntu partition by taking some space from Windows.

I've written some posts about how to do either one.
EXPAND  /
[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

2.5GB  INSTALL
[HOWTO: 2.5 GB System Partition - What Went Wrong?]("http://ubuntuforums.org/showthread.php?p=7658271")

I would recommend reinstalling unless you are very familiar with partitioning.

Let us know if you have any questions.

---

### Post by cadefy on 2009-10-07
justin@cad:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/sda5             2.3G  2.2G     0 100% /
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M  104K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  160K 1007M   1% /dev
tmpfs                1007M   76K 1007M   1% /dev/shm
lrm                  1007M  2.4M 1005M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda1              49G   36G   14G  73% /media/Stuff
/dev/sda2             247G   67G  181G  27% /media/IMPORTANT
justin@cad:~$ 

I have backed up all my important stuff to my external so it doesn't worry me if I lose anything on this hard drive, so to reinstall do I just pop the cd back in, go back to Live version and click the Install button like I originally did? This time I'll make sure I move the slider, by the way yes it was Side by side :)

thank you for your help, I wasn't expecting an answer so quick.

---

### Post by drs305 on 2009-10-07
Yes, there is a pic of the Step 4 slider bar in the link I provided. You will just need to slide it left. As I mentioned, 8GB is the recommended minimum but it depends how much data you plan on keeping in your /home folder.

You aren't the first user to face the reinstallation. It took the developers a bit of time to figure out why it defaulted to something the system couldn't use, but they have now identified it.

You don't need to do it now, but once you have successfully installed Ubuntu would you please return to this thread and mark it SOLVED with the Thread Tools link near the top right of the first post. You can also unmark it there if necessary.

---

### Post by cadefy on 2009-10-07
Thanks for your help mate, I'll give it a go. :)

Also by any chance you wouldn't know about if installing World of Warcraft on Ubuntu is fairly easy would you?

---

### Post by XCan on 2009-10-08
Don't feel bad, tons of people fell into this hdd-space trap, I'm beginning to think it was by design to mess with people. :p 

For your wow issues: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=1922](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1922)

---

### Post by cadefy on 2009-10-08
Thanks guys, helped me so much :)

also how do I mark this thread "SOLVED" ?

---

### Post by drs305 on 2009-10-08
> **cadefy said:**
> Thanks guys, helped me so much :)

also how do I mark this thread "SOLVED" ?

Glad things seem to be sorted out. 

To mark a thread SOLVED, the original poster can click on the Thread Tools link near the top right of the first post. You can also *unmark* it there, but hopefully this won't be necessary.  ;-)

---

