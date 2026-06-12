---
title: "Missing sound modules??"
date: 2009-09-25
forum: General Help
---

### Post by vivaldibabe on 2009-09-25
After recently installing ubuntu 9.04 on my acer aspire, I found my headphone jack did not work. Then all sound went out after I tinkered with my alsa-base the other day...
After removing and reinstalling alsa-utils and alsa-base, I still can't find the problem.

I ran:

sudo modprobe

only to find that I have none of my sound modules...?? But ubuntu does recognize my soundcard, so I'm at a complete loss of what to do. Help??

---

### Post by Liolikas on 2009-09-25
If you lucky enough to remember module names you need so just:
modprobe <name>
If works add this to startup modules list manually.

---

### Post by vivaldibabe on 2009-09-25
Hm, I will look into that. THanks.
And if I can't find the specific module names?.. Is there a site I can reference, perhaps? (with any more luck)

---

### Post by fragos on 2009-09-25
The headphone jack is usually uses the same output as the PC speakers and will turn those speakers off when plugged in and direct the speaker sound to the headphones.

---

### Post by vivaldibabe on 2009-09-27
fragos-
But if I'm missing the PC speaker sound to begin with, then I won't have headphone jack sound. Any more advice about finding/reinstalling the proper modules?

---

### Post by fragos on 2009-09-27
Right click the speaker applet icon and select volume control. By default PC speaker will be mute and have volume set to 0.

---

### Post by vivaldibabe on 2009-09-28
Nope, it still thinks that all volume preferences are good to go to play something. It just won't play. I've checked anywhere and everywhere I can think of to make sure that I didn't somehow mute it... =\

---

### Post by vivaldibabe on 2009-09-28
What if I just re-installed ubuntu?
All my info is still backed-up on my external from when I installed last time, and then I would only have the headphone jack to worry about, not all my sound. 
Getting kinda discouraged here. =\

---

### Post by fragos on 2009-09-28
Right click the speaker icon and select preferences. At the top of the window is a drop down that selects the sound device controlled. There will be a number of choices. Try the one with (Alsa mixer) instead of (Pulse Audio). In my case I use the 1st one in the list which is "VIA 8237 (Alsa mixer)". You may have a different sound chip set so you may not have VIA like me.

---

### Post by vivaldibabe on 2009-09-28
Alrighty, I see where I should have more than one option- but I don't.
Under the device options drop-down I only have Pulseaudio under playback...

---

### Post by fragos on 2009-09-28
The only other thing I can think of is to open sound preferences and run the test trying whatever options are offered. I'm not sure the playback choice is what you want, it's not what I'm using.

---

### Post by vivaldibabe on 2009-09-28
I tried all the tests with all possible options.. and nothing works.
BTW, I really appreciate this. I know we noobs can be a pain in the neck at times. :lolflag:

And what exactly is the difference in playback and capture here? I feel as if I'm missing lots of the picture here, sigh.

---

### Post by fragos on 2009-09-28
Capture probably refers to sound stored as in Line-in. I have options for Capture and Playback as well as for the device without specification of what purpose. I use the generic one that was selected by default during install of Ubuntu. I for one am running out of suggestions. What I suggested has always worked for me. I wish I could have been more helpful. The title of your post may be limiting those that might have suggestions. Your problem may not have anything to do with missing modules and just to a lack of sound.

---

### Post by vivaldibabe on 2009-09-28
I did lose sound after playing with my modules, however. 
That is to say, I lost my internal speaker sound after that; my headphone jack/external speakers weren't working and I never got them to work. =(

Maybe I'll try reposting with a broader title.

---

