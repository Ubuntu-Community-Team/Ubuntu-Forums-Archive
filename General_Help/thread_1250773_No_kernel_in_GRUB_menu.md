---
title: "No kernel in GRUB menu"
date: 2009-08-26
forum: General Help
---

### Post by jacoblyles on 2009-08-26
I am using Ubuntu 9.04. I have had Ubuntu for awhile, and there were a ton of extra kernels in my boot menu, so I used synaptic to remove all the old ones. Now, there are no kernels that show up in my GRUB menu, only "Ubuntu 9.04, memtest86+' and Windows XP.


Did I accidentally remove the kernel I was using, too? If so, is there any way to get my computer to boot into linux again?

---

### Post by bchurchill on 2009-08-26
What you need to do is change /boot/grub/menu.lst to get your kernels back.  There are automated ways of doing this. 

Go into menu.lst and look for a section something like this:

```

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=2

```then change the 'howmany' value on _the last line_ to reflect the number of kernels you want (it will actually generate twice this number: one recovery and one normal).  If nothing like this is anywhere in your menu.lst, just skip to the next step.

then run 
```

sudo update-grub

```and choose the package maintainer's version.  If this doesn't work then post the contents of:

```

cat /boot/grub/menu.lst

```and

```

ls /boot

```

---

### Post by oldfred on 2009-08-27
You may be to the point that you have to reinstall. I removed gdm and gnome but from the command line was able to reinstall.

If they are all gone and not just missing from menu.lst.
You may try using the live cd to chroot into you machine and do a update.

I copied this from a grub update procedure:
1. Boot with any live CD 
2. Get a root shell and make a folder (mkdir ubuntu)
3. mount the root (/) partition of ubuntu (e.g. mount /dev/hda ubuntu 4. chroot the mounted partition (chroot ubuntu)
5. sudo apt-get update && sudo apt-get upgrade
5. Exit the shell
6. Reboot

Before you delete kernels you should run:
uname -r 
which tells you what you what version you are running. You can delete all others but it is best to keep at least one old one also just in case the current one has issues.

---

### Post by bchurchill on 2009-08-27
> **oldfred said:**
> You may be to the point that you have to reinstall. I removed gdm and gnome but from the command line was able to reinstall.

If they are all gone and not just missing from menu.lst.
You may try using the live cd to chroot into you machine and do a update.

I copied this from a grub update procedure:
1. Boot with any live CD 
2. Get a root shell and make a folder (mkdir ubuntu)
3. mount the root (/) partition of ubuntu (e.g. mount /dev/hda ubuntu 4. chroot the mounted partition (chroot ubuntu)
5. sudo apt-get update && sudo apt-get upgrade
5. Exit the shell
6. Reboot

Before you delete kernels you should run:
uname -r 
which tells you what you what version you are running. You can delete all others but it is best to keep at least one old one also just in case the current one has issues.

I'm not sure what you're trying to say.  If there are kernels remaining (my guess is there are) then they should not be deleted.  In general, you shouldn't delete the kernels you don't want unless you're really short on disk space; instead /boot/grub/menu.lst should be updated to hide these kernels from view.

If indeed there are no kernels in /boot, then you'll likely need to reinstall, but again, I'm pretty sure this is not the case.

---

### Post by nothingspecial on 2009-08-27
Have a look at [[COLOR="Magenta"]this[/COLOR]]("http://maratux.blogspot.com/2009/03/oops-removed-all-kernels.html")

---

