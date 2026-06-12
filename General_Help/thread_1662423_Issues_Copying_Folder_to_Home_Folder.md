---
title: "Issues Copying Folder to Home Folder"
date: 2011-01-08
forum: General Help
---

### Post by zbollman on 2011-01-08
Hello,

I'm not positive if this is in the correct section but I am hoping so. I am running dual-boot with Windows 7 and Ubuntu 10.10. I hunted down my files from Windows that I need for school (old papers, research, etc.) and found it under "file system" --> "host" --> "users" --> "zbollman". I can access all of my files and I'm happy now that I don't have to boot between the two constantly to get what I need. However, I tried to copy the file to my home folder, but it said I do not have enough room. I'm about 5GB short. How do I go about allocating more space so that I can copy this folder so that all of my information is easily accessible?

Thanks,
Zach

---

### Post by tredegar on 2011-01-08
There's no need to copy the files from the windows partition, just navigate to "file system" --> "host" --> "users" --> "zbollman" and bookmark that place. Now it will show up under "Places".

Or you can just make a link from your desktop to "file system" --> "host" --> "users" --> "zbollman"

If you really need more space on your linux partition, you need to boot to a live CD and resize your _unmounted_ partitions with **gparted**. Best to take a backup before you try this.

---

### Post by WorMzy on 2011-01-08
If what you have said is true, then you are not actually dual booting, you've installed Ubuntu inside Windows using Wubi. This means that you're essentially running a virtual machine, and the "disk" you've installed to is simply a file on the Windows partition.

See this guide for advice on how to get around the fixed "disk" size:
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

You may also want to consider installing Ubuntu to a partition instead:
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?)

---

### Post by tredegar on 2011-01-08
Ahhh Wubi (Yuk)
Disregard my advice - I thought the OP was dual-booting.

---

### Post by zbollman on 2011-01-08
Thanks for the help. I thought I was dual booting, but I guess not. Soooo much to learn! I'll go through and install with its own partitition. Would this be difficult for a new user?

Thanks,
Zach

---

### Post by oldfred on 2011-01-08
Forum member bcbc has a nice HOWTO:

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Many users try Ubuntu with wubi then upgrade to a full install, from the creator of wubi:

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

---

