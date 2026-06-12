---
title: "Upgrade from 11.10 to 12.04 failure"
date: 2012-06-07
forum: General Help
---

### Post by unitedanarchy on 2012-06-07
I tried upgrading from 11.10 to 12.04 but it failed, And I tried to copy the error so I could paste it here but it didn't actually copy for some reason so I don't have the original error report. But afterwards a bunch of WEIRD stuff happened, Like when I booted in it wouldn't do anything, It was just black. So I went into recovery mode and the root terminal and typed startx and it gave a weird error message, So I installed ubuntu-desktop because that apparently got removed. And when I started it everything was really weird and looked horrible. Things went black and were all glitchy, So I went into LXDE and so far everything is fine. I reinstalled ubuntu-desktop again to see if that would help. I went into aptitude multiple times and updated and tried to upgrade my stuff multiple times sudo apt-get update && sudo apt-get upgrade. And it worked, It just didn't really download anything so I don't think much is fixed what ever is broken. So now I tried to upgrade again in LXDE and now I have this error message 

Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
E:Unable to correct problems, you have held broken packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug using the command 'ubuntu-bug update-manager' in a terminal.


but aptitude and synpantic package manager both don't say I have broken packages so I don't know what it wrong.

---

