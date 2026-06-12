---
title: "direct boot to command line interface possible?"
date: 2009-12-24
forum: General Help
---

### Post by yanvolking on 2009-12-24
Hello Community,

My computer has a Windows XP / Ubuntu 9.10 dual boot.  I use mainly Ubuntu and increasingly in command line interface as my linux shell experience develops.  I find it simpler and above all much faster than working in the GUI.

Question:  Is there a way of booting directly to command line interface (shell prompt) without having to load the full Ubuntu  session?  This would be a great way of saving time for certain tasks that can be executed in CLI.

Thanks

---

### Post by lloyd_b on 2009-12-24
If you remove GDM ("sudo apt-get remove gdm"), the system will boot to a console login. 

If you need X for something, then "startx" in the console will bring it up.

I seem to recall that it's possible to deactivate GDM without actually uninstalling it, but I don't recall the command (hopefully someone else will wander by and provide it).

Lloyd B.

---

### Post by sisco311 on 2009-12-24
You have several options:

[list=i]
[*]rename the Upstart job:
```
sudo mv /etc/init/{gdm.conf,gdm.conf.noexec}
```

NOTE: if you reinstall/upgrade gdm the file is recreated.



[*]edit the file and comment out the *start on* entry:
```
# gdm - GNOME Display Manager
#
# The display manager service manages the X servers running on the
# system, providing login and auto-login services

description     "GNOME Display Manager"
author          "William Jon McCann <mccann@jhu.edu>"

**#**start on (filesystem
**#**          and (graphics-device-added fb0 PRIMARY_DEVICE_FOR_DISPLAY=1
**#**               or drm-device-added card0 PRIMARY_DEVICE_FOR_DISPLAY=1
**#**               or stopped udevtrigger))
stop on runlevel [016]
...

```

to start gdm run:
```
sudo initctl gdm start
```



[*]edit the file and add a new event to the *start on* entry. i.e. start it on runlevel 3:

```
# gdm - GNOME Display Manager
#
# The display manager service manages the X servers running on the
# system, providing login and auto-login services

description     "GNOME Display Manager"
author          "William Jon McCann <mccann@jhu.edu>"

start on ([B]runlevel 3 
          and [/B]filesystem
          and (graphics-device-added fb0 PRIMARY_DEVICE_FOR_DISPLAY=1
               or drm-device-added card0 PRIMARY_DEVICE_FOR_DISPLAY=1
               or stopped udevtrigger))
stop on runlevel [016]

```


to start gdm run:
```
sudo initctl gdm start
```
or
```
sudo initctl emit runlevel 3
```

NOTE: You can boot in runlevel 3 by appending the *linux* line in GRUB with **3**

```
linux /boot/vmlinuz<-version> root=UUID=<uuid> ro quiet splash **3**
```



[*]comment out */usr/sbin/gdm* in the /etc/X11/default-display-manager file:
```
#/usr/sbin/gdm
```

[/list]

---

### Post by blueridgedog on 2009-12-24
Why not simply:

```
sudo mv /etc/init/gdm.conf /etc/init/gdm.save
```

Then reboot?  I have not tried it, but it should work.  I will give it a try in a VM and report back.

EDIT:  This works as expected in a 9.10 test virtual machine and can be easily undone with:

sudo mv /etc/init/gdm.save /etc/init/gdm.conf

By way of clarification:  gdm is started in Ubuntu via the new "upstart" tool which stores config files in /etc/init.  Each file ending with .conf is run, those ending in something else are not.  If you do the change, you can always get X to start with "startx".

---

### Post by falconindy on 2009-12-24
Append 'text' to the kernel options in Grub.

Also, consider a lighter distro if you're not going to be using a GUI.

---

### Post by ticthak@AOL.com on 2009-12-24
The no edit version- boot into recovery mode, you can drop to cli right from there (last 2 entries in the menu, with or without networking)

---

### Post by lloyd_b on 2009-12-24
> **ticthak@AOL.com said:**
> The no edit version- boot into recovery mode, you can drop to cli right from there (last 2 entries in the menu, with or without networking)

This is a BAD idea for normal use.  Recovery mode does drop you immediately to a CLI, but it has you logged in as root, where the slightest mistake can have disastrous consequences.

Lloyd B.

---

### Post by blueridgedog on 2009-12-24
> **lloyd_b said:**
>  it has you logged in as root

Also, many services are not started, which will/may be needed.

---

### Post by yanvolking on 2010-01-02
Hi Guys,

Thanks for your replies.  I have chosen Sisco331's solution : 

sudo mv /etc/init/{gdm.conf,gdm.conf.noexec}
for the direct to CLI boot and simply use "startx" command to go to the GUI.

Then back to CLI with "sudo shutdown -P now" to shut down.

Problem solved.

---

