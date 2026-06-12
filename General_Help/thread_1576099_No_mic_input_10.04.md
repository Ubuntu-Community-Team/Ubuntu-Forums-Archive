---
title: "No mic input 10.04"
date: 2010-09-16
forum: General Help
---

### Post by creatox on 2010-09-16
I've googled the crap out of this, and searched the forum for similar post, found a lot of things to try, but couldnt find a resolution.. so here we go

Im running 10.04 on a machine i built.  
mobo: MSI 785GM-P45
audio chipset: VIA VT1708S

I'm getting audio output just fine but nothing i do will get the input lvl in sound preferences to o. (mic is not muted)

ive tested the mic on my laptop (also running 10.04). it works fine there..
ive tried changing the setting with gnome-alsa and PulseAudio >> no dice.

tried this too:
step 1. Launch terminal and type " gksudo gedit /etc/modprobe.d/alsa-base.conf "

step 2. Add "options snd-hda-intel position_fix=1"

still no dice.  

any advice or suggestions would be greatly appreciated.

---

### Post by MooPi on 2010-09-16
in terminal ```
alsamixer
```
Now on keyboard select F4, this will show capture devices. Select your mic with the arrow keys. Select F6 to set driver. Select proper driver and set desired volume with the up and down arrows. Press ESC and test if your mic functions.

---

### Post by creatox on 2010-09-16
Thanks for the reply MooPi, 
unfortunately, no dice.  Still no input lvl

F6 on mine isnt driver, it specifies sound card.  I'm using alsamixer 1.0.22.  is that what you got?

---

### Post by MooPi on 2010-09-16
I'm sorry mine is the same I listed wrong name. What are your choices when you select F6 ?

---

### Post by Vigh on 2010-09-16
you could try upgrading to the latest version of alsa, fixed my microphone problems and I didn't change any *.conf files.

---

### Post by creatox on 2010-09-16
> **MooPi said:**
> I'm sorry mine is the same I listed wrong name. What are your choices when you select F6 ?
-default
0 HDA ATI SB
1 HDA ATI HDMI

---

### Post by MooPi on 2010-09-16
> **creatox said:**
> -default
0 HDA ATI SB
1 HDA ATI HDMI
I would test each but my money is on 0 HDA ATI SB

---

### Post by creatox on 2010-09-16
Yeah, thats what I'm using.  I've got onboard hdmi, but thats only half duplex.

? about alsa, all i've got installed is the mixer, do I need the alsa-driver package as well?

---

### Post by MooPi on 2010-09-16
It is already installed if you have the mixer.Going for dinner be back shortly
Try this command in terminal ```
dpkg --get-selections>installed
```
This will dump a text in your home folder listing all install applications. Open text and Ctrl + f to seach for alsa.

---

### Post by creatox on 2010-09-16
> **MooPi said:**
> It is already installed if you have the mixer.Going for dinner be back shortly
Try this command in terminal ```
dpkg --get-selections>installed
```
This will dump a text in your home folder listing all install applications. Open text and Ctrl + f to seach for alsa.
alsa-base					install
alsa-utils					install
bluez-alsa					install
gnome-alsamixer					install
gstreamer0.10-alsa				install


hmmm... no driver? 
just downloaded it, attempting install

---

### Post by MooPi on 2010-09-16
I believe you have everything you need without a new driver.
Open up alsamixer again and make certain nothing is muted. It will be marked with two MM.

---

### Post by creatox on 2010-09-16
WOOT!!
did all this, problem solved
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/comment-page-4/#comment-862](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/comment-page-4/#comment-862)

thanks for all the help yall!!!

---

### Post by OldGaf on 2010-09-19
> **creatox said:**
> WOOT!!
did all this, problem solved
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/comment-page-4/#comment-862](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/comment-page-4/#comment-862)

thanks for all the help yall!!!

link does not work......

---

### Post by creatox on 2010-09-19
hmm.. looks like the server is down.  
In my haste i posted a direct link to a comment i made on the page, here is the proper link for when the site comes back online
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

and the google cache: 
[http://webcache.googleusercontent.com/search?q=cache:Ngzse4LNkSEJ:monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/+upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04&cd=1&hl=en&ct=clnk&gl=us](http://webcache.googleusercontent.com/search?q=cache:Ngzse4LNkSEJ:monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/+upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04&cd=1&hl=en&ct=clnk&gl=us)


and, for some reason the only version i could get working is the text-only-google-cache, so here it is too:
[http://webcache.googleusercontent.com/search?q=cache:Ngzse4LNkSEJ:monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/+upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04&hl=en&gl=us&strip=1](http://webcache.googleusercontent.com/search?q=cache:Ngzse4LNkSEJ:monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/+upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04&hl=en&gl=us&strip=1)

---

### Post by Finn bjerke on 2010-11-26
Try this
 
[http://isallmaroon.wordpress.com/2010/05/08/no-microphone-input-in-skype-ubuntu-10-04/](http://isallmaroon.wordpress.com/2010/05/08/no-microphone-input-in-skype-ubuntu-10-04/)
 
worked 4 me..

---

### Post by Smallwheels on 2010-11-27
> **Finn bjerke said:**
> Try this
 
[http://isallmaroon.wordpress.com/2010/05/08/no-microphone-input-in-skype-ubuntu-10-04/](http://isallmaroon.wordpress.com/2010/05/08/no-microphone-input-in-skype-ubuntu-10-04/)
 
worked 4 me..


This worked for me too. I didn't know that pavucontrol was a bunched up word meaning Pulse Audio Volume Control. Once I learned that by doing an on-line search, I went to the software center and downloaded the Pules Audio Volume Control. 

I did have a problem with it. It didn't work on Microphone One. I switched to Microphone Two and it did work for me after I turned off the Skype automatic volume control in the Skype Options menu. 

I'm very pleased to say that I've solved two Ubuntu 10.04 problems in one day: getting my headset microphone to work and getting DVDs to play. Just a few more bugs to work out and I'll have a fully functioning free Operating System. :)

---

