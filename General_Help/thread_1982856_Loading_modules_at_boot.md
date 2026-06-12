---
title: "Loading modules at boot"
date: 2012-05-19
forum: General Help
---

### Post by Gannin on 2012-05-19
I'm running Ubuntu 12.04.

My system has a conflict between the nforce smb and the ACPI.  The specific message is:

[    5.405128] ACPI: resource nForce2_smbus [io  0x0700-0x073f] conflicts with ACPI region SM00 [io 0x700-0x73f]

After doing some research it seems this is an old problem that many people have, and it's a shame it hasn't been fixed yet.

This error results in two things for me.  First, the onboard ethernet adapter won't work in Linux, and second, Linux won't shutdown or reboot the computer.  It just hangs when you try.

But, I found something of a solution to all of this.

If I boot into recovery mode, drop to a root prompt, and then run:

```

rmmod forcedeth
modprobe forcedeth msi=0 msix=0

```

And then exit recovery mode and resume with a normal boot, my networking will work and the computer will shutdown and reboot properly.

If I boot into normal mode then try to rmmod forcedeth, the system just freezes.

My question is, how do I get the module to load with those paramaters automatically at boot?  I've added a forcedeth.conf file to /etc/modprobe.d with the following contents:

```

options forcedeth msi=0 msix=0

```

But that doesn't do anything.  Booting normally still doesn't give me networking access or properly manage the shutdown / rebooting of the computer even with the above file in place.

Are there any other options for getting the module loaded with the proper paramaters automatically during boot so I don't have to manually boot into recovery mode and manage the module myself every time?  Thanks!

---

### Post by 2F4U on 2012-05-19
Maybe the system needs the exact two commands (rmmod/modprob) to work properly, so I would try to add these two commands to /etc/rc.local. The content of this file is executed with root privileges when the system boots. The file has to end with

exit 0

The file can be edited with any text editor.

---

### Post by Gannin on 2012-05-19
The only reason "rmmod forcedeth" has to be run is because by the time the system boot gets to that point, it's already loaded the forcedeth module so it has to be removed so it can be reloaded with the proper parameters.  If I could get forcedeth to load with the proper parameters from the beginning, there would be no need to remove the module first.

I tried adding the rmmod and modprobe commands to rc.local, unfortunately by the time rc.local gets run, the boot process is already too far along.  When it hits the rmmod command, the system completely freezes, just like if you try to use the rmmod command after completely booting the system normally.

Next I tried creating a new service in /etc/rc2.d/ that would run those commands, but the same thing.  The system just froze.  I moved the priority of the service all the way to the top, but again, the same thing.  The system just froze.

So, I thought maybe if I blacklisted the module so it wouldn't load automatically, then there would be no need to rmmod it and I could just modprobe it later after doing a normal boot, either manually or from a script.

I added a "blacklist forcedeth" line to /etc/modprobe.d/blacklist.conf, but that didn't work.  After the system finished booting, it had still loaded forcedeth even though I had tried to blacklist it.

Edit:

So it turned out the solution was a lot more simple than I realized.

I tried just about everything to run rmmod early enough in the boot sequence so that it wouldn't freeze the computer, or loading forcedeth with the proper parameters.  I played around with /etc/initramfs-tools/modules, I played around with adding scripts to the /etc/initramfs-tools/modules/scripts directories, updating the initramfs each time, I tried removing the module file itself from /lib/modules trying to get it to not load so I could at least load it manually, but none of that worked.

Then I started playing around with the scripts in /etc/init/ and I realized if the module was reloaded with the right parameters early enough in the boot sequence, the module wouldn't have to be removed with rmmod first.

So it turns out simply adding the line "forcedeth msi=0 msix=0" to /etc/modules takes care of it.

I should add this doesn't seem to work on Ubuntu 10.04, only on Ubuntu 12.04.  I haven't tried in the in-between releases or other distros, but I imagine it should work fine on other distros as it should be more a function of the newer kernel and how it loads things than anything else.

In Ubuntu 10.04, forcedeth won't load properly no matter what you do.  Even if you boot into recovery mode and try to rmmod it, the system will freeze, and if you try to simple reload it with modprobe, it doesn't load properly.

So it looks like even though you have to jump through some hoops to get it working with Ubuntu 12.04, there have been some improvements to compatibility in the newer Ubuntu version, which is good, because that's what you want to see with newer versions of Linux anyhow.

---

