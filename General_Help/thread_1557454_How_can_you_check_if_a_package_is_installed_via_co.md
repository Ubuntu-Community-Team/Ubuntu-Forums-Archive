---
title: "How can you check if a package is installed via command line?"
date: 2010-08-20
forum: General Help
---

### Post by tjones00 on 2010-08-20
After sifting through numerous apt-get apt-cache apt-file tutorials I still can't find a command to check if a package is installed via the terminal command/line.

I know there must be some way to do it.

Say I want to check if any package from the libavcodec*.deb family is installed how could I do this without a gui eg synaptic?

---

### Post by drs305 on 2010-08-20
For now, you can use:
```
aptitude show <packagename>
```

Example:
aptitude show gimp

The "for now" disclaimer is that aptitude won't be in 10.10, at least as planned for now.

---

### Post by tjones00 on 2010-08-20
Wow that was fast thank you.

I guess wildcards don't work with it so you need to use the exact name.

```
xbmc@xbmc-HTPC:/$ aptitude show alsa*
E: Unable to locate package alsa*
xbmc@xbmc-HTPC:/$ aptitude show alsa-utils
Package: alsa-utils
State: installed
Automatically installed: no
Version: 1.0.22-0ubuntu5
Priority: optional
Section: sound
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 2,056k
Depends: libasound2 (> 1.0.22), libc6 (>= 2.8), libncursesw5 (>=
         5.6+20071006-3), whiptail | dialog, module-init-tools, lsb-base (>=
         3.0-9), linux-sound-base (>= 1.0.15-1), udev, upstart-job
Recommends: alsa-base (>= 1.0.15-1), pciutils
Conflicts: alsa-base (< 1.0.9b-3), udev (< 0.060)
Breaks: udev (< 136-1)
Provides: audio-mixer
Description: ALSA utilities
 This package contains utilities for configuring and using ALSA, including: 
 o amixer: command line mixer
 o alsamixer: curses mixer
 o amidi: read from and write to ALSA RawMIDI ports
 o aplay, arecord: command line playback and recording
 o aplaymidi, arecordmidi: command line MIDI playback and recording
 o aconnect, aseqnet, aseqdump: command line MIDI sequencer control
 
 ALSA is the Advanced Linux Sound Architecture.
Homepage: http://www.alsa-project.org/


```

Still thanks again it should work for me.

---

### Post by drs305 on 2010-08-20
If you want to use wild cards, you could use this command to find specific versions, but you don't even need the "*". Just type as much of the name as you wish:
```
grep "Package: <packagename>" -A1 /var/lib/dpkg/status

```
It will provide all instances of packages which match what you've typed and the status. If the list is too long, type more of the "packagename" to reduce the number of returns.

Example:
grep "Package: linux-image-2.6.32" -A1 /var/lib/dpkg/status

---

### Post by WorMzy on 2010-08-20
> **drs305 said:**
> For now, you can use:
```
aptitude show <packagename>
```

Example:
aptitude show gimp

The "for now" disclaimer is that aptitude won't be in 10.10, at least as planned for now.

Same works for apt-cache.

```
apt-cache show gimp
```

Of course, a better (imo) way of searching for installed packages is to use dpkg-query.

```
dpkg-query -l gim*
```

This'll show any packages matching that expression, including their status (e.g. installed [ii] or uninstalled [un])

If you just want to view installed packages, you can cut it down with grep, e.g.

```
dpkg-query -l gim* | grep ii
```

---

### Post by drs305 on 2010-08-20
> **WorMzy said:**
> 
```
dpkg-query -l gim* | grep ii
```

I'd say that one is the best meets the needs of the OP, since it's simple, uses wildcards, and also gives the version number. Thanks.

---

