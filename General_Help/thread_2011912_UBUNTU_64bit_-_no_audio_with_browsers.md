---
title: "UBUNTU 64bit - no audio with browsers"
date: 2012-06-28
forum: General Help
---

### Post by studiofreak on 2012-06-28
chrome or firefox are the same no audio when playing youtube and other vid sites, so i re installed flash, it fixed it for 10 minutes then the audio stopped working again!

also the vids start, then stop then start again after about 3 seconds.

anyone come across these problems and how do i fix them?

Thanks

---

### Post by jemadux on 2012-06-28
perhaps you will need help via irc on freenode server and #alsa channel;)

---

### Post by jmfal on 2012-06-28
Welcome to Ubuntu

The Ubuntu Restricted Extras should help with the sound problems

```
  sudo apt-get install ubuntu-restricted-extras       
```

If that doesn't work replace the hyphens with a space.

---

### Post by studiofreak on 2012-06-28
ok thanks jm fal.

ill try that first the extras

@jemadux ive been using linux/ubuntu in a few different distro forms for a while and usually can fix my own problems but this one has me stumped!

i have  professional studio and switching/switched everything over to ubuntu of which if i cant smooth things with ubuntu studio (with added different desk top on one namely unity as i actually like it low and behold!) then im going to have to do a fresh install on the main studio pc with kxstudio as its only OS and then this one office/2nd studio/live drum studio controller (with alesis usb pro and alesis trigger IO which i have working in ubuntu studio with live drums) then i am going to have to dual boot this 2nd machine with kxstudio which is just extra hassle i actually dont really need or want and i like ubuntu studio 64bit.

anyway long rant a bit ill see if it works if not ill try get on the alsa irc

thanks for your help both of you much appreciated

:guitar:

---

### Post by studiofreak on 2012-06-28
@ jfal

the command returns this:


ubuntu-restricted-extras is already the newest version.
The following packages were automatically installed and are no longer required:
  libboost-filesystem1.46.1 gambas2-gb-gtk gambas2-gb-gui
  libboost-system1.46.1 libboost-iostreams1.46.1 gambas2-runtime
  gambas2-gb-settings gambas2-gb-qt gambas2-gb-gtk-ext gambas2-gb-form
Use 'apt-get autoremove' to remove them.

-----------------------------------------------------

so i ran:

sudo apt-get autoremove


ill see if that does anything if not im on the irc chan this eve as its driving me up the wall and rather than giving in id rather learn how to fix it as giving in gets you now where!

p.s. ive already got a method of installing a generic KVM under ubuntu 11.10 and 12.04 that actually works with full res and even dual screens on the studio pc just using the kvm to switch the monitor connected to the 2nd pc so one of the monitors goes directly into the pc on the studio pc. if anyone needs help with that, its long winded but it works and is stable.

Thanks again

---

