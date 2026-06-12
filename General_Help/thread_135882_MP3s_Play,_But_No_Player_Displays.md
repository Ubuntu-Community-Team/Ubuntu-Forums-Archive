---
title: "MP3s Play, But No Player Displays"
date: 2006-02-24
forum: General Help
---

### Post by Mark76 on 2006-02-24
I just get a black screen.  Which is odd.

---

### Post by Trab on 2006-02-24
umm...
alot more information would be helpful...
how are u opening the mp3...
is it just one mp3 or everyone of them...
this sounds like mplayer (Which runs in a terminal unless differently configured), and if it is so, you can try running totem to play ur mp3...
open a terminal...type ```
 totem 
``` and then open the mp3 in that... if that works i can help u set it up to be automatic...
take a screen shot if u need to.

---

### Post by Mark76 on 2006-02-24
Basically I just clicked on the link and it played a few seconds after starting to download.

And, no it's not streaming audio.

---

### Post by Mark76 on 2006-02-24
Hey.  What does this mean?

> (totem:12959): Gnome-WARNING **: Accessibility: failed to find module 'libgail-gnome' which is needed to make this application accessible
GTK Accessibility Module initialized

(totem:12959): Gnome-WARNING **: Accessibility: failed to find module 'libatk-bridge' which is needed to make this application accessible

(totem:12959): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(totem:12959): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed




:?

---

### Post by Trab on 2006-02-24
huh.... does totem open? or does it just show that then close...
if it closes, in a terminal type 
```

sudo apt-get install totem-xine 
```
and then try...

---

### Post by Mark76 on 2006-02-26
Is mozplugger the right app for .wmv and .mov files?

Only, that's what my browser is ddefaulting to.

---

### Post by huckem on 2006-02-26
You may want to try using XMMS for your MP3's...  You can get it by running 

sudo apt-get install xmms

It is a great GUI and very customizable.

---

### Post by Mark76 on 2006-02-26
I already have XMMS installed.  What path should I use (usr/lib/xmms/?)?

---

### Post by huckem on 2006-02-26
that path should work, although I find the GUI method much easier.  Just right-click on any .mp3 file, click properties, and then change the 'opens with' option to XMMS.  You may also need to install the XMMS-MP3 pkg to get them to play, I dont remember if XMMS comes with native mp3 support in ubuntu.  It's been a while since I installed it.

---

### Post by Mark76 on 2006-02-27
Well, it appears that xmms has some effect, since I can adjust the volume, tone and balance using that.   But stop/play/pause/ff/rw don't work :?

---

### Post by Mark76 on 2006-03-01
Here's a screenshot to show you what happens.  The MP3 was playing during this, but I had no control over anything other than volume and balance

---

### Post by Mark76 on 2006-03-02
Anyone?

Surely that's just a little weird? :-?

---

### Post by akiro.yamamoto on 2006-03-02
What plugin is associated with mp3 playback for you.
I'm using mplayer and the mplayer plugin (Firefox 1.0.7)
Do a about:plugins and ckeck what you have selected for .mp3 playback.

---

### Post by akiro.yamamoto on 2006-03-02
Damn smiley :p
what I meant is type 
about : plugins (without the space) in the address bar of your browser. ;)

---

### Post by Mark76 on 2006-03-02
I'm using Opera 8.51 and according to my advanced preferences MP3s are using the mozplugger 1.7.1 (path = usr/lib/mozplugins/mozplugger.so). For streaming MP3s and downloads.

---

