---
title: "Compiling Problems"
date: 2006-01-26
forum: General Help
---

### Post by Chubtoad on 2006-01-26
I'm trying to compile ffmpeg from cvs, and this is one of my few tries at trying to do such things, and I'm running into a lot of problems, as I usually do.

I ran the command to get ffmpeg from their cvs repository

cvs -z9 -d:pserver:anonymous@mplayerhq.hu:/cvsroot/ffmpeg co ffmpeg

then I did ./configure --enable-gpl --enable-pp --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr --enable-xvid --enable-mp3lame

and that seemed to be okay, but when i tried to do make, it errors out and I dont know how to fix it at all, any help would be greatly appreciated. This is the end of the make output


xvid_rc.c: In function âff_xvid_rate_control_initâ:
xvid_rc.c:67: error: âxvid_plugin_2pass2_tâ has no member named âvbv_sizeâ
xvid_rc.c:68: error: âxvid_plugin_2pass2_tâ has no member named âvbv_maxrateâ
xvid_rc.c:69: error: âxvid_plugin_2pass2_tâ has no member named âvbv_initialâ
make[1]: *** [xvid_rc.o] Error 1
make[1]: Leaving directory `/home/mythtv/ffmpeg/libavcodec'
make: *** [lib] Error 2

---

### Post by amohanty on 2006-01-26
I think ffmpeg is in the graphics - universe section. Have you tried enabling universe and installing via synaptic?

AM

---

### Post by Chubtoad on 2006-01-26
Yes, I have enabled those and installed ffmpeg, however the problem is the one in the repositories does not have xvid support. As I have been unable to find a precompiled one that does I have resorted to trying to compile from cvs, as ffmpeg does not have freqeuent releases at all.

If anyone knows of a repository that is compatible with debian/ubuntu that has xvid support built in, please direct me there. thanks

---

### Post by amohanty on 2006-01-27
can you post the output of the ./configure you ran above?

AM

---

### Post by stillboy on 2006-01-30
I am having the same problem, my guess is that ffmpeg is being built against a newer version of xvid , although I am not sure. I am guessing that we need to build against the cvs xvid.... i think ;)

---

### Post by RAOF on 2006-01-30
I compile CVS ffmpeg just fine against Ubuntu packaged xvids.  Do you have the requisite -dev packages installed?  I'd start with "sudo apt-get build-dep ffmpeg", to get most of the build dependencies, and then "sudo aptitude install libxvidcore-dev liblame-dev" to get the xvid & lame libraries required.

Also, the ffmpeg ./configure doesn't actually check to see that you have the dependencies for the options you've selected, so you need to make sure you've got the -dev packages before trying to build it.

---

### Post by stillboy on 2006-01-31
actually, i just found this- [http://po-ru.com/diary/fixing-ffmpeg-on-ubuntu/](http://po-ru.com/diary/fixing-ffmpeg-on-ubuntu/) might be a bit easier. I installed and had no probs

---

