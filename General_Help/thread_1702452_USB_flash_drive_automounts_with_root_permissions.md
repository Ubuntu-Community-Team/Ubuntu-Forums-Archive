---
title: "USB flash drive automounts with root permissions"
date: 2011-03-07
forum: General Help
---

### Post by MountainX on 2011-03-07
This is driving me crazy: sometimes when I insert any USB flash drive, it automounts and opens a root Nautilus folder! Talk about insecure!

Sometimes it will also give one of several different error messages. Just now, inserting a USB drive gave this error:

ROOT <-- title is set by Compiz & indicates this window has root permissions
Unable to mount KINGSTON
A job is pending on /dev/sdf1

**BUT, it does mount!**

I have also seen this error:
Unable to mount "2.0 GB Filesystem"
DBus error org.gtk.Private.RemoteVolumeMonitor.NotFound: The given volume was not found


The problem is inconsistent. When it is happening, if I reboot, the issue goes away and inserting media works normally (opens a normal non-root Nautilus folder). I'm not sure what triggers the issue to come back, but inevitably it does.

I happens with any media, so the problem is not the specific USB flash drive.

My first step was to change the permissions of /media to my user account. That's didn't resolve it. Then I removed a couple lines I had added to /etc/fstab**, but that didn't solve it.

Suggestions?

Here's what I looked at so far (without finding a solution):
USB automounts with root privileges as /media/usb0? [http://ubuntuforums.org/showthread.php?t=1605540](http://ubuntuforums.org/showthread.php?t=1605540) 
Can't unmount USB flash drive (needs root?) [http://ubuntuforums.org/showthread.php?t=665810](http://ubuntuforums.org/showthread.php?t=665810)
Mounting USB Drive without being root [http://ubuntuforums.org/showthread.php?t=116213](http://ubuntuforums.org/showthread.php?t=116213)
**usb hard drive mounts with root being the owner [http://ubuntuforums.org/showthread.php?t=372435](http://ubuntuforums.org/showthread.php?t=372435)**

> ** these are the lines I had in, but removed from, /etc/fstab:
#for security of shared memory
tmpfs /dev/shm tmpfs defaults,nosuid,noexec,rw 0 0

# use ramdisk for temporary files
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0

---

### Post by MountainX on 2011-03-08
Saw this news today: [http://www.h-online.com/open/news/item/USB-driver-bug-exposed-as-Linux-plug-pwn-1203617.html](http://www.h-online.com/open/news/item/USB-driver-bug-exposed-as-Linux-plug-pwn-1203617.html)

> MRW says that it has assembled a suitable USB device for this purpose, boasting in a Tweet of a "Linux plug&pwn".

Well, that's already happening to me even without "a suitable USB device." Any USB stick causes my system to open a root window without even asking for password!

---

### Post by MountainX on 2011-03-12
seriously need some help with this... or tell me where else I should ask the question please.

---

### Post by MountainX on 2011-03-26
bumping. Please suggest something, even if it is another forum where I should be posting this question. Thanks.

---

### Post by MountainX on 2011-03-29
Either this forum has died or my questions no longer fit the audience or something else mysterious is going on that is preventing people from seeing any questions I post... it would be funny except I really could use some help with these problems. Maybe I just need to pay Canonical for support. Maybe that was their plan all along? (Just kidding.)

---

### Post by Rebootkid on 2011-04-03
Not that its dead. I just don't have an answer for you yet.
In fact, I found this thread by looking for the solution for someone else.

Just to wrap my head around things, can you tail your messages file while you plug in the drive? I can try and draw commonalities and see if I can figure out an underlying issue.

---

### Post by MountainX on 2011-04-03
> **Rebootkid said:**
> can you tail your messages file while you plug in the drive? 

Yes, I'll do that when I'm back at my computer and post it. Thanks!

---

### Post by roshan18 on 2011-05-20
I have founded an alternative which mounts usb flash drives with user permissions (also posted here : [http://ubuntuforums.org/showthread.php?p=10839425&posted=1#post10839425](http://ubuntuforums.org/showthread.php?p=10839425&posted=1#post10839425))

**ALTERNATIVE : devmon (udisks wrapper)**
Install devmon ([http://igurublog.wordpress.com/downloads/script-devmon/](http://igurublog.wordpress.com/downloads/script-devmon/)) following the instructions : [http://igurublog.wordpress.com/downloads/ppa/](http://igurublog.wordpress.com/downloads/ppa/) ; instead of 'pcmanfm-mod', install 'devmon'.
There are options to customize, but I just used the default and launched the devmon as a background process through the command 'devmon &'.
USB flash drive automounts with user permissions. It can be unmounted through the 'Unmount' menu option on right-clicking the mounted USB flash drive. Note: I don't see a 'Safely Remove Drive' option in the menu, which was present in previous releases.
cdrom automounts. It can be unmounted through the 'Eject' menu option on right-clicking the mounted cdrom.
In System->Preferences->Startup Applications, I added the command 'devmon' with name "Devmon" so that the same command will be run automatically for every user session. However, this is restricted to the current user in which I added it. For 'Startup Programs for all current and future users', I found :
[http://ubuntuforums.org/showthread.php?t=1230487](http://ubuntuforums.org/showthread.php?t=1230487)
So I ran this command :
```
sudo mv ~/.config/autostart/devmon.desktop /usr/share/gnome/autostart/
```
Now, everything works as in previous releases, albeit the missing 'Safely Remove Drive' option.

---

