---
title: "NVIDIA driver install failed, No boot"
date: 2011-01-24
forum: General Help
---

### Post by wannabegeek on 2011-01-24
hi all,

I am unable to boot at all after attempting an NVIDIA driver install following these instructions:
[http://www.ubuntugeek.com/howto-inst...ucid-lynx.html]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html")

I got the point where I run the script. Got an error that the script failed, do I want to try  to install anyways.
I clicked yes, then got another mnessage that Nouveau has a conflict with NVIDIA driver, do I want to 
add a file to modprobe configuration to attempt to disable Nouveau.

I click yes....install still fails and now no boot...
original post is:
[http://ubuntuforums.org/showthread.php?t=1674866](http://ubuntuforums.org/showthread.php?t=1674866)


your advice is appreciated,
wbg


EDIT: found modprobe.d in /etc and see a file called blacklist nouveau
gonna trash it and see if I can re-boot into OS

---

### Post by wannabegeek on 2011-01-24
deleting the .conf file at /etc/modprobe.d allowed me to boot again.

still need to figure out how to get NVIDIA driver installed....

---

### Post by tnngator on 2011-01-24
Nouveau is the open source version of the NVIDIA driver you can go to synaptic and completely remove it then install 3rd party drivers use the live cd to boot or reinstall since you cant boot

---

### Post by tnngator on 2011-01-24
BTW sudo apt-get upgrade will bring you to the present aka maverick  or should anyway

---

### Post by wannabegeek on 2011-01-24
thanks for reply...

I found an alternate instruction set....which ironicly didn't work as expected, but was able to skip steps .
For those who may find themselves here, this is the link.

[http://trycatch.iblogger.org/tips-n-tricks/how-to-install-nvidia-drivers-in-ubuntu-10-04-lucid-lynx](http://trycatch.iblogger.org/tips-n-tricks/how-to-install-nvidia-drivers-in-ubuntu-10-04-lucid-lynx)

The nvidia drivers are now showing up in the GUI for propritary drivers and my logout problems appears to have gone away.

---

