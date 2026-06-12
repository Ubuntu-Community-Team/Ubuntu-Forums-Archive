---
title: "Skype Mic Not Working Karmic"
date: 2009-10-31
forum: General Help
---

### Post by branislavski on 2009-10-31
Ok, i know there is a million posts about this but i still cant figure it  out. I have installed and played with "pedvechooser" (pulse audio chooser) but im still stuck with the mic not working in skype plus its really low in other programs like sound recorder for example. I have no clue and its frustrating cause i need skype to be in touch with people but i have to boot stupid vista to talk to them normally.
Lately i get this crazy thoughts that just maybe windows 7 is a good idea, but then i slap myself and im ok again. :D

I have a HP pavilion dv 9730us

bane@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by Zoot7 on 2009-10-31
I've the same problem aswell with the inbuilt mic beside the Webcam in my Dell XPS M1530 just in Skype. I haven't gone fiddling too much with Pulseaudio yet, not too big an issue since I generally use the headset for skype anyway.
I had it working in Jaunty but that was by simply removing pulseaudio entirely, and I'd rather not do that now.

Anyway, I too would be interested if anyone was any advice on this issue.

EDIT: I did find a solution earlier, but it was simply to disable Pulseaudio when you start skype and then re-enable it after you're done.

---

### Post by andddlay on 2009-10-31
Here's what I did.  Just got it working.

System>Preferences>Sounds then go to the input tab and unmute the input volume and bump up that to the max :P

Hope I helped.

---

### Post by woodybrando on 2009-11-01
thx andddlay,
i been stuck for a week or so trying to figure out how to get the internal mic to work on my netbook with karmic and skype. And you were right, I just needed to turn up the volume on the mic. I swear I'd tried this ten times before but for some reason this time it worked. 

The mic seems more staticky than normal, the signal to noise is low but it's better than silence. thx. jayson

---

### Post by andddlay on 2009-11-01
> **woodybrando said:**
> thx andddlay,
i been stuck for a week or so trying to figure out how to get the internal mic to work on my netbook with karmic and skype. And you were right, I just needed to turn up the volume on the mic. I swear I'd tried this ten times before but for some reason this time it worked. 

The mic seems more staticky than normal, the signal to noise is low but it's better than silence. thx. jayson

Glad that problem got resolved for you :)

---

### Post by branislavski on 2009-11-01
Im glad it worked for you guys but my problem persits, in my input section there is no settings posible because its all greyed out.

---

### Post by TenPlus1 on 2009-11-03
I just got my mic working by going into the mixer controls, adding v_refout and enabling the switch under the switch tab... :)

---

### Post by mihaidoru on 2009-11-05
Thank you andddlay, it worked.
I had problems with using the headset mic.
I just had to choose Microphone 2 (Microphone 1 was the default) in input tab, and increase the volume a bit.
I'm on DELL vostro 1510.
Glad that it works now, on Jaunty I had loads of issues with the former Skype version.

---

### Post by Notselfcreated on 2009-11-10
Acer Aspire One D150 netbook, same problem, no solutions work so far.

I have:
[LIST]
[*]Installed padevchooser and ensured that the "Recording" tab is set correctly when using a Skype test call.
[*]Unchecked all "Mute" options and checked "Record" in the mixer settings and sound settings.
[*]Tested with default "Sound Recorder" (it works fine there).
[*]Installed linux-backports-modules-alsa-karmic-generic
[*]Set all volume options to max.
[*]Unchecked "Allow Skype to control... etc. etc." in the Skype options.
[*]Read nearly every post on the subject.
[*]Pulled out most of my hair.
[/LIST]

---

### Post by NiksaVel on 2009-11-12
Hi guys,

I have Acer Aspire One D-250 and A-110  the problem is same on both...

I can normally use external mic.

Internal mic works normally in gnome-soundrecorder, but there is no sound going through it for skype... 

