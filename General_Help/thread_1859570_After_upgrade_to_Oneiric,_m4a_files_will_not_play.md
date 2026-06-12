---
title: "After upgrade to Oneiric, m4a files will not play"
date: 2011-10-14
forum: General Help
---

### Post by pierce_g on 2011-10-14
I haven't had any trouble playing m4a files prior to upgrading.

I've tried reinstalling Rhythmbox and the gstreamer plugins (good, bad, and ugly) to no avail.

The specific error is:
```

No packages with the requested plugins found
The requested plugins are:
MPEG-4 AAC demuxer
```Thanks in advance. Let me know if any log files/configuration files would be helpful.

---

### Post by Tman5293 on 2011-10-14
Try this:

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by pierce_g on 2011-10-14
I already have the latest restricted extras. I tried reinstalling just to be sure but that didn't work.

---

### Post by Tman5293 on 2011-10-14
Try searching for mpeg4 in the software center. That came up with the right codecs for me. If that doesn't work try searching for aac in the software center and those codecs come up as well.

Did the files you are trying to play come from iTunes?

---

### Post by andrew.46 on 2011-10-14
I will admit that I am not fully up to speed with Oneiric yet but perhaps you could make sure you have the [Medibuntu repository enabled]("https://help.ubuntu.com/community/Medibuntu") and then run:

```
sudo apt-get install mplayer smplayer libavcodec-extra-53
```

and this should enable playback through SMPlayer at least. I have to say that I have not tested this myself yet......

---

### Post by pierce_g on 2011-10-14
I searched for mpeg4 and aac, and it looks like I already have the right codecs.

libavcodec-extra-53, the gstreamer plugins, and libfaad2 are already installed.

The files work in smplayer, so I'm not sure why Rhythmbox is still having trouble.

I think most of these files are held over from my iTunes/Rhapsody days. I've since switched to other formats, but m4a's still comprise about 15% of my library. They are license free files, though, and they worked prior to the upgrade.

---

### Post by sgage on 2011-10-14
> **pierce_g said:**
> I searched for mpeg4 and aac, and it looks like I already have the right codecs.

libavcodec-extra-53, the gstreamer plugins, and libfaad2 are already installed.

The files work in smplayer, so I'm not sure why Rhythmbox is still having trouble.

I think most of these files are held over from my iTunes/Rhapsody days. I've since switched to other formats, but m4a's still comprise about 15% of my library. They are license free files, though, and they worked prior to the upgrade.

Rhythmbox working fine here with m4a files. All I did was install ubuntu-restricted extras. Not sure what could be going on...

---

### Post by pierce_g on 2011-10-14
Well I figured it was time to get rid of the m4a files anyway, so I converted them to flac with pacpl.

Problem solved, as far as I'm concerned. :D

---

### Post by thathatman on 2011-10-14
I had the same problem. Here's what I did to fix it:
open ~/.gstreamer-0.10
remove or rename the registry.x86_64.bin
Open your music player.
it'll regenerate the registry file and correctly use the aac plugin.

Glad I could contribute an answer rather than a question this time!

---

### Post by colan on 2011-10-17
Confirming that junking the registry file worked!  Thanks.

---

### Post by chox_de on 2011-10-18
Great, that also worked for me under Ubuntu 64bit with Amarok.

I've been searching alot because of that issue, how did you figure out?

---

### Post by dashaun on 2011-10-19
> **thathatman said:**
> I had the same problem. Here's what I did to fix it:
open ~/.gstreamer-0.10
remove or rename the registry.x86_64.bin
Open your music player.
it'll regenerate the registry file and correctly use the aac plugin.

Glad I could contribute an answer rather than a question this time!

You are correct sir!  That's exactly what I was looking for!

Thanks!

---

### Post by d.j.yotta on 2011-10-27
Thank you!
Junking the registry files (there were three of them and I had to delete the .bin not the .x86_64.bin) worked.
Now I can listen to my music again :)

---

### Post by mastapat11 on 2011-11-01
> **thathatman said:**
> I had the same problem. Here's what I did to fix it:
open ~/.gstreamer-0.10
remove or rename the registry.x86_64.bin
Open your music player.
it'll regenerate the registry file and correctly use the aac plugin.

Glad I could contribute an answer rather than a question this time!

OMG!!  Thank you!
this worked perfect :)
now i don't have to strangle anybody ;)

---

### Post by froglet1 on 2011-11-22
thank you so much I had been having problems and this totally solved it! thanks soo much :KS:KS:KS:KS:KS

---

### Post by prahar on 2011-12-06
> **thathatman said:**
> I had the same problem. Here's what I did to fix it:
open ~/.gstreamer-0.10
remove or rename the registry.x86_64.bin
Open your music player.
it'll regenerate the registry file and correctly use the aac plugin.

Glad I could contribute an answer rather than a question this time!

thanks a lot! This has been bothering me for a while!!!

---

### Post by xuampy on 2011-12-29
> **thathatman said:**
> I had the same problem. Here's what I did to fix it:
open ~/.gstreamer-0.10
remove or rename the registry.x86_64.bin
Open your music player.
it'll regenerate the registry file and correctly use the aac plugin.

Glad I could contribute an answer rather than a question this time!

Just to confirm this works also on 11.10 Oneiric x64 and Banshee. Thank you very much for the tip! :KS:KS:KS:KS

---

### Post by wearebeautiful on 2012-01-16
> **thathatman said:**
> I had the same problem. Here's what I did to fix it:
open ~/.gstreamer-0.10
remove or rename the registry.x86_64.bin
Open your music player.
it'll regenerate the registry file and correctly use the aac plugin.

Glad I could contribute an answer rather than a question this time!
Trying this but I can't open the gstreamer folder. I get this error from terminal:
```
Couldn't get a file descriptor referring to the console
```

Any and all help is welcome! Apologies for the bump.

---

### Post by Chronon on 2012-01-17
Maybe provide the command you entered that led to that error.

---

### Post by dewdrop_world on 2012-07-17
Sorry to revive an old thread -- these instructions did not help me.

I recently upgraded to 12.04, and I copied my old 10.04 Music folder from a backup. From the beginning (without installing any extra packages), rhythmbox could play m4a files that I had previously encoded and imported under 10.04. But it won't allow me to import any new m4as.

I deleted the gstreamer registry, relaunched rhythmbox, still can't import.

I installed ubuntu-restricted-extras, relaunched rhythmbox, still can't import.

I checked to see that gstreamer-bad was installed -- it is. (Of course, it must have been -- otherwise, I couldn't have played the old m4a files.)

Under 10.04, I did try some other media players (Amarok, Banshee) but gave up on them because their iPod integration seemed flaky. Has that improved? (Sorry for asking instead of trying it myself... I had a really rough time upgrading last week and I'm pretty much burned out on installing packages to find out that they won't do what I wanted. It's a bit of a repeat of last week -- rip a CD, try to use it in RB, oh no, there's a problem... 45 minutes later, still not working.)

Thanks,
James

---

