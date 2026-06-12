---
title: "Unable to boot past rcS"
date: 2010-07-13
forum: General Help
---

### Post by WizRd on 2010-07-13
Hi All,
 
I am running Ubuntu 8.04.4 LTS with kernel 2.6.24-28-server.  Something went a little haywire a few weeks ago and since then I have been unable to boot the server.  Using a bootable USB drive I was able to modify a few settings... in particular 
 
/etc/default/rcs
```
 
SULOGIN=yes
VERBOSE=yes

```
 
When I enter the root password (sulogin variable) I am dropped to a shell where I am able to remount the root partition, mount all LVM partitions, run swapon followed by init 2 or telinit 2 (depends what mood I'm in) and the system will continue to boot and mostly function as normal.  The biggest issue is processes become zombies which eventually stuffs up the system to the point that it needs to be rebooted.
 
The last part of a normal boot that I see is urandom starting, which returns ok then the system hangs.  Thinking I was being to impatient I left the system in this state for 24 hours and it still had not booted...
 
I have tried adding /etc/inittab out of desperation but this hasn't actually done anything.  I have ran aptitude to ensure there were no broken packages, which there was, since fixing these packages nothing has changed, the boot process still hangs at the end of rcS and never automatically changes to another runlevel.
 
When the system is stuck at this point CTRL-ALT-DEL does work and reboot the system but again this doesn't really do anything magical to help me.
 
I have checked dmesg and /var/log/syslog and nothing appears to be logged or mention that it is still trying to start a process that is failing or failed to change run levels.
 
I updated to the latest kernel last night in the hope that this would somehow magically fix things, again no change.
 
I uncommented debug=echo in /etc/init.d/rc and this just made things worse that it never actually gave me the prompt to put the root password and just hangs at the same point.
 
I ran debsums last night and checked all the "changed" files that failed the verification and nothing stood out that would indicate an issue with booting.
 
I am reluctant to run do-release-upgrade as the last time I did this resulted in rebuilding the box after the dpkg package failed to download correct which then removed dpkg from the system and didn't install the new package... as you can imagine this completely stuffed up the box.  This wasn't a Ubuntu issue it was a mirror issue I have with internode, I'm just concerned about running it...
 
I'm sure that I have missed some of my troubleshooting or information about what I have looked at to try to resolve this so any recommendations even if I have done it will be done again as I am now desperate to try and get this fixed.
 
Any suggestions or advice anyone can give would be appreciated.

---

