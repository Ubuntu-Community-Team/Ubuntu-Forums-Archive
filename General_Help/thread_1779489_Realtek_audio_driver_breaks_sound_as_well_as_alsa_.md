---
title: "Realtek audio driver breaks sound as well as alsa tools, can I uninstall it?"
date: 2011-06-10
forum: General Help
---

### Post by dwigyit on 2011-06-10
Hello :)

I have an MSI GX660(r) which runs Ubuntu 11.04 and Windows. As the audio only comes out of the sub woofer (is it called that? It's quiet and deep and pops the speaker with anything high pitch, no matter how quiet), I decided to try installing the Realtek HD audio driver, which had fixed a few of my Windows problems with sound in the past.

The driver was installed from here [http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=23&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=23&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false)

I installed it by running it as root as it says, but now no sound works at all, and the sound manager says that there is no sound hardware other than dummy audio. On top of that, alsamixer and alsaconfig and all such tools give errors. alsamixer, for example, says "cannot open mixer: No such file or directory". I was wondering if anyone could tell me how to remove or fix the driver as, even when the sound only came out of the sub woofer, I could still use headphones. Now I can't use anything... :(

Of course, if anyone knows how to fix the whole sound issue, including the sub woofer thing, then that would be cool too! There are quite a few threads about it, but they all included adding lines to alsa-base.conf which never worked for me.

---

### Post by dwigyit on 2011-06-11
This is the content of the installer script - in case it helps...

> #!/bin/sh

######## VERSION 1.0 ########

kaversion=`uname -r`
kversion=`echo $kaversion | cut -d . -f 1`
kpatchlevel=`echo $kaversion | cut -d . -f 2`
ksublevel=`echo $kaversion | cut -d . -f 3`
kextraversion=`echo $kaversion | cut -d . -f 4`

. ./version

echo ".....Decompress Driver source v1.0.24-$ver"
tar jxvpf alsa-driver-1.0.24-$ver.tar.bz2 > /dev/null 2>&1
sync

echo "Compile Driver........"
cd alsa-driver-1.0.24
./configure --with-cards=hda-intel
make
make install
if test $kpatchlevel=4; then
   ./snddevices
fi
cd ..

## del audio stat file
if [ -f /etc/asound.state ]; then
   rm -rf /etc/asound.state > /dev/null 2>&1
fi

## sample wave
if [ -d /usr/share/sounds/alsa ]; then
     bzip2 -d test.wav.bz2
     cp -f test.wav /usr/share/sounds/alsa
     bzip2 test.wav
else
     mkdir /usr/share/sounds/alsa
     bzip2 -d test.wav.bz2
     cp -f test.wav /usr/share/sounds/alsa
     bzip2 test.wav
fi

echo "Remove Folder....."
rm -rf alsa-driver-1.0.24 > /dev/null
if test $kpatchlevel=4; then
   alsaconf
fi

---

### Post by dwigyit on 2011-06-16
Does anyone reading this think that my only option is to reinstall, because I'd rather not do that but I will if I'm told it's the only way?

---

### Post by jonpday on 2011-08-20
I've got the same problem, I've tried a million things and none of them worked.  Did you find a solution other than re-installing Ubuntu?

---

### Post by dwigyit on 2011-08-20
Nope - sorry. I just reinstalled it :(

---

