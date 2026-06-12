---
title: "Can't solve boot errors -- likely Plymouth problem"
date: 2011-12-11
forum: General Help
---

### Post by marrabld on 2011-12-11
I have been having problems with plymouth for a while now, every since I upgraded to 11.10.  Possibly because I have the proprietary Nvidia drivers installed.

My errors began when pylmouth would just drop to a blank screen complaining about something (sorry didn't write it down) but I was able to <ctl><alt> F1 to get to terminal and start lightdm from the command line.

This morning even that stopped working, when I boot I get the error

```
mountall: symobl lookup error: mountall: ply_boot_client_flush()
```

I cant get force a fdsck as I get a "read only file system" error if I try it from a recovery.  And I can't mount my file system at all.

Booting from a live USB allows me to touch <mount point>/forcefdck  But rebooting doesn't change anything.

As a last resort, I tryed renaming my 

/sbin/plymouthd to 
/sbin/__plymouthd  

But when I reboot, plymouth still gives me the error.  And yes, I made sure /sbin/plymouthd was removed.

If I try and update grub with something like without quite splash from a recovery console, I get the old read only file system junk.

Any ideas or help would be greatly appreciated.

---

### Post by marrabld on 2011-12-12
Furthermore,  If I boot from liveCD  I can't unencrypt my home folder.  I can mount my private directory but all of the filenames are screwed up.  The disk utility says the file system check is fine and their is no problem with the disk.

sudo apt-get reinstall mountall plymouthd 

seems to reinstall, but same error.

non of the other linux images allow me to boot, except one of the old one does give me a splash screen.  But just hangs with the same error when I ctl alt F1.

Any advice?  I have my uni work on there I need to get one with.  Yes I have backups of my major files, but there may be some I haven't.  So a re-install is really my last resort.

---

### Post by marrabld on 2011-12-12
Okay, I got my folder decrypted.  I used

```

chroot /media/<drive>
sudo ecryptfs-recover-private 

```


But I had to 

```
  
chown root:root /usr/bin/sudo
chmod 4111 /usr/bin/sudo

```

So I am backing up my home folder.  But I still can't fix the boot problem.  I would rather not do a complete install as I have LOTS of data to transfer and LOTS of programs to download on little bandwidth to get back to where I was.

---

