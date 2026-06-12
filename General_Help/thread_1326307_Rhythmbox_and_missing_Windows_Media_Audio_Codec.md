---
title: "Rhythmbox and missing Windows Media Audio Codec"
date: 2009-11-14
forum: General Help
---

### Post by somking95 on 2009-11-14
I have a clean install of 9.10. I am trying to build my music library in Rhythmbox. Evidently, I am missing codecs for some windows audio file type. Rhythmbox can't find a plug in to handle the file type and will not finish building my library. I pasted the error message below. I have installed various gsteamer packages and w32 package but still get the error. 

Can anyone point me to the correct package?   



> ** (rhythmbox:4029): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:4029): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|Windows Media Audio decoder|decoder-audio/x-wma, wmaversion=(int)4, bitrate=(int)304240


---

### Post by somking95 on 2009-11-14
This problem appears to be solved but I don't know which step solved it. Basically, I uninstalled some gstreamer packages. I assume that I didn't have the codec installed when first running Rhythmbox and then installed too many packages looking for the right one. Either way, it appears to be working.

---

### Post by arnab_das on 2009-11-14
> **somking95 said:**
> This problem appears to be solved but I don't know which step solved it. Basically, I uninstalled some gstreamer packages. I assume that I didn't have the codec installed when first running Rhythmbox and then installed too many packages looking for the right one. Either way, it appears to be working.

install the ubuntu restricted extras pack.

sudo apt-get install ubuntu-restricted-extras

---

### Post by somking95 on 2009-11-14
> **arnab_das said:**
> install the ubuntu restricted extras pack.

sudo apt-get install ubuntu-restricted-extras

thanks for the reply

I had installed that package but for some reason the codec wasn't found but its working now.

---

### Post by sivlardemalle on 2009-12-31
I have this problem as well. Only since 9.10 on a clean install.

A work-around is to install 
sudo apt-get install libxine1-ffmpeg

and amarok. And to play wma and mp3 through amarok.

---

### Post by Jabz.biz on 2009-12-31
I also have both packages installed, yet i get the error message. Hmmm...will watch it for a while.

---

