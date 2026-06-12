---
title: "skype -pulseaudio"
date: 2009-09-19
forum: General Help
---

### Post by gmseed on 2009-09-19
Just installed Skype beta 2.1 but when I make a test call in the "Options|Sound Devices" the sound goes through the laptop speakers rather than my headphones and it does not record my test message.

I use a Plantronics headset with earphones and microphone.

The problem seems to be that the only option in the "Microphone", Speakers" and "Ringing" comboboxes is "PulseAudio server (local)" and would expect to select the Planatronics device, as I can in the System-Sound dialog box.

Anyone else experienced the same problem and found a solution?

Thanks for your help.

Ubuntu 8.10
Dell laptop Inspiron 6000

---

### Post by kostkon on 2009-09-19
It's not a problem, per se. Nevertheless, you need to install the *PulseAudio Device Chooser* utility (using *Synaptic*) to redirect the sound coming in and out of *Skype* to your USB headset.

More info [here]("http://ubuntuforums.org/showthread.php?t=1130384") (it also applies to 8.10).

Hope that helps.

---

### Post by gmseed on 2009-09-20
Hi

Thanks for your reply.

I installed the PulseAudio Device Controller via the Synaptic Package Manager via package "padevchooser", and required libraries.

I now see the "PulseAudio Preferences" in ""System|Preferences" menu item. There are 3 tabs in this dialog, none of which seem relevant: "Network Access", "Multicast/RTP" and "Simultaneous Output".

Incidentally, in the package installer description it states:

"...simple GTK tool which registers an icon in the tray area..."

However, I don't see any icon on the top/bottom desktop menu bars?

I restarted my m/c and tried the Skype Test Call again, without any luck. It's doing exactly as before and sending the test sound through the speakers and not recording my message.

Cheers

Graham

---

### Post by 3rdalbum on 2009-09-20
Run the "padevchooser" program in the terminal or in the Alt-F2 box. Also add it to your Startup Applications.

You will get the little icon in your notification area that looks like an audio plug. Click this and go to Volume Control.

Start Skype and start the Test Call, and presently you'll see Skype appearing under the Playback and Recording tabs. Click the little popup menu arrow to the right of each Skype entry and go to Move Stream and then the device that you want the audio to come to/from.

Pulseaudio will remember this setting.

---

### Post by theanswriz42 on 2009-09-20
> **3rdalbum said:**
> Run the "padevchooser" program in the terminal or in the Alt-F2 box. Also add it to your Startup Applications.

You will get the little icon in your notification area that looks like an audio plug. Click this and go to Volume Control.

Start Skype and start the Test Call, and presently you'll see Skype appearing under the Playback and Recording tabs. Click the little popup menu arrow to the right of each Skype entry and go to Move Stream and then the device that you want the audio to come to/from.

Pulseaudio will remember this setting.

I tried that but seem to be getting the following error when trying to open up the volume control:


**
ERROR:pavucontrol.cc:574:void StreamWidget::setVolume(const pa_cvolume&, bool): assertion failed: (v.channels == channelMap.channels)


This is on 64 bit 9.04

---

### Post by Bucky Ball on 2009-09-20
Are you talking about the 'Choose Audio Playback Device' in 'Skype-> Options'? I run Skype with Plantronics headset and there is no recognition of them. They just work but I don't use pulse. I set it to the hardware port (at least I imagine that is what it is) for the headphone socket of the laptop.

Not on my laptop right now but will have more detailed look later. Identical setup but I use 8.04

---

### Post by gmseed on 2009-09-20
Hi 3rdalbum

Thanks for your reply. I ran "padevchooser" as stated and now get the icon in the task bar and able to select "Volume Control" before loading Skype. However, once the Skype test message is executed then the padevchooser Volume Control dialog vanishes and repeated selection does not make it reappear, but just results in a flicker of the screen?

If I quit the padevchooser application and re-run via Alt-F2 then get the same flicker but no application UI?

Thanks

Graham

---

### Post by gmseed on 2009-09-20
Hi 3rdalbum

I ran the "padevchooser" again, but this time in the terminal window and it runs ok until the Skype test call is run upon which it throws the following exception, output to the terminal window:

ERROR:pavucontrol.cc:473:void StreamWidget::setVolume(const pa cvolume&, bool): assertion failed: (v.channels == channelMap.channels)

Doesn't look good!!

Graham

---

### Post by gmseed on 2009-09-20
Hi

I see that user "theanswriz42" has experienced the same error on 64-bit 9.04.

I'm using a 32-bit m/c running 8.10.

Graham

---

### Post by frogbrains on 2009-09-20
Having exactly, EXACTLY the same problem as you, right down to not being able to open Volume Control in the device chooser.  Such a pain in the ****!  Hope someone finds a fix soon.

---

### Post by gmseed on 2009-09-20
Hi

Found a way around this Ubuntu-Skype problem --> use gizmo:

[http://gizmo5.com/pc/](http://gizmo5.com/pc/)

I went to the download page:

[http://gizmo5.com/pc/download/](http://gizmo5.com/pc/download/)

and downloaded "Gizmo DEB Install Package" version 3.1.0.79 for libstdc++6 [I checked the synaptic package manager to ensure that I needed libstdc v6].

It installed a breeze and here's the great bit. I then went to the "Gizmo|Preferences|Audio" and selected my Plantronics device without a hitch.

Then performed a test call with the new account default of $0.10.

Wow - Skype should take a few lessons from Gizmo on user setup!!

Cheers

Graham

---

### Post by Bucky Ball on 2009-09-20
As mentioned, if your sound is working on everything else you shouldn't have to change anything in the system.

The changes should be made in Skype->Options->Playback Device

---

