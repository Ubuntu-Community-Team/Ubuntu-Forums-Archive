---
title: "Can't login - failed to load module 'dri', no space left on device"
date: 2011-07-03
forum: General Help
---

### Post by SydneyGB on 2011-07-03
I'm unable to login to my Kubuntu Lucid.  The login screen takes my password, blanks, then returns me to the login screen.  I'm  getting some graphics errors when running from recovery mode as well as the no space left on device error when attempting to start x from the terminal.  Here are some outputs:

When starting from recovery mode, selecting failsafeX from the Recovery Menu: 

> Ubuntu is running in low-graphics mode

The following error was encountered.  You may need to update your configuration to solve this.

(EE) Failed to load module "dri" (module does not exist, 0)
(EE) RADEON(O): [dri]RADEONDRIGetVersion failed (libdri too old)
(EE) RADEON(0): Acceleration initializatoin failed
(EE) GLX erro: Can not get required symbols.

When I choose Run Ubuntu in low-graphics mode for just one session, I get a different login screen to what I'm used to and an error box pops up in the corner, telling me the configuration defaults for GNOME Power Manager were not installed properly.  I cannot login from this screen either.  It takes the password, blanks, and returns to this login screen, as with the regular login.

In terminal mode, I can login successfully. kstart returns "cannot connect to X server".  When I try to startx, I get the following errors:

> /usr/bin/startx: line 155: cannot create temp file for here-document: No space left on device
/usr/bin/startx: line 171: cannot create temp file for here-document: No space left on device
/usr/bin/startx: line 171: cannot create temp file for here-document: No space left on device

Fatal server error:
Server is already active for display 0
  If this server is no longer running, remove /tmp/.X0-lock and start again.

ddxSigGiveUp: Closing log
No protocol specified
giving up.
xinit: Resource temporarily unavailable (errno 11): unable to connect to X server
xinit: No such process (errno 3): Server error.

df -h:

> Filesystem            Size Used Avail Use% Mounted on
/dev/sda4              97G   94G     0 100% /
none                  1.8G  328K  1.8G   1% /dev
none                  1.8G     0  1.8G   0% /dev/shm
none                  1.8G  292K  1.8G   1% /var/run
none                  1.8G     0  1.8G   0% /var/lock
none                  1.8G     0  1.8G   0% /lib/init/rw
/dev/sdc1             3.8G  1.7G  2.2G  45% /media/usb


fdisk -l: 
> 
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf5623874

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6        1918    15360000    7  HPFS/NTFS
/dev/sda3   *        1919       25533   189687487+   7  HPFS/NTFS
/dev/sda4           25534       38391   103281885   83  Linux

Disk /dev/sdc: 4041 MB, 4041211904 bytes
128 heads, 63 sectors/track, 978 cylinders
Units = cylinders of 8064 * 512 = 4128768 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04dd5721

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         979     3946464+   c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(977, 127, 63) logical=(978, 101, 37)


I ran du -k in root, but the output is very large.  Is there a specific part of the output I should be looking at, or should it be run from a different directory?

I've come to the conclusion that my root partition is full, but I'm not sure how to clear space, or how much to clear once I work out how to do it.  I removed a few packages with apt, but it doesn't seem to have any effect.  df -h shows that root is 100% full, yet it has 3GB free.  I've grown comfortable with Ubuntu in the couple years I've been using it, yet this level of problem-solving is a bit nerve-wracking to me.  I've been considering reinstalling (this machine is running Lucid upgraded from Karmic and Jaunty and has a few oddities), but I hate the idea of being forced to reinstall because I can't overcome this problem.  I'd greatly appreciate any input you folks can give me on this.  If you need any other information or outputs from terminal commands, I'm happy to provide it.

---

### Post by TeoBigusGeekus on 2011-07-03
Can you post us the output of
```
cd /
du -h --max-depth=1 2>/dev/null | sort -h
```

