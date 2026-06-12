---
title: "And the award for the most illogical system goes to..."
date: 2010-03-15
forum: General Help
---

### Post by Lockheed on 2010-03-15
Yes, you guess it! Ubuntu &#8211; which always beats any Windows by at least two lengths!

Maybe 6 months ago I would be surprised, but after a year of putting up with all that ridiculous ubuntu problems, nothing amazes me any more.

I just resized my swap partition (located at the end of the disk), and I have no more sound in Ubuntu. Go figure.

This is what's happening when I try to restart ALSA:
```
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/juha/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/juha/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-codec-conexant snd-hda-intel snd-hda-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-codec-conexant snd-hda-codec snd-pcm snd-timer snd-page-alloc).
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/juha/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-intel snd-hda-codec-conexant snd-hda-codec snd-pcm snd-timer snd-page-alloc.
Loading ALSA sound driver modules: snd-hda-intel snd-hda-codec-conexant snd-hda-codec snd-pcm snd-timer snd-page-alloc.

```

---

### Post by blazemore on 2010-03-15
I'd demand a refund if I were you.
Failing that, try these:
```
sudo killall pulseaudio
sudo alsa force-reload
```

---

### Post by Lockheed on 2010-03-15
I do not have pulseaudio and forcing reload alsa makes no difference.

---

### Post by Lockheed on 2010-03-15
Even upgrading to newest ALSA did not help.

---

### Post by prodigy_ on 2010-03-15
> **Lockheed said:**
> Even upgrading to newest ALSA did not help.
Err. Why are you tinkering with ALSA at all? FUSE is giving you errors, not ALSA. Please, show what output ```
mount
``` (without any arguments) gives.

And it's quite logical, actually, that you started getting filesystem-related errors after making changes to your partitions. ;-)

---

### Post by Lockheed on 2010-03-15
> **prodigy_ said:**
> Err. Why are you tinkering with ALSA at all? FUSE is giving you errors, not ALSA. Please, show what output ```
mount
``` (without any arguments) gives.
Well, I needed an upgrade anyway.
Here's what mount shows:
```
/dev/sda6 on / type ext4 (rw,relatime,errors=remount-ro,commit=120)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/sda1 on /media/c type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /media/d type ext4 (rw)
/dev/sda8 on /media/agora type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/juha/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=juha)

```


> **prodigy_ said:**
> And it's quite logical, actually, that you started getting filesystem-related errors after making changes to your partitions. ;-)
Oh, I can see clearly how changing partition layout relates to file-system errors. I just can't see the correlation with sound system.

---

### Post by prodigy_ on 2010-03-15
Sorry for wrong info. I've found out that this behavior with ~/.gvfs is actually normal (dumb FUSE devs think it's ok to disallow root to stat an inode). 

Your sound problem might be just a coincidence then. There's a howto here for Intel HDA troubleshooting:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

But since reloading ALSA doesn't give you any errors and you don't use pulseaudio, first type ```
alsamixer
``` and check volume levels. Also check your **/etc/modprobe.d/alsa-base-conf** file and comment out power-saving options.

---

### Post by Lockheed on 2010-03-15
I run gnome-alsamixer and un-muted PCM, which was muted by resizing SWAP partition! OMG.

---

### Post by tgalati4 on 2010-03-15
The muting is done so you don't hear the bits screaming during the swap resize.

---

### Post by jocko on 2010-03-15
> **Lockheed said:**
> I run gnome-alsamixer and un-muted PCM, which was muted by resizing SWAP partition! OMG.
And the award for jumping to illogical conclusions goes to...:biggrin:

I'm pretty sure the muted pcm was completely unrelated to the resized swap. It just happened to happen at roughly the same time.

---

### Post by Lockheed on 2010-03-15
> **jocko said:**
> And the award for jumping to illogical conclusions goes to...:biggrin:

I'm pretty sure the muted pcm was completely unrelated to the resized swap. It just happened to happen at roughly the same time.
Well then, why it didn't happen at 1000 other reboots or operations?
Not the first time Ubuntu does something weird. Let me just name few examples:
- inability to connect to wifi netwotks on channels below 3 (regardless of geographical location)
- different system screwups at every other boot
- and the most recent one:

upgrading from 1.0.21 to 1.0.22 broke my sound.

For example, I am playing a song but when I pause it, or the song ends, computer keeps repeating last 0.2 second of the sound.
The same happens with every other sound my computer generates. To get some silence, I need to mute the sound completely.

