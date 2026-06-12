---
title: "Managing audio I/O"
date: 2011-08-06
forum: General Help
---

### Post by Choco_Bob on 2011-08-06
Greetings.

Maybe this should be in absolute beginner talk, but ah well... :P

Namely, I have only recently started using Ubuntu (3 days ago, mainly for audio engineering experimenting), and this is the 1st major milestone I ran into, and it involves my external sound card (a Line 6 TonePort GX). The device itself consists of one standard quarter-inch jack slot on the front side, and the output goes via the smaller kind of jack (the green one), and is connected to the PC via USB. There are no official Debian drivers for it, but I did manage to find some unofficial ones ([http://www.ubuntugeek.com/how-to-install-a-line6-guitarport-or-toneport-ux1-or-gx.html](http://www.ubuntugeek.com/how-to-install-a-line6-guitarport-or-toneport-ux1-or-gx.html)). The device is recognized and I have 3 outputs now:

Internal Audio Analog Stereo

Barts HDMI Audio [Radeon HD 6800 Series] Digital Stereo (HDMI)

TonePort GX Analog Stereo

and only ONE input (the TonePort GX one) - note that the Internal Audio input disappeared (I have my headphones input in the tower, the output on the TonePort, and the speaker output in the tower - the TonePort input is only for when I connect my guitar, that's the quarter-inch jack slot).

What I want to do is make it so that I can freely switch from headphones to speakers and back depending on whether or not I'm playing (keep in mind that the signal is processed in the device, so I can't input there and output from the tower) or listening to music (at one point I managed to make the output switching work, but it seems to bug if I switch several times, and then I have to restart).

For the processing software, I've installed Rakarrack, and since I didn't figure out QJack or whatever it was, I tried to establish a connection with Patchage, but that didn't go over well either. The main issue is that I can't use these kinds of programs to make Rakarrack receive a signal. I also understand there is this Wine software which emulates Windows - if there's anyone who can help me run GearBox (the official application from Line 6 for processing), I'd be very thankful. Is there a terminal command which tells me which devices are out2, out3, etc. (I used a similar command when identifying my wireless card's logical something as "wlan0")?

Sorry for the wall of text, I didn't know how to make it shorter. :)

---

### Post by gordintoronto on 2011-08-06
You might find it helpful to learn how to use alsamixer. You can Google alsamixer tutorial.

Audacity is the most popular sound processing program. Run system/administration/synaptic package manager to install it. (First install the "restricted extras," if you have not already done so.)

It might help people to help you if you mentioned what version of Ubuntu you are using.

---

### Post by CatKiller on 2011-08-06
If you want to use JACK to route your audio around (which is recommended when you're recording or doing other srs bsns) you'll need to start a JACK server. QJackctl is the easiest way to do this. It's not ever-so user-friendly, but it is the best tool for the job. Getting to grips with Linux audio will take you on a mind-bending journey.

---

### Post by Choco_Bob on 2011-08-07
I've been using Audacity for quite some time on Win7, but for recording and post-production. It can't really process in real-time as far as I understand. :)

I've ran alsamixer a few times, and I tried getting to grips with the JACK control programs, but I can't seem to route anything properly, and THAT'S where I need help! :D

So if anyone could help me configure this step-by-step, I'd be very thankful (if you need any information, I'll be more than happy to provide, for starters - I'm using the latest version of Ubuntu (11.xx, Natty Narwhal or something :)).

---

### Post by CatKiller on 2011-08-07
> **Choco_Bob said:**
> I've been using Audacity for quite some time on Win7, but for recording and post-production. It can't really process in real-time as far as I understand. :)
You can, but you'll need to use JACK. It's essentially a low-latency patch-bay. Connecting things together is pretty much all it does. Like all sound engineering stuff, it's complicated as a whole, but it's really very many quite simple things.

---

### Post by niko123456 on 2011-08-07
headphones = plugged into your external sound card (line 6)?

speakers = plugged into your internal sound card (inbuilt)?

I know what you're trying to do, but its difficult to use more than one sound card simultaneously. generally you'd solve this problem by plugging a mixer into your external sound card and your speakers and headphones into the mixer. 

----

apart from your problem (maybe I have misunderstood it), here are my tips for good audio recording on linux:

- Use a distro made for the purpose (Ubuntu Studio / Planet CCRMA)
- Use Qjackctl
- Use Ardour

- don't use Audacity.. its crap.

---

### Post by Choco_Bob on 2011-08-07
That is the correct setup niko123456.

Now, I've done a bit more experimenting and I'll chalk up all the bugs to the 3rd-party drivers. First off, switching the I/O to my Line 6 in the sound preferences kills all sound (playing someting in Banshee results in the marker standing at 0:00), but when I restart, all seems functional. Even before the system entirely boots, if my guitar is connected, I hear a dry signal going through the device and exiting on the headphones (but even the dry signal cracks up if I hit the strings a bit harder). QJack doesn't recognize any devices (doesn't even allow me to press "Start"), but Patchage does, and it even automatically links everything when I run Rakarrack. However, it seems to still make the input my mic (on the headphones) and it outputs to the speakers, and I can't reroute any Line 6 stuff (it shows me 2 system captures, 8 playbacks (?!), and 2 separate MIDI (through) ports of some kind).

What further steps can I take?

EDIT: It seems that after 10-15 minutes the sound crashes again, on its own. Are there really no drivers for these Line 6 devices other than the ones I linked to in the 1st post? :/

---

### Post by niko123456 on 2011-08-07
slow down.. above post requires too much thought to unravel.

i don't understand what the problem is now. a microphone? 

does your line6 work OK? ie, you hear your guitar through the headphones that are plugged into it?

if yes, then thats as good as you'll get. you'll have to forget about trying to run more than one soundcard (linux speak = interface) at a time - ie, input with your line6 but output on your internal speaker. 

its more of a hardware limitation than a software one.

---

### Post by niko123456 on 2011-08-07
USB audio has a long history of being badly supported on linux. ..but you're lucky that it seems to be working for you, so that's the good news. 

here is a good workflow:

restart the computer.
plug in your USB sound card.
load Qjackctl.
click on the setup in Qjackctl and select the appropriate interface (your USB card).
click Start on qjackctl. 
click on 'Connect'. 
connect your guitar (on the left hand side, the 'capture') to the output (on the right hand side). 

you should now hear a dry guitar sound. 

now load rackarack. connect your guitar on the left, to rackarack on the right. connect rackarack on the left to your output on the right. if your brain clicks at this point, and you understand what you just did - you're good. if not, then we can't go any further.

---

