---
title: "Ubuntu 9.10 won't boot UNEXPECTED INCONSISTENCY"
date: 2009-11-18
forum: General Help
---

### Post by billlyum on 2009-11-18
A few days after successfully upgrading to 9.10 I turned on my computer and the the boot screen started a filesystem check.  It then crashed and the following DOS screen came up:
[I]
/dev/sda5 contains a filesystem with errors, check forced.
Filesystem checks are in progress (ESC to cancel)
/dev/sda5: Inodes that were part of a corrupted orphan linked list found
/dev/sda5: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY (ie: -a or -p options)
mountall: fsck/[427] terminated with status 4
mountall: filesystem has errors: /
init: mountall main process (419) terminated with status 3
Mount of filesystem Failed
A maintenance shell will now be started 
CTRL D will terminate this shell & retry 
root@IBM:~#_[/I]

If I press CTRL D the following comes up:
[I]
mountall start/starting
fsck from util-linux-ng 2.16
/dev/sda5 contains filesystem with errors. check forced
swapon: /dev/disk/by-uuid/f6100565-d920-4d6f-b253-b1bd2f5650ec: swapon failed: device or resource busy
mountall: swapon: /dev/disk/by-uuid/f6100565-d920-4d6f-b253-b1bd2f5650ec [793] Terminated with status 255
mountall: Problem activating swap swapon: /dev/disk/by-uuid/f6100565-d920-4d6f-b253-b1bd2f5650ec
/dev/sda5: Inodes that were part of a corrupted orphan linked list found
/dev/sda5: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY (ie: -a or -p options)
mountall: fsck/[787] terminated with status 4
mountall: filesystem has errors: /
init: mountall main process (786) terminated with status 3
Mount of filesystem Failed
A maintenance shell will now be started 
CTRL D will terminate this shell & retry 
root@IBM:~#_[/I]

I'm hoping I can somehow fix this and get back to business as usual w/ my previously working 9.10 setup.  Worst case scenario I'd like to save my files, wipe that partition and install a fresh 9.10.

I don't know how to accomplish either of the above so any direct help or pointing me in the right direction would be really appreciated.

---

### Post by billlyum on 2009-11-18
bump

---

### Post by Cheesemill on 2009-11-18
You're going to have to give more details, error messages etc.

Also please note it's forum policy to only bump after 24 hours :KS

---

### Post by billlyum on 2009-11-19
Sorry about the premature bump.  I edited the original post to show the exact output from DOS.  Hopefully this helps.

---

### Post by billlyum on 2009-11-23
Can I get a bump now?

---

### Post by jeb800e on 2009-11-23
Try running fsck again, if you can.

---

### Post by ejetzer on 2009-11-24
I have the exact same problem. I'm gonna try using fsck.

EDIT:After runing fsck, I can boot my computer without problems, and hav gone back to the usual little problems (random freeze for everything but the mouse, and random full boot)
Thanks!

---

### Post by billlyum on 2009-11-25
fsck worked like a charm.  It basically asked me if I wanted to fix a bunch of stuff, all to which I say yes, and upon reboot everything worked perfectly.

Thanks for the tips!

---

### Post by icc4p on 2009-11-25
sorry for posting on solved topic. thx you for saving my ubuntu laptop

---

### Post by billlyum on 2009-11-26
So after working for a couple days I'm back to having the same issue I initially had. It started with certain folders and applications not opening and then upon restart the OS crashed w/ the same type of errors as in the original post.  

This time FSCK found similar problems but with different #'s (ie: *Inode 221201 was part of the orphaned inode list. FIXED.* but in the first fsck it was a different inode #)

Any thoughts?

---

### Post by cariboo on 2009-11-26
Go to System-->Administration-->Disk Utility and check the health of your hard drive.

---

### Post by F for Fragging on 2009-12-28
I&#8217;ve encountered this problem yesterday. I was taking a look at many photos, (JPEG files) with Eye of GNOME, browsing through them rather quickly. When I finished seeing the photos in the directory, I went up a level in the directory tree in Nautilus, and then I notice that the folder icon has a lock on it. I check permissions, but they are normal, so the lock shouldn&#8217;t be there. I enter the directory again and try to view the photos again, but they wouldn&#8217;t open.

After googling for this problem I&#8217;m happy I&#8217;m not the only one who has seen this, because I read some problem descriptions which match mine. After they wouldn&#8217;t open I decided to reboot, and encountered the UNEXPECTED INCONSISTENCY message after a refusal to mount the root partition. I repaired it with fsck.

After fsck did it&#8217;s job I thought everything was fine and Ubuntu booted normally again. I start browsing through the same photos again, and guess what, exactly the same happens once more! The cycle repeated and again I had to repair with fsck.

After that I simply decided to delete the affected/cursed directories containing the photos, didn&#8217;t need them any longer anyway. Since then the problem hasn&#8217;t turned up, but I&#8217;m scared to start viewing my photos again...

This bug &#8211; I assume it is a bug &#8211; frightens me. I followed the previous comment and used the Disk Utility, but that reports my disk is perfectly healthy. I expected nothing else, because I&#8217;m dual booting the machine with Windows 7 besides Ubuntu 9.10, Windows 7 never had any problems.

I&#8217;m sure it can&#8217;t be my hardware, Ubuntu must be culprit. Does anyone know a Launchpad bug number? Google didn&#8217;t show me any.

EDIT: a more [refined]("http://www.google.com/search?hl=en&safe=off&client=firefox-a&rls=com.ubuntu%3Anl%3Aofficial&q=site%3Alaunchpad.net+unexpected+inconsistency&aq=f&oq=&aqi=") google search query did reveal some bugs. [This]("https://bugs.launchpad.net/ubuntu/+bug/423925") one, [this]("https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/432070") one, [this]("https://bugs.launchpad.net/ubuntu/+bug/95026") one and [this]("https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/48563") one. I suspect that this is a very difficult bug to hunt down though, because at least I can&#8217;t reproduce it reliably.

EDIT: the two bug reports which matter most seem to be [#423247]("https://bugs.launchpad.net/ubuntu/+source/clock-setup/+bug/423247") and [#268808]("https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/268808"), these have many duplicates. Also, they are marked as fixed in 9.10, but we all still seem to be affected by this bug in 9.10.

---

