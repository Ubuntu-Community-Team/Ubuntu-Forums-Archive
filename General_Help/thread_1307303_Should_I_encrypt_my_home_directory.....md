---
title: "Should I encrypt my home directory...."
date: 2009-10-31
forum: General Help
---

### Post by DracoJesi on 2009-10-31
so 9.10 Beta and now the official release give you this option, but is it necessary? what are the cons here? can I still access my home directory as root?

---

### Post by DracoJesi on 2009-10-31
I shouldn't have posted a thread during the release date, you're all probably playing around with Karmic,  and those who haven't converted to ext4 prior and aren't comfortable deleting GRUB are most likely customizing :)

and those who are here are probably helping the newbies, that's ok, I can wait... I'm going to do a video tour explaining things, and I'm already running the Beta so I can take time to get used to recordmydesktop....

I plan to cover the basic things, interface, software center, synaptic ect...

I also want to attempt to show that the terminal really isn't so scary, I feel so many err....virtually all videos miss this....

I don't really want to talk about Compiz other than just mentioning it because there are plenty of other videos about it, and people tend to talk about Compiz so much everything else gets overshadowed or forgotten all-together..... if time does permit, I may talk about a plug in two that is very useful but hardly ever talked about.... like being able to group and tab windows and and perhaps magnify

I would also like to show Wine, last I checked, it wasn't in synaptic by default, but this is great... I'll show users how to add sources

and perhaps I'll add Compiz during the video, you wouldn't believe people tell me Compiz doesn't work... I say "what do you mean?", They are like, "I installed it and nothing happen" the fact that you have to run it.... (it automatically replaces Metacity as default when I install it though or that to manage it you need to install the settings manager is beyond them....   

as for compiling from source or any other method... I'm not sure that's needed in this video, what do you think?

I want it to be an informative video but not "too much", I don't want to scare people away nor do I want it to be so long it's boring....

so I ask you? what do you feel would be beneficial for new users to know?

what would you have me include?

everybody here will be up soon and getting up and ready for something, but I don't think I'll be going, and this will give me the time to work on this uninterpreted...... 

oh and one of the first things I should do is talk about how to get or try it..... that you don't have to worry about not being able to go back to Windows....

input will be greatly appreciated.... the video will probably be put on youtube, not sure were else I'd host it.... but I encourage it be used elsewhere :) and I make it available in several formats.... which format should I record in btw?

geeaz, I should change the title here......

I just saw the notice for the party, heading there now :) 

and yes, I used the torrent ;)

---

### Post by misfitpierce on 2009-10-31
> **DracoJesi said:**
> I'm going to do a video tour explaining things, and I'm already running the Beta so I can take time to get used to recordmydesktop....

I plan to cover the basic things, interface, software center, synaptic ect...

I also want to attempt to show that the terminal really isn't so scary, I feel so many err....virtually all videos miss this....

I don't really want to talk about Compiz other than just mentioning it because there are plenty of other videos about it, and people tend to talk about Compiz so much everything else gets overshadowed or forgotten all-together..... if time does permit, I may talk about a plug in two that is very useful but hardly ever talked about.... like being able to group and tab windows and and perhaps magnify

I would also like to show Wine, last I checked, it wasn't in synaptic by default, but this is great... I'll show users how to add sources

Sounds like a nice idea and a nice way to help out some on 9.10 that are new or confused with the video you plan on making... Great contribution idea :P

---

### Post by DracoJesi on 2009-10-31
> **misfitpierce said:**
> Sounds like a nice idea and a nice way to help out some on 9.10 that are new or confused with the video you plan on making... Great contribution idea :P

unfortunately though, it wont be happening until I figure this out:

```
draco@Draco-laptop:~$ recordmydesktop
Initial recording window is set to:
X:0   Y:0    Width:1280    Height:800
Adjusted recording window is set to:
X:0   Y:0    Width:1280    Height:800
Your window manager appears to be compiz


Detected compositing window manager.
Reverting to full screen capture at every frame.
To disable this check run with --no-wm-check
(though that is not advised, since it will probably produce faulty results).

Initializing...
Buffer size adjusted to 4096 from 4096 frames.
Opened PCM device hw:0,0
Playback frequency 22050Hz is not available...
Using 44100Hz instead.
Recording on device hw:0,0 is set to:
2 channels at 44100Hz
Capturing!
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.
Broken pipe: Overrun occurred.

```

I'm glad I know how to start something from the terminal because I downloaded the GUI frontend...... nowhere to be found

---

### Post by andrewabc on 2009-10-31
Only encrypt if security is necessary.

Encrypting will slow down your computer.

[Ubuntu 9.10 Home Encryption Performance](www.phoronix.com/vr.php?view=14187)

---

### Post by DracoJesi on 2009-10-31
ok so I found out it was an audio related error, and the site that told me that to run it with --no-sound to fix the problem, obviously I a little skeptical as clearly that looks like turning the sound off... but it insisted that was what I should do.... so I did

Recordmydesktop does record now, but I was right, no sound it fixed the problem technically I suppose, but it sure didn't provide a solution

I could use a second program to capture the audio, but that just doesn't sound like a good idea...

so I'll tweak my audio settings and see what happens

oh wait, I suppose I wont, because it's only listed one audio device when in Jaunty, I had 3 or 4, but I know not all of them were really audio devices, to be fair..

---

### Post by NCLI on 2009-10-31
If you encrypt your home folder, you will need a password to access it, even as root. Ubuntu gives you this password on first boot.

---

### Post by DracoJesi on 2009-10-31
ok so I think I may have found a way to get the audio to work, meanwhile I went to get my mic.... now, I can't get it to work because for some reason for input, everything is greyed out, no matter what audio profile I choose...

the ability to change application volume much easier is very nice.... but I'm starting to think that the audio preferences have undergone a major downgrade :(

ok I turned the device off and the device off and then selected the duplex profile, it is reading input from the microphone 1 connecter, accurately two, but no matter how high I turn the volume I can't hear a thing

> **NCLI said:**
> If you encrypt your home folder, you will need a password to access it, even as root. Ubuntu gives you this password on first boot.

so I cant choose my own password?

what about the configuration files in the home directory, programs need to access those, how does that work....?

---

### Post by DracoJesi on 2009-10-31
I even tried the backports, same problem.... I don't get it, it's reading the pitch, it shows there is incoming input and it matches up to when I speak.....

I've tried everything I can think of except for testing the mic itself, and it's a pretty crappy mic so if it did go out, I wouldn't be surprised....

I do noticed it shows the input constantly toward the high side, and I wasn't talking very loud at all..... so I'm starting to think the it's the mike....... I go grab something else to test the jack with....

it works on a jaunty machine, just tried...... but not well....

headphones do work

> **andrewabc said:**
> Only encrypt if security is necessary.

Encrypting will slow down your computer.

[Ubuntu 9.10 Home Encryption Performance](www.phoronix.com/vr.php?view=14187)

thanks :)

---

