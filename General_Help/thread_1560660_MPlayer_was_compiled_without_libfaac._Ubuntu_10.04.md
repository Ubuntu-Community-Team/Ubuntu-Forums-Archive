---
title: "MPlayer was compiled without libfaac. Ubuntu 10.04"
date: 2010-08-25
forum: General Help
---

### Post by Ben Leedham on 2010-08-25
Hi,

 On previous versions of Ubuntu I have used mencoder to convert avi to mp4 for my iPhone using this command:

```
mencoder <input-file>.avi -o <output-file>.mov -vf \
dsize=480:352:2,scale=-8:-8,harddup -oac faac -faacopts \
mpeg=4:object=2:raw:br=128 -of lavf -lavfopts format=mp4 \
-ovc x264 -sws 9 -x264encopts \
nocabac:level_idc=30:bframes=0:bitrate=512:threads=auto:turbo=1:global_header:threads=auto:subq=5:frameref=6:partitions=all:trellis=1:chroma_me:me=umh
```

In all honesty I don't have too much of an idea what all the options mean, but it always worked, up until upgrading to Ubuntu 10.04.

Now when I try and run it I get this error:

MPlayer was compiled without libfaac. See README or DOCS.

Can anyone suggest what I could do to solve this? From what I can see in the command above it appears that faac is specified as the audio encoder, can I use an alternative or do I have to re-install Mencoder?

Cheers.

---

### Post by andrew.46 on 2010-08-25
Hi Ben,

A license problem lead to faac being removed, I believe that Medibuntu has a MEncoder package that allows aac transcoding though for Lucid. Just be aware that the Medibuntu repository seems to be having a few technical problems at the moment...

Andrew

---

### Post by Ben Leedham on 2010-08-25
Thanks very much Andrew, that pointed me in the right direction, much appreciated.

For anyone else having a similar problem, what I did was:

```
sudo apt-get remove mencoder
```

to remove mencoder, then added the Medibuntu repository, instructions can be found here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Just run the first 2 shell commands specified in that link.

Now reinstall mencoder:

```
sudo apt-get install mencoder
```

You should see it contacting the Medibuntu repo for the download. I tried running my command again and it all went smoothly.

---

### Post by andrew.46 on 2010-08-25
Hi Ben,

> **Ben Leedham said:**
> Thanks very much Andrew, that pointed me in the right direction, much appreciated.

No problems :). The faac removal issue has been unpopular with Lucid users although I appreciate the licensing issues that face the Ubuntu developers. Looks like the issue has not been resolved in Maverick either...

Andrew

---

### Post by mc4man on 2010-08-25
> Looks like the issue has not been resolved in Maverick either...
Doesn't appear so though I think it was momentarily  enabled in 10.10  ( blue ver.

From changelog
> .................
ffmpeg (4:0.6-2ubuntu1) maverick; urgency=low

  * merge from debian/experimental. remaining changes:
    - don't disable encoders
    - don't build against libfaad, libdirac, librtmp and libopenjpeg (all in universe)

 -- Reinhard Tartler <siretart@tauware.de>  Sun, 11 Jul 2010 11:00:54 -0400

ffmpeg (4:0.6-2) experimental; urgency=low

  [ Fabian Greffrath ]
  * Enable RTMP[E] support via librtmp.
  * [COLOR="Blue"]Disable aac encoder[/COLOR], see README.Debian.
  * Fix obsolete-relation-form for the internal dependencies.
  * Merge debian/README.Source into debian/README.source and add section
    headers.
  * Remove obsoleted support for the non-free libamr-nb/wb.

  [ Reinhard Tartler ]
  * enable runtime-cpudetect
  * conditionally build against opencore-amr if installed in the build
    environment
  * update upstream url in debian/copyright
  * fix usage documentation in debian/get-orig-source.sh
  * update dep3 headers for debian/patches/900_doxyfile
  * add proper replaces for moving presets back to ffmpeg
  * make debian/patches gbp-pq friendly
  * Add VP80 fourcc to libavformat/riff.c
  * Backport-AAC-HE-v2
  * bump Standards-Version, no changes needed

 -- Reinhard Tartler <siretart@tauware.de>  Tue, 29 Jun 2010 09:07:56 +0200

ffmpeg-extra ([COLOR="Blue"]4:0.6-1ubuntu1[/COLOR]) maverick; urgency=low

  * merge from 'main' package. Changes:
    - build against faad, dirac, libopenjpeg, x264, mp3lame and xvidcore

 -- Reinhard Tartler <siretart@tauware.de>  Wed, 16 Jun 2010 13:04:08 +0200
......

This bug has good explanations from James Westby and Reinhard Tartler
( there were actually 2 issues, allow aac encoding and allow libfaac itself
[https://bugs.launchpad.net/ubuntu/+source/faac/+bug/374900](https://bugs.launchpad.net/ubuntu/+source/faac/+bug/374900)

---

### Post by sthomas505 on 2010-10-21
> **Ben Leedham said:**
> Thanks very much Andrew, that pointed me in the right direction, much appreciated.

For anyone else having a similar problem, what I did was:

```
sudo apt-get remove mencoder
```to remove mencoder, then added the Medibuntu repository, instructions can be found here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Just run the first 2 shell commands specified in that link.

Now reinstall mencoder:

```
sudo apt-get install mencoder
```You should see it contacting the Medibuntu repo for the download. I tried running my command again and it all went smoothly.


Many thanks, Ben and Andy for this.

---

### Post by m4dm1k3 on 2011-05-04
> **Ben Leedham said:**
> Thanks very much Andrew, that pointed me in the right direction, much appreciated.

For anyone else having a similar problem, what I did was:

```
sudo apt-get remove mencoder
```to remove mencoder, then added the Medibuntu repository, instructions can be found here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Just run the first 2 shell commands specified in that link.

Now reinstall mencoder:

```
sudo apt-get install mencoder
```You should see it contacting the Medibuntu repo for the download. I tried running my command again and it all went smoothly.

Thanks a lot ! It help me .

---

