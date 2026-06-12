---
title: "Python 2.6 uninstalled. Job in danger!"
date: 2010-07-19
forum: General Help
---

### Post by Cyahnidde on 2010-07-19
Edit: Running Ubuntu 9.04

My boss isn't very good at linux so he asked me to clear some files. Alright, he has Python 3.0 on so I went to synaptic and uninstalled python 2.6 and ALL files accosiated with it. Once it was done, I noticed almost all my programs were gone except open office programs a few other things. Even my internet was gone. So I panicked and reset the PC. Bad mistake.
I got an error similar to this(leaving things out for sake of time):


```

Kinit: No resume image, doing normal boot...

Ubuntu 9.04 CalebWork2009 tty1

CalebWork2009 login: (put in username)
password: (put in pass)
[tells my last login]

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the individual files  in /usr/share/doc/*/copyright

Ubuntu comes with ABSOLUTLEY NO WARRANTY, to the extent permitted by applicable law.

To access official Ubuntu docmentation, please visit:
http://help.ubuntu.com/
caleb#CalebWork2009:~$         (basically gives me a command prompt)

```
My boss returns from a trip in about 16 hours and I will be fired if he sees this. Help me fix it. Ubuntu is the only system running on the laptop. I try to grab my ubuntu disc and boot it to reinstall, but when I go to my boot menu(F12) and press it, it just takes me back to this. I even tried to boot a windows disc and it took me to the same screen.

I REALLY NEED FAST URGENT HELP! THANKS! :(

---

### Post by oldfred on 2010-07-19
The ability to boot a liveCD was not changed by your uninstall of python. Either with f12 or a change in BIOS you should be able to boot the liveCD. If not then maybe the liveCD is scratched and not working.

You need to chroot from the liveCD into the system and reinstall the missing applications.

To chroot:
kansasnoob------------------------------
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)
Neat huh?
Added sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

kansasnoob's change sda5 to correct partition
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

# new for lucid & karmic 
dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl

Once chrooted into your system:
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
# reinstall desktop
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop

That should reinstall most of the missing apps. I think desktop needs python but if not then you can just run:
apt-get install python

---

### Post by Buttons840 on 2010-07-19
Go to synaptic and try to reinstall python2.6, hopefully the original debian packages are still hanging around and you can reinstall without an internet connection?  Actually, python2.6 is probably part of the compressed image that comes with the standard Ubuntu install disk.

As you've learned python 3.0 is not backwards compatible and thus is no replacement for the many scripts that apparently run on python 2.6.

---

### Post by Cyahnidde on 2010-07-19
> **Buttons840 said:**
> Go to synaptic and try to reinstall python2.6, hopefully the original debian packages are still hanging around and you can reinstall without an internet connection?  Actually, python2.6 is probably part of the compressed image that comes with the standard Ubuntu install disk.

As you've learned python 3.0 is not backwards compatible and thus is no replacement for the many scripts that apparently run on python 2.6.

I auctually lol'd. Don't you understand I can't access the desktop?

---

### Post by Cyahnidde on 2010-07-19
> **oldfred said:**
> The ability to boot a liveCD was not changed by your uninstall of python. Either with f12 or a change in BIOS you should be able to boot the liveCD. If not then maybe the liveCD is scratched and not working.

You need to chroot from the liveCD into the system and reinstall the missing applications.

To chroot:
kansasnoob------------------------------
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)
Neat huh?
Added sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

kansasnoob's change sda5 to correct partition
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

# new for lucid & karmic 
dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl

Once chrooted into your system:
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
# reinstall desktop
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop

That should reinstall most of the missing apps. I think desktop needs python but if not then you can just run:
apt-get install python


Is there a way to let my PC be able to boot a live without going to this error? I tried to chroot or whatever and I got errors no matter what. Invalid commands and what not.

---

### Post by Buttons840 on 2010-07-19
You need to set your BIOS to boot from the CD (or USB stick, if your using a live USB stick).  To access your BIOS you usually press delete, F2, F12, or some other key as the computer is first booting.  Then a ugly (yet usable) screen will present itself and you can navigate with the arrow keys and set different options.  Look at the boot options and try to set the disk drive to the highest boot priority and then the computer will boot from the CD instead of the hard drive.

---

### Post by WorMzy on 2010-07-19
After you've booted into Ubuntu and are presented with the commandline, can you press Alt+F7 and get to the login screen? Try Ctrl+Alt+F8 too. If neither of those work, then get back to the command line (tty) with Ctrl+Alt+F1.

From the command line, test your internet connectivity with
```
ping -c 3 www.google.com
```
If it works and all the packets were recieved, then run
```
sudo apt-get install ubuntu-desktop
```

---

### Post by tekkidd on 2010-07-19
is their a desktop? if their is no desktop try to do 
[CODE]sudo apt-get install ububntu-desktop[CODE]

and see if that works

also as far as booting into the system you need to go into the bios and tell it to boot from the cd first. Also if all else fails, pop open the computer, take the HDD out stick it in another machine, boot into the cd from that machine and install on that HDD (the one you took out) then stick it back in.

---

