---
title: "Configuring Skype Sound Karmic Koala"
date: 2009-11-18
forum: General Help
---

### Post by ProgressionMurph on 2009-11-18
Hello everyone!  I've been having configuring my Skype's sound.  I have tried uninstalling pulseaudio and that made made the sound in Skype not work.

I don't know if any of this information will be usefull:

alex@InMotion:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

When I contact echo sound test service I can hear the ringing and the lady speak but recording my voice doesn't seem to work.

When I connect to someone else I can't hear them and they can't hear me.

Feeling quite lost on were to begin.  Any help is much appreciated.

Sincerely,
Alex

---

### Post by emaydubya on 2009-11-18
You might have to turn the mic on, I did.
I ran kmix and checked, and of course, the mic was muted. I think it defaulted to muted after Karmic upgrade.

Another thing was I completely uninstalled and purged everything Pulse Audio. That fixed my other sound problems. YMMV

---

### Post by hellmet on 2009-11-18
I use pulseaudio + internal mic on my Thinkpad, and all works good.
How about you tell us more about your hardware, and why you removed pulseaudio.

---

### Post by ProgressionMurph on 2009-11-18
I read somewhere that removing pulse audio fixed their sound problems.  I'm using a Fujitsu T5010.

---

### Post by ProgressionMurph on 2009-11-18
I use a Fujitsu T5010.  Someone mentioned to me removing pulse audio might be helpful.  I used Alsa on jaunty.

---

### Post by hellmet on 2009-11-18
And how about the headset and the MIC ? USB or regular?

---

### Post by ProgressionMurph on 2009-11-18
Internal Mic.

---

### Post by El_Shrander on 2009-11-18
Getting the microphone to work on Skype with Ubuntu 9.10 hasn't been easy for me either, but I eventually came across a useful tidbit of information on a Spanish blog (I'd like to quote the source, but i can't seem to find the right link anymore):

Step 1: Close all the audio programs that might be using the loudspeakers (Rythmbox, etc.).
Step 2: Open the terminal and run: sudo killall -9 pulseaudio
Step 3: Open Skype and test your mic's configuration, it might be a little too low by default, but it should work now.

It works every time for me, at least :D Good luck.

---

### Post by snuggs on 2009-11-18
> **El_Shrander said:**
> Getting the microphone to work on Skype with Ubuntu 9.10 hasn't been easy for me either, but I eventually came across a useful tidbit of information on a Spanish blog (I'd like to quote the source, but i can't seem to find the right link anymore):

Step 1: Close all the audio programs that might be using the loudspeakers (Rythmbox, etc.).
Step 2: Open the terminal and run: sudo killall -9 pulseaudio
Step 3: Open Skype and test your mic's configuration, it might be a little too low by default, but it should work now.

It works every time for me, at least :D Good luck.

this may be a different problem, in which case i don't want to derail, but my skype mic works fine... on the first call.. then if i make a second. they can't hear me. does a setting possibly change between call 1 and call 2?

---

### Post by ProgressionMurph on 2009-11-19
Can get everything to work except I can't hear other peoples voices and they can't hear mine.

---

### Post by InaBanina on 2009-11-20
My problem with Skype is that I could be heard just fine but I couldn't hear the person I'm talking to very well. The sound is horribly choppy. It's the same when I try to use the Sound Test service. 

Just FYI, I'm using Skype 2.1.0. I've read some suggestions in other threads to remove pulseaudio and install other audio applications but since I'm new to Ubuntu, I'm still quite hesitant to mess around with anything that might later have disastrous consequences for a panicky newbie like me, lol. Any suggestions? :P

---

### Post by InaBanina on 2009-11-20
By the way, I used to have a problem with the mic too. The volume was way too low and though I'd try raising it with the applet, it kept on going back to minimum. I'm not sure if that's the same problem the others have here, but I found that this simple solution worked for me.

In Skype, go to Options > Sound Devices > Uncheck "Allow Skype to automatically adjust my mixer levels" 

