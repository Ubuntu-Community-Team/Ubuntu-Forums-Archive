---
title: "Ubuntu 9.10 mic problem help please"
date: 2010-01-28
forum: General Help
---

### Post by tonytouch0099a on 2010-01-28
I  have an external mic that i am trying to use but its not working.  is there some plugin that i need to have?  it works on other computers that have windows.  the mic plugs into the microphone jack its not an onboard mic or a usb.  if anyone could help that would be really great

---

### Post by marshmallow1304 on 2010-01-28
Did you check your sound settings?

System->Preferences->Sound
Check the Input tab.  Experiment with the Volume, Connector, and Device settings there.

---

### Post by tonytouch0099a on 2010-01-28
i dont a connector option or device settings.  is there a way to get those options?

---

### Post by marshmallow1304 on 2010-01-28
> **tonytouch0099a said:**
> i dont a connector option or device settings.

This is 9.10, correct?
Press Alt+F2, type gnome-volume-control and hit enter.  Is that the same as System->Preferences->Sound ?

If yes, upload a screenshot of the dialog on the Input tab.

---

### Post by ~dr,j on 2010-01-29
hey all~
i'm having the same problem. i had to make a new user account a few days back, now in the new account (the old one got screwed up [but the mic input still worked there]) the mic no longer works.

i've tried running a line cable from my ham radio to the mic/line in and get nothing, i also tried a headset (i use for skype and echolink) and also get nothing.

i opened the sound program (the one you mentioned) and i have selections under 'input' for mic 1, mic 2, and line in. (i have dual entergraded mics that have never worked in ubuntu) and even if i crank the 'input volume' to max i can't get it to work.

any idea's/advice would be awesome! thanks in advanced!

~j

p.s.
i'm using ubuntu karmic (9.10) 32 bit edtion. if it would help to know the cpu/ram/laptop model etc lemme know :P

---

### Post by marshmallow1304 on 2010-01-29
You might also try messing around with the Profile on the Hardware tab.

---

### Post by Smaulsnet on 2010-01-29
I too am having this problem. I have checked my audio settings as well as alsamixer and have not found anything that appears to be out of place. I have tried my onboard sound card and a pci sound card SB audigy se both seem to be detected properly but I still can't get the input to work on either. Tried all input ports on both cards and front panel and even tried a second headset thinking mine might be broken. 
 
Any help would be appreciated.
 
This is ubuntu 9.10 x64

---

### Post by ~dr,j on 2010-01-30
marshmallow~
i looked at the hardware tab, i have only have the 1 device option. i do however have 3 profiles:
analog stereo input
analog stereo output
analog stero duplex

i would assume input would put it to where just the input devices (mic's line in etc) would work....output for speaker/headphones out...and duplex would do both....is this correct? 

also, i booted into micro$uck win. 7 to test the line in/mic jack and it DOES work fine there....so i eliminated the jack as the problem so sadly it's gotta be some setting....
hope with the forums help this can get figured out! (i always have found our user forums a great resource! nice, patient and kind knowladgable people! i'm soo glad i converted to ubuntu way back in the dapper days :P)

~j

---

### Post by edanto on 2010-01-30
I'm having a similar problem - but I'm not quite sure of how Ubuntu is supposed to be configured for sound.

I moved over completely to Ubuntu just a week or two ago and everything works great except when I put a headset into use skype then (1) the mic doesn't work and (2) sound continues to come out of the speakers as well as the headphones.

I went into the System/Preferences/Sound and tried to experiment with everything... but I don't know the difference between the different options in Input Device etc.  Where can I find some guidance about that, please?

---

### Post by Smaulsnet on 2010-01-30
I have somewhat resolved my issue with my mic. In my case I found my mic was working but was just to quiet to record. I use the alsamixer to turn up my mic boost a little and it made a small difference. My problem now is that I am only able to record from my mic or use skype is with my mic boost turned all the way up. That would be fine but with settings to that extreme the background noise is almost unbearable. 
Hope this helps.

---

### Post by tonytouch0099a on 2010-01-30
yes i am using 9.10

how do i upload a picture for you to see

---

### Post by tonytouch0099a on 2010-01-30
here is a screen shot of the input tab

---

### Post by edanto on 2010-01-30
I have something very similar.  It looks like it should make sense.... it just doesn't.

Like...which one of these inputs should I choose? Does it make a difference? Do I have to change it if I want to record a streaming radio show? 

But I suppose the first question is, how do I get a clean mic sound for skype!?  Any help from more experienced Ubunters would be much appreciated.

---

### Post by edanto on 2010-02-02
No answers?  

Let me clear up the question I have.  What settings do I change so that my mic will work?

thanks!

---

### Post by edanto on 2010-03-13
I'd really appreciate any help that people could give me with this, or if you could say where I might find out?

---

### Post by alexsimps on 2010-04-12
I have the same problem (on dell 1420) way too quiet even after i maxed out every mixer i could find. Check out and see if you can make any sense of this maybe? [https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/275998](https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/275998)

---