I have found a suggestion here to install pavdevchooser but nothing new there. It did, however give me a Pulseaudio Volume Control icon under the "Sound & Video" menu and I can also see there on the "Input level" that it doesn't record any sound, even though gnome-soundrecorder works, and indicates recording sound, even at the same time.

I am almost certain this is some weird pulseaudio issue, but I have no idea how to go about it.  Using external mic for now, but it's a lame solution with the inbuilt one staring at me...

---

### Post by applejuicekiss on 2009-11-15
same here.  Aspire One D250.  mic works for other things, but nothing but quiet static comes back from the skype echo test.

---

### Post by GOrwell on 2009-11-21
Hi, for the aspire one d150 (i have this one) i've found a workaround.

Open alsamixer and change the mic volume (CAPTURE). The left side to 0 and the right to 100.

Open **alsamixer**, push **F6** to choose the Audio card. Push **F5** (All). Move with arrow keys on **CAPTURE**.
Push **Z** to decrease the left column and **E** to raise the right one.
Now start skype and it should work. I think it should work also in the D250.

By

Pascal

---

### Post by Nonno Bassotto on 2009-11-22
GOrwell you've made my day!!!!!!!!! It really works!!! :-D

---

### Post by NiteSoul on 2009-11-22
> **GOrwell said:**
> Hi, for the aspire one d150 (i have this one) i've found a workaround.

Open alsamixer and change the mic volume (CAPTURE). The left side to 0 and the right to 100.

Open in a terminal or console **alsamixer**, push **F6** to choose the Audio card. Push **F5** (All). Move with arrow keys on **CAPTURE**.
Push **Z** to decrease the left column and **E** to raise the right one.
Now start skype and it should work. I think it should work also in the D250.

By

Pascal

This procedure also work with AOD250!

Thank you very much!

---

### Post by blackest_knight on 2009-12-11
here is a bit of a work around for skype and linphone

/bin/sh -c "PULSE_SERVER=127.0.0.1 linphone-3"
/bin/sh -c "PULSE_SERVER=127.0.0.1 skype"

and probably most other applications as well 
alsamixer should allow the correct input to be selected i-mic / e-mic 
while it works essentially the application fails to connect to pulseaudio and falls back to good old alsa. 

it's easy enough to create a desktop launcher for this or edit the menu entry.

Hopefully a real solution will be available sooner or later. at least this saves uninstalling pulse and should mean less of a disruption when a fix is issued.

---

### Post by joes7 on 2009-12-11
Check your driver / hardware manager.

---

### Post by Holden99ca on 2009-12-12
> **GOrwell said:**
> Hi, for the aspire one d150 (i have this one) i've found a workaround.

Open alsamixer and change the mic volume (CAPTURE). The left side to 0 and the right to 100.

Open **alsamixer**, push **F6** to choose the Audio card. Push **F5** (All). Move with arrow keys on **CAPTURE**.
Push **Z** to decrease the left column and **E** to raise the right one.
Now start skype and it should work. I think it should work also in the D250.

By

Pascal

Un-freaken-believable. Nice work!

---

### Post by applejuicekiss on 2009-12-28
thanks GOrwell,

not sure why that works, but it does on my d250.  much appreciated.

---

### Post by coskierken on 2009-12-28
And/or, install "pavucontrol" through synaptic and adjust mic volumes until it works.  Had the same problem with a new D250, also.  Fixed now!

---

### Post by cotcot on 2010-01-01
I also had the problem with the internal microphone (of an ACER 1810TZ). The solution mentioned in [[COLOR="Red"]this[/COLOR]]("http://forum.notebookreview.com/showthread.php?t=434638") thread solved the problem.

---

### Post by Qu4rk on 2010-01-08
Has anyone noticed that you have do the right click, turn volume up trick multiple times?

Sometimes if I make a skype to skype call, hang up & then call a cell phone (and vice versa), the volume goes back low again.  I then have to do the right click, turn volume up.  Anyone know why this is?

