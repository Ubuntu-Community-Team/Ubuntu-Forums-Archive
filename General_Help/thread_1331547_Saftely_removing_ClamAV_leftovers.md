---
title: "Saftely removing ClamAV leftovers"
date: 2009-11-19
forum: General Help
---

### Post by pgibson on 2009-11-19
A month or two (or three?) ago, using Synaptic in Intrepid, I had installed clamav, clamtk, clamdocs and possibly one or two other clam things that seemed useful.  Later I decided to remove all this (again using Synaptic), but it doesn't seem all the bits and logs and pieces have been removed.

I hadn't noticed this until today, when I ran a full system scan using Avast antivirus.  It screamed "ALERT!" because it found a clamav file in /var/lib/clamav. It's a false positive, but I wondered why it was there at all, so I googled /var/lib/clamav and read an [archived post on these forums]("http://ubuntuforums.org/archive/index.php/t-725496.html") from a user with a similar problem.  

The fix for that person was to peruse Synaptic entries for "clam" items that allowed for complete removal ... doing so greatly reduced the number of items remaing, and sudo rm -r /whatever/wasLeft cleaned it up.  I've reinstalled clamav, clamtk, clamav-daemon, and "completely removed" them, and that reduced the amount of cack remaining.  ```
sudo locate clam
``` shows that I'm down to:

```
/etc/clamav
/etc/apparmor.d/usr.bin.freshclam
/etc/clamav/freshclam.conf
/etc/init.d/clamav-freshclam
/etc/logcheck/ignore.d.server/clamav-freshclam
/etc/logrotate.d/clamav-freshclam
/etc/network/if-down.d/clamav-freshclam-ifupdown
/etc/network/if-up.d/clamav-freshclam-ifupdown
/etc/ppp/ip-down.d/clamav-freshclam-ifupdown
/etc/ppp/ip-up.d/clamav-freshclam-ifupdown
/etc/rc0.d/K20clamav-freshclam
/etc/rc1.d/K20clamav-freshclam
/etc/rc2.d/S20clamav-freshclam
/etc/rc3.d/S20clamav-freshclam
/etc/rc4.d/S20clamav-freshclam
/etc/rc5.d/S20clamav-freshclam
/etc/rc6.d/K20clamav-freshclam
/usr/share/app-install/desktop/clamtk.desktop
/usr/share/app-install/icons/clamtk.xpm
/usr/share/k3d/shaders/imager/k3d_clamptoalpha.sl
/usr/share/k3d/shaders/imager/k3d_clamptoalpha.sl.slmeta
/usr/share/tcltk/tk8.5/ttk/clamTheme.tcl
/var/lib/clamav
/var/lib/clamav/daily.cld
/var/lib/clamav/main.cld
/var/lib/clamav/mirrors.dat
/var/lib/dpkg/info/clamav-freshclam.list
/var/lib/dpkg/info/clamav-freshclam.postrm
/var/lib/ucf/cache/:etc:clamav:freshclam.conf
/var/log/clamav
/var/log/clamav/freshclam.log
/var/log/clamav/freshclam.log.1
/var/log/clamav/freshclam.log.2.gz
/var/log/clamav/freshclam.log.3.gz
/var/log/clamav/freshclam.log.4.gz
/var/log/clamav/freshclam.log.5.gz
/var/log/clamav/freshclam.log.6.gz
/var/log/clamav/freshclam.log.7.gz
```


Which of these can I safely remove? In the archived post, /var/lib/clamav, /etc/clamav and /var/log/clamav are all indicated ... but this is "under the hood" stuff that leaves me a bit nervous to hack-n-slash away with a delete key and I could really use some guidance.

Oh, and I should mention that yesterday I upgraded to Jaunty, so I'm wondering if the "reinstall-uninstall" trick may not work if there are Intrepid specific data involved.  I dunno.

Thanks in advance.:)

---

### Post by MyR on 2009-11-19
"If it ain't broke, don't fix it."

In synaptic, on the left hand panel, click status, then "not installed (residual config" and tell it to completely remove anything regarding clamav.  Otherwise just leave your system alone, those files aren't hurting anything.

peace

---

### Post by pgibson on 2009-11-19
Hey Myr,

Yeah, normally that's my motto too.  If Avast hadn't been bothered by whatever it found in the file, I wouldn't have given it a thought.  I had images of having Avast start and stop, start and stop as it slogged through vestigal clamav files.

As you suggested, I tried the Synaptic's status, not installed (residual config).  Nothing clammy showed up.

Apparently, however, the chaff that's left after I reinstalled-uninstalled isn't dangerous looking.  since your reply I've done a thorough scan without alarums.  It seems all is well.  Huzzah.:)

Thanks for the confirm.

Peace

---

