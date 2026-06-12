---
title: "Pysdm messed up usb external drive permission"
date: 2010-07-01
forum: General Help
---

### Post by Jasdev Singh on 2010-07-01
Hi, 

I installed Pysdm to automount an internal and an external usb harddrive. Theres nothing wrong with it, I just wanted it to mount at boot. 

After installing Pysdm (and not clicking anything), I just left everything at default. 

However, all is fine except that the USB drive suddenly is on read only mode now. I checked Psydm and true enough for some reason the option for "Mount System in Read Only Mode" came out. So I unchecked it, restart - nothing happens. Its the same. Tried all the other options too "umask for directory permissions in octal dmask=277" and the others too "umask=277, gid=users, fmask=227" but it came to a point that it doesnt even mount anymore. All same thing - whenever I tried to write unto the drive it says somewhere along the line (sorry cant give exact description now its not working) "you dont have permission" 

I've checked numerous forums and boards, in mounting and unmounting, checking filesystem (its fine) and I believe its a matter of permissions, I may be wrong - I dont know. Please help.

*Update
When I copy stuff to the drive it says "Permission Denied". In the Properties of the drive on 'Permissions' tab it says "The permissions of "sdc1" could not be determined.

---

