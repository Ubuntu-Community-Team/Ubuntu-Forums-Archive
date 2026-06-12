---
title: "Repairing/reinstalling HAL after disk rescue"
date: 2009-07-05
forum: General Help
---

### Post by alexander750 on 2009-07-05
Hello all...

I've got a rather thorny problem. Recently the hard drive in my Ubuntu box failed, causing a freeze during the boot process. Using the instructions for cloning a working Ubuntu installation (with [FONT=Courier New]ddrescue[/FONT]) I was able to get my machine up and running again.

Almost.

When booting, I briefly see the normal Ubuntu splash screen, and then the init process reverts to text mode. After this completes, X starts and the login screen appears, again apparently normally. But after I log in, I get an alert:

"Internal Error: Failed to initialize HAL!"

and I also have no network access. Anything involving shutdown or reboot is also very slow.

Booting from the Live CD (which gives me working Internet access), I was able to search for solutions on this site. After checking the usual suspects (damaged initrc, hardware going bad, etc.) and rechecking the old hard drive, the consensus appeared to be that I needed to repair or reinstall HAL somehow; instructions were provided for doing this via apt-get. The "gotcha" here is, without Internet access, ```
sudo apt-get install hal
``` will fail.

My question is, therefore, how can I reinstall HAL either (a) from the CD-ROM, or (b) while booted from the Live CD (which normally mounts the hard drive read-only)?

---

### Post by blueridgedog on 2009-07-05
You can boot off of the LiveCD and then chroot your existing file system, then reinstall hal (though I don't know if that will solve you problem).

The following assumes your internal hard disk with your non-booting / is mounted on /media/disk, adjust if it is otherwise or post the output of:
```

sudo fdisk -l
```

If you want help mounting it.

Once booted and satisfied you drive is mounted, you can do the following to switch to using the hard drive root fs:

```

sudo mount --bind /dev /media/disk/dev
sudo chroot /media/disk
```

At this point you can run atp-get commands on your non-booting file system, while using the network connectivity provided by the LiveCD.

Note that you may need the --reinstall option in apt-get.

---

### Post by alexander750 on 2009-07-05
Hello again, and thanks for the advice!

Unfortunately when I reinstalled HAL [FONT="Courier New"]apt-get[/FONT] exited with an error. Here's the code:

```

root@ubuntu:/# sudo apt-get install --reinstall hal
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic libgconf2-ruby libatk1-ruby1.8 ruby1.8
  libgconf2-ruby1.8 libglib2-ruby1.8 libcairo-ruby1.8 libgdk-pixbuf2-ruby1.8
  libgtk2-ruby1.8 libruby1.8 linux-headers-2.6.24-19 libpango1-ruby1.8
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 420kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com hardy-updates/main hal 0.5.11~rc2-1ubuntu8.2 [420kB]
Fetched 420kB in 3s (109kB/s)
(Reading database ... 163113 files and directories currently installed.)
Preparing to replace hal 0.5.11~rc2-1ubuntu8.2 (using .../hal_0.5.11~rc2-1ubuntu8.2_i386.deb) ...
invoke-rc.d: initscript hal, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
invoke-rc.d: initscript hal, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/hal_0.5.11~rc2-1ubuntu8.2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
invoke-rc.d: initscript hal, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/hal_0.5.11~rc2-1ubuntu8.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

After rebooting, I get the same "Failed to initialize HAL" error, which leads me to believe the problem is elsewhere...perhaps somewhere in the initrc process. The commands 
```

sudo lspci
dmesg|tail

```
 when executed from within the Live CD, don't seem to indicate any hardware errors.

Luckily, the Ubuntu box--an aging Athlon 1600-based desktop built out of cast-off bits of other PCs, many of which were dumpster rescues--isn't my primary machine. If all else fails, I can always start over (perhaps with Jackalope).
:lolflag:

---

### Post by blueridgedog on 2009-07-06
It is as I feared in my prior post, that HAL was a symptom, not a cause.  I suggest a reinstall versus searching out what files were corrupted.

---

### Post by alexander750 on 2009-07-06
I'm getting Jackalope now, via torrent (on my primary computer--the one with the half-eaten fruit on its cover, running a 64-bit BSD variant). All it needs is time. ;)

Thanks for the help anyway...

---

