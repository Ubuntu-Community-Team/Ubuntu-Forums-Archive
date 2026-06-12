---
title: "HELP!!! Debian package manager crash!"
date: 2011-05-15
forum: General Help
---

### Post by Michelle Rachel Ellert on 2011-05-15
ARG! PLEASE HELP! DEBIAN PACKAGE MANAGER BUG!?
The package manager is scrambled in my Ubuntu 11.04.
It started with the repositories list being scrambled with multiple entries.
Now when the Package Manager is launched it just accesses the hard drive forever.
I did give it a half an hour just in case so it clearly stuck in a loop of some
kind.
What I'd like to know is: Is there some way to reset, clear, turn off or
de-select the added Repositories list from the command line (terminal.)
This seems to be the only way since the Package Manager gets stuck. And, yes, I
do belive I did give it adiquate time. 10 minutes of disk thrashing should be adiquate. 
Keep in mind that I'm only slightly competent with Linux and have no idea where
the Debian Package Manager data is located or how it works.
If I go poking around without at least some guidance I may make things
worse.
Please respond to: [email]michelleellert1956@gmail.com[/email] (preferred) or
[email]michelleellert@yahoo.com[/email]

Update: The problem seems to be spreading. Got stuck again while saving this
message. Turned off the system, rebooted to recovery mode and did a file system
check. Okay for now. Switching to clean OS on other partition.

I'll check for answers there but it's only Ubuntu 10.04 and I'd very much
prefer to have 11.04 working and not have an effectively dead partition and don't
want to loose everything on it with a re-format and 2 day re-install process
(no installation disk.)
---------
I tried removing all entries in "/etc/apt/sources.list.d/" text files. They did appear to be the appropriate references. However, the problem remains. In Package Manager I get a "duplicate references" error and then endless (over 15 minutes) disk thrashing. judging from the slight occasional flash of the drive light it's just doing the same seek endlessly. Seems this is a Ubuntu Package Manager problem not Debian.

Maybe a workaround update from command line would be useful though not a fix.
Any ideas?
MRE

---

### Post by Michelle Rachel Ellert on 2011-05-16
I meant no disrespect by posting my email address. I'm new to this forum thing and will try to stick to protocol in the future.
I went to the Debian forum and was told to go to the Ubuntu forum then told to go to Debian. 
Anyway. It does seem to be an Ubuntu Package Manager problem since after clearing all repository references in "/etc/apt/sources.list" I still get the "Duplicate Resource."
Since this is immediately followed by total lock-up requiring power down I am unable to reprint the error message verbatim here. I could copy it down by hand but don't really want to run PM again since I have to do a Rescue Mode file system check after powering down and the stress on the computer and myself is something I'd like to avoid if possible.
Apparently PM maintains it's own repository list that has become circular (just an educated guess.)
Thank you and I'll check back later.
MRE

---

### Post by oldos2er on 2011-05-16
Let me see if I'm understanding you correctly. You have two separate installs of Ubuntu 10.04 and 11.04, and 11.04's package management is unusable, is that right? Disk-thrashing sounds like a potential hard disk problem not related to your package manager though, but it's hard to say. 

You can generate a new sources.list here: [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

Could you please list your hardware specs, and post the output of ```
sudo fdisk -l
```

---

