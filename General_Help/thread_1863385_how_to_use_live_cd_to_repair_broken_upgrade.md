---
title: "how to use live cd to repair broken upgrade"
date: 2011-10-17
forum: General Help
---

### Post by etsauer on 2011-10-17
Hi, I accidentally powered my computer down while running the upgrade to 11.10, and now I am unable to boot into ubuntu (neither graphical or text mode). 

I have seen many articles such as this one ([http://galigio.org/2009/11/29/how-to-repair-a-bad-upgrade-on-ubuntu/](http://galigio.org/2009/11/29/how-to-repair-a-bad-upgrade-on-ubuntu/)) for repairing broken 

I do have a live cd for Karmic sitting around. Is there any way to use that to get into my current broken install so that I can try some of these suggestions?

Any other ideas on what I can try?

---

### Post by oldfred on 2011-10-17
It would be better if your liveCD was the current verison. You should have a Linux liveCD or Windows repair CD for every version of operating system installed. 

You may be able to chroot into your system and finish/repair the upgrade if it has done part of the upgrade. # is comments do not type/copy them.

drs305 chroot to purge & reinstall grub2 (you may or may not need the grub install)
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)


#Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

#reinstall kernel:
sudo apt-get update
sudo apt-get install linux-image
sudo update-grub

---

### Post by etsauer on 2011-10-17
Hi thanks for the help. That all worked and seemed to go well, but I'm still having the same problem before. This is what happens:

-Start computer
-Boots as far as first ubuntu loading screen )purple background with ubuntu logo and loading animation (......)
-See text of packages that are loading:

    speech-dispatcher disabled; edit /etc/default/speech-dispatcher
      *Stopping save kernel messages
      *Starting configure network device
    
    *Starting configure network device security
    
    *Starting VirtualBox kernel modules
    
    *Starting bluetooth

    * (orange asterisk) PulseAudio configured for per-user sessions
                                                        saned disabled; edit /etc/default/saned

-At this point it stops loading services and just hangs

Any ideas??

---

### Post by oldfred on 2011-10-17
The most common problem is video. But it could be just some other parameter setting. What video card do you have?  Can you boot recovery mode? To command line? I have nVidia and have to use nomodeset on first boot until nVidia driver is installed. With 10.10 it installs nVidia's 173 which is not quite right, s/b current but it at least boots.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

---

### Post by etsauer on 2011-10-17
just realized that the grub purge and reinstall didn't seem to work. Not sure if that's where the problem is, but when a run ```
apt-get purge grub-common
``` I get the following error:

```
runlevel:/var/run/utmp: No such file or directory
```

Afterwards, the purge cuts off.

Same thing happens when i try to install the Grub packages.

---

### Post by etsauer on 2011-10-17
I'm not exactly sure what model i have, but its a lenovo thinkpad running basic intel graphics.

---

### Post by etsauer on 2011-10-18
Also tried some of the boot options (i.e. nomodeset) to no avail.

---

### Post by etsauer on 2011-10-18
After many failed attempts, I finally decided to go another route, which was to create a bootable USB stick of 11.10 from within my 9.10 live cd. After booting into the up to date live usb, I was able to do a somewhat successful upgrade (still having some issues with pieces of the UI missing).

---

