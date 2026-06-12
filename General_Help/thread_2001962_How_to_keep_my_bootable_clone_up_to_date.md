---
title: "How to keep my bootable clone up to date?"
date: 2012-06-11
forum: General Help
---

### Post by NTL2009 on 2012-06-11
I finally managed to make a bootable clone of my old and new systems (I moved from Ubuntu 10.04 to Xubuntu 12.04). It was important to me to be able to boot the clone with the original system drive still installed, so I had to modify the UUIDs, etc/fstab, and /etc/initramfs-tools/conf.d/resume, and then perform update-initramfs, grub-install and update-grub on the clone. 

So keeping my documents up-to-date should be simple with Grsync. I think that should work for /home to capture any setting changes. 


**But... what about /root?** Seems like if I get updated to a new kernel on the running system, that will cause changes to some boot files, over-writing the UUID changes on the clone when I Grsync, making my clone un-bootable. :( If I exclude those boot files, I won't get the kernel update (right?). 

Is there any alternative to the fstab & resume file edits, and the update-initramfs, grub-install, and update-grub dance? I'm making lots of changes as I set up my system, so I want to back up the system/config frequently for now. I'm considering making a script to automate that (but I have little scripting experience). Or am I missing the boat somewhere? 

NTL2009

---

### Post by oldfred on 2012-06-12
I am not a fan of RAID, but that sounds like what you want - RAID 1.
[http://en.wikipedia.org/wiki/Standard_RAID_levels](http://en.wikipedia.org/wiki/Standard_RAID_levels)
[https://help.ubuntu.com/12.04/serverguide/advanced-installation.html](https://help.ubuntu.com/12.04/serverguide/advanced-installation.html)

I do not have to immediately reboot. I can install in less than an hour and use rsync to backup /home and other settings so I can have the system restored fairly quickly.

---

### Post by wilee-nilee on 2012-06-12
I do as oldfred suggests as well using a rsync gui only called grsync very so often fore home and clone every so often. The rsync makes a copy of home that is accessible it is not compressed if run with this in mind.

I also keep a list of all installed apps with a reload option, and the sources list, and the sources.list.d backed up as well. My reinstalls are short and painless.

I found out how to do this recently and thought it might be helpful to some people. To output this information to a file in your home directory you would use,

Code:
dpkg --get-selections > installed-software

And if you wanted to use the list to reinstall this software on a fresh ubuntu setup,

Code:
dpkg --set-selections < installed-software

followed by
Code:
dselect

dselect needs to be installed is all on a fresh install.

Finally I use clonezilla as a cloner, I like it as it saves the mbr as well.

---

### Post by NTL2009 on 2012-06-12
[COLOR="Red"][ edit - cross-posted with **wilee-nilee** ][/COLOR]So maybe this approach would be better:

[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)

Basically, I'd start with a fresh install, then grsync /home, and then follow that procedure to get a package list and sync the installed apps. I would want to do this by copying the packages, my internet connection isn't so fast, it could take a long time to download again.

I'll do more reading, but I'm assuming/hoping this could be done incrementally - if I had installed just two apps in between syncing, the 'clone' would just pick up those two new apps?

My other assumption is that all the settings/configs I need are in my /home (customization that I've done), so this would get everything looking identical on the two systems?

If this works smoothly, no partition size matching required, no UUID conflicts - that's good, IMO.


NTL2009

---

