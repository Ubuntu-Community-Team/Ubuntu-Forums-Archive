---
title: "=awsome!"
date: 2010-03-29
forum: General Help
---

### Post by n1co on 2010-03-29
Hey every1! Im completely new to linux! its been only my 3rd day..and im sooooooo excited n happy discovering this world!!!

Everything seems Awsome so far.. I ve been playing with compiz alot! messing with open office..gimp..pidgin and alot other kool stuff..while studying this forum, sourceforge, alsa etc..!!! everything works fine and in a brand new way some how..
The only problems i have are.. 

1) microphone wont record or function anyway! i checked alsa project and figured that i m unfortunate to have a sound card that only  output is supported... :S (sound blaster audigy se) and anyway i say unfortunate cause i m a regular skype user.. 
Is there any other way around this problem? my search didn find anything...so im hoping for some genious advice!?!?!

and 2) i m trying to install some new updates and it is taking ALOT of time to finish..it runs non stop for 12 hours..and hasn finished yet!!!! is that even possible..???? 
right now it says...               found linux image /boot/vmlinuz-2.6.31-21-generic-pae 
and the same thing goes in every line...if u know what i mean?!?!

Any ideas would be greatly appreciated!!! and make me alot happier of course!!!!! :D:D:D:D:P

---

### Post by lotharmat on 2010-03-29
I'm not too sure the world could cope with you a whole lot happier! ;):D

Welcome to the forums btw!

---

### Post by n1co on 2010-03-29
> **lotharmat said:**
> I'm not too sure the world could cope with you a whole lot happier! ;):D

Welcome to the forums btw!

Yeaaah! im over enthusiastic smtms.. I know.. anyway! thanks for your welcome!!!

---

### Post by doas777 on 2010-03-29
> **n1co said:**
> 
and 2) i m trying to install some new updates and it is taking ALOT of time to finish..it runs non stop for 12 hours..and hasn finished yet!!!! is that even possible..???? 
right now it says...               found linux image /boot/vmlinuz-2.6.31-21-generic-pae 
and the same thing goes in every line...if u know what i mean?!?!

Any ideas would be greatly appreciated!!! and make me alot happier of course!!!!! :D:D:D:D:P

Welcome!

could you give us a screenshot? it would probably help in diagnosing your issue

---

### Post by n1co on 2010-03-29
> **doas777 said:**
> Welcome!

could you give us a screenshot? it would probably help in diagnosing your issue


Thank you!!! nice to be here!!!!

Here's a screenshot! :S
as i said be4 it goes like this for hours..and i can see it hasnt stuck or anything...it just says the same thing on evey line..

---

### Post by realzippy on 2010-03-29
&#922;&#945;&#955;&#969;&#963;&#972;&#961;&#953;&#963;&#949;&#962; !

You misedited your screenshot..if it was an *apt-get update* hanging,
I would kill it; ctrl + c


...to your mic prob:
Do you have an onboard soundchip?
It should be possible to run both (onboard+audigy) and use the onboard mic input...

---

### Post by n1co on 2010-03-29
> **realzippy said:**
> &#922;&#945;&#955;&#969;&#963;&#972;&#961;&#953;&#963;&#949;&#962; !

You misedited your screenshot..if it was an *apt-get update* hanging,
I would kill it; ctrl + c


...to your mic prob:
Do you have an onboard soundchip?
It should be possible to run both (onboard+audigy) and use the onboard mic input...


&#922;&#945;&#955;&#974;&#962; &#963;&#945;&#962; &#946;&#961;&#942;&#954;&#945;!! &#904;&#955;&#955;&#951;&#957;&#945;&#962; &#942; google translation??? :D:D:D

I just edited it once so that it would be more clear..it should be ok now...?
i quess i could kill the update but...should I???

about sound prob....i tried that..but didn work either cause my mb's sound chipset (C-Media CMI9738) isnt supported by alsa either..it isnt even listed... :S
Either i m the unluckiest ******* around..or i have a terrible voice..u name it :p:p:p

---

