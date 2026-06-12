---
title: "DvD Playback - libdvdcss already installed but not working"
date: 2006-06-11
forum: General Help
---

### Post by LordofHaha on 2006-06-11
Just because no one seems to see beyond DvD Playback, I will repeat **I have libdvdcss installed**!!!

- Tried installing (with no success) via: 
[https://wiki.ubuntu.com/RestrictedFormats#head-49d7b89e22f864732e033a68a77cfe144f23af8c](https://wiki.ubuntu.com/RestrictedFormats#head-49d7b89e22f864732e033a68a77cfe144f23af8c)
Automatix Script
[http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

But still not able to view dvds get the message in totem for example that says:
" An error occured:
The source seems encrypted, and canot be read. Are you trying to play an encrypted DVD without libdvdcss?"
* Note VLC does not seem to work either *

My current installed libs related to libdvd are:
libdvdcss2 (v1.2.9.1plf3)
libdvdnav4 (v0.1.9-3)
libdvdread3 (v0.9.4-5.1)

My current box setup is:
- AMD Sempron 64bit (Using Ubuntu 32bit, because was having too many issues with the 64 bit distro)
- ATI Radeon X300SE
- Intergrated Sound via: MSI Socket 754/ATI RS482/PCI-E/A&V&L Motherboard

*** Edit: was able to get mplayer to work, after trying the fake copy of /usr/lib to /usr/local/lib (sorry closed the thread of that one so can't show the exact thing i did), but without dvdmenus - other players still not working ***

---

### Post by plexi50 on 2006-06-11
Totem will not play DVD's unless you install gstreamer-xine from Synaptic (it will remove the current gstreamer, you cannot have both). VLC needs a little hand holding to get it going, be sure you type your device name in when you try to open the desk, usually /dev/cdrom.

---

### Post by Imexius on 2006-06-11
Have you installed w32codecs?

---

### Post by LordofHaha on 2006-06-11
yes have the w32codecs.

any recommendation on where to grab gstreamer? I didnt see it in the package manager.

---

### Post by yteh on 2006-06-11
[QUOTE=plexi50]Totem will not play DVD's unless you install gstreamer-xine from Synaptic (it will remove the current gstreamer, you cannot have both). VLC needs a little hand holding to get it going, be sure you type your device name in when you try to open the desk, usually /dev/cdrom.[/QUOTE]

I believe it should be totem-xine. In synaptic, search for totem-xine. That will remove totem-gstreamer. Then, try playing your dvd in Totem. Also, in the Help->About menu of Totem, you should see "...using xine-lib...".

Hope this helps.

---

### Post by phlexy on 2006-06-13
I'm using totem-xine instead of totem-gstreamer but I still get "The source seems encrypted, and canot be read. Are you trying to play an encrypted DVD without libdvdcss?"

Here's what terminal gives me: 
libdvdnav: Using dvdnav version 1.1.1 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Encrypted DVD support unavailable.
libdvdread: Attempting to use device /dev/hdc mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/ben/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4
libdvdnav: Using dvdnav version 1.1.1 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Encrypted DVD support unavailable.
libdvdread: Attempting to use device /dev/hdc mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/ben/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4

Does anyone know what I'm supposed to do to fix this? I followed [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) but still no luck. 

I'm new, be nice :D

---

### Post by LordofHaha on 2006-06-13
phlexy did you try and use a different media player? (thats what made it work for me in the end)

---

### Post by phlexy on 2006-06-13
@LordofHaha: yeah, several. MPlayer and Gxine Movie Player. Both crash when they get to the DVD menu (like Totem).

---

### Post by yteh on 2006-06-13
Looks like you don't have libdvdread3 installed. You can search for it in Synaptic. Install it.

Then run "sudo /usr/share/doc/libdvdread3/examples/install-css.sh".

Hope this helps.

---

### Post by disturbed1 on 2006-06-13
Purge the plf version of libdvdcss2.

Go here [http://www.debian-multimedia.org/](http://www.debian-multimedia.org/)

(or just add deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch main to your sources list)

Try Marillat's libdvdcss2, I have no issues using Totem with GStreamer, nor VLC for CSS encyrpted DVDs.

Or just use Ubuntu's built in script to install libdvdcss
sudo /usr/share/doc/libdvdread3/examples/./install-css.sh

Here's what's in my /usr/lib 
```

/usr/lib$ ls *dvd*
libdvdcss.so.2  libdvdcss.so.2.0.8  libdvdnav.so.4  libdvdnav.so.4.0.0  libdvdplay.so.0  libdvdplay.so.0.0.1  libdvdread.so.3  libdvdread.so.3.0.0


```

I've used both Marillat's libdvdcss, and compiled from source without any issues. Original source is available here [http://www.videolan.org/vlc/download-sources.html](http://www.videolan.org/vlc/download-sources.html)

---

### Post by p0ptart on 2006-06-13
I am having the same issue with my dvd playback regardless of player. My /usr/lib shows the same as yours. Is it because I am using the 64bit 6.06 install? can anyone suggest anything?

** update - I installed the xine ui and that works flawlessly. Not sure why nothing else will work but I guess as long as I can play my DVD's i'm happy. Everything else has been so easy with this install!! In retrospect I guess I would go with the 32bit version as   
it seems to be easier to deal with and I'm not sure i'm getting enough performance increase to justify the problems.

---

### Post by phlexy on 2006-06-13
@yteh: Cheers, it worked :D

---

### Post by yteh on 2006-06-13
Sweet!

---

### Post by LordofHaha on 2006-06-15
p0ptart... I personally had to switch to 32bit to get things working :o( If your not too committed to 64, i'd back to 32 while we wait for some better drivers to be created for the 64bit version... (I tried doing the compile it myself thing and didnt work...)

---

### Post by ekravche on 2007-07-28
I'm going to try this seems a bit strange because this error is occuring in the middle of a movie for me so I'm beginning to suspect that the disk is damaged or something

---

### Post by rbmorse on 2007-07-28
> **p0ptart said:**
>  In retrospect I guess I would go with the 32bit version as   
it seems to be easier to deal with and I'm not sure i'm getting enough performance increase to justify the problems.

I'm surprised that you are seeing any performance increase at all.

---

### Post by Flaphal on 2008-07-04
> **yteh said:**
> Looks like you don't have libdvdread3 installed. You can search for it in Synaptic. Install it.

Then run "sudo /usr/share/doc/libdvdread3/examples/install-css.sh".

Hope this helps.
yteh, when I try to run "sudo /usr/share/doc/libdvdread3/examples/install-css.sh" it can't find it. I browsed to the folder and I don't have "/examples/" but install-css.sh was right there in "/libdvdread3/".

I ran it, but still no luck. Otherwise I have the exact same issue as LordofHaha.

Any suggestions? 

(..hoping posting in such an old thread isn't futile :) )

---

### Post by jackcy on 2008-07-12
I am having the same issue on kubuntu 8.04 hardy. I installed libdvdcss2 these ways:
[LIST]
[*]sudo /usr/share/doc/libdvdread3/install-css.sh
[*]sudo /usr/share/doc/kaffeine/install-css.sh
[*]with aptitude out of medibuntu repositories
[/LIST]

sudo aptitude search libdvdcss2 informsme that it is installed.
BUT: libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_1.VOB (0x0032d440)!!

I have this error with all players: xine, kaffeine, totem, vlc, ...

I don't think it could be a hardware problem, must be something with the libdvdcss2 package.

---

### Post by jackcy on 2008-07-12
OK, I got it. The region code was not set correctly on my dell xps 1330.

I downloaded regionset with

sudo aptitude install regionset

and changed the region code of my dvd drive:

regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:                                
RPC Phase: II                                                
type: SET                                                    
vendor resets available: 4                                   
user controlled changes resets available: 5                  
drive plays discs from region(s):, mask=0xFF             

Would you like to change the region setting of your drive? [y/n]:y
Enter the new region number for your drive [1..8]:2               
New mask: 0xFFFFFFFD, correct? [y/n]:y                            
Region code set successfully!        

As you can see there war NO region set. So I need the region for europe --> 2                            

After setting the code, the disc could be played back without any problem.
 Here is a list of availabe region codes:
1 North America (USA and Canada)
2 Europe, Middle East, South Africa and Japan
3 Southeast Asia, Taiwan, Korea
4 Latin America, Australia, New Zealand
5 Former Soviet Union (Russia, Ukraine, etc.), rest of Africa, India
6 China 


Hope this helps.

---

