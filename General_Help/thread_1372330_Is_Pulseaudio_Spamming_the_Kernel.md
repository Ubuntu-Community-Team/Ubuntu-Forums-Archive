---
title: "Is Pulseaudio Spamming the Kernel?"
date: 2010-01-04
forum: General Help
---

### Post by Anzan on 2010-01-04
I am just wondering if anyone knows anything about this.

This box runs 9.10. There was an update this morning. For gnome-screensaver and a few minor things. This is likely unrelated.

At about 8:05 my backup drive (mounted in etc/fstab) started to hum loudly and with some variations. I opened guake and arrowed up history to the command
find /mnt/backup/ -type f -mtime -1 -exec ls -l {} \;
which returned no output. I tried several times. I also opened the backup mount in Nautilus. It read that there were 0 items but showed 180.3 GB of free space.

I turned off the backup drive and turned it back on. Nothing had changed. I turned the drive off.

I shut down the box. I turned the drive back on. I restarted.

The backup mounted and all is fine. The command returns output and Nautilus shows the files.

Logs seem to show the kernel being spammed by pulseaudio (which is of foul repute and vile infamy) and this throwing off other processes. I know of someone else who had similar difficulties.

Does anyone know anything about this? Thanks in advance.

---

### Post by Saiko Berry on 2010-01-04
Pulseaudio is broken some hardcore in 9.10 it seems. Im having a lot of errors with it including .. apparently its crashing my xlsession.

---

### Post by Anzan on 2010-01-04
Crashing X? That's really egregious.

Does anyone else have any comments or information?

---

### Post by dcstar on 2010-01-05
> **Anzan said:**
> I am just wondering if anyone knows anything about this.

This box runs 9.10. There was an update this morning. For gnome-screensaver and a few minor things. This is likely unrelated.

At about 8:05 my backup drive (mounted in etc/fstab) started to hum loudly and with some variations.
........

And you have disabled Tracker and any other packages which may scan and index files?

---

### Post by Anzan on 2010-01-05
Oh, yes. I have never found Tracker to be able to find anything I look for so haven't had it (or Beagle) running since 8.04.

---