---

### Post by SydneyGB on 2011-07-03
> **TeoBigusGeekus said:**
> Can you post us the output of
```
cd /
du -h --max-depth=1 2>/dev/null | sort -h
```

Thanks for the reply!  I ran it with sort -n.  I dunno if your -h was a typo, but I've got no -h switch for sort. :)
> 0     ./proc
0     ./sys
4.0K     ./.kde
4.0K     ./mnt
4.0K     ./root
4.0K     ./selinux
4.0K     ./.Trash-0
5.9G     ./usr
6.6M     ./bin
7.8M     ./sbin
8.0K     ./.config
15G      ./home
16K      ./lost+found
20M      ./etc
22G      .
28K      ./media
40K      ./tmp
113M     ./boot
208K     ./srv
308M     ./opt
316K     ./dev
589M     ./var
847M     ./lib

The big files here are obviously /usr and /home.  But what is . and why the heck is it so big?

---

### Post by TeoBigusGeekus on 2011-07-04
> **SydneyGB said:**
> I dunno if your -h was a typo, but I've got no -h switch for sort.
Not a typo; you will have this option in the future, perhaps when lucid updates its coreutils. It's human readable size sorting.


> **SydneyGB said:**
> The big files here are obviously /usr and /home.  But what is . and why the heck is it so big?
. is the current directory. So your /root partition is reported by du to use 22gb.
df on the other hand reports the root partition to be 94gb.
I smell something fishy...

When in terminal mode, run
```
sudo rm /tmp/.X0-lock
```
and then
```
startx
```
Post back with the result.

---

### Post by SydneyGB on 2011-07-04
> **TeoBigusGeekus said:**
> 
. is the current directory. So your /root partition is reported by du to use 22gb.
df on the other hand reports the root partition to be 94gb.
I smell something fishy...

When in terminal mode, run
```
sudo rm /tmp/.X0-lock
```
and then
```
startx
```
Post back with the result.

After removing the .X0-lock and running startx I get basically the same error message as above, with these additions:

> _XSERVTransSocketUNIXCreateListener: ...SocketCreateListener() failed
_XSERVTransMakeAllCOTSServerListeners: server already running

Fatal server error:
Cannot establish any listening sockets - Make sure an X server isn't already running

Please also check the log file at "/var/log/Xorg.0.log" for additional information

The Xorg-0.log mentions the _XSERV errors above.  At the bottom are these lines:

