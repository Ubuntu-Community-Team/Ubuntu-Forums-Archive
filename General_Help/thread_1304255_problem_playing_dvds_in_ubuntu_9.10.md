---
title: "problem playing dvds in ubuntu 9.10"
date: 2009-10-29
forum: General Help
---

### Post by AnimeFreak on 2009-10-29
ok i am having a problem getting DVD playbck (or to play)

i just updated to 9.10 and did so via fresh install

i have tried a few solutions that have worked in the past with no success 
plus i am not sure  as to what 9.10 all has so i don't want to do anything 
to mess it up 

any ideas or help are greatly appreciated

thank you in advanced

---

### Post by AnimeFreak on 2009-10-29
figured it out but i take no credit

i got the answer here

[http://ketil.vestby.name/2009/06/19/how-to-enable-dvd-playback-on-ubuntu-9-10/](http://ketil.vestby.name/2009/06/19/how-to-enable-dvd-playback-on-ubuntu-9-10/)

so if any one else is have a similar issue here is the answer

Just copy and paste everthing in the box below 
into a terminal and wait about 10 - 15 min and enjoy:]

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list 
--output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo
 apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q 
update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs 
totem-mozilla libdvdcss2 totem-xine xine-ui libxine1 libxinerama1 libxine1-all-plugins 
libxine1 libxine1-ffmpeg libdvdnav4 libdmx1 libdvdread4 gstreamer0.10-plugins-bad 
gstreamer0.10-plugins-ugly vlc smplayer smplayer-themes smplayer-translations && 
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by railroad cat on 2009-11-14
I have tried this code and a few others and my Dvd's will play, but the image and sound skip. I am very sad because in 9.04 they played fine. why is this problem occurring?

---