---

### Post by prodigy_ on 2010-03-15
> **Lockheed said:**
> inability to connect to wifi netwotks on channels below 3 (regardless of geographical location)
Funny. Need to check this out. (I always used CH6.)

> **Lockheed said:**
> different system screwups at every other boot
upgrading from 1.0.21 to 1.0.22 broke my sound.
Maybe it's time to upgrade to 9.10? YMMV, but I had much less hardware-releated issues with it.

---

### Post by Lockheed on 2010-03-15
> **prodigy_ said:**
> Funny. Need to check this out. (I always used CH6.)
Check this out: [_this_]("http://ubuntuforums.org/showthread.php?t=1410413").


> **prodigy_ said:**
> Maybe it's time to upgrade to 9.10? YMMW, but I had much less hardware-releated issues with it.
It would erase all my customization I did over the last 10 months.
If I have to do fresh install, I'll probably go for Arch.

---

### Post by dcstar on 2010-03-15
> **Lockheed said:**
> Yes, you guess it! Ubuntu – which always beats any Windows by at least two lengths!

Maybe 6 months ago I would be surprised, but after a year of putting up with all that ridiculous ubuntu problems, nothing amazes me any more.

I just resized my swap partition (located at the end of the disk), and I have no more sound in Ubuntu. Go figure.
........

And resizing the Swap partition changes the UUID which breaks things - refer to the many HOWTOs on how to fix your system when the Swap partition is changed.

---

### Post by Lockheed on 2010-03-16
> **dcstar said:**
> And resizing the Swap partition changes the UUID which breaks things - refer to the many HOWTOs on how to fix your system when the Swap partition is changed.
Funnily enough, according to **ls -l /dev/disk/by-uuid**
the UUID of the SWAP partition has not changed.

---

### Post by blazemore on 2010-03-16
With all due respect, [correlation does not imply causation.]("http://xkcd.com/552/")

---

### Post by Lockheed on 2010-03-16
I'd love to engage in philosophical discussions, but I need to get my sound playback fixed first.

---

### Post by Lockheed on 2010-03-16
> **prodigy_ said:**
> Maybe it's time to upgrade to 9.10? YMMV, but I had much less hardware-releated issues with it.
I just upgraded and my sound is still screwed.

---

### Post by Megafag on 2010-03-16
> **Lockheed said:**
> I just upgraded and my sound is still screwed.

Then use windows XP.

its a lot more logical ;)

---

### Post by Lockheed on 2010-03-16
It is, sadly it is also less powerful.
Might try Arch, though.

---

### Post by prodigy_ on 2010-03-16
> **Lockheed said:**
> I just upgraded and my sound is still screwed.
Try to remove ALSA and reinstall it from an official repository. Karmic uses v1.0.20 by default. For me it works. (Toshiba laptop, Conexant CX20549 sound.)

---

### Post by Megafag on 2010-03-16
> **Lockheed said:**
> It is, sadly it is also less powerful.
Might try Arch, though.

Try Crunchbang, its a crapload of fun.

---

### Post by soltanis on 2010-03-16
CTFO, it's just ALSA being ALSA. At least your sound screwed up for some kind of reason, however dumb it was; my experience with ALSA is that sound screws up for no reason whatsoever.

[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

OSS4 >>>> ALSA >= OSS3

Enjoy having your sound system back. PS Don't forget to reboot **after** blacklisting ALSA but **before** installing the package. Otherwise the ALSA modules get in the way and your computer gets sad/errors.

---

### Post by dcstar on 2010-03-16
> **Lockheed said:**
> Yes, you guess it! Ubuntu – which always beats any Windows by at least two lengths!

Maybe 6 months ago I would be surprised, but after a year of putting up with all that ridiculous ubuntu problems, nothing amazes me any more.

I just resized my swap partition (located at the end of the disk), and I have no more sound in Ubuntu. Go figure.

This is what's happening when I try to restart ALSA:
```
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/juha/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/juha/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-codec-conexant snd-hda-intel snd-hda-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-codec-conexant snd-hda-codec snd-pcm snd-timer snd-page-alloc).
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/juha/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-intel snd-hda-codec-conexant snd-hda-codec snd-pcm snd-timer snd-page-alloc.
Loading ALSA sound driver modules: snd-hda-intel snd-hda-codec-conexant snd-hda-codec snd-pcm snd-timer snd-page-alloc.

```

As a test, create a new user, log in and see if the sound works on that account.

---

