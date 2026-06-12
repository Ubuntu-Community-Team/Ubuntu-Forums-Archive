---
title: "Can't boot"
date: 2012-06-27
forum: General Help
---

### Post by Boppy3125 on 2012-06-27
I'm running a Mythbuntu server that has one drive for / and boot and such, then a pair of drives in a software raid.  This machine is both my MythTV backend recording TV and my home fileserver.  All other Ubuntu machines in the house mount an NFS share at boot.  Everything was acting up so I rebooted my server and it sat at the startup splash screen.  I then noticed one electrical outlet had the GFCI tripped that had one network switch on it.  Well, now I am still stuck, I have tried rebooting a couple of times but it doesn't make it any further.  My one Windows laptop is on my network just fine.  Other Android devices are fine, but all Ubuntu based systems can't boot.  I expect it comes down to this one server.

So, it is stuck at the splash screen.  I try ALT-F2 and get a blinking cursor at top and nothing else.  When I insert a USB drive, I do get some feedback on that screen, but still no login or anything.

When I try to ping my address I get response, so networking is up.

When I browse from my Windows machine I can see the Samba shares and access the files that are shared.

I guess I could boot with a live USB Ubuntu to fix things if I knew what to look at.  Can anyone help me further?

---

### Post by Boppy3125 on 2012-06-27
I just booted off live USB and then installed gparted to remind myself of my partition layout.  Looks like I created a mirrored boot partition.  So I think I need to install mdadm to be able to look for logs and look at the config files...  I am googling for that now, but I could still use some assistance for knowing what to look for once I get that mounted...

---

### Post by Boppy3125 on 2012-06-27
So I now have mdadm installed, array assembled, and now mounted.  So I am looking for any advice on what I can look at to tell me where my issue is on boot...  Anyone know the boot process?

---

### Post by Boppy3125 on 2012-06-27
OK, so nothing interesting that I see under the /var/log directory that is getting updated on this boot, all timestamps here look like they are from the day I did the initial reboot.  What can I do with grub to help me see what is happening?  I don't think I mentioned that I am on 12.04 Mythbuntu.

---

### Post by vidtek on 2012-06-28
> **Boppy3125 said:**
> OK, so nothing interesting that I see under the /var/log directory that is getting updated on this boot, all timestamps here look like they are from the day I did the initial reboot.  What can I do with grub to help me see what is happening?  I don't think I mentioned that I am on 12.04 Mythbuntu.

Boppy-  No-one seems to be assisting you with this, so I'll stick my 5 eggs in.  Have you tried update-grub?  It may be as simple as running this.  You will have to do it from a live cd/dvd and a chroot environment to make it work. run blkid or fdisk -l as root to see which sd(x) is.
```
mount /dev/sdx /mnt
mount --bind /dev /mnt/dev
mount --bind /dev/pts /mnt/dev/pts
mount --bind /sys /mnt/sys
mount --bind /proc /mnt/proc
chroot /mnt 
```
#I think, trying to remember off top of my head
this gets you into your system, then you can run  ```
update-grub
```and```
grub-install /sdx
```

Get out of the chroot environment with cntl-d

and gracefully unmount 
```
umount /mnt/dev/pts
umount /mnt/dev
umount /mnt/sys
umount /mnt/proc
umount /mnt

```
reboot.

Let us know.
Tony.

---

### Post by Boppy3125 on 2012-06-28
Thank you for your response.  I was able to tweak what you gave me and reinstall grub.  (Some sudo and changing out md0 and finally pointing to each my drives rather than partitions)

No joy though.  It is still stuck on the mythbuntu splash screen with the dots going by.  They just keep marching by, but I don't make any progress...

Again, network seems to be up, samba server seems to be up, but that seems like all.  Based on what I just tried I think the filesystem for boot seems intact.  I just wish I could find some logs that could tell me what is happening.  

I guess maybe tomorrow night I will try to go back to my live USB env and mount the md0 dev again, and add an export of / so I can try to mount that from another computer while it is in this state.  But that will be tomorrow.

Thanks for the idea Tony.

---

### Post by vidtek on 2012-06-28
> **Boppy3125 said:**
> Thank you for your response.  I was able to tweak what you gave me and reinstall grub.  (Some sudo and changing out md0 and finally pointing to each my drives rather than partitions)

No joy though.  It is still stuck on the mythbuntu splash screen with the dots going by.  They just keep marching by, but I don't make any progress...

Again, network seems to be up, samba server seems to be up, but that seems like all.  Based on what I just tried I think the filesystem for boot seems intact.  I just wish I could find some logs that could tell me what is happening.  

I guess maybe tomorrow night I will try to go back to my live USB env and mount the md0 dev again, and add an export of / so I can try to mount that from another computer while it is in this state.  But that will be tomorrow.

Thanks for the idea Tony.

Boppy-

You've got the marching dots-you could try disabling the "quiet-splash" in the (once again from memory-hope I get it right-at work now with only windoze machines for company) /etc/default/grub.conf or cnf, and edit that file so you just get a text boot.

Hopefully it will hang at the salient point and give you a clue as to what gives.

Tony

---

### Post by Boppy3125 on 2012-06-28
That helped.  I have it fixed now.  Thanks.

For anyone coming across this later, some further detail...  So I needed to edit my mounted drive's /etc/default/grub file looking for GRUB_CMDLINE_LINUX_DEFAULT, changing "quiet splash" to "".  Oh, then I had to follow some steps from your #5 post of the mounts and chroot then I could sudo update-grub.  (I forgot to do that part first time and didn't understand why the splash was still happening.)

That allowed me to see the progress where I saw it hang for about 2 minutes starting NFS, then pop a message about a mount failing.  That was the issue.  I had recently shutdown my previous MythTV server, but this was the first reboot of the new server since that was shut down.  The mount was needed for migrating data over.  I just simply edited my /etc/fstab file and commented out that line.  Now everything is back running.

Ubuntu is trying to make everything user friendly by hiding all that boot progress, but that really makes it hard to see what breaks...

Thanks again for your help, Tony.  I couldn't have done it without your help.

---

### Post by vidtek on 2012-06-29
You're welcome, it's what open-source is all about.
Tony

---

