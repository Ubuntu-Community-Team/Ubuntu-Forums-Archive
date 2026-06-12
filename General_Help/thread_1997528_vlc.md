---
title: "vlc"
date: 2012-06-05
forum: General Help
---

### Post by ajits on 2012-06-05
VLC player did not play vedio cd why ? please help me...

---

### Post by dino99 on 2012-06-05
what happen when you try to read one ?
do you get a warning/error dialog box ?

which ubuntu & vlc are you running ?

i suppose you need to install some more gstreamer codecs

---

### Post by ajits on 2012-06-05
> **dino99 said:**
> what happen when you try to read one ?
do you get a warning/error dialog box ?

which ubuntu & vlc are you running ?

i suppose you need to install some more gstreamer codecs

when I try to play a video cd (.dat file) vlc show an error message is"file reading failed,  vlc could not read the file (input/output error).but it can play the same format file from hard disc. also the same vcd play in mediaplayer of widows xp. I use ubundu 12.04.please help me to solve it..;)

---

### Post by wallaroo on 2012-06-05
You need to make sure that VLC knows it's playing a VCD and its using a 'CD' device  (not a 'DVD').

In VLC just go to 'Media' -> 'Open Disc', then select 'SVCD/VCD' and change the Device setting to the appropriate 'CDROM' device.

Hit 'Play' and you should have more success.

---

### Post by ajits on 2012-06-06
I did the same procedure in earlier.but now just change my way,ie media>open(advanced)>disk>svcd/vcd>disc Device- change to /dev/cdrom2.then start to play.
THANKS  FOR YOUR KIND DIRECTIONS.

---

