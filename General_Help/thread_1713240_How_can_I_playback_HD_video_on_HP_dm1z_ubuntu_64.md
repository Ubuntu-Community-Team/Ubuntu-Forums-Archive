---
title: "How can I playback HD video on HP dm1z ubuntu 64"
date: 2011-03-23
forum: General Help
---

### Post by headlice on 2011-03-23
HD video is not watchable.

I know the hardware can handle it, because I am dual booting Windows 7 and it can play back the video just fine, if I have CCCP codecs installed.

So what I think is going on is a codec issue- I dont have the right ones.

PC= HP dm1z
OS= Ubuntu 10.10 x64
RAM= 4GB

I have tried:

Smplayer
VLC
Totem
Mplayer

None work.

Thanks

---

### Post by devguy on 2011-03-24
See My Post [here]("http://ubuntuforums.org/showthread.php?t=1706536&highlight=dm1z").  (Specifically the VAAPI section).  You need Catalyst 11.2 (AKA FGLRX).

---

### Post by headlice on 2011-03-24
> **devguy said:**
> See My Post [here]("http://ubuntuforums.org/showthread.php?t=1706536&highlight=dm1z").  (Specifically the VAAPI section).  You need Catalyst 11.2 (AKA FGLRX).

I have Catalyst 11.2 installed.

While in vdpau-video-0.7.3 directory:

```
sudo make
```

```
...blah blah..



vdpau_driver_template.h:641: error: 'vdpau_LockSerface' undeclared (first use in this function)
```

What do I have to do to compile correctly?

I did do./configure beforehand

---

### Post by devguy on 2011-03-27
> **headlice said:**
> I have Catalyst 11.2 installed.

While in vdpau-video-0.7.3 directory:

```
sudo make
```

```
...blah blah..



vdpau_driver_template.h:641: error: 'vdpau_LockSerface' undeclared (first use in this function)
```

What do I have to do to compile correctly?

I did do./configure beforehand

AMD has no support for VDPAU.  You need to follow the tutorial on the XBMC forums (which I have linked in the page I linked you to) to compile XBMC with VAAPI support.

---

