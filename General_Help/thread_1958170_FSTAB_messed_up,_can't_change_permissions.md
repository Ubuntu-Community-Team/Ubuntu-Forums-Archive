---
title: "FSTAB messed up, can't change permissions"
date: 2012-04-13
forum: General Help
---

### Post by hturbulence on 2012-04-13
Hi, I'm new to Ubuntu and Linux in general (I messed with it years ago).  I'm running 11.10 and messed up fstab.  I did create a .bak of it before I messed it up, but I cannot change the permissions to restore my backup. 

When I try running chmod on it, it says it's a read only file system.  I only created one user as administrator, so I should have the ability to change it.  Any ideas?

I can boot into recovery mode, but not into the GUI.  So in recovery mode, I tried copying my bak over the messed up file, but can't.  Then I tried using gedit to undo what I know I messed up, but it says can't start display.  Any help here would be awesome, too!

Thanks!  :oops:

---

### Post by matt_symes on 2012-04-13
Hi

The easiest way to do it may be from a LiveCD/USB.

Kind regards

---

### Post by hturbulence on 2012-04-13
Blah, I was hoping to find a different way so I could learn some commands.  So if I boot from a live CD, I'll be able to access the ubuntu partition?  Will ubuntu automatically mount a local drive when it boots from a CD, or would I have to do it myself?

---

### Post by oldfred on 2012-04-13
You can do it with command line. I did not want to rename my fstab, so I named my backup to back. If you use man to review a command use q to quit.
```

fred@fred-MavericDT:~$ cd /etc
fred@fred-MavericDT:/etc$ ls fst*
fstab  fstab.backup
fred@fred-MavericDT:/etc$ man mv
fred@fred-MavericDT:/etc$ sudo mv fstab.backup fstab.back
[sudo] password for fred: 
fred@fred-MavericDT:/etc$ ls fst*
fstab  fstab.back

```

Best to confirm that it is still ok.
sudo mount -a
If no typos it just remounts everything or gives errors that you have to fix before rebooting.

You also can use 
gksudo nautilus

but you have to be careful not to modify anything else as you can move any system file.

---

### Post by matt_symes on 2012-04-13
Hi

> **hturbulence said:**
> Blah, I was hoping to find a different way so I could learn some commands.  So if I boot from a live CD, I'll be able to access the ubuntu partition?  Will ubuntu automatically mount a local drive when it boots from a CD, or would I have to do it myself?

You can remount the drive rw if it is being mounted read only when you boot.

```
sudo mount -t <fstype> -o rw <devicename> <mountpoint>
```so something along the lines

```
sudo -t ext4 -o remount,rw /
```may work as long as you do not get device busy or read only errors. If you do then use the n option of mount if /etc/mtab is readonly.

```
sudo -t ext4 -**n**o remount,rw /
```That may work. Try it and see as i would be interested to know if it works.

Kind regards

---

### Post by hturbulence on 2012-04-13
Thanks for the advice.  Neither Fred's nor Matt's worked :(

Fred, I kept getting the "read only" error.  Matt, I kept getting an error that certain devices were busy.  I tried killing the processes on those devices, but still nothing.

I did learn a little bit, though, which is cool.  I used the WUBI isntaller, so I'm going to uninstall it and reinstall it.  Now that I understand how the WUBI installer works, I'm going to do an actual install.  I didn't know that it just put an image on the hard drive that it mounted.

---

### Post by oldfred on 2012-04-14
If my instructions did not work, then you needed Matt's first. 

I did just have my 12.04 come up read-only as I was adding settings for SSD and one did not work. So when I re-booted it was read only. I ad to experiment which fstab entry was wrong, as I thought I needed all of them, but was able to fix fstab & then it worked again. But I did all that from another install, by mounting it and then running instructions like I posted.

---

