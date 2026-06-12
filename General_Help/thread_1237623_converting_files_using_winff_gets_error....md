---
title: "converting files using winff gets error..."
date: 2009-08-11
forum: General Help
---

### Post by stlsaint on 2009-08-11
im trying to convert movies to mpeg4 etc etc but when i attmept to use winff to conver avi to mpeg4 i get this...and it wont do anything...please help or give another program for video conversion...


echo -n "\033]0; Converting luso-sc.avi (1/1)\007"
/usr/bin/ffmpeg -i "/home/stlsaint/Desktop/luso-sc.avi" -r 29.97 -vcodec libx264 -s 640x480 -aspect 4:3 -flags +loop -cmp +chroma -deblockalpha 0 -deblockbeta 0 -b 1250k -maxrate 1500k -bufsize 4M -bt 256k -refs 1 -bf 3 -coder 1 -me_method umh -me_range 16 -subq 7 -partitions +parti4x4+parti8x8+partp8x8+partb8x8 -g 250 -keyint_min 25 -level 30 -qmin 10 -qmax 51 -qcomp 0.6 -trellis 2 -sc_threshold 40 -i_qfactor 0.71 -acodec libfaac -ab 112k -ar 48000 -ac 2 "/home/stlsaint/Desktop/completed torrents/luso-sc.mp4"
read -p "Press Enter to Continue" dumbyvar
rm "/home/stlsaint/.winff/ff090811140327.sh"

---

### Post by paul.gevers on 2009-08-12
In the menu -> Options: swich off the "Show CMD line" option.

---

