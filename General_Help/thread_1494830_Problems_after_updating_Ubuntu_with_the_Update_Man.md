---
title: "Problems after updating Ubuntu with the Update Manager"
date: 2010-05-27
forum: General Help
---

### Post by CoreInsanity on 2010-05-27
I started the update manager and went to get some food (600MB on DSL is not exactly quick). I come back a little bit later and my screen is completely messed up. Multi-colored streaks going across it, and the resolution looked like it was reset to 800x600 or something. On the screen was this error box that I could not fit on the screen correctly, but noticed it gave me a bash command do run (It had an error but I couldn't really make it out because it distorted the crap out of my display). 

So, I shut down the computer, and start it up and executed the command it gave me:

```
dpkg-reconfigure sysv-rc
```

Then it gave me something that looked like it was the error that had popped up:

```

Unable to migrate to dependency-based boot system

Tests have determined that problems in the boot system exist which
prevent migration to dependency-based boot sequencing:

package initscripts left obsolete init.d script behind, insserv:  
warning: script 'K20acpi-support' missing LSB tags and overrides, 
insserv: warning: script 'S12dbus' missing LSB tags and overrides,
insserv: warning: script 'network-manager' missing LSB tags and   
overrides, insserv: warning: script 'apport' missing LSB tags and 
overrides, insserv: warning: script 'console-setup' missing LSB tags and
overrides, insserv: warning: script 'plymouth-splash' missing LSB tags  
and overrides, insserv: warning: script 'udevtrigger' missing LSB tags  
and overrides, insserv: warning: script 'acpi-support' missing LSB tags 
and overrides, insserv: warning: script 'irqbalance' missing LSB tags   
and overrides, insserv: warning: script 'rsyslog' missing LSB tags and  
overrides, insserv: warning: script 'cron' missing LSB tags and   
overrides, insserv: warning: script 'udevmonitor' missing LSB tags and  
overrides, insserv: warning: script 'plymouth' missing LSB tags and     
overrides, insserv: warning: script 'dmesg' missing LSB tags and  
overrides, insserv: warning: script 'plymouth-stop' missing LSB tags and
overrides, insserv: warning: script 'acpid' missing LSB tags and
 overrides, insserv: warning: script 'procps' missing LSB tags and 
overrides, insserv: warning: script 'anacron' missing LSB tags and
overrides, insserv: warning: script 'atd' missing LSB tags and    
overrides, insserv: warning: script 'udev' missing LSB tags and   
overrides, insserv: warning: script 'udev-finish' missing LSB tags and  
overrides, insserv: warning: script 'mysql' missing LSB tags and  
overrides, insserv: warning: script 'ufw' missing LSB tags and    
overrides, insserv: warning: script 'failsafe-x' missing LSB tags and  
 overrides, insserv: warning: script 'avahi-daemon' missing LSB tags and 
overrides, insserv: warning: script 'dbus' missing LSB tags and   
overrides, insserv: warning: script 'gdm' missing LSB tags and    
overrides, insserv: warning: script 'plymouth-log' missing LSB tags and 
overrides, insserv: warning: script 'module-init-tools' missing LSB tags
and overrides,          
 
 If the reported problem is a local modification, it needs to be fixed   
manually. If it's a bug in the package, it should be reported to the BTS
and fixed in the package. See                                     
[http://wiki.debian.org/LSBInitScripts/DependencyBasedBoot](http://wiki.debian.org/LSBInitScripts/DependencyBasedBoot) for more
information about how to fix the problems preventing migration.   
                                                                  
To reattempt the migration process after the problems have been fixed,
run "dpkg-reconfigure sysv-rc". 

```


I looked at their website and that doesn't really help me much. I also went back to the update manager, and it tells me:

> 
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.


The Synaptic package manager tells me I have 4 broken packages on my system, so I use the broke filer and it has listed:

> 
brltty
brltty-x11
libudev0
python-newt


Should I go ahead and remove these?

Also, just to paste the output of that command:

```

coreinsanity@coreinsanity:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libboost-date-time1.40.0 libboost-thread1.40.0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libatspi1.0-0 libncursesw5 libnewt0.52 udev
The following packages will be upgraded:
  libatspi1.0-0 libncursesw5 libnewt0.52 udev
4 upgraded, 0 newly installed, 0 to remove and 743 not upgraded.
6 not fully installed or removed.
Need to get 0B/1,171kB of archives.
After this operation, 565kB disk space will be freed.
Do you want to continue [Y/n]

```

I have not accepted yet, however.

Also, the Gnome GUI is different looking (I had a darker colored theme, now it looks like it reset to something with the same color scheme as windows classic), and the appearance settings don't seem to do anything, but the effects are still on everything.

I am not sure if all of these problems are related or what, and I am fairly new to Linux so I decided I should probably post here.

Thanks :)

---

### Post by CoreInsanity on 2010-05-27
I hate to bump this, but I really need to fix it asap.

Thanks.

---

