---
title: "Sound Problems"
date: 2011-04-13
forum: General Help
---

### Post by Aydos on 2011-04-13
I have had issues trying to use a VOIP client. I recently made an unsolved post about using Mangler, but I wonder if my problem goes deeper than that.

When I have a USB headset plugged into my system and set the options on the audio mixer to creative usb headset and not default audio it will work with the program Mangler that I use.

It will randomly stop picking up my voice. If I look the audio mixer the drop down boxes are set to default, but they always look like that when I open it even when the mic is working.

If I keep changing it to Creative USB Headset and hitting apply over and over again and closing Mangler it will eventually work.

Is there something that I can do to make it stay on my creative usb headset for the mic.

I have had this problem on Ubuntu 10.04 Kubuntu 10.10 and openSUSE 11.4

On openSUSE when the mic stops picking up my voice the volume icon in the bottom left corner will have a popup saying that the sound system is defaulting to the default from my headset.

Since they all use Pulse I thought that might help.

---

### Post by Aydos on 2011-04-13
bump

---

### Post by BertN45 on 2011-04-14
I hope I understood the problem, because it sounded a little bit cryptic to me.

Do not use te pulse audio mixer from the Gnome panel, if you are dealing with more then 1 audio device. it does not support that type of configurations very well. I am using Pulse Audio Volume Control and I have a perfect separation between my USB headset and the built in Internal Audio.  The settings are also remembered after a re-boot. When I plug-in my headset, it is directly connected to Skype and my music is always directed to my internal audio chip set and I can use both at the same time. It is nicely separated. Only the pulse audio equalizer destroys those settings, but only for the current session. 

In PA Volume control you have to select the right device for each application in the "playback" and "recording" tabs **during** playback or recording. The names are a little bit confusing, playback is audio output and recording is audio input. You can also select the default volume setting, but that is less interesting. Afterwards those settings will be remembered for the rest of your Ubuntu life.

Ubuntu kills a little bit a perfect audio architecture, by providing inadequate default controls.

---

### Post by Aydos on 2011-04-14
Awesome this sounds very promising. Does it work in KDE or is there a KDE equivilent?

---

### Post by BertN45 on 2011-04-14
I expect it will work for kde too, just try it.

---

### Post by Aydos on 2011-04-14
I am still having problems making it work. 

There is a list that has things like Analog Stereo Output, Digital Stereo, Duplex, IEC958, and various mixtures of these. I have not clue what to put it on. It just will not pick up my mic permanetly even with the pulse volume control.

I am at a loss as of what to do at this point.

---

### Post by BertN45 on 2011-04-19
I have been installing Xubuntu Beta 2 on the PCs in the house, so I gave been off line for some time.

I think you have been looking in the tabs "output devices" and "input devices" and there you can't select something per application. Just use the defaults there or use what suits your speakers and microphone the best.

To select which device yo want to use for e.g. output, you have to go to the playback tab. You have to use the application for which you want to select another output device. For instance for Skype I do a test call and then I see Skype appear in that playback tab.
You can change the audio device by pressing the button with the audio device to the right after the name of the application. In my case it reads: "Internal Audio Analog Stero" and that is connected to my speakers. If you click, it will show a list of available audio devices and you can tick the one you want, e.g USB Headphone. From that moment on that audio device stay assigned to Skype, so if you start Skype it will automatically use the USB Headphone.

You have to do the same for Recording tab for any application that you want to give a non default audio input device. But you can only select the device, while that application is active and playing/recording.

It seems that in the Input Device tab they have added a green "set as fall back" button, I have unselected those,I do not need a fall back.

Note that the new version of Skype distributed this week now has a button "open pulseaudio volume control" in the audio settings section.

---

