---
title: "Seriously borked computer installing ffmpeg from svn"
date: 2010-12-14
forum: General Help
---

### Post by castironpants on 2010-12-14
OMG PLEASE HELP!

I'm running 10.10 and I have an ATI HD5470 and I was trying to add VAAPI support. I was told to compile and install a newer version of ffmpeg from SVN, which I did. I had to uninstall all the current/medibuntu libav* codecs to do so. I want to uninstall it but whenever I try to do anything in Synaptic it tries to reinstall the standard codecs before it can remove ffmpeg so it says

```
E: /var/cache/apt/archives/libavutil-extra-50_4%3a0.6-2ubuntu3+medibuntu1_i386.deb: trying to overwrite '/usr/lib/libavutil.so.50', which is also in package ffmpeg SVN-r25943-1
E: /var/cache/apt/archives/libavformat-extra-52_4%3a0.6-2ubuntu3+medibuntu1_i386.deb: trying to overwrite '/usr/lib/libavformat.so.52', which is also in package ffmpeg SVN-r25943-1
E: /var/cache/apt/archives/libswscale0_4%3a0.6-2ubuntu6_i386.deb: trying to overwrite '/usr/lib/libswscale.so.0', which is also in package ffmpeg SVN-r25943-1
E: /var/cache/apt/archives/libavdevice52_4%3a0.6-2ubuntu6_i386.deb: trying to overwrite '/usr/lib/libavdevice.so.52', which is also in package ffmpeg SVN-r25943-1
E: /var/cache/apt/archives/libpostproc51_4%3a0.6-2ubuntu6_i386.deb: trying to overwrite '/usr/lib/libpostproc.so.51.2.0', which is also in package ffmpeg SVN-r25943-1


```

I can't uninstall this broken version and I can't get all the applications that had to be uninstalled back! What do I do?!

---

### Post by sikander3786 on 2010-12-14
Try cleaning your apt-get cache.

```
sudo apt-get clean
```

---

### Post by castironpants on 2010-12-14
Phew, tried sudo dpkg -P --force-all ffmpeg, and it seems to have worked.

---

