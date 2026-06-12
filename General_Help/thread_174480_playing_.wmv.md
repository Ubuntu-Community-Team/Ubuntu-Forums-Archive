---
title: "playing .wmv"
date: 2006-05-11
forum: General Help
---

### Post by jeisma on 2006-05-11
hello!

ive already done this:

wget -c [ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb)

sudo dpkg -i w32codecs_20050412-0.0_i386.deb

but i still cant play "some" .wmv files using either vlc, kaffeine or totem. the slider and sound shows the file is being read, but it doesnt show the video.

what else do i need?

thanks!

---

### Post by Dr. Nick on 2006-05-11
I think vlc and totem have their own drivers for wmv and dont rely on the w32codecs, dont quote me on this though. Have you installed the gstreamer plugins for wmv?

---

### Post by DOtSlaSHuCantCME on 2006-05-11
[QUOTE=jeisma]hello!

ive already done this:

wget -c [ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb)

sudo dpkg -i w32codecs_20050412-0.0_i386.deb

but i still cant play "some" .wmv files using either vlc, kaffeine or totem. the slider and sound shows the file is being read, but it doesnt show the video.

what else do i need?

thanks![/QUOTE]


Hi............i know Totem looks for codecs at /usr/lib/win32  check if dir is there,worst
comes to worst got here [http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html) and download the essential package ,then Create or Extract to /usr/lib/win32 dir.

More ideas will come...........

---

### Post by jeisma on 2006-05-11
[QUOTE=Dr. Nick]I think vlc and totem have their own drivers for wmv and dont rely on the w32codecs, dont quote me on this though. Have you installed the gstreamer plugins for wmv?[/QUOTE]

hi!

i've already done these too!

sudo apt-get install gstreamer0.8-plugins
sudo apt-get install gstreamer0.8-lame
sudo apt-get install gstreamer0.8-ffmpeg
sudo apt-get install lame
sudo apt-get install sox
sudo apt-get install ffmpeg
sudo apt-get install mjpegtools
sudo apt-get install vorbis-tools
sudo apt-get install w32codecs
gst-register-0.8

what else is needed?

thanks!

---

### Post by Dr. Nick on 2006-05-11
not sure what else to do exactly, Do you have a example of one that wont play that you could link to so others could check?

---

### Post by jeisma on 2006-05-11
i will try to install mplayer. i hope it works. thanks!

---

