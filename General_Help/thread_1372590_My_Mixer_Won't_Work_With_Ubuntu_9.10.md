---
title: "My Mixer Won't Work With Ubuntu 9.10"
date: 2010-01-04
forum: General Help
---

### Post by derekeverett on 2010-01-04
Long story short... I have sifted through endless docs.. some that I understood and some that I didn't, I have posted in these forums twice (not one response) and asked my local LUG for ideas and I got nothing.

I have an audio mixer that I am desperate to get working with Ubuntu 9.10, and despite working fine with Vista (so I know it's not my hardware or Mic's etc.) I can't achieve this to save my life. 

At this point, I would like to just go with what works and stick with Vista, but like a fool it was me who suggested to some long distance collaborators that we all try to use Ubuntu. Now I am the only one not working...

I am frustrated to no end here. But I figure I will ask one more time and pray that someone can help me here. 

How can I get Ubuntu to accept my mixer as input for audio recording??

I should also state that I am having no other audio issues that I am aware of, and that the cheap, sounds like crap mic that is built into my monitor DOES work with Ubuntu. I need to change away from this mic as the input source and over to my mixer which is connected to my sound card. 

Sorry to repeat myself here but I wish to stress that this configuration of mics into mixer into computer is something I have been doing for years on the mac and with windows so I know the problem here lies with Ubuntu. And like I say, I am dual booting now on an HP desktop with Vista and I have success with Vista.

If somebody can help me get this working I promise I won't use cuss words for 6 months, I will be nicer to animals, I will reduce my carbon footprint, and I will help a child learn to read. Also, I will donate 10% of my income tax refund to a charity of your choosing. Ok 20%. 

That's all I got.

Thanks

---

### Post by jamesisin on 2010-01-04
Shall I assume you are using PulseAudio?

You can take a look at how I configured PA to work with my Decco pre-amp:

