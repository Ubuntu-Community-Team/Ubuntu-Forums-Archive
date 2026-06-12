---
title: "No Sound from Logitech USB Audio Speakers"
date: 2009-09-07
forum: General Help
---

### Post by SlimBiggins on 2009-09-07
I just changed over from XP to Ubuntu about two weeks ago. Needless to say, I know little to nothing about Linux. I know my speakers are not broken for a few reasons. In System > Preferences > Sound I can get a test sound to work when (and only when) I have the sound playback for Sound Events and Music and Movies set to: USB AUDIO USB Audio (OSS). In VLC Media Player, I was able to get sound by changing the General Audio Settings. Under Output Type I have UNIX OSS audio output selected and under Output Device I have /dev/dsp1. The default was /dev/dsp, but after doing some reading in the forums I was able to solve that problem. So, basically I get no sound from the OS when it starts or shutsdown, and no audio period unless I'm playing through VLC. I get not audio from web pages that use Flash (and I have the plug-ins installed). I've been trying to get full system audio for two weeks now and its getting frustrating, so this is my first thread. I've read tons of other threads, but was unable to get any results, no matter when I did. PLEASE HELP.   Sincerely,  The New Guy

---

### Post by drnoelkelly on 2009-09-08
Hi 

I had this exact same problem with Logitech USB speakers on an Acer Revo ION.  It seems to stem from effectively having multiple sound cards once you plug in the USB speakers.  I scratched my head for quite a while and fiddled with various things but then decided to disable the onboard sound card in the BIOS.

This left the default (and only) sound card as the Logitech USB one.  Now everything works great including Skype.  Fortunately my wife's webcam has a mic built in so we don't need the mic input from the onboard card.

HTH
Cheers

---

### Post by erikthedrink on 2009-09-08
I've got logitech usb speakers too.  In Xubuntu, go to Applications, then Accessories, then Terminal.  In Terminal, type

[FONT=Georgia][SIZE=4]asoundconf set-default-card 1[/SIZE][/FONT]

Then close and re-open your browser (Mozilla Firefox) or restart your system.
:popcorn:
Note, if you unplug your usb speakers, your laptop speakers will take over.  In order to re-establish contact with the usb speakers, you will need to (plug them back in) restart the system.

---

### Post by SlimBiggins on 2009-09-09
drnoelkelly & ericthedrink: This is my first reply to my first thread in the Ubuntu Forum. I haven't even tried to config anything from a reply thread yet, (except reading others'), and I would like to say the following: NEVER IN MY LIFE have I ever got such a speedy response to a critical problem. I'm going to do what you guys said to do then write my real reply. This reply is simply to express how GREATFUL I am to being part of a community where people are willing to help others. I mean this with full sincerity. I don't want to waist alot of the forum's space, but I would like to say a B-I-G T-H-A-N-X. Whether, it works or not, I'm still amazed how friendly of a forum this is.  -SlimBiggins

---

### Post by SlimBiggins on 2009-09-09
erikthedrink: I have tried the asoundconf approach before and had no luck. Still thanks for the response.

drnoelkelly: The BIOS approach worked PERFECT! Thank you so much. I've been going nuts trying to find a solution. One of my ideas was to see if I could stop ubuntu from recognizing the sound card. I just didn't know how to go about it. As soon as I rebooted ( after I turned the sound off in my BIOS) I finally got to hear the ubuntu startup sound. I tested my multimedia files everything sounds great. I didn't even have to configure VLC like I had before. I installed Adobe Flash, went to YouTube to check it out and everything seems to work fine. Thanks again. I think I'm going to be Linux4Life now.

ANYONE ELSE WHO HAS THIS PROBLEM: Disabling the sound in BIOS is the way to go!

---

