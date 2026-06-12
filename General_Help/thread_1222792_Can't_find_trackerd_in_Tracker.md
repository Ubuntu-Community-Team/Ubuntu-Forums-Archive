---
title: "Can't find trackerd in Tracker"
date: 2009-07-25
forum: General Help
---

### Post by bhagwad on 2009-07-25
I'm trying to install Tracker Search, but after installation, when I run "trackerd", I get:

trackerd: command not found

Other tracker tools such as preferences and tracker search are all there, but as expected, there's nothing indexed.

trackerd is not found in usr/bin along with the other tracker files - I've uninstalled an reinstalled several times over, but still nothing.

The Internet and Google have been of no help so far - any ideas anyone?

I'm using 9.04 Jaunty...

---

### Post by ptn107 on 2009-07-25
If you installed the 'tracker' package then it is here:
/usr/lib/tracker/trackerd

---

### Post by bhagwad on 2009-07-25
> **ptn107 said:**
> If you installed the 'tracker' package then it is here:
/usr/lib/tracker/trackerd

Hooray! Thank you! - it's there. Now why didn't the documentation mentioned that? Two days of hunting comes to an end :)

---

### Post by ptn107 on 2009-07-25
There's a nifty [I think] little program called 'apt-file' you can install to find that kind of stuff out.

Install:
```
sudo aptitude install apt-file && apt-file update
```

Then to search (like for trackerd):
```
sudo apt-file search trackerd
```
which gave me...
```
casper: /usr/share/initramfs-tools/scripts/casper-bottom/36disable_trackerd
live-initramfs: /usr/share/initramfs-tools/scripts/live-bottom/36disable_trackerd
tracker: /etc/xdg/autostart/trackerd.desktop
tracker: /usr/lib/tracker/trackerd
tracker: /usr/share/autostart/trackerd.desktop
tracker: /usr/share/man/man1/trackerd.1.gz
```

Showing that '/usr/lib/tracker/trackerd' belongs to the 'tracker' package.

---

### Post by bhagwad on 2009-07-25
> **ptn107 said:**
> There's a nifty [I think] little program called 'apt-file' you can install to find that kind of stuff out.

Install:
```
sudo aptitude install apt-file && apt-file update
```Then to search (like for trackerd):
```
sudo apt-file search trackerd
```which gave me...
```
casper: /usr/share/initramfs-tools/scripts/casper-bottom/36disable_trackerd
live-initramfs: /usr/share/initramfs-tools/scripts/live-bottom/36disable_trackerd
tracker: /etc/xdg/autostart/trackerd.desktop
tracker: /usr/lib/tracker/trackerd
tracker: /usr/share/autostart/trackerd.desktop
tracker: /usr/share/man/man1/trackerd.1.gz
```Showing that '/usr/lib/tracker/trackerd' belongs to the 'tracker' package.

Thanks a whole bunch - very useful!

---