[http://www.soundunreason.com/InkWell/?p=1318](http://www.soundunreason.com/InkWell/?p=1318)

You'll just have to use the Input Devices tab instead of the Output Devices tab.

---

### Post by Jenkins1 on 2010-01-04
Hi,

You may have tried these ideas but;
right click the little speaker and go prefernces.
select the input tab and then change the drop down box to one of the options. ( i suspect Line-in is a likley choice) keep trying until you have tried them all and found one that works. The screen-shot attached shows the window that I am on about. 

If that doesn't work try going applications > ubuntu software centre
type alsa in the serch bar and install gnome alsa mixer and adjust your alsa input settings to see if that is a problem.

---

### Post by derekeverett on 2010-01-04
Thanks so much for your help so far guys I appreciate it very much.

I installed gnome-alsa mixer and have gotten my system to the point that I can now hear my mixer's output in the headphones, but I can't seem to get the record function to pick it up. 

When I press record using Sound Recorder nothing happens. Unless, I choose the input option that appears to be the mic built into my monitor - but that ones sounds terrible and is of no use to me.

I'm not sure if I'm running pulseaudio or not.. how would I find out? I can tell you that nothing with this name comes up under Applications->Sound/Video. I am running 9.10 64 bit, pretty much the default install if that provides any info.

So in short, I can hear the audio I desire now, I just can't record it. Any further suggestions?

---

### Post by jamesisin on 2010-01-04
Sorry, if you enter which pulseaudio in a command line and get an output (probably /usr/bin/pulseaudio) you have it installed.  It is the default sound mixer for Ubuntu.  As fate would have it, it was not implemented very well.  As force would have it, the troops have provided this:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

That will get PA on track.  Then you can follow my post.

Let me know how that goes.

---

### Post by ajgreeny on 2010-01-04
Run alsamixer in terminal and see if you have a channel "Mic Select"  as I think you may need to choose the second mic if there is one built in, as number 1 will be that and number 2 will be the external mic.

Alsamixer in terminal is much better in my opinion than gnome-alsamixer.

---

### Post by derekeverett on 2010-01-04
I don't appear to have a mic select option. But thank you. I'm still working away at this and reading everyone's suggested material but I'm not having much luck.

I can still hear the desired audio in the headphones but can't record it.

---

### Post by derekeverett on 2010-01-04
Thanks for all your help everybody!

The issue remains.. I still can't record the incoming audio so if anyone has any suggestions please let me know.. I would love to get it working.

However for the time being the group I am working with on this collaboration has decided that we shall return to Windows where I am not having any troubles.

I now see why people occasionally loose their minds in these forums and announce their return to another OS... there is just too much stuff that just plain doesn't work in Linux or is WAY to difficult to get working properly.

---

### Post by switch10 on 2010-01-04
Hey man.

What software are you using to record??  Ardour?  What kind of mixer is it?  what is the interface, i.e. USB, Firewire?  Are you using the RT kernel?

My band uses Ardour to record our music.  I have a USB multimix 8 that works flawlessly with Linux.  I'd like to know more if you are still having an issue with this.

Dave

---

### Post by switch10 on 2010-01-04
> **derekeverett said:**
> I don't appear to have a mic select option. But thank you. I'm still working away at this and reading everyone's suggested material but I'm not having much luck.

I can still hear the desired audio in the headphones but can't record it.

go to system>prefs>sound, click on the input tab..  what does it say??

---

### Post by jamesisin on 2010-01-04
switch10 - Nice font.

---

### Post by derekeverett on 2010-01-04
I only need to record the one condenser mic...

It's running through the mixer and I am running from the mixer with a cable that is 2 RCA out and 1 1/8 inch jack into the sound card. (see attachment for picture)

As far as audio program I'm using.. I will settle for just getting this working with Sound Recorder for now! No sense in firing up recording software if your inputs don't work. But I will check out your suggestions should I ever get this working.

---

### Post by derekeverett on 2010-01-04
System->Pref->Sound->Input as requested....

---

### Post by switch10 on 2010-01-04
and selecting 089d does nothing??

---

### Post by derekeverett on 2010-01-04
There is no disable option there.. How would I do that?

I was able to mute the crappy mic in pulseaudio, but all that did was stop me from hearing it in the headphones. When I record, it still either records nothing or records the crappy mic, depending on my settings at System->Pref->Sound->Input tab.

Nothing seems to allow for recording of the mixer output, despite my being able to hear it fine with the headphones!

I just had a baby 5 months ago so I can't even shoot myself in the head and be done with it.

---

### Post by derekeverett on 2010-01-04
> **switch10 said:**
> and selecting 089d does nothing??

Selecting that ensures that I record the crap mic.

---

### Post by jamesisin on 2010-01-04
No, that Internal Analog Audio Stereo ought to be your microphone input.  Can you confirm that you are attached to the correct input (sometimes sound is still possible when connected to an output for example)?

---

### Post by derekeverett on 2010-01-04
> **jamesisin said:**
> No, that Internal Analog Audio Stereo ought to be your microphone input.  Can you confirm that you are attached to the correct input (sometimes sound is still possible when connected to an output for example)?

How shall I confirm? It records fine in Vista, is that confirmation?

---

### Post by jamesisin on 2010-01-04
Sorry, what I mean is... I've done this in the past where I set up a system and had audio problems because I plugged into the wrong 1/8" plug (I've seen systems with 5 plugs and odd coloring systems).  I just meant to see that you are certainly plugged into the microphone input and not some other input.

Which brings another question to mind.  Can you tell us a little about your input?  Sound card or onboard?  How many inputs/outputs and types?

This has me very curious and I would like to see it resolved (though perhaps not as much as you would).

---

### Post by switch10 on 2010-01-04
I am at a loss here.  This seems like it would work without any problems.  Have you tried any other distro's?


> **jamesisin said:**
> switch10 - Nice font.

thanks man :)

---

### Post by todak on 2010-01-04
Is the mixer output running into the Line In of the soundcard or the Mic input??

---

### Post by derekeverett on 2010-01-04
> **todak said:**
> Is the mixer output running into the Line In of the soundcard or the Mic input??