### Post by steeldriver on 2012-06-28
I have no idea if your problem is related (I really don't understand the audio hierarchy) but on my 64-bit Mythbuntu w/ AMD/ATI graphics I had to set a default pulseaudio output device via /etc/asound.conf (or ~/.asoundrc should do the same I think) to get HDMI audio out of flashplayer in either browser - see the following thread

[http://ubuntuforums.org/showpost.php?p=12016931&postcount=2](http://ubuntuforums.org/showpost.php?p=12016931&postcount=2)

---

### Post by studiofreak on 2012-06-28
its maybe something to do with ALSA and [http://blogs.adobe.com/flashplayer/2012/02/adobe-and-google-partnering-for-flash-player-on-linux.html](http://blogs.adobe.com/flashplayer/2012/02/adobe-and-google-partnering-for-flash-player-on-linux.html) this pepper thing that I would hazard a guess that adobe and google have right royally f*____ it up?

strange here is what doesn't work and one thing i found that does! its odd!

a) youtube, plays vid no sound

b) soundcloud, button presses, the grey area loads up to say the track has loaded and then

c)[http://jplayer.org/](http://jplayer.org/) jplayer plays the music of the demo contained on that page

WEIRD! very strange!!!!!!! So I am baffled

I shall try get on the IRC chan but I have never used it in my life so it may take me a while

thanks again

---

### Post by studiofreak on 2012-06-28
@ steeldriver

It is just the analogue output of the onboard intel boards audio i am using for the internet i also have an m-audio 10/10 delta lt (in both machines 1 each) but this one i need to get going first, ive used m audio delta in the past but with delta tdif and i had it working with linux going into a tascam tdm1000 16 chan digital desk with a tdif cable

but all i want is browser audio! lol you think being able to make all this work in my studio with linux i could get browser audio! haha but alas, no!

thanks for the suggestion though :guitar:

---

### Post by studiofreak on 2012-06-28
OK tried the ALSA IRC chan, no one replied and i had to restart the browser as I am currently banging my head against a virtual brick wall here trying to fix it!

I am a musician I use youtube to learn in general and for documentaries etc as well as other websites for audio someone tried to give me a link to soundcloud earlier and all i could do was save it and say id listen later on as trying to fix a problem!

that doesnt really look to good when your sent a link to audio from a DMC world champion and DMC team champion DJ does it really! lol

so i must fix! PLEASE help me?!

---

### Post by jmfal on 2012-06-28
If you are using fire fox click on tools and click on ADD-ONS  and enable the two players for totem (vlc and win media) .
I had problems with them disabling for some reason and finally they stayed enabled.

---

### Post by studiofreak on 2012-06-28
thanks jfal

The extras command i did that part and it was already upto date and installed

im hazarding a guess at this right now [http://blogs.adobe.com/flashplayer/2012/02/adobe-and-google-partnering-for-flash-player-on-linux.html](http://blogs.adobe.com/flashplayer/2012/02/adobe-and-google-partnering-for-flash-player-on-linux.html) being the culprit for some reason? Obviously im not to the bottom of this yet!

Also im using chrome mainly but i have firefox installed as well as standard, all up to date on both i made sure of that just now.

still no audio? when i right click on a video on youtube for the flash settings they freeze and i cant use them nor can i get them off the screen i have to reload the browser. ill try firefox and what you said to do, ill report back!


i will get to the bottom of this i really do not want to have to install kxstudio on a dual boot with ubuntu studio that would be absolutely ridiculous!

---

### Post by studiofreak on 2012-06-28
@jmfal

i did what you said in firefox, i disabled them, re started fire fox, re enabled them but still the same!

youtube vids start, then stop and re start with no audio!

its driving me crazy!

hope someone can help me the alsa irc chan is not responding at all to me i dont know why!?

---

### Post by jmfal on 2012-06-28
I forgot about this

firefox>> edit >> preferences >> applications >> click on "MPEG-4 video and select quick time plugin in firefox in the dropdown box.

right below is "MPEG video" select VLC PLUGIN from dropdown box

Then go back to the add-ons manager and enable them.

---

### Post by studiofreak on 2012-06-28
@jmfal

they were already set to that, i disabled them and then where your saying in edit>pref>applications etc they wont show up if disabled, so i re enable, checked again, same

---

### Post by studiofreak on 2012-06-28
@ steeldriver

i have no * /etc/asound.conf * in etc

? any ideas?

---

### Post by studiofreak on 2012-06-28
@ steeldriver

i realize my mistake now you have to create your own system wide one, like you say in your post but i was unclear until i read into it on alsa wiki help page

sudo aplay -l

*/ returns /*


**** List of PLAYBACK Hardware Devices ****
card 0: M1010LT [M Audio Delta 1010LT], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: VT1705 Analog [VT1705 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 2: VT1705 HP [VT1705 HP]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
-----------------------------------------------------------------

I am thinking im gna try this system wide setting first i can always delete and re boot if it doesnt work fingers crossed!

thanks

---

### Post by studiofreak on 2012-06-28
@ steeldriver !!!!!!!!!!

You are the man!!!!!!! after a reboot fixed!! round of applause to you sir!

That fixed it and now it should be good!


I thank you greatly and gratefully sir!

the studio freak :guitar:

---

### Post by steeldriver on 2012-06-28
glad it worked for you as well :) 

if you could mark the thread [SOLVED] that will keep the forum mods happy

---

### Post by studiofreak on 2012-06-28
thanks, sorry for not marking as solved i thought i had, doing many things and drinking much black coffee haha

thanks for the help guys!

cheers :popcorn:

---

