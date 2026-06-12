---
title: "Good judgement comes from experience, and experience comes from bad judgement."
date: 2010-03-24
forum: General Help
---

### Post by randizzle on 2010-03-24
This is not really an appeal for help, because I believe have done everything I can do to try and recover (to no avail). I want to share this story so that others hopefully can benefit.

Yesterday I accidentally pulled the power cord out of the back of my machine while booted into Ubuntu, which I installed via Wubi. 

Upon reboot I was greeted with the (initramfs) prompt from BusyBox. Restarting again in verbose mode revealed that "/host/ubuntu/disks/root.disk does not exist." I also found this bug report...

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/226622]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/226622")

So based on this I believed either the NTFS dirty flag is set or the partition is corrupted. The first thing I try is to boot via live CD to see if I can mount the partition. I am able to mount the partition, but unable to cd into root.disk. I tried ntfsfix, which reported that there were some serious problems and that I should run chkdsk. (Here is where I was dumb, at this point I should have done a back up of files on that partition)

I finally found this blog post where someone described my scenario..

[http://creekcodes.blogspot.com/2009/01/wubi-ubuntu-wont-boot-missing-rootdisk.html]("http://creekcodes.blogspot.com/2009/01/wubi-ubuntu-wont-boot-missing-rootdisk.html")

Based on all this, I boot into windows and run chkdsk. It reports success. I reboot into ubuntu and am greeted with the same error described above. &*@#&@!

I boot back into windows and chkdsk apparently deleted my root.disk file. Double &*@#&@!

A little research revealed that is just something that chkdsk does occasionally. Documentation seems to indicate that I *should* have had a folder called C:/found.000 which would have contained a copy of root.disk. This folder nor the root.disk file was anywhere to be found on any drive on the machine.

At this point I am realizing that I am probably totally screwed. I installed GetDataBack for NTFS and tried to find root.disk on the hard drive. This was unsuccessful.

I blame myself for not having a recent backup but part of me wants to punch microsoft in the dangly bits.

I will be reinstalling Ubuntu but I will never use or recommend Wubi to anyone again. Obviously, there is only so much that the good folks ate Wubi can do to mitigate this problem, but this is a show stopper as far as I am concerned. It is far too easy to lose power to a machine.

If anyone has any suggestions, I would love to hear them. Or if you want to reply just to call me an idiot, then you know, you can do that too.

---

