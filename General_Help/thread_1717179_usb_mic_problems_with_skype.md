---
title: "usb mic problems with skype"
date: 2011-03-29
forum: General Help
---

### Post by kooley on 2011-03-29
hello, iv recently downloaded and installed skype, and i am having problems with getting my mic to work, i have a usb mic i got with a playstation game called rockband, the mic works just fine with audacity but i cant seem to get it working in skype.

when i try and config. skype for the mic under: Skype>Options>Sound device, there are 3 drop down menus for mic, speakers, and Ringing, all of these are set to "PulseAudio Server (local)", and the drop down menus don't have any other options under any of the catagories, how can i get skype to recognize my usb mic to get it to work?

thank you

---

### Post by prshah on 2011-03-29
> **kooley said:**
> all of these are set to "PulseAudio Server (local)", how can i get skype to recognize my usb mic to get it to work?


Click the volume control applet (near the date/time), and choose "Sound preferences"; open the "Hardware" tab and ensure that you have atleast one input device (may be combined as a singe input/output device). Then, click the "Input" tab, and "choose" the relevant input device. Unmute the input and adjust volume until the sound meter registers sound.

if you run into problem, please post back with screenshot of the Sound preferences window, Input tab.

---

### Post by kooley on 2011-03-29
when i clicked on the volume thing by the date/time a this is what i got: (see attachment) nothing is muted and there is not hardware tab am i looking in the wrong thing?

---

### Post by kooley on 2011-03-29
can any one help me figure out what im doing worng?

---

### Post by PARO on 2011-03-31
You're not doing anything wrong, pulse audio is like that, awsome when it works, but of the 3 computers i have ubuntu on i've had to get rid of pulse audio on at least 2 because of issues it has with their sound cards/mics/etc. on numerous occasions. the recent update broke mic support in my logitec usb webcam/mic, and my netbook could hear (through left speaker only) and use the mic in programs like audacity and sound recorder, but not for sip telephony or skype. so simple solution uninstall pulse audio and use alsa instead. eventually pulse audio will iron things out, until then i've found it way to time consuming searching fixes to all the different problems that popup from time to time in pulse. so right now i have no pulse audio on any of my computers :/.

---

### Post by PARO on 2011-03-31
Better solution! if you want to keep pulseaudio... and why wouldn't you. i was able to get it working by installing gnome-alsa-mixer and moving the mic to a max audio level of about 75% you can still move the mic boost all the way up if you want it louder though. You can also tinker with this directly when in Ekiga (if you use Ekiga also). So.. i guess i can still use PA on this netbook again after all :).

---

### Post by prshah on 2011-03-31
> **kooley said:**
> can any one help me figure out what im doing worng?

What version of Ubuntu are you using? If you do not know, check with the (Applications-Accessories-Terminal) terminal command```
cat /etc/lsb-release
```

---

### Post by kooley on 2011-04-01
thank you all for your suggestions im going to try them now, 
and i am using kubuntu 9.10 (karmic)

---

### Post by kooley on 2011-04-01
i just tried the gnome-alsamixer and couldnt get my usb mic working with skype, i also tried removing it and still not working, and i think the problem is that i cant select anything other than pulse audio server in skype 2.1

---

### Post by lidex on 2011-04-02
[Scrap that - I see this is kubuntu.]

Did you install pulse? If so you can remove it, it shouldn't be required.

---

### Post by kooley on 2011-04-02
yea i tried removing pulse, but nothing changes in skype lol its only option is still pulseaudio

---

