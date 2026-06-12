---
title: "Working Joystick/Gamepad to MIDI solution in Ubuntu Linux -"
date: 2010-08-30
forum: General Help
---

### Post by indstr on 2010-08-30
This thread isn't really a question, but just information to people who may do future websearches and have the same problem that I did. 
 
The problem was: I needed a streamlined way to convert joystick/gamepad messages from more than 1 joystick into to MIDI data, and have it save the configuration and load it automatically every time I start the program, so there is no "extra steps and loading of presets" and it's just ready to play. (The purpose of this is a homemade drum kit which uses parts from several different game controllers). There aren't a lot of native Linux solutions that can do this. Aseqjoy is one of the few and I did not have very much luck with it. I turned to Windows programs via Wine (there are many), but most of them I could not get to work. 
 
I tried: Rejoice, Vmidijoy, midijoys, glovepie, rb2midi, and several others, the names of which I do not remember. I also tried using Reaper's built-in joystick to MIDI support. Had various issues with all. I got the closest with Rejoice, but when it came down to it, the MIDI messages were not actually transmitting. 
 
I found EdrumMonitor, which technically worked, but it was a complete pain because I had to load 2 instances of it, make sure I had the correct controller selected, and then load the config file. Another program called "MIDItar hero" also worked but it required loading Max/DSP, a bunch of extra steps.
 
I did more research and found a program called Mijoy pro vst that looked like it would do the trick, unfortunately it costs about $35 and the demo is crippled (random dropouts)... 
 
After several hours of digging last night, I found an unexpected surprise.. This very obscure program called "ShoRyuKen2" - It's so obscure that the website is not even up anymore. (Here is the original website's link - [http://perso.wanadoo.fr/silicon_silicium/](http://perso.wanadoo.fr/silicon_silicium/) ).. However, I was lucky enough that not only did it come up in the Internet Archive's "Wayback Machine", but also the download link to the program was small enough that they had also archived the program!
 
Here is a link to the archived page with download working as of August 30, 2010:
[http://web.archive.org/web/20060514075041/http://perso.wanadoo.fr/silicon_silicium/](http://web.archive.org/web/20060514075041/http://perso.wanadoo.fr/silicon_silicium/) 
 
I will also host the file on my own webspace, just in case the Internet Archive link goes down for some reason - [http://www.loopproject.com/filebase/sdcompo/organic_io/shoryuken2.rar](http://www.loopproject.com/filebase/sdcompo/organic_io/shoryuken2.rar)
(I couldn't get it to attach to this post) 
 
So what I have done with ShoRyuKen2, is load 2 instances of it up in Reaper, which I was already running for some acoustic drum triggers. The solution is perfect because now all I have to do is run Reaper and all my audio to MIDI and gamepad to MIDI are all loaded at the same time. But it would probably work more like a standalone in vsthost/DSSI-vst or fst. 
 
I posted this because there have been many times that a websearch for a problem I have been having has led me to an ubuntuforums post, which has solved my problem. So hopefully someone in the future will get some use out of this.. Or at least it may help to preserve this obscure but well implemented and useful program.
 
Edit: One last thing, shoryuken2 as a vst inside of Reaper in Wine runs faster (less audio delay) than Edrum Monitor did in Wine. I am use JACK with low latency (less than 5ms), and also the WineASIO driver... But Edrum Monitor had slightly noticable latency, while Reaper has none whatsoever, with my audio to midi triggers, or the joystick to midi. This is with Ubuntu Studio 9.10 with a custom kernel compiled specifically for low latency audio.

---

### Post by indstr on 2010-12-04
An update a couple of months on:

I have found a program that is MUCH better than Shoryuken2, it is called "joystickctrl" by a fellow named [COLOR=#000000][FONT=Arial, Helvetica, sans-serif][SIZE=2]Daniel            Palomo Vinuesa. 

It is also a vst plugin, but it works a lot better, has a lot more features, and less quirks. 

Again, it is obscure and the original website is also down. But, the Internet archive has saved the day again:

Link:
[/SIZE][/FONT][/COLOR][http://web.archive.org/web/20080803195142/http://vinuesa.club.fr/projet-flou/english/joystickctrl.htm](http://web.archive.org/web/20080803195142/http://vinuesa.club.fr/projet-flou/english/joystickctrl.htm)

Advantages over shoryuken2:

* Ability to assign MIDI channels per trigger instead of only for the whole gamepad
* Ability to send "clean" MIDI CC signals (Yes! I now finally have a working hi-hat pedal)  (I had some problem with Shoryuken2 sending random unwanted MIDI CC data to Addictive Drums, so it was screwing with my hihat configuration)
* Ability to configure velocity information
* MUCH easier to see which button you are configuring, since there is a little light that lights up when you hit the button. Versus Shoryuken2's annoying trial-and-error method
* "Joystick number" is always consistent (I had problems in Shoryuken2 with the button configuration changing unpredictably even when my joysticks were assigned to the same joystick number. I really couldn't figure out but joystickctrl does not do this)
* Ability to assign the "refresh rate" of the program. Conceivably to save CPU
* It's faster... The triggering seems faster than Shoryuken

Only 1 downside is it uses slightly more CPU/RAM per instance, but it's definitely worth the benefits.

Good luck to anyone in the future who may need this info.

---

### Post by m3x1c0 on 2011-03-21
Hi im trying to do what you did but havent been able to download the joystickctl software where can I get it? and would i be able to use it to control a midi program native to linux?

---

### Post by SteSullivan on 2013-01-17
Linux has a much better internal MIDI system than other operating systems - use kaConnect or a similar utility to "wire up" your internal MIDI network and it should work just fine.

You can download the application at the link posted earlier ([http://web.archive.org/web/20080803195142/http://vinuesa.club.fr/projet-flou/english/joystickctrl.htm](http://web.archive.org/web/20080803195142/http://vinuesa.club.fr/projet-flou/english/joystickctrl.htm)) - there is a download link at the top.

---