### Post by zuerston on 2010-03-29
> **n1co said:**
> &#922;&#945;&#955;&#974;&#962; &#963;&#945;&#962; &#946;&#961;&#942;&#954;&#945;!! &#904;&#955;&#955;&#951;&#957;&#945;&#962; &#942; google translation??? :D:D:D

I just edited it once so that it would be more clear..it should be ok now...?
i quess i could kill the update but...should I???

about sound prob....i tried that..but didn work either cause my mb's sound chipset (C-Media CMI9738) isnt supported by alsa either..it isnt even listed... :S
Either i m the unluckiest ******* around..or i have a terrible voice..u name it :p:p:p

You must kill it, if it's hanging, no matter how much it hurts! :P

---

### Post by realzippy on 2010-03-29
&#922;&#945;&#955;&#974;&#962; &#963;&#945;&#962; &#946;&#961;&#942;&#954;&#945;!! &#904;&#955;&#955;&#951;&#957;&#945;&#962; &#942; google translation???

No,babel,do not have hellenic keyboard.
(but used to be few month in athens long time ago,some phrases remain..)

Sorry for your mic (also kicked my soundblaster after migrated to linux);
get yourself a cheap noname card what runs according to ubuntu hardware data base...

[https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards](https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards)

...maybe you have seen this :

[http://ubuntuforums.org/showthread.php?t=634290&highlight=microphone+test](http://ubuntuforums.org/showthread.php?t=634290&highlight=microphone+test)

1) Right click the speaker on panel, choose "Open Volume Control"
2) Click "Options" tab. If you don't see the options tab, edit preferences and enable "Digital input source", this will make it appear.
3) Change the "Digital Input Source" to "Digital Mic 1" from "Analog Inputs".

To set the mic volume, edit the preferences and enable "digital". A "Recording" tab appears. Move the slider up for the Digital setting. Use the sound recorder to test your sound levels.

---

### Post by gychang on 2010-03-29
Indeed, in contrast to the initial post, I have been at trying sevreal distros, and I finally found ubuntu is the only one that properly support tsclient (to connect to my XP office machine) easily.

Thanks for a great distro...

gychang

---

### Post by zuerston on 2010-03-29
> **gychang said:**
> Indeed, in contrast to the initial post, I have been at trying sevreal distros, and I finally found ubuntu is the only one that properly support tsclient (to connect to my XP office machine) easily.

Thanks for a great distro...

gychang

[IMG]http://zuerst1.com/email-stuff/ubuntu.jpg[/IMG][IMG]http://zuerst1.com/email-stuff/thumbup.gif[/IMG]** _It's the best ! _**

---

### Post by n1co on 2010-03-29
> **zuerston said:**
> You must kill it, if it's hanging, no matter how much it hurts! :P

LOL!!! alright..I did!:D:D:D

---

### Post by n1co on 2010-03-29
> **realzippy said:**
> &#922;&#945;&#955;&#974;&#962; &#963;&#945;&#962; &#946;&#961;&#942;&#954;&#945;!! &#904;&#955;&#955;&#951;&#957;&#945;&#962; &#942; google translation???

No,babel,do not have hellenic keyboard.
(but used to be few month in athens long time ago,some phrases remain..)

Sorry for your mic (also kicked my soundblaster after migrated to linux);
get yourself a cheap noname card what runs according to ubuntu hardware data base...

[https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards](https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards)

...maybe you have seen this :

[http://ubuntuforums.org/showthread.php?t=634290&highlight=microphone+test](http://ubuntuforums.org/showthread.php?t=634290&highlight=microphone+test)

1) Right click the speaker on panel, choose "Open Volume Control"
2) Click "Options" tab. If you don't see the options tab, edit preferences and enable "Digital input source", this will make it appear.
3) Change the "Digital Input Source" to "Digital Mic 1" from "Analog Inputs".

To set the mic volume, edit the preferences and enable "digital". A "Recording" tab appears. Move the slider up for the Digital setting. Use the sound recorder to test your sound levels.


I just tried that again.. :( but nothing seems to work when i got digital...not even sound!...i quess im gonna have to wait for alsa guys to do their magic...or purchase some old compatible card like u suggest...!!! Thank you alot for you suggestions realzippy!! appreciate!!!!!

---