> 
(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole:VT_GETSTATE failed: Bad file descriptor
 ddxSigGiveUp: Closing log

On a whim I did sudo killall XOrg and startx again.  My screen blanked but nothing else seemed to happen.  Switching back to Ctrl-Alt-F7 I see a heap of messages all over the screen, such as > * /etc/rc2.d/S19mysql: ERROR: The partition with /var/lib/mysql is too full!  Not starting Disabled via /etc/default/i8kbuttons.
*Not starting.  Disabled via /etc/default/i8kmon.
*Starting Samba 4 daemon samba
Unknown paramater encountered: "max log size"
Ignoring unknown parameter "max log size"

There were several 'ignoring unknown parameter' errors: syslog, passdb backend, unix password sunc, passwd program, pam password change, map to guest, usershare allow guests.  At the bottom of the screen is "[ OK ] Home directory /etc/timidity not ours."

On Ctrl-Alt-F1 (should I call that tty1?) are a heap of success messages and the repetition of "(EE) GLX error: Can not get required symbols".  I can't get back to a terminal prompt on that terminal, even with a Ctrl-C.  I logged in on tty2 and killed Xorg again.  On tty1 I now have: 
> xinit: connection to X server lost.

waiting for X server to shut down error setting MTRR (base = 0xe0000000, size=0x10000000, type = 1) Inappropriate ioctl for device (25)
ddxSigGiveUp: Closing log

xinit: unexpected signal 2.

Hope I didn't go too far/off in the wrong direction here.  Also hope some of these error messages mean something to you.

---

### Post by SeijiSensei on 2011-07-04
You must have some large files in the filesystem root.  Perhaps they're hidden?  Try "cd /; sudo ls -la" and see what's there other than the standard directories.  (The "a" option means "all" including hidden files.)

Some file transfer programs like rsync first create a hidden file for the destination data, then move it to replace the original.  If you interrupt a program like this, you can end up with large hidden files.

---

### Post by TeoBigusGeekus on 2011-07-05
Try what the previous post said; other than that... sorry, mate, I'm out of ideas.

---

### Post by SydneyGB on 2011-07-05
> **SeijiSensei said:**
> You must have some large files in the filesystem root.  Perhaps they're hidden?  Try "cd /; sudo ls -la" and see what's there other than the standard directories.  (The "a" option means "all" including hidden files.)

Some file transfer programs like rsync first create a hidden file for the destination data, then move it to replace the original.  If you interrupt a program like this, you can end up with large hidden files.

Here's the result of 'sudo ls -la' in root:
```
total 128
drwxr-xr-x  24 root root  4096 2011-07-02 10:43 .
drwxr-xr-x  24 root root  4096 2011-07-02 10:43 ..
drwxr-xr-x   2 root root  4096 2011-06-06 10:22 bin
drwxr-xr-x   3 root root  4096 2011-05-03 09:35 boot
drwxr-xr-x   2 root root  4096 2011-02-03 14:55 .config
drwxr-xr-x  18 root root  3960 2011-07-05 09:35 dev
drwxr-xr-x 173 root root 12288 2011-07-05 09:44 etc
-rw-------   1 root root   416 2010-01-13 13:52 Google-googleearth.desktop
drwxr-xr-x   6 root root  4096 2011-07-02 13:58 home
lrwxrwxrwx   1 root root    33 2011-04-29 18:37 initrd.img -> boot/initrd.img-2.6.32-31-generic
lrwxrwxrwx   1 root root    33 2011-03-21 07:57 initrd.img.old -> boot/initrd.img-2.6.31-23-generic
drwx------   4 root root  4096 2011-02-03 14:55 .kde
drwxr-xr-x  22 root root 12288 2011-06-15 09:53 lib
drwx------   2 root root 16384 2009-10-18 15:03 lost+found
drwxr-xr-x   6 root root  4096 2011-07-04 10:35 media
drwxr-xr-x   2 root root  4096 2009-04-13 05:33 mnt
drwxr-xr-x   5 root root  4096 2010-10-28 11:27 opt
dr-xr-xr-x 122 root root     0 2011-07-05 05:34 proc
drwx------  36 root root  4096 2011-07-04 10:45 root
drwxr-xr-x   2 root root  4096 2011-06-15 20:31 sbin
drwxr-xr-x   2 root root  4096 2009-03-06 11:21 selinux
drwxr-xr-x   4 root root  4096 2011-06-22 18:07 srv
drwxr-xr-x  12 root root     0 2011-07-05 05:34 sys
drwxrwxrwt   7 root root 16384 2011-07-05 09:34 tmp
drwx------   4 root root  4096 2010-10-18 10:43 .Trash-0
drwxr-xr-x  11 root root  4096 2011-02-03 15:13 usr
drwxr-xr-x  18 root root  4096 2011-06-15 10:22 var
lrwxrwxrwx   1 root root    30 2011-04-29 18:37 vmlinuz -> boot/vmlinuz-2.6.32-31-generic
lrwxrwxrwx   1 root root    30 2011-03-21 07:57 vmlinuz.old -> boot/vmlinuz-2.6.31-23-generic

```
I don't see anything phenomenally large, though I didn't poke into the subdirectories at all.  If I had the GUI running I'd have a go at it with Baobab.  But then, if I had the GUI running I wouldn't need your help.  :confused:

---

