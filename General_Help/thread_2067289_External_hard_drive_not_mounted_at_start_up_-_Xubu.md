---
title: "External hard drive not mounted at start up - Xubuntu 12.04"
date: 2012-10-06
forum: General Help
---

### Post by windyrij on 2012-10-06
Hello:
I have seen this problem on 2 systems running Xubuntu 12.04, a new Lenovo Core i3 laptop and an older AMD64 desktop. It does not happen with Xubuntu 10.04.2.

When the system is started, the external hard disk (WD Elements 1TB) is recognised - icon on desktop -, but not mounted. The external drive can be mounted from the desktop icon.  If the drive is hot-plugged when the system is running, it is recognised and mounted.  As I use Simple Backup to run every day at a fixed time, the external drive needs to be mounted. The system is not run 24/7, so the drive needs to mount at start up.

I have tried adding an entry to etc/fstab, using UUID. When re-booted, the drive was not recognised (missing from desktop).

```
UUID=94D0D34CD0D332EA /media/ext_backup ntfs defaults
```    ( UUID from sudo blkid, /ext_backup created in /media first)

I have installed mountmanager, and run through the USB wizard, but the drive is still not mounted at start up. mountmanager shows the drive (sdb1)
> Mount the partition during start of the operating system as checked.

Is this problem likely to be cured in  12.10?

Any assistance would be great - thanks

John

---

### Post by Backharlow on 2012-10-06
I have an Xubuntu 12.04 desktop - no external ntfs drive though. Maybe that fstab is getting run before the device gets mapped to /dev by the kernel? I would maybe try putting the mount command into a cron job, that runs after boot.
I know that Xubuntu 12.04 can mount ntfs at boot with fstab as in internal disk here.

---

### Post by drmrgd on 2012-10-06
Not having used Xubuntu, this might be a dumb question, but is the drive not mounting at startup, or is it mounting and just not putting the icon on the desktop?  I'm not sure how Xubuntu handles putting the icons on the desktop.  Just for sake of clarity, though, with the fstab entry still in place, check /media/ext_backup from the terminal or from your file manager to see if it's there.  If it is, then the drive is mounting at start up and that's not the problem.  

You can also check the mounted drives with:

```
cat /etc/mtab
```

just to see if it's in the list.

I'm wondering if there's a setting not correct in Xfce settings manager or Thunar (I sort of remember reading that something needs to be turned on to see removable devices on the desktop).

---

### Post by LewisTM on 2012-10-06
drmrgd is basically right. Xfce handles drives and icons differently than GNOME/Nautilus.

Any hot-pluggable or mountable drive will show up on the desktop. If you add it to fstab, it is no longer considered user hot-pluggable but rather part of the base filesystem. It will still appear wherever you set it to be mounted. 

If you want to have the old behavior of a desktop icon for your drive, and have it mounted at login, add this command as a Startup Application.
```
bash -c "gvfs-mount -d `readlink -f /dev/disk/by-uuid/94D0D34CD0D332EA`"
```
Or more simply 
```
gvfs-mount -d /dev/sd##
``` if you know your device location.

Cheers!

---

### Post by LewisTM on 2012-10-08
I just realized there is another, perhaps easier way to make you drive appear on the desktop.
If you follow Xfce's logic, anything user mountable should be displayed on the desktop. So adding the 'user' switch to fstab should do the trick:
```
UUID=94D0D34CD0D332EA /media/ext_backup ntfs defaults,**user** 0 0
```
As a bonus, any user can mount or unmount the drive without using sudo.

Cheers!

---

### Post by windyrij on 2012-10-09
Hello folks:

Thank you all very much for replying

Backharlow:
 I am sure that you are correct, it looks like fstab is getting read before the external hard drive has woken up.

Drmrgd:
1. /ext_backup is in /media.
2.  Here is the result of cat /etc/mtab:
(With the line UUID=........... added to ext/fstab, or the line suggested by LewisTM added to Application Autostart ```
&#65279;
bash -c "gvfs-mount -d `readlink...
```)
```
/dev/sda1 / ext4 rw 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
gvfs-fuse-daemon /home/john/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=john 0 0
/dev/sdb1 /media/Elements fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
```However, without the added line in Application Autostart, even with the edit to /etc/fstab to try to mount sbd1, there is no icon on the desktop.

LewisTM:
1. Thanks a lot for the line using gvfs, in Application Autostart. With this the external drive is listed in mtab, and right-clicking on the desktop icon gives the “Eject Volume” option.
2.  I tried adding ‘user 0 0‘ to the line in fstab as suggested, and removing the line using gvfs from Application Autostart, but the result was no icon for the drive on the desktop. So that line is removed from fstab, and the new line :
```
bash -c "gvfs-mount -d `readlink -f /dev/disk/by-uuid/94D0D34CD0D332EA`"
```replaced in Application Autostart.
 I have run Simple Backup to check that I can write a backup. It does write a backup to the specified folder on the external HD. Job done!
What is gvfs achieving here? Google has not given me an idea.

Many thanks to all of you for taking the trouble to reply. I’ll mark this solved. Thanks, folks,

John

---

### Post by LewisTM on 2012-10-09
Great!

Did you check to see if your drive was mounted in /media when using  fstab? It's still possible it does appear but is not shown on the desktop. That would change the problem from serious to purely cosmetic.

Anyways, GVFS is what gets called by Ubuntu when you connect to either a remote network share or a removable medium. It mounts a removable drive in /media if you connect it while Ubuntu is up, but it does not do it at login unless you force it with a gvfs-mount command. The same kind of command would also work for Windows shares or FTP sites and uses the GNOME keyring for caching passwords. Handy if you want to reconnect to remote shares at login, although I prefer to use Gigolo which does the same thing but will retry until the network becomes available.

---

### Post by windyrij on 2012-10-10
Hi, LewisTM

First, thanks for your explanation about gvfs, that makes it a lot clearer.

I tried including the line in fstab, to mount the external drive (Elements). The addition (.... gvfs...) to Application Aurostart was still enabled.

On reboot, Elements does not show up in /media, and no desktop icon. So what that tells me, I don't know.

Still, as the Application Autostart command cures the problem, I'm happy with that, but if you would like me to try anything else, let me know.

As an aside, my wife's new laptop uses a 500MB Seagate FreeAgent Godrive, which is USB powered. These will not work with Linux, due to a powersave system. Under Windows, this is not a problem. The fix for Linux is to run it in a Windows environment, go into the setup program on the disk and set the Sleep Time to Never, You probably know this on anyway, but it might help somebody, as Seagate are not Linux-friendly.

Thanks again,   John

---

