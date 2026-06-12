---
title: "skype mic problem with ubuntu 10.04"
date: 2010-07-26
forum: General Help
---

### Post by jmangas on 2010-07-26
Hi everyone, 

I am new to this and I recently switched to Ubuntu on my laptop it is a lenovo thinkpad R61 it has in intel centrino chip and i can't get the mic to go through to the other person. i can hear them just fine and i can hear myself through my speakers but the other person can not hear me. I don't really know much about Ubuntu so I will give you any info you ask for as long as you can tell me how to get the info. 

Thanks

Jon

---

### Post by drpjkurian on 2010-07-26
Hi
Please first do the skype test call. If that goes fine, then it must be the problem at that end.

---

### Post by jmangas on 2010-07-26
I do a test call but what happens is i get to the point were it says to speak into your mic and it replays it however i never hear anything back. it does the say thing in the sound recorder my mic doesn't seem to be working it is an internal mic sorry i forgot to mention that

---

### Post by drpjkurian on 2010-07-26
Ok then that solved my doubt of your statement > i can hear myself through my speakers.
Please do the following trouble shooting first.It may help you

First: check your Sound recording(Mic)It can be done by using sound recorder programe. Navigate to that programe through Application-->Sound and video--> Sound recorder
If this works that shows that your Mic is fine
If this doesn't work go to system-->preferences-->sound and select the available drivers for sound recording and test it.

Second: Sometimes the Mic works flawlessly in the above mentioned procedure, but does not work in Skype. In that case go to preferences in Skype and change the settings for sound recording.

Hope this may help you. It has solved my problem

---

### Post by MooPi on 2010-07-26
I found this info very helpful in setting up my mic for skype. Using alsamixer and some of the commands helped me set the volume to an acceptable level. Before I started my mic was zeroed out. It pertains to usb mic but can be used to set your mic volume as well.
[http://wiki.audacityteam.org/index.php?title=USB_mic_on_Linux]("http://wiki.audacityteam.org/index.php?title=USB_mic_on_Linux")

---

### Post by jmangas on 2010-07-26
Okay when I do the sound recorder it never plays anything back to me and  i have yelled and it doesn't replay any sound when I go back and try to  replay it.

when i go to system-->preferences-->sound it  brings up the box like it should and shows sound effects, hardware,  input, output, and applications. what should i be testing under hardware  it shows 

internal audio 1 output / 1 input analog stereo duplex

then below that is a box for settings for the selected device:
profile analog stereo duplex is the current one but it also has:
off, 
analog stereo input, 
digital stereo duplex (IEC958), 
digital stereo duplex (IEC958) output + analog stereo input, 
analog stereo output, 
and the current selected one analog stereo duplex

I only get sound from the analog stereo output and the analog stereo duplex

---

### Post by jmangas on 2010-07-26
those smiles should be 8's, also other ppl still can't hear me on skype

---

### Post by sousedstvi on 2010-08-19
hello, jmangas.

I was having a similar problem with a thinkpad r61/ubuntu 10.04

I was able to record using and external mic, the Ubuntu sound recorder and the Skype test call using the following steps:

* In System>Preferences>Sound> Hardware, Profile, I chose Analog stereo Duplex

*In the Input tab, for connector, I chose the default Microphone 1

*still in Input, "Chose a device for sound input", I clicked the radio button for the only choice: Internal audio analog stereo.

*I also made sure the Input volume was not muted and the slider was in the middle

hope that helps!

---

### Post by neffezzle on 2010-08-21
I have the same issue, using Lenovo R61i Ubuntu Lucid the built in mic doesn't work but the mic jack does.  Any ideas on how to fix this?

sound prefs show: analog stereo duplex for hardware the mic level is maxed out and not muted only one device is available "Internal Audio Analog Stereo"

note that alsamixer shows 2 internal input sources but only allows me to adjust the other says LR CAPTURE in all red

---

### Post by neffezzle on 2010-08-21
changed CAPTURE device in alsamixer to external device now the internal mic works but isn't very loud

---

### Post by smarmytime on 2010-08-22
> **neffezzle said:**
> changed CAPTURE device in alsamixer to external device now the internal mic works but isn't very loud
If you go to System > Preferences > Sound, and then go to the Input tab, there is a volume slider, with a sound meter. You should be able to do a mic check using the slider and the input level meter, and bring the volume to the level you want.

---

