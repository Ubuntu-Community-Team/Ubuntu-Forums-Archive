---
title: "Boot freeze! Total system failure!?!"
date: 2009-08-23
forum: General Help
---

### Post by stozi on 2009-08-23
If I hit alt+crtl+f1 just as the boot progrss bar appears and freezes, I get> Starting up...
[ 5.150764] longhaul: APIC detected. Longhaul is currently broken in this configuration.
Loading, please wait...
19+4 records in
19+4 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/e67ee425-9f98-4682-bad4-419dav383a49)=dev(8,1)
kinit: trying to resume from: /dev/disk/by-uuid/e67ee425-9f98-4682-bad4-419dav383a49
kinit: no resume image, doing normal boot...
runninit: /sbin/init: no such file or directory
[7.765118] kernel panic - not synching: Attempted to kill init!

Is this to do with the kernel update yesterday which which seemed odd in not raising the version number? It booted up once, but nothing worked properly. Could an electrical problem (which I deem very possible) have caused a series of file system errors? Is there anything I can do except try to reinstall?

---

### Post by P4man on 2009-08-23
Im guessing the kernel upgrade didn't go well?
 
If you boot from a live cd can you verify /sbin/init really doesn't exist?
In fact, check if you can mount the drive at all.

---

### Post by stozi on 2009-08-25
so can I fix it with a cd?

---

### Post by calrogman on 2009-08-25
When you see the boot timer, press 'Esc', then press 'e', go to the kernel line and press 'e' again, remove 'quiet splash' then press 'Esc', then 'b'.

Post some of the output, this will help us figure out what's wrong.

---

### Post by stozi on 2009-08-27
I couldn't get any output that way calrogman, still logo & progress bar... trying the recovery mode got some verbage though. 

[IMG]http://farm3.static.flickr.com/2667/3861493284_fc186d9139.jpg[/IMG]

I just bought a DVD drive (only $5, probably hot), but I hope I don't need to do a complete reinstall.

---

### Post by P4man on 2009-08-27
Looks like the kernel can't mount the root partition.
Could be a hosed filesystem or a bad drive.

Since you got a cd, boot from it, and see if you can mount the disk ?

---

### Post by stozi on 2009-08-28
I mounted it in the puppy livecd. At first it didn't show up there, but for some reason When I hit reboot, the screen just refreshed without rebooting, but with the drive suddenly there on the desktop, fully mountable. 

Now from the Xubuntu live cd it comes up if I try to install, saying 'this computer has ubuntu 9.04 on it' and shows ubuntu 9.04 on /dev/sda2. However, if I fumblingly do 'mount /dev/sda2' in terminal says it's not in /etc/fstab or /etc/mtab. However /dev/sda2, the swap, is in fstab. both say they are a 'block device.' 

much of that is likely inconsequential, I don't know.

Thanks for the help!!

---

### Post by P4man on 2009-08-28
that mount command you enteted is incorrect (without fstab entry). From a xubuntu live cd however, you shouldn't even need to. If you go to places, you should see the disk. click it once to mount it, click it again to open it.

If that fails, you can try this:

sudo mkdir /mnt/ubuntudisk
sudo mount /dev/sda2 /mnt/ubuntudisk

it should mount in /mnt/ubuntudisk

Once its mounted, have a look in the /sbin folder and verify if there is a "init" file. Make sure to check that on the ubuntu drive, and not the filesystem of the live cd (or puppy cd).

If it fails to mount, check it

```
sudo fsck -f /dev/sda2
```

You should run that when its not mounted, btw, if it is mounted, unmount it first (umount /dev/sda2)

---

### Post by stozi on 2009-08-28
there is an init file. sda2 doesn't come up in thunar on xubuntu livecd, I lazily just found it from puppy.

---

### Post by P4man on 2009-08-28
what happens when you try to mount the drive in xubuntu? Do you get an error message ?

Also, can you check the drive for errors in puppy?

---

### Post by stozi on 2009-08-28
fugg it bro, I'm reinstalling. Only program files there anyway. Thanks tho! If you know how to configure my usb wlan in ubuntu server that'd be great, because it couldn't in the install. it's realtek, so should be easy.

switched to #! Linux.

---

