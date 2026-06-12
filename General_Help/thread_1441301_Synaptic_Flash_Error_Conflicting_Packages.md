---
title: "Synaptic Flash Error: Conflicting Packages"
date: 2010-03-28
forum: General Help
---

### Post by DanYeomans on 2010-03-28
[FONT=Verdana][SIZE=2]Hey everybody, every time I open up Synaptic Package Manager, I get the dialogue, "You have 1 broken package, use the Broken Filter to locate it." So I do, and I find flashplugin-nonfree. So I try to reinstall it, and the two packages that are installed are flashplugin-nonfree and flashpluin-installer. However, I always get this error message: 

> E: /var/cache/apt/archives/flashplugin-installer_10.0.45.2ubuntu0.9.10.1_amd64.deb: conflicting packages - not installing flashplugin-installerCan someone explain to me why I'm having this problem if possible, and, how I can fix it? I know it has SOMETHING to do with conflicting packages, of course.[/SIZE][/FONT]

---

### Post by efflandt on 2010-03-28
Try uninstalling flashplugin-nonfree and then see if you can fix flashplugin-installer.

flashplugin-nonfree was a transitional package not currently needed.  Maybe that is interfering with flashplugin-installer updates, or do you have some other flash plugin installed?

If you are using the real 64-bit flash per instructions elsewhere, you would be using neither flashplugin-nonfree nor flashplugin-installer (which is actually 32-bit flash with nswrapper).

---

### Post by DanYeomans on 2010-03-28
I do remember installing a flash deb, but It hasn't really worked, I want to uninstall everything flash right now so I can install this stuff right, but I can't locate the other version of flash.

---

### Post by windows_killer on 2010-04-20
Hi guys, 
I have the same problem with my Ubuntu 9.10. I am using 64-bit computer and 64-bit Ubuntu. When I tried to install Flashplayer I got the message

"E: /var/cache/apt/archives/flashplugin-installer_10.0.45.2ubuntu0.9.10.1_amd64.deb: conflicting packages - not installing flashplugin-installer "

I tried to un-install all flash-player by "Synaptic Package Manager" and even un-install firefox. Then re-install them back. But still got this problem. 

I have tried many way I could. But now I am stuck.

Any HELP please!

---

### Post by windows_killer on 2010-04-20
found the solution

[http://ubuntuforums.org/showthread.php?t=1435710](http://ubuntuforums.org/showthread.php?t=1435710)

---

