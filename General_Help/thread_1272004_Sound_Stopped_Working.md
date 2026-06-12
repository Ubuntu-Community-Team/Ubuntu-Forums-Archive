---
title: "Sound Stopped Working"
date: 2009-09-21
forum: General Help
---

### Post by Naitogunjin on 2009-09-21
Hello everybody,
My sound stopped working a second ago and i checked the volume control and the alsamixer and nothing is muted. When i first login the ubuntu login sound still works but as soon as im logged in nothing has sound. If anybodys got some tips let me know.
Word out.

---

### Post by Naitogunjin on 2009-09-21
Again the sound is not working on my ubuntu 9.04 laptop.

---

### Post by hamsandwich on 2009-09-21
you haven't given much information to go on...what kind of soundcard, etc. But do you have the pulseaudio utilities installed? That's the first place I go to debug.

```
sudo apt-get install padevchooser paman paprefs pavucontrol pavumeter
```

I use the pulseaudio device chooser play system sounds and debug that way. Also under the device chooser you can select "configure local sound server" and select "simultaneous output" to create output on all local sounds cards, if you happen to have more than one (such as on on motherboard, one on PCI card).

---

### Post by aerojad on 2009-09-21
same issue just happened to me.  I have 9.04 and a Creative Soundblaster Audigy 4 - which I've been using in Linux for years.  I downloaded the programs hamsandwich mentioned and I can see the indicator bars in pluseaudio's volume control that say there's sound being produced, my Audacious visualization shows sound, but nothing is coming out of my speakers or headphones.

Alrighty went through everything I could see and nothing is muted.  This all started, as far as I can tell, after my most recent security updates.

---

### Post by ngrieb on 2009-09-21
Same happens to me, but only when I try and change my start-up sound to a custom sound using the login util under System> Admin > Login Window, from what I have gathered, the system sounds on startup use a different sound driver from the norm cause they have not loaded yet. I would suggest turning off the system start-up sounds for now, but I would like an answer as to why I can't have both, or how to fix it. It seems like the login window sounds might compete with the System > Preferences > Sounds sometimes...could this be a problem? If anyone knows I would like to find a solution as well.

I am running an nForce 2 series integrated card, with the ALSA mixer under Ubuntu 8.10.  

Thanks.

---

### Post by Naitogunjin on 2009-09-22
Oh ok yea that is exactly what i did before the sound stopped working. I added a custom false login sound to the login menu and the sound stopped working. Ill try disabling it.
Yes an answer would be nice too.

---

### Post by ngrieb on 2009-09-22
Ya the odd thing is that it sometimes works, and sometimes goes back to default, or has no sound. It's not a consistent thing. You can change the login ready sound with no problem though.

---

### Post by Johndo1 on 2009-09-23
I had the same exact problem on 9.04 and when I disabled my cool start up sounds it fixed my sound issues. A minor price to pay for audio but its still irritating...:(

---

### Post by ngrieb on 2009-09-25
Ya, I don't want to have to pay that price, and little things like this need to be resolved. 

Compiz is the same way, why can't I just view Totem video's with it on? It's not that hard to turn off, but it requires you go into system and blah, blah, and turning it back on takes a while. I like at least being able to drag windows to other desktops without using the key commands, and wish it would just work.
 
Additional custom features should not be that hard to manage, and this is where mainstream Windows or Mac people get fed up and stop trying to use Linux (which sucks, cause Linux is great!). I'll look for a solution to these things and get back when I have the answer.

---

