---
title: "Hamfax using /dev/dsp how to make it work on 10.04 with pulseaudio"
date: 2010-08-05
forum: General Help
---

### Post by MechaMechanism on 2010-08-05
Hamfax is using the old /dev/dsp.  How do I make Hamfax work with the audio system in 10.04.  Can I use Pulseaudio?

---

### Post by h3n5y on 2010-12-09
+1

Got the same problem here.
Maybe through /dev/snd? 

~$ ls -lR /dev/snd
/dev/snd:
total 0
drwxr-xr-x  2 root root      60 2010-12-09 18:03 by-path
crw-rw----+ 1 root audio 116, 7 2010-12-09 18:03 controlC0
crw-rw----+ 1 root audio 116, 6 2010-12-09 22:11 pcmC0D0c
crw-rw----+ 1 root audio 116, 5 2010-12-09 22:06 pcmC0D0p
crw-rw----+ 1 root audio 116, 4 2010-12-09 18:04 pcmC0D1p
crw-rw----+ 1 root audio 116, 3 2010-12-09 18:03 seq
crw-rw----+ 1 root audio 116, 2 2010-12-09 18:03 timer

/dev/snd/by-path:
total 0
lrwxrwxrwx 1 root root 12 2010-12-09 18:03 pci-0000:00:14.5 -> ../controlC0

---

### Post by chsc on 2011-07-18
hamfax 0.6.4 in Ubuntu only supports the OSS sound interface, where the sound is sent through device files like /dev/dsp. The kernel module snd_pcm_oss provides this interface for compatibility. You could try to modprobe the snd_pcm_oss module manually to see if this provides the missing /dev/dsp device files.

The device files in /dev/snd/ belong to the ALSA sound interface. hamfax 0.7 includes support for the ALSA sound interface:
[http://sourceforge.net/news/?group_id=28799](http://sourceforge.net/news/?group_id=28799)

If the snd_pcm_oss kernel module does not work, you could try using hamfax 0.7. The source code is available here:
[http://sourceforge.net/projects/hamfax/files/](http://sourceforge.net/projects/hamfax/files/)

---

### Post by MechaMechanism on 2011-07-18
> **chsc said:**
> hamfax 0.6.4 in Ubuntu only supports the OSS sound interface, where the sound is sent through device files like /dev/dsp. The kernel module snd_pcm_oss provides this interface for compatibility. You could try to modprobe the snd_pcm_oss module manually to see if this provides the missing /dev/dsp device files.

The device files in /dev/snd/ belong to the ALSA sound interface. hamfax 0.7 includes support for the ALSA sound interface:
[http://sourceforge.net/news/?group_id=28799](http://sourceforge.net/news/?group_id=28799)

If the snd_pcm_oss kernel module does not work, you could try using hamfax 0.7. The source code is available here:
[http://sourceforge.net/projects/hamfax/files/](http://sourceforge.net/projects/hamfax/files/)
Thanks for the heads up about version 0.7.

---

### Post by chsc on 2011-07-26
Now looking at this again on Ubuntu 11.04: There is no more kernel module that provides the OSS interface. But you could use the userspace compatibility library aoss:```
sudo apt-get install alsa-oss
aoss hamfax
```

---

### Post by chsc on 2011-08-01
Another option would be grabbing the new 0.8.1 version from the PPA: [https://launchpad.net/~ubuntu-hams/+archive/ppa](https://launchpad.net/~ubuntu-hams/+archive/ppa)

---

