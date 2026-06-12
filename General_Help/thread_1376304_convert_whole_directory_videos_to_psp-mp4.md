---
title: "convert whole directory videos to psp-mp4"
date: 2010-01-09
forum: General Help
---

### Post by rfrayer on 2010-01-09
ok guys i thought id share this script i put together this is asuming you either compiled mplayer or have all the win32codecs installed with mencoder

```
#!/bin/bash
for i in *.flv; do
v=`basename "$i" .mp4`
mencoder \
\
\
"$i" \
\
-oac lavc -ovc lavc -of lavf -lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:vpass=1:vbitrate=384:acodec=libfaac -af lavcresample=24000 -vf scale=368:208,harddup -lavfopts format=psp -ofps 15 -o /dev/null \
&& \
mencoder \
\
\
"$i" \
\
\
-oac lavc -ovc lavc -of lavf -lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:vpass=2:vbitrate=384:acodec=libfaac -af lavcresample=24000 -vf scale=368:208,harddup -lavfopts format=psp -ofps 15 -o \
\
\
"$v.mp4" \
&& rm divx2pass.log
done
```change the flv in to whatever file extension you are converting to psp mp4 in

```
for i in *.flv; do
```
i made my script in /usr/bin/flv2psp

---

### Post by rfrayer on 2010-01-09
ok i did a little modifying tlo makw the script more extension friendly


```
#!/bin/bash
rename -v 's/\.FLV$/\.flv/' *.FLV
for i in *.flv; do
v=`basename "$i" .mp4`
mencoder \
\
\
"$i" \
\
-oac lavc -ovc lavc -of lavf -lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:vpass=1:vbitrate=384:acodec=libfaac -af lavcresample=24000 -vf scale=368:208,harddup -lavfopts format=psp -ofps 15 -o /dev/null \
&& \
mencoder \
\
\
"$i" \
\
\
-oac lavc -ovc lavc -of lavf -lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:vpass=2:vbitrate=384:acodec=libfaac -af lavcresample=24000 -vf scale=368:208,harddup -lavfopts format=psp -ofps 15 -o \
\
\
"$v.mp4" \
&& rm divx2pass.log && rename -v 's/\.flv.mp4$/\.mp4/' *.flv.mp4
done
mkdir old-files/ && mv *.flv old-files/
echo ".........."
echo "...................."
echo ".............................."
echo "Conversion Is Complete!!!..."
```Ive included some deb files to install make sure you have the medibuntu repos activates by the fallowing

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

after instalation just cd into the directory and run the script
example

flv2psp
avi2psp
mpg2psp

[http://ubuntu.global-web.us/mpg2psp-i386.deb](http://ubuntu.global-web.us/mpg2psp-i386.deb)
[http://ubuntu.global-web.us/flv2psp-i386.deb](http://ubuntu.global-web.us/flv2psp-i386.deb)
[http://ubuntu.global-web.us/avi2psp-i386.deb](http://ubuntu.global-web.us/avi2psp-i386.deb)

---

