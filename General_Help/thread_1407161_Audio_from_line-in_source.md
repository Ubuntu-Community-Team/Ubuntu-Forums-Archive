---
title: "Audio from line-in source"
date: 2010-02-14
forum: General Help
---

### Post by TennTux on 2010-02-14
I have an audio source that I want to listen to through my PC speakers. My computer has both a mic(rophone) and a line-in audio connector. I am able to use the "gnome-sound-recorder 2.28.1" under Karmic Koala to record from these sources and then I can play back the sound.

However, I'm more interested in listening to the audio then recording. Though, recording would be nice if it where available too. Using Rhythembox Music Player, Movie Player and Audacious2 I am able to play CD(s), Pod Cast feeds, Files and possibly other sources I'm not seeing anything to handle hard wired input to my sound card as an option.

Do I need to open a device as a source? Do I need an extension to one of these players? Am I missing something obvious?

---

### Post by DGortze380 on 2010-02-14
> **TennTux said:**
> I have an audio source that I want to listen to through my PC speakers. My computer has both a mic(rophone) and a line-in audio connector. I am able to use the "gnome-sound-recorder 2.28.1" under Karmic Koala to record from these sources and then I can play back the sound.

However, I'm more interested in listening to the audio then recording. Though, recording would be nice if it where available too. Using Rhythembox Music Player, Movie Player and Audacious2 I am able to play CD(s), Pod Cast feeds, Files and possibly other sources I'm not seeing anything to handle hard wired input to my sound card as an option.

Do I need to open a device as a source? Do I need an extension to one of these players? Am I missing something obvious?

Assuming GNOME.

Click on volume applet -> Volume Control -> Preferences 

Select Line-in

Click Close

You should now be able to control Line-in. Unmute and adjust accordingly.

---

### Post by TennTux on 2010-02-15
> **DGortze380 said:**
> Assuming GNOME.

Click on volume applet -> Volume Control -> Preferences 

Select Line-in

Click Close

You should now be able to control Line-in. Unmute and adjust accordingly.

Ok. I guess I'm a little dense this evening. Not my usual condition. ;-)

I'm having a little trouble following DGortze380's instructions.

In "Applications->Sound & Video" I have a number of applications including: Audacious2, Movie Player, Rhythmbox Music Player, Sound Recorder, Volume Control and Volume Monitor. I checked out each except Volume Monitor which fails with an error. As far as I can follow none of them has a "*->Volume Control->Preferences" with a "Line-in" option.

When I hear "Applet" I think Java in a web browser. I have disabled both Java Script and Java in my web browser.

Could I please have another clue. :-)

---

### Post by DGortze380 on 2010-02-15
> **TennTux said:**
> Ok. I guess I'm a little dense this evening. Not my usual condition. ;-)

I'm having a little trouble following DGortze380's instructions.

In "Applications->Sound & Video" I have a number of applications including: Audacious2, Movie Player, Rhythmbox Music Player, Sound Recorder, Volume Control and Volume Monitor. I checked out each except Volume Monitor which fails with an error. As far as I can follow none of them has a "*->Volume Control->Preferences" with a "Line-in" option.

When I hear "Applet" I think Java in a web browser. I have disabled both Java Script and Java in my web browser.

Could I please have another clue. :-)

That's probably my fault. By "Volume Applet" I mean the the app on your top Gnome panel, looks like a speaker, controls the volume for Master.

As far as recording, I use Audacity. Install from synaptic. And yes, you will have to choose an input source in the program as well, and adjust the volume accordingly. In Audacity Edit -> Preferences, Under Recording -> Device Select select the device that represents your line-in jack.

---

### Post by audiomick on 2010-02-15
The sound card needs to be set to run duplex too, as far as I know. I can get to that with a right click on the volume icon, select "audio options" and look on the second tab "harware" in the pop up window.

---

### Post by TennTux on 2010-02-15
> **DGortze8828000]Assuming GNOME.

Click on volume applet -> Volume Control -> Preferences

Select Line-in

Click Close

You should now be able to control Line-in. Unmute and adjust accordingly.
[/QUOTE]

[QUOTE=DGortze380 said:**
> That's probably my fault. By "Volume Applet" I mean the the app on your top Gnome panel, looks like a speaker, controls the volume for Master.


Thanks for getting back to me.

I see... I'm quite a bit closer. My speaker is on the bottom of my screen (I may have moved it) and when I right click I'm given 2 options: mute, sound preferences.
Sound preferences brings up a dialog with: Sound Effects, Hardware, Input, Output and Applications. When I choose Input I have options for Analog Microphone 1, Analog Microphone 2 and Analog Line-in with a couple of others. When I select the correct source I even see the fluttering input level as I would expect.

> **TennTux said:**
> I have an audio source that I want to listen to through my PC speakers. My computer has both a mic(rophone) and a line-in audio connector. I am able to use the "gnome-sound-recorder 2.28.1" under Karmic Koala to record from these sources and then I can play back the sound.

... I'm not seeing anything to handle hard wired input to my sound card as an option.

Do I need to open a device as a source? Do I need an extension to one of these players? Am I missing something obvious? 


However, as I originally stated I was able to use the simple little "Sound Recorder" application to successfully record and play back. My issue has always been with monitoring the live feed, not with inputing from the source.

I was thinking my issue was more with Audacious2 or Rhythimbox and how to tell them to play from this source. These apps give options to play a file or play a location but I'm not sure which file to load on my system or which URL to provide to correspond to the Analog Microphone or Analog Line-in.   ?

I hope I have successfully explained my issue.

---

