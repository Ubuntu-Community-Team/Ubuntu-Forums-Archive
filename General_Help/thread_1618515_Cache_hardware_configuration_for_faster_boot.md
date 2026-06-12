---
title: "Cache hardware configuration for faster boot?"
date: 2010-11-10
forum: General Help
---

### Post by thunder9861 on 2010-11-10
Hello.

I am using Ubuntu Maverick on my Eeepc 701, and everything is working quite nicely. 
Since I only have 4GB SSD drive, my setup is that the LiveCD is booted from the SSD, while my 'casper-rw' partition is on a 4GB SD card. I have 2GB of ram and do not use swap.

I am wondering if there is a way to somehow cache the results of the hardware probe and configuration, and insert the cache into LiveCD by remastering it. The idea is that less time will be needed to boot, since everything that was found from the first boot was saved.

Of course this would mean that particular modified LiveCD wouldn't reliably boot on anything other than my system (or one like it), but seeing as how my hardware won't change in the future, it isn't a problem.

Is something like this possible? I'm not afraid of recompiling a kernel or rebuilding an initramfs if needed.

A possible alternative idea to accomplish this would be to boot up the vanilla LiveCD as normal, configure a swapfile, hibernate, then inject this swapfile into the LiveCD image.

This way, every boot would automatically just be resuming from hibernation. This could potientally mess with the casper-rw partition, but that is something I would worry about later (and I am not opposed to just eliminating the casper-rw partition altogether and running off ram each boot). 

The other problem might be that the swapfile would probably need to be the size of my ram (2GB). Chances are, after a fresh boot my ram will be mostly empty, therefore would it be possible to compress the swapfile (like swapfile.gz)?

I will be looking into either alternative, but I was hoping to get some opinions / ideas on how to accomplish this (or whether it has already been done!)

Thank you for any help.

Possible relevant threads:
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)
[http://wiki.geteasypeasy.com/Fix:_hibernate](http://wiki.geteasypeasy.com/Fix:_hibernate)
[http://www.informit.com/articles/article.aspx?p=1565700&seqNum=4](http://www.informit.com/articles/article.aspx?p=1565700&seqNum=4)
[http://ubuntuforums.org/showthread.php?t=1594694](http://ubuntuforums.org/showthread.php?t=1594694)

---

### Post by dcstar on 2010-11-10
> **thunder9861 said:**
> Hello.

I am using Ubuntu Maverick on my Eeepc 701, and everything is working quite nicely. 
Since I only have 4GB SSD drive, my setup is that the LiveCD is booted from the SSD, while my 'casper-rw' partition is on a 4GB SD card. I have 2GB of ram and do not use swap.
........

"LiveCD" boots are designed to work on all possible hardware, if you want faster boots then use the netbook install:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by thunder9861 on 2010-11-11
One of the reasons that I am fond of the LiveCD type boot is because of the Squashfs / Unionfs pair. My usual routine is to LiveCD boot and make all my customizations, which all get saved to the casper-rw partition. Then I reboot without persistence, squashfs the casper-rw partition and place it in the casper directory of the live cd. 

This method, while perhaps somewhat strange, allows me to ensure that my system stays "frozen" the way I like it. Any tinkering I do that potentially messes something up only requires me to clear out the casper-rw partition for everything to return to working order.

The squashfs aspect of the LiveCD is essential to me, especially since I don't have a lot of disk space to begin with. While I am aware that there is a way to use squashfs and unionfs (or aufs) on a normal installation, I would like to think that a netbook install is not my only option.

Thank you for your response, but I would still like a more definitive answer to my question.

Does anybody have knowledge (or know where I should be looking) on this subject?

---

### Post by thunder9861 on 2010-11-12
It seems that there is a kernel cheatcode that allows you to choose a resume partition at boot time:
 'resume=/dev/<partition>' where <partition> is the swap partition that a hibernation has been saved to. 
 
 When I get a chance I am going to play with this option. It might be  possible to set up my SD card as swap, hibernate, set the lock switch on  the card, and modify the LiveCD's boot menu to tack on this command.

---

### Post by thunder9861 on 2010-11-18
My initial attempts at hibernating the Livecd failed. 
I set my SD card as swap and the hibernation process wrote the hibernation data to it, but I couldn't get it to resume at boot. 

However, I honestly think that it is possible to hibernate and resume a live cd, so I will continue off in this direction for a while.

If anyone has any information that might help me, pertaining either to hibernation with a live cd, or the original goal described above, please post.

If I manage to succeed, I will write up a How-to, since a couple Google searches seem to imply that others are also wondering how to hibernate a live cd.

Thank you.

Related posts:
[http://art.ubuntuforums.org/showthread.php?p=659761](http://art.ubuntuforums.org/showthread.php?p=659761)
[https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/367848](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/367848)
[http://www.linuxforums.org/forum/kernel/152208-horm-hibernate-once-resume-many.html](http://www.linuxforums.org/forum/kernel/152208-horm-hibernate-once-resume-many.html)
[http://en.gentoo-wiki.com/wiki/TuxOnIce](http://en.gentoo-wiki.com/wiki/TuxOnIce)
[http://tinycorelinux.com/forum/index.php?PHPSESSID=75mkp72gv87e0eq576lr4c4ro5&topic=455.0](http://tinycorelinux.com/forum/index.php?PHPSESSID=75mkp72gv87e0eq576lr4c4ro5&topic=455.0)

---

