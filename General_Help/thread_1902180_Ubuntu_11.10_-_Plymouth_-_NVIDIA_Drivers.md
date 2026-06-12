---
title: "Ubuntu 11.10 - Plymouth - NVIDIA Drivers"
date: 2011-12-30
forum: General Help
---

### Post by stressed on 2011-12-30
Lately I've been forced to do quite a bit of research concerning NVIDIA drivers and Plymouth on Ubuntu 11.10.  This is for a standalone computer, not a laptop.  For whatever reason, if you install NVIDIA drivers for an NVIDIA chipset video card on Ubuntu 11.10, you will have an issue...  There seems to be several posts concerning this with no real good workaround.  Here is a link to the general problem:  [http://askubuntu.com/questions/68220/system-wont-boot-with-nvidia-driver-enabled](http://askubuntu.com/questions/68220/system-wont-boot-with-nvidia-driver-enabled) .  Forget about using CTRL-ALT-F1/F7 - video goes away completely and doesn't return.

At this link:  
[http://ubuntuguide.org/wiki/Ubuntu:Oneiric#Install_Latest_Nvidia.2FATI_drivers](http://ubuntuguide.org/wiki/Ubuntu:Oneiric#Install_Latest_Nvidia.2FATI_drivers) , it does state, "Plymouth does not reliably work with nVidia drivers and during bootup a blank screen may result for several seconds."  Several seconds really amounts to a bootup hang.  The user just can't get past the screen listed above.  There are some tips within this link, but from further research it doesn't look like they are very helpful.

So what's a user to do?  I come to the well of knowledge asking for help.  Yes, this occurs on a fresh install of Ubuntu 11.10, no upgrade.  Yes, I do have NVIDIA GPUs.  Yes, I do need the drivers for development/GPU use.  Have the Ubuntu developers not looked at this issue?  Have the Ubuntu developers decided not to provide a "patch" for this issue (sudo apt-get update/upgrade)?  Needless to say, this is very frustrating.  I'm relatively new to Ubuntu and I like what I see so far.  I don't want to have to do more research on finding a different distro to use if I don't have to.

Does anyone know of a fix for this issue?  Any suggestions would be helpful and I thank you in advance.

---

### Post by QIII on 2011-12-30
It is a problem.  If you can eventually get to the login screen you're fine for the moment.  I wouldn't give Ubuntu the boot because of it.  (But I wouldn't say you shouldn't try other distros, either.  In fact, I encourage that.)

Remember that "several posts" complaining about this does not give you visibility of the thousands of posts that aren't happening because others are not having the same problem.

But that doesn't mean it should be made light of.

---

### Post by dino99 on 2011-12-30
here is a temporary workaround until we get the numerous needed fixes:

sudo apt-get install  xserver-xorg-video-nouveau

[https://bugs.launchpad.net/bugs/+bugs?field.searchtext=nvidia&orderby=-date_last_updated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://bugs.launchpad.net/bugs/+bugs?field.searchtext=nvidia&orderby=-date_last_updated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)

---

### Post by stressed on 2012-01-02
dino99:  I can't get to a terminal after the driver is installed to even type in the syntax you provided.

I guess I'll have to just wait until the next version of Ubuntu is released to see if the issue is fixed there.  Until then, I don't know what to do.

I thank everyone for their responses though.

---

