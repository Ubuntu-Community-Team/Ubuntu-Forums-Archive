---
title: "Package dependencies from manual compiled packages"
date: 2010-06-29
forum: General Help
---

### Post by drzee on 2010-06-29
I have tried every conceivable thing. Searched high and low on google - but I have not found a solution.

I have compiled FFMPEG (and also mplayer and x264) from scratch to always run the latest version.

I install ffmpeg using "checkinstall". 

When compiling FFMPEG manual and installing with checkinstall ffmpeg provides the following libraries:

libavutil49, libavcodec52, libavdevice52, libavformat52, libavfilter0, libpostproc51, libswscale0

These can NOT be installed via apt-get (or similar) or the checkinstall will fail. So I have not installed them.

The problem now is when I need to install a package (.dep or from Synaptic) that requires one of these a prerequisite. Then it is not "registered" by Synaptic that these are already provided through the FFMPEG build. 

I have tried to use the --provides flag on checkinstall and I can also see in Synaptic that on the ffmpeg package I installed with checkinstall that it says it provides said packages. I even have tried to modify the checkinstall script and add:

Replaces: libavutil49, libavcodec52, libavdevice52, libavformat52, libavfilter0, libpostproc51, libswscale0

This also triggers Synaptic to list that ffmpeg replaces the packages. 

But still when I try to install anything that needs these packages it is not recongnized that they are provided by FFMPEG and when I install one of them (e.g. apt-get install libavformat52) then it replaces the FFMPEG library and FFMPEG stops working.

So what is going wrong? Is this a bug in Synaptic? How is it possible under ubuntu to install manual compiled packages and have them "act" as correct dependencies for others?

Anyone?

I use ubuntu 9.10 ...

Thanks!

---

### Post by FakeOutdoorsman on 2010-06-29
See [this thread](http://ubuntuforums.org/showpost.php?p=9508173&postcount=1068) on how to create a FFmpeg package that will provide the additional libraries into the package management system.

Also, if you do create a package using this method, then it still does not guarantee that a package from the repository will work with it because these packages may be set to use a certain libav* version and the compiled libav* may not match this, as far as I know.

---

### Post by drzee on 2010-07-06
Thanks - that at least pointed me in the right direction. Believe I can  make it work correctly like that.

One thing though - is there an  easy way to generate a "debian/confflags" file? Or some guidelines how  this file should look etc?

Thanks!

---