I was just triple checking that. I am for sure 100% in the "in" jack. I do also have a mic jack.. and I tried that too but no dice.

---

### Post by jamesisin on 2010-01-04
I think you should see a change when you attach something to the mic input v attaching something to the line in (in the input section of PA if not also in System Sound).  The name should change or the dropdown list should change.  Do you see anything like that?

---

### Post by derekeverett on 2010-01-04
I just switched it to "mic" and have checked everything I can think of in Preferences and in Pulse Audio. Nothing is working. I'm gonna take a few minutes break before I slam my face into the wall a few times.

Thanks for all your help guys. I'll be back to try some more in a few.. as always any other ideas would be appreciated.

---

### Post by todak on 2010-01-04
Did you install ubuntu on the same machine as you have/had Windows? Or did you move the mixer/mic setup from one machine to the current ubuntu machine? Is the condenser mic self-powered (i.e., battery) or does it get its power from the mixer?

---

### Post by derekeverett on 2010-01-04
> **todak said:**
> Did you install ubuntu on the same machine as you have/had Windows? Or did you move the mixer/mic setup from one machine to the current ubuntu machine? Is the condenser mic self-powered (i.e., battery) or does it get its power from the mixer?

Hi, yes it's the same machine. I'm dual booting between Vista and 9.10. I thought I should make it clear that I'm not using a virtual machine. It was a good clean fresh install.

The condenser mic uses phantom power supplied by the mixer. As I have mentioned earlier, in Ubuntu I can hear the audio picked up by the mic - I just can't record it. In Vista, everything INCLUDING recording works.

---

### Post by jamesisin on 2010-01-04
This is not likely it, but open Volume Control and make sure microphone is not muted.

There is a device list, you can seek through that for your microphone input (or your line in) and ensure that no muting is borking matters.

---

### Post by jamesisin on 2010-01-04
Actually, poking around inside the Volume Control I find that several places show a Toggle Audio Recording button next to the Mute button...

---

### Post by derekeverett on 2010-01-04
> **jamesisin said:**
> This is not likely it, but open Volume Control and make sure microphone is not muted.

There is a device list, you can seek through that for your microphone input (or your line in) and ensure that no muting is borking matters.

I will re-check for that as soon as I can. I am in Vista right now as I need to get some work done here.

Is it possible that it could be muted AND I would still hear the audio picked up by the mic/mixer? I ask because I did find how to mute the crappy built into my monitor mic that I hate and the opposite was true, I could not hear it anymore through the headphones but it would record still if I set the input to that mic in preferences.

---

### Post by derekeverett on 2010-01-04
> **jamesisin said:**
> Actually, poking around inside the Volume Control I find that several places show a Toggle Audio Recording button next to the Mute button...

Can you send me a screen shot so I know exactly what your looking at? Are you still running 8.10? I wonder if there is a difference?

---

### Post by jamesisin on 2010-01-04
Oops.  9.10...  I really ought to rebuild this machine.

In Volume Control under Hardware, change your profile (presumably to Analog Stereo Input) then under Input find your mic input by banging a microphone until you see the meter bounce.

I suppose that was even less helpful.

---

### Post by MIJ-VI on 2010-07-15
> **derekeverett said:**
> I will re-check for that as soon as I can. I am in Vista right now as I need to get some work done here.

Is it possible that it could be muted AND I would still hear the audio picked up by the mic/mixer? I ask because I did find how to mute the crappy built into my monitor mic that I hate and the opposite was true, I could not hear it anymore through the headphones but it would record still if I set the input to that mic in preferences.

Hi derekeverett.

It's possible that you don't have permission to use audio devices under Ubuntu 9.10.

Checking permissions and resources
[https://wiki.ubuntu.com/DebuggingSoundProblems#Checking%20permissions%20and%20resources](https://wiki.ubuntu.com/DebuggingSoundProblems#Checking%20permissions%20and%20resources)

(An excerpt from...)

Debugging Sound Problems
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

---

