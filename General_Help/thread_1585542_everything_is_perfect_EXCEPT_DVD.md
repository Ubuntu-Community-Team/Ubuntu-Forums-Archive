---
title: "everything is perfect EXCEPT DVD"
date: 2010-09-30
forum: General Help
---

### Post by THIRTH on 2010-09-30
I've tried many many things but getting this computer to read my dvds is impossible.

Totem:
Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc.

VLC:
I just hear the CD-ROM running, but nothing happens with the DVD, no sound, no video.

Any suggestions?

---

### Post by mc4man on 2010-09-30
installing libdvdcss2 may prove fruitful

In terminal

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```



To fill in gstreamer plugins for totem, rhythmbox, ect.

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly
```

---

### Post by THIRTH on 2010-09-30
No change =\ ..of course lol

---

### Post by mjitkop on 2010-09-30
Have you already checked this help page:
[https://help.ubuntu.com/10.04/musicvideophotos/C/video-dvd.html](https://help.ubuntu.com/10.04/musicvideophotos/C/video-dvd.html) ?

I just remembered that I had a similar problem recently. I used to be able to play DVDs at some point and then one day it didn't work anymore. Totem was telling me it had no permissions to open the DVD drive or something to that effect. I remembered then that not long before that I had installed Handbrake as I was trying different things. I unsinstalled Handbrake and everything was fine after that.

---

### Post by THIRTH on 2010-09-30
I have all of those installed now and there is a new error.

Totem says:
An error occurred
Could not read from resource

---

### Post by davidmohammed on 2010-09-30
try installing all the restricted plugins

i.e.

sudo apt-get install ubuntu-restricted-extras

---

### Post by THIRTH on 2010-09-30
No change, unfortunate but thanks for the help

---

### Post by dv3500ea on 2010-09-30
Try opening a terminal (Applications -> Accessories -> Terminal) and entering this:
```

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update && sudo apt-get install libdvdcss

```
You can copy it then past it into the terminal by pressing ctrl-shift-v.
This will enable a software repository not included b default for legal reasons and install the DVD decrypting codecs needed to play commercial DVDs.

---

### Post by THIRTH on 2010-09-30
Same old message

Cannot read from resource from Totem

and VLC just wants nothing to do with it, no messages, so cold.

---

### Post by SeijiSensei on 2010-09-30
Try [smplayer]("http://smplayer.sourceforge.net/") (sudo apt-get install smplayer).  I really don't know why this isn't a much more widely distributed media player compared to things like Totem.

If it won't play, look under Options > View Logs > mplayer.  You may get some useful information there.  You're probably missing [libdvdread]("http://www.tech-recipes.com/rx/2765/ubuntu_enable_dvd_playback/").

---

### Post by mc4man on 2010-09-30
Well you can stop chasing codecs, libs, plugins - you have all you need.

Just so we now what drive you have could you run this and post what's shown (ignore the warning about running as super-user
```
lshw -C disk
```

---

### Post by THIRTH on 2010-09-30
all it gives me is that warning thing, nothing else...

---

### Post by mc4man on 2010-09-30
Well then use sudo, though only care about what's listed on *-cdrom: section(s)
( as in 
sudo lshw -C disk
(only wanted so could have vlc open the dvd directly from a command, doesn't really matter though easier if the /dev links for the drive are known.

If you wish try this - 
put a dvd in the drive, close out any pop up or player.
Open home folder -> view -> show hidden files, locate the .dvdcss folder and delete it.

Then in terminal
```
 export DVDCSS_VERBOSE=2
```
```
vlc > vlc_output.log 2>&1
```
when vlc opens go Media -> open disc -> play (make sure dvd is selected, should be
whatever happens then ck. the log in home folder and post.

If the log indicates no issue with authenticating the drive and getting the keys but vlc still doesn't play or crashes then try -
close vlc if still open
```
vlc --vout x11
```
and try to play the disk

---

### Post by mc4man on 2010-10-01
Ok - you have a matshita dvd drive. (you'll notice in log a failure to auth.
 With these drives **a region must be set** and **you can only play dvd's from that region.**
(there is a new firmware hack for **some** matshita dvd drives that allows playback from any region but not something that can be done in linux 

to set region or ck. if it's been set
```
sudo apt-get install regionset
```

With a disk in the drive run this in terminal
```
regionset
```

If line 4 says type: None and you see user controlled changes resets available: 5
then set to your region
(most likely 1 - usa or 2 europe
> 1 	United States, Canada, Bermuda, U.S. territories
2 	Europe (except Russia, Ukraine, and Belarus), Middle East, Egypt, Japan, South Africa, Swaziland, Lesotho, Greenland
3 	Southeast Asia, South Korea, Republic of China (Taiwan), Hong Kong, Macau
4 	Mexico, Central America, South America, Australia, New Zealand, Oceania
5 	Afghanistan, Ukraine, Belarus, Russia, Africa (except Egypt, South Africa, Swaziland, and Lesotho), Central and South Asia, Mongolia, North Korea
6 	People's Republic of China, Hong Kong
7 	Reserved for future use (found in use on protected screener copies of MPAA-related DVDs and "media copies" of pre-releases in Asia)
8 	International venues such as aircraft, cruise ships, etc.

If it shows set then copy the terminal and post back
If you set a region then go ahead and delete the .dvdcss folder again and try vlc normally

(do not change regions to match dvd's - after 5 sets the drive is locked at last change

---

### Post by THIRTH on 2010-10-01
You are a genius, and if you are a semi attractive female, you're now my wife!!!!! 

DVD working =)

---