Thanks

---

### Post by olofcadiz on 2010-01-09
I have got the microfone working and I did like this

Open system>preferenses>sound and adjust
[IMG]http://olofpark.com/volume.png[/IMG]

Open gnome volume on upper panel to the right and adjust
[IMG]http://olofpark.com/gnomevolume.png[/IMG]

Open alsamixer -V all and adjust
[IMG]http://olofpark.com/alsa1.png[/IMG]
[IMG]http://olofpark.com/alsa2.png[/IMG]

Remove skype apt-get remove skype eller med synaptic
Restart computer
Install skype-debian_2.0.0.72-1_i386.deb
open option>sound and adjust
[IMG]http://olofpark.com/skype.png[/IMG]

open alsamixer -V all and adjust microfon settings for your computer

Good luck

---

### Post by oneindelijk on 2010-01-13
Hi Girls, 

I've had the same problem as described above and in some other forums. My micro volume was set to very low and I couldn't change it.
I discovered that Skype's option "automatically adjust sound levels" was the cause of this.
Hope this solution might help anyone :-)

Sam (on Karmic Koala)

---

### Post by Qu4rk on 2010-01-13
> **oneindelijk said:**
> Hi Girls, 

I've had the same problem as described above and in some other forums. My micro volume was set to very low and I couldn't change it.
I discovered that Skype's option "automatically adjust sound levels" was the cause of this.
Hope this solution might help anyone :-)

Sam (on Karmic Koala)

This is spot on.  This should be posted in the Wiki somewhere.

Good Job oneindelijk!

---

### Post by Kaliman_ on 2010-01-14
> **Notselfcreated said:**
> Acer Aspire One D150 netbook, same problem, no solutions work so far.

I have:
[LIST]
[*]Installed padevchooser and ensured that the "Recording" tab is set correctly when using a Skype test call.
[*]Unchecked all "Mute" options and checked "Record" in the mixer settings and sound settings.
[*]Tested with default "Sound Recorder" (it works fine there).
[*]Installed linux-backports-modules-alsa-karmic-generic
[*]Set all volume options to max.
[*]Unchecked "Allow Skype to control... etc. etc." in the Skype options.
[*]Read nearly every post on the subject.
[*]Pulled out most of my hair.
[/LIST]


Yeap... did all your steps as well and nothing worked... including the last one...

---

### Post by siraf on 2010-01-22
Oh man, GOrwell: you rock!

How on earth did you figure that one out?

---

### Post by Kooster on 2010-05-03
This was GENIUS!!! Running Lucid on aspire one ZG5 and it worked like a dream. Just hope that the guys at ubuntu wil notice this in future releases

---

### Post by motoperpetuo on 2010-05-20
i have a dell inspiron 530, running karmic. i had to do the following to get my microphone to work with skype:

1)Go to System | Preferences | Sound
2)Input tab
3)Under Connector, choose Microphone 2.
4)Make sure “Input volume” is not muted, and turn the volume up to max.

i guess the default, Microphone 1, may have been the microphone jack on the back of the computer. also, the input volume sets itself to something other than max on its own. anyway, main thing is it works. just spent 45 minutes talking to a friend over in ukraine with no problems.

---

### Post by ThomasBrehme on 2010-05-22
> **GOrwell said:**
> Hi, for the aspire one d150 (i have this one) i've found a workaround.

Open alsamixer and change the mic volume (CAPTURE). The left side to 0 and the right to 100.

Open **alsamixer**, push **F6** to choose the Audio card. Push **F5** (All). Move with arrow keys on **CAPTURE**.
Push **Z** to decrease the left column and **E** to raise the right one.
Now start skype and it should work. I think it should work also in the D250.

By

Pascal

You Rock! Thanks also from my friend who has that laptop!

To be also helpful: It worked on Aspire One ZG5

---