### Post by Mark76 on 2006-03-02
MozPlugger 1.7.1	
audio/wav	wav	
audio/x-wav	wav	
video/x-msvideo	avi	
video/mpeg	mpeg,mpg,mpe,m2v,m1v,mpa	
audio/basic	au	
video/quicktime	qt,mov	
video/x-ms-asf	asf,asx	
application/smil	smi,smil	
audio/vnd.rn-realaudio	ra	
audio/x-realaudio	ra	
application/vnd.rn-realmedia	rm	
application/pdf	pdf	
audio/x-pn-realaudio	rmm,ram	
audio/x-pn-realaudio-plugin	rpm	
audio/mpeg	mp3,mp2,mpga	
video/x-mpeg	mpeg, mpg, mpe	
video/x-mpeg2	mpv2, mp2ve	
video/mp4	mp4	
video/msvideo	avi	
video/fli	fli, flc	
video/x-fli	fli, flc	
application/x-mplayer2	wmv,asf,mov	
video/x-ms-wmv	wmv	
application/x-quicktimeplayer	mov	
image/x-macpaint	pntg,mov	
video/x-quicktime	mov,qt	
video/x-theora	ogg	
video/theora	ogg	
video/ogg	ogg	
video/x-ogg	ogm,ogv	
audio/mp3	mp3	
audio/x-mp3	mp3	
audio/mpeg2	mp2	
audio/x-mpeg2	mp2	
audio/mpeg3	mp3	
audio/x-mpeg3	mp3	
audio/x-mpeg	mpa,abs,mpega	
audio/x-ogg	ogg	
application/x-ogg	ogg	
application/ogg	ogg	
audio/x-basic	au,snd	
audio/x-pn-wav	wav	
audio/x-pn-windows-acm	wav	
audio/vnd.rn-realvideo	rv	
audio/x-ms-wax	wax,wma	
application/x-pdf	pdf	
text/pdf	pdf	
text/x-pdf	pdf

And for almost everything else :o

---

### Post by akiro.yamamoto on 2006-03-02
Now I use the mplayer-ui plugin for embedded multimedia 
playback in firefox 1.0.7, because I remember getting some erratic errors
with mozplugger.
However at one point I had opera and that plugin worked just fine
with no upsets that I can remember.
So if you want you can try:
wget [http://www.ahacic.5gigs.com/ubuntu/mplayerplug-in_3.11-1_i386.deb](http://www.ahacic.5gigs.com/ubuntu/mplayerplug-in_3.11-1_i386.deb)
sudo dpkg -i mplayerplug-in_3.11-1_i386.deb
You should get controls with that.
Pause - Previous - Next etc.
Hope this helps.

---

### Post by Mark76 on 2006-03-02
Erm.

> mark-williams@098786weq:~$ wget [http://www.ahacic.5gigs.com/ubuntu/m....11-1_i386.deb](http://www.ahacic.5gigs.com/ubuntu/m....11-1_i386.deb)
--13:27:55--  [http://www.ahacic.5gigs.com/ubuntu/m....11-1_i386.deb](http://www.ahacic.5gigs.com/ubuntu/m....11-1_i386.deb)
           => `m....11-1_i386.deb'
Resolving [www.ahacic.5gigs.com](www.ahacic.5gigs.com)... 64.40.114.20
Connecting to www.ahacic.5gigs.com|64.40.114.20|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
13:27:56 ERROR 404: Not Found.

mark-williams@098786weq:~$ udo dpkg -i mplayerplug-in_3.11-1_i386.deb
bash: udo: command not found

mark-williams@098786weq:~$ wget [http://www.ahacic.5gigs.com/ubuntu/m....11-1_i386.deb](http://www.ahacic.5gigs.com/ubuntu/m....11-1_i386.deb)
--13:29:55--  [http://www.ahacic.5gigs.com/ubuntu/m....11-1_i386.deb](http://www.ahacic.5gigs.com/ubuntu/m....11-1_i386.deb)
           => `m....11-1_i386.deb'
Resolving [www.ahacic.5gigs.com](www.ahacic.5gigs.com)... 64.40.114.20
Connecting to www.ahacic.5gigs.com|64.40.114.20|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
13:29:56 ERROR 404: Not Found.

mark-williams@098786weq:~$ sudo dpkg -i mplayerplug-in_3.11-1_i386.deb


---

### Post by Mark76 on 2006-03-03
Bump.

---

### Post by akiro.yamamoto on 2006-03-03
Here this is my own link.
[http://www.savefile.com/files/9971611](http://www.savefile.com/files/9971611)
download the file, then 
sudo dpkg -i mplayerplug-in_3.11-1_i386.deb
That will install the plugin.
Hope this helps.

---

### Post by Mark76 on 2006-03-03
mark-williams@098786weq:~$ sudo dpkg -i mplayerplug-in_3.11-1_i386.deb
Password:
dpkg: error processing mplayerplug-in_3.11-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 mplayerplug-in_3.11-1_i386.deb
mark-williams@098786weq:~

---

### Post by akiro.yamamoto on 2006-03-03
Uninstall mozplugger 1.71
and install
mozilla-mplayer from the repos.
It's supposed to be version 3.17

Check my attatched image:

---

