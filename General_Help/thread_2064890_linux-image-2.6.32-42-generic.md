---
title: "linux-image-2.6.32-42-generic"
date: 2012-09-30
forum: General Help
---

### Post by gizzacroggy on 2012-09-30
Hi,

I have an issue with linux-image-2.6.32-42-generic.

I can no longer enter synaptic package manager and in ubuntu software centre the button to install new software is gone.

i have an error symbol (red no entry sign) due to only being able to do partial upgrades. When i click on it, it says:
"The package 'linux-image-2.6.32-42-generic' is in an inconsistent state and needs to be reinstalled, but no archive can be found for it. Please reinstall the package manually or remove it from the system."

I tried removing it - 
claire@claire-laptop:~$ sudo remove linux-image-2.6.32-42-generic 
[sudo] password for claire: 
sudo: remove: command not found
claire@claire-laptop:~$ sudo apt-get remove linux-image-2.6.32-42-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package linux-image-2.6.32-42-generic needs to be reinstalled, but I can't find an archive for it.

Any suggestions? i have searched on forums but not found anything specific to this,

Thanks

Claire

---

### Post by Iowan on 2012-09-30
Similar thread here:
[http://ubuntuforums.org/showthread.php?p=12266575#post12266575](http://ubuntuforums.org/showthread.php?p=12266575#post12266575)

---

