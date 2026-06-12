---
title: "Can I use Ubuntu to rescue infected XP"
date: 2012-02-23
forum: General Help
---

### Post by hwally on 2012-02-23
I have a dell desktop with xp is there a way to use Ubuntu to clean out any viruses or trojans that may be infecting it.

---

### Post by mardybear on 2012-02-23
Howdy.

Booting Linux from a liveCD should allow you to access/change/delete any desired files. Ubuntu has a liveCD download, so does Puppy Linux...i'm sure there are others. From my experience, Puppy Linux basically gives you full control/access over your hard drive data.

This would, however, be a manual process, not automated like Spybot or an antivirus program. This method would, therefore, only be practical if you knew exactly which file(s) you wanted to remove.

Also, if you use this method be careful what you delete as your actions could make the operating system inoperable. When in doubt simply rename suspect files rather than remove (eg. change virus.exe file to virus.exe.old), as they they can then always be permanently deleted later.

I don't know anything about bootable anti-virus software, maybe Google or someone else could help.

mardybear

---

### Post by mastablasta on 2012-02-23
I think redobackup based on ubuntu has some cleaners/repair utilities.
 
but anyway if you stay with ubuntu - i would suggest using Xubuntu for this (as it is lighter on resources and less likely to have any issues with graphcis card etc.). putting it on USB instead of on CD (you can use linuxliveusb or unetbootin) and create a persistant drive. this way you can install to this live OS and keep the instalation on it. you can install antivirus software (here is more info on AV software in Linux: [https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)).
 
otherwise normal Live media (liveCD or Live USB without persistance) boot the whole system into RAM and when you go out all changes are lost. with persistant USB changes remian on the liveOS.
 
in both cases you can then mount the disk or do virus scan/cleaning on it.
 
oh i think redobackup works better (only?!) from CD.

---

### Post by dragonfly41 on 2012-02-23
This article suggests one approach ..

[http://www.howtogeek.com/howto/14434/scan-a-windows-pc-for-viruses-from-a-ubuntu-live-cd/](http://www.howtogeek.com/howto/14434/scan-a-windows-pc-for-viruses-from-a-ubuntu-live-cd/)

[http://www.avast.com/linux-home-edition](http://www.avast.com/linux-home-edition)

but one of the comments to this article suggests using WinPE

[http://apcmag.com/windows_pe_20_a_tiny_version_of_windows_for_system_maintenance.htm](http://apcmag.com/windows_pe_20_a_tiny_version_of_windows_for_system_maintenance.htm)

I haven't tried either approach but since I've got Vista / Ubuntu in dual boot I might try this out .. as an insurance policy in case Vista gets hit.

For virus scanning I use AVG in Vista and nothing in Ubuntu.


[EDIT]

I've just tried installing Avast on ubuntu 10.10 but it didn't install.

Looking at system requirements it reads ..
> 
Any Linux distribution (x86 platform only) with GLIBC version 2.1 or higher and pthreads libraries installedSo does Ubuntu have these installed (can't see them in Synaptics Package Manager)?


....

unetbootin has a Kaspersky option on the distro menu ..

....

---

### Post by muteXe on 2012-02-23
I have used this in the past:
[http://support.kaspersky.com/faq/?qid=208282173](http://support.kaspersky.com/faq/?qid=208282173)

---

### Post by Mark Phelps on 2012-02-23
+1 for the Kaspersky Rescue CD.

Avira also provides a free, downloadable antivirus CD image.

---

### Post by hwally on 2012-02-23
I'm amazed at your generous responses.  You've given me a lot to look into I'll keep you posted.  Thank you.

---

### Post by idoitprone on 2012-02-24
You can use clamav but this open souce antivirus pails in comparison to commerical such as karsparky

---

