---
title: "General Permissions issue"
date: 2009-10-12
forum: General Help
---

### Post by elggarc on 2009-10-12
The other day I left my system running firefox for a few minutes. When I came back firefox was no longer running and from that point on my system has been screwed, but exactly what is wrong and why I cannot tell.

So, I will describe four examples of the symptoms I have observed and the limited investigation I have done.

**Observed symptoms**

1) Opening an odt document in OpenOffice results in the product briefly attempting to load before disapearing without displaying any message or error.

2) Opening the calculator results in just the outline of the application's dialog appearing with no controls displayed at all (ie no buttons, no textbox etc).

3) Opening the update manager does the same as the calculator.  Blank dialog.

4) On the first (and only the first) attempt to run firefox I get a message box pop up which states:

> Could not initialize the browser's security component. The most likely cause is problems with files in your browser's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the browser and fix the problem. If you continue to use this browser session, you might see incorrect browser behavior when accessing security features.

There is a mozillaZone article with a screenshot and various details on the message here:
[a mozillaZine article]("http://kb.mozillazine.org/Could_not_initialize_the_browser_security_component")

When I click OK to this message firefox disappears.

All subsequent attempts display a blank message box entitled "Closing Firefox", which doesn't even have an OK button.

**Investigation**

Following some research I have been leaning towards the problem being one of permissions.

Knowing very little about linux I changed the permissions on the root folder from 700 to 755 and the permissions on the proc folder from 555 to 755.  Following these changes Firefox continues to display the warning message at startup but now runs, although I suspect I cannot use SSL.

In case it helps (or anyone can spot something out of place), here is the original "ls -l" command output:
```
craig@elggarc4:/$ ls -l
total 84
drwxr-xr-x   2 root root  4096 2009-09-06 19:55 bin
drwxr-xr-x   3 root root  4096 2009-09-06 19:57 boot
lrwxrwxrwx   1 root root    11 2009-05-06 19:42 cdrom -> media/cdrom
drwxr-xr-x  15 root root  3920 2009-10-12 20:51 dev
drwxr-xr-x 144 root root 12288 2009-10-12 20:51 etc
drwxr-xr-x   3 root root  4096 2009-05-06 19:52 home
lrwxrwxrwx   1 root root    33 2009-09-06 19:57 initrd.img -> boot/initrd.img-2.6.28-15-generic
lrwxrwxrwx   1 root root    33 2009-05-09 22:22 initrd.img.old -> boot/initrd.img-2.6.28-12-generic
drwxr-xr-x  19 root root  4096 2009-09-06 19:56 lib
drwx------   2 root root 16384 2009-05-06 19:42 lost+found
drwxr-xr-x   3 root root  4096 2009-10-12 20:51 media
drwxr-xr-x   2 root root  4096 2009-04-13 10:33 mnt
drwxr-xr-x   3 root root  4096 2009-09-21 22:42 opt
dr-xr-xr-x 139 root root     0 2009-10-12 20:50 proc
drwx------  15 root root  4096 2009-07-25 15:21 root
drwxr-xr-x   2 root root  4096 2009-09-06 19:55 sbin
drwxr-xr-x   2 root root  4096 2009-03-06 16:21 selinux
drwxr-xr-x   2 root root  4096 2009-04-20 14:59 srv
drwxr-xr-x  12 root root     0 2009-10-12 20:50 sys
drwxrwxrwt  14 root root  4096 2009-10-12 20:52 tmp
drwxr-xr-x  12 root root  4096 2009-05-06 22:32 usr
drwxr-xr-x  15 root root  4096 2009-04-20 15:07 var
lrwxrwxrwx   1 root root    30 2009-09-06 19:57 vmlinuz -> boot/vmlinuz-2.6.28-15-generic
lrwxrwxrwx   1 root root    30 2009-05-09 22:22 vmlinuz.old -> boot/vmlinuz-2.6.28-12-generic

```

I'm using Ubuntu 9.04 and Firefox 3.0.13

Any assistance is greatly appreciated.

---

### Post by elggarc on 2009-10-12
Additional note:  I don't seem to have the "back" button enabled in Firefox anymore.

---

### Post by elggarc on 2009-11-11
Update:

I ran fsck which found and fixed a number of problems on the hard disk.
Various things to do with iNodes and orphaned linked lists.

This sorted the issues for a while.

I believe I have traced the ultimate cause of the problem to a hardware issue.  Swapping out RAM chips has certainly made a difference.

I believe this issue should now be considered closed.

---