That suggestion could be found here: [http://forum.skype.com/index.php?showtopic=463251](http://forum.skype.com/index.php?showtopic=463251)

After, I went over to Preferences > Sound > Input then toggled the mic volume to maximum. I haven't had a problem since.

---

### Post by mirrorbox on 2009-11-23
Also having problems with mic and skype on 9.10. Used to work fine in 9.04, but stopped working in 9.10. I had no sound at all in 9.10, but removing pulseaudio helped and sound now works in all application, the only problem is sound input in skype. I'm using skype 2.0, tried to experiment with alsamixer - raised all levels to up, enabled capturing on all devices, etc, but I cannot hear my own voice in test call, only noise.

Any ideas how to fix it?

---

### Post by mirrorbox on 2009-11-23
> **mirrorbox said:**
> Also having problems with mic and skype on 9.10. <snip>

Updates on my problem: got pusle installed back and managed to get sound working with it - just need to enable 'Surround' in alsamixer (I don't know why I have to though). But cannot get mic working.... tried even audacity and arecord and cannot record anything, so it seems to be like general ALSA problem.

---

### Post by mdurham on 2009-11-23
Hi Guys, Can anyone please save my sanity and explain to me how:
I have a usb phone handset plugged in permanently.
How do I get the received sound from Skype to come from the usb phone and all other sounds from the computer sound card?
I can get all sound from phone only or all sound from the card only.
I have no problem with the microphone as I can select the sound source when Skype is running using "Pulseaudio Device Chooser".
Any help would be most appreciated.

Cheers, Mike

---

### Post by mirrorbox on 2009-11-24
> **mirrorbox said:**
> Updates on my problem: got pusle installed back and managed to get sound working with it - just need to enable 'Surround' in alsamixer (I don't know why I have to though). But cannot get mic working.... tried even audacity and arecord and cannot record anything, so it seems to be like general ALSA problem.

Update: I've fixed my problem.

I've added this line to alsa-base.conf:


options snd-hda-intel model=3stack-dig

Then played with alsamixer a bit and got stuff working.

---

### Post by welshmike on 2009-11-27
> **El_Shrander said:**
> Getting the microphone to work on Skype with Ubuntu 9.10 hasn't been easy for me either, but I eventually came across a useful tidbit of information on a Spanish blog (I'd like to quote the source, but i can't seem to find the right link anymore):

Step 1: Close all the audio programs that might be using the loudspeakers (Rythmbox, etc.).
Step 2: Open the terminal and run: sudo killall -9 pulseaudio
Step 3: Open Skype and test your mic's configuration, it might be a little too low by default, but it should work now.

It works every time for me, at least :D Good luck.

Thank you. That worked for me (killing the pulseaudio process). I thought I'd have to do that after every boot but after second reboot today Skype microphone continues to work.

---

### Post by TDK800 on 2009-11-27
Alex, try this, fixes mic, for Skype too, and pulseaudio is still installed: [http://ubuntuforums.org/showthread.php?p=8397068](http://ubuntuforums.org/showthread.php?p=8397068)

---

### Post by Gendor on 2009-11-29
I have an Intel-based sound card on a HP laptop. I had some issues with sound in Skype on 9.04, and configured the *Sound out* and *Ringing* settings to "pulse", with *Sound In* still configured as "HDA Intel (hw:Intel,0)" to get it working. 

After upgrading to 9.10, any sound from within Skype would be very intermittent/scratchy/garbled. Changing the settings to "HDA Intel (hw:Intel,0)" would just result in no sound. But when I **leaved** the settings on "HDA Intel (hw:Intel,0)" and **restarted** (you might have to restart your computer as Skype doesn't want to close on its own) it worked perfectly.

I'm hypothesizing that if you have your Skype settings on "pulse" and you change it to something else, Skype is still connected to the Pulseaudio server, but when you (force) exit it disconnects, and on restart it's able to play the sound through your ALSA sound mixer. Anybody's thoughts on this?

---

### Post by farchumbre on 2009-12-08
hi
i have a thinkpad x300 and ubuntu 9.10.
i can use an external mic with skype, but my internal mic it is not recognized by pulseaudio, and i can't find a way to turn it on as I had with the ubuntu 9.04 version. any ideas?

---

