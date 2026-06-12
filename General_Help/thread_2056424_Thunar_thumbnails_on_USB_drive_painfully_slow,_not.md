---
title: "Thunar thumbnails on USB drive painfully slow, not using embedded exif thumbnails"
date: 2012-09-11
forum: General Help
---

### Post by 7bit on 2012-09-11
I have seen some references that tumblerd which thunar is apparently using can create thumbnails from embedded exif thumbnails in jpeg files. However, this does not seem to work for me, it seems it is reading the complete huge image files to create thumbnails.  

When I plug in my photo camera with maybe a few hundred (new) jpg files on it, (each one has 3MB) and open the folder in thunar it starts creating thumbnails and obviously before I can do anything useful with that folder view (besides simply copying *all* photos which is not what I always want) I need to wait until all thumbnails for all new images are created.  

Thumbnail creation for a few hundred new images takes many minutes, approximately one image per second.  

I have experimented with different file managers (after unmounting, deleting the thumbnails cache and re-mounting the camera). Nauilus has the same problem. Rox on the other hand is incredibly fast and also one of my self-written tools to display a folder with photos that uses exiftool to extract all thumbnails will be able to generate more than 10 thumbnails per second (approximately the same speed as rox and also the same speed when doing this on windows XP with explorer).  

Can anybody confirm that it behaves like this on other xubuntu machines too? Empty ~/.thumbnails/ folder and then plug in an USB drive with a few hundred MB worth of jpegs (images from most cameras should have embedded thumbnails) and open the folder in thunar?  

If this works for others then maybe I am missing something or have messed up my configuration? Is there anything I could do to find out what is going on or what is missing?  

TIA, 
Bernd

---

### Post by LewisTM on 2012-09-11
I can confirm that the thumbnailer is very slow in Xfce 4.8, 1 image per second as you describe. This used to be very irritating.
_Used_ to be because it's fixed in [Xfce 4.10]("https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10"). I get about 5 images per second.
Version 4.10 is so far spotless for me, I encourage you to upgrade without a second delay :D

Cheers!

---

### Post by 7bit on 2012-09-11
> **LewisTM said:**
> 
_Used_ to be because it's fixed in [Xfce 4.10]("https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10"). I get about 5 images per second.
Version 4.10 is so far spotless for me, I encourage you to upgrade without a second delay

Thank you for that link, I did not know that there is a ppa for the new version specifically for 12.04 (I didn't even search for it because I did not expect it to exist)

I have installed it and although there are a few things finally fixed (single click open for example)  the thumbnailing is still as slow as it was before and it is still not making use of the exif embedded thumbnails.

For example curently on my camera there are 48 images, most of them around 3 MB, the camera is connected with USB-2.0. After clearing the ~/.thumbnails/ folder and clearing buffers and caches between each measurement and then measuring how long it takes to generate 48 thumbnails I measure the following times:

thunar: 52 seconds
rox: 4 seconds
my own tool (using of exiftool which is written in perl!): 4 seconds

So I assume I should file a bug. Since it is mentioned somewhere that tumblerd can and *will* use exif data for jpeg thumbnails maybe just someone forgot a configure switch when building the ubuntu binary? Where is the best place to file this bug, ubuntu bug tracker or somewhere directly at xfce?

____
PS: 
Here is evidence that tumbler should support exif thumbnails:
[http://git.xfce.org/xfce/tumbler/tree/plugins/jpeg-thumbnailer/jpeg-thumbnailer.c](http://git.xfce.org/xfce/tumbler/tree/plugins/jpeg-thumbnailer/jpeg-thumbnailer.c)  (line 537)
[http://permalink.gmane.org/gmane.comp.desktop.xfce.commits/12236](http://permalink.gmane.org/gmane.comp.desktop.xfce.commits/12236)

So its implemented but for some reason its broken? I can provide an image from my camera if needed, my thumbnails can be read by exiftool and by rox and and also by the python exif thingie that is used by jbrout and none of them reports any errors on my images.

---

### Post by LewisTM on 2012-09-11
I guess you can report at the Ubuntu bug tracker, referring to package tumbler.

Tumbler is faster than before and runs really quick on a USB stick, but I admit ROX is even faster. I guess that on a slow memory card, generating each thumbnail is not an option. 

In fact if tumbler could load the exif thumbnail, it might enable Thunar to preview files over remote connections such as SFTP. That, I would like!

Good luck!

---

### Post by dannyboy79 on 2012-12-25
i know this is off topic but how did you get xfce-4.10 within 12.04? I added the ppa but when I hit apt-get update && apt-get upgrade it says this:
```
The following packages have been kept back:
  exo-utils libexo-1-0 libgarcon-1-0 libthunarx-2-0 libxfce4ui-1-0
  libxfce4util-bin libxfcegui4-4 orage parole thunar thunar-data thunar-volman
  xfce4-appfinder xfce4-cpugraph-plugin xfce4-datetime-plugin xfce4-dict
  xfce4-indicator-plugin xfce4-mailwatch-plugin xfce4-netload-plugin
  xfce4-notes xfce4-notes-plugin xfce4-notifyd xfce4-panel xfce4-places-plugin
  xfce4-power-manager xfce4-power-manager-data xfce4-quicklauncher-plugin
  xfce4-screenshooter xfce4-session xfce4-settings xfce4-systemload-plugin
  xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfconf xfdesktop4
  xfdesktop4-data xfwm4 xubuntu-default-settings xubuntu-desktop

```
so it's holding them back for some reason, is it maybe because I have synaptic set to only show LTS releases? thanks for any suggestions.

---

### Post by LewisTM on 2012-12-25
Try apt-get dist-upgrade

---

### Post by dannyboy79 on 2012-12-25
> **LewisTM said:**
> Try apt-get dist-upgradethank you, that was it.

---

