---
title: "Why has their been no fix????????/"
date: 2010-06-05
forum: General Help
---

### Post by ibe2fly4chu on 2010-06-05
well i am sitting here, checking on my earlier threads and yet still no one has replied helping me fix my no sound issue after logging into ubuntu. From prior searches it seems its a problem that is happening in ubuntu's updates. Why hasnt there been a fix for this in their updates yet...and also anyone care to help me currently fix this issue?

When i start ubuntu i hear the drums on the login screen. however after logging in there is no audio from flash videos or any music files i try to play. I did check in terminal and it seemed my card was being recognized. 

my card is: rd 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by Dayofswords on 2010-06-05
[QUOTE=time from your thread start]11 Hours Ago [/QUOTE]
i have a [thread going from a few months ago]("http://ubuntuforums.org/showthread.php?t=1418834") with no one knowing the answer yet

[LIST=1]
[*]we are users, not tech support from a big company getting paid
[*]we are also not know-it-alls, we may or may not know how to fix your issue. we can probably help you with an issue we have had
[*]the internet is not your personal tech support army
[*]11 hours is hardly anything
[/LIST]

---

### Post by Rodney9 on 2010-06-05
This might help - [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by ibe2fly4chu on 2010-06-06
@Dayofswords:
first of all nobody expected the internet to be their personal tech support. And we are users blah blah thats the kind of attitude that dont get things fixed. I was clearly just asking if its a known bug why havent the developers issued a fix yet. As far as it goes if you dont feel the need to state a helping answer just dont bother to post a reply...i mean, really...even if you stated your point and then even try to point me int he right direction it wouldnt have been so bad. You think i get paid for my answers on here? no. So next time before posting smart remarks pay attention to the the post.

---

### Post by ibe2fly4chu on 2010-06-06
went through that entire guide...did every form of troubleshooting on it. Even uninstall and reinstall all the sound drivers/modules. Still no luck.  Any more suggestions?

---

### Post by diablo75 on 2010-06-06
So, just to be clear (based on what you said about the problem in previous posts).  You hear the drums at the login screen, where you're asked to type in a username and password, but then hear no sound from that point on.  No "Splash" sound with that choir and snapping fingers and crickets in the wind, and nothing else, right?  I'm not certain, but I'm thinking PulseAudio doesn't come into use until after the login screen, so if my guess is correct, something else (maybe ALSA) is used to pipe the sound output to the sound card until after you've logged on.

If that's the case, and if my assumptions are correct, then the problem has something to do with PulseAudio.  Something you should check after logging in is to see what PulseAudio's output settings say.  To do this:

1.  Left-Click on the little speaker/volume icon once to pop-out a little drop down menu that shows "Mute", a volume slider and option that says "Sound Preferences..."

2.  In this window are at least 5 tabs across the top:  Sound Effects, Hardware, Input, Output and Applications.  While you're here, make sure the slider at the top is somewhere in the middle and the mute box is unchecked.

3.  Click on the Hardware Tab first.  You might have multiple audio devices listed here if you have a webcam or something, so be sure you click once on your soundcard chipset to highlight it.

4.  Below the hardware listing box, there is an area called "Settings for the selected device:" with a pop-out box called "Profile:".  This is where you can tweak the way sound is output from your sound card.  Do you want it to be just a two-channel stereo analog output, or do you want it to use the digital output instead (won't work if you don't have a digital output on your card, but can still be selected by accident).  Do you want to include the microphone input with your output in the profile (aka, "Duplex"), do you want to have up to 7.1 channel analog surround sound with digital outputs enabled (if available) and the microphone, etc. etc.;  there are a LOT of options, but not all of them will work correctly.

5.  Experiment with the profile selection in the hardware tab:  Get an mp3 and start to play it in the background while shuffling through the profile listings to try different ones out; maybe you'll find one that works.

6.  If you never hear anything, check your applications tab to see if the audio playing application you started a few steps earlier is being muted, or see if the app itself is muting it's own output to the sound server.

This is really all I have to suggest for this problem.  I've had my problems with PulseAudio in the past and have run without it in the past.  It's easy to remove but a little bit of a pain to adapt to the alternative (having to install alsa mixer to replace the one that goes missing; unable to change your global audio settings which means some applications have to be manually reconfigured to use ALSA instead of Pulse by their default, etc.)  You might try this experiment:

With all applications closed, open a terminal window and type:

```
pkill pulseaudio
```

This will kill the pulseaudio process.  Once that's done, open an application for producing sound and see if it works.  If it does... well, then we're at least getting closer to finding a solution.


Also, off topic:

In my experience, you'll get the highest number of eyes reading your post if it fits in the Absolute Beginner forum, and quite frankly, I'm surprised by how much stuff I would consider "Advanced" is found there (in other words, feel free to post just about anything in there).   From looking at your history, you've only posted questions about the issue you are having in General Help and Installation & Upgrades forums, which don't get as much traffic and aren't as good a place to post about an audio issue like you're having.  So if this thread doesn't pan out a solution for you, try the Absolute Beginner forum or better yet, the Multimedia & Video forum.

---

### Post by ibe2fly4chu on 2010-06-06
Thanks for the advice diablo75. I shuffled through all the profiles provided ( there was but one lol) while playing an mp3 in the background. STill no luck though T.T..but i do think you are on to something about pulse audio...i am a bit affriad to uninstall it because i might not get it working like it supposed to be when i re install it. And by the way, your re-iteration of my problem is EXACTLY what is happening. Again, thanks for the adivice^^

---

### Post by Spr0k3t on 2010-06-06
> **ibe2fly4chu said:**
> When i start ubuntu i hear the drums on the login screen. however after logging in there is no audio from flash videos or any music files i try to play. I did check in terminal and it seemed my card was being recognized.

I've had the same problem with the same hardware once before during an upgrade.  Following the link Rodney posted will fix the issue.  It's the main sticky in the multimedia/video forum, so it's not hard to find.  Another really solid bit of information to look through is on the [Ubuntu Help Wiki](https://help.ubuntu.com/community/SoundTroubleshooting)

Essentially, pulseaudio is working fine... just the rest of the software needs to be configured.  Regarding your main question of topic, it's not a high priority fix since there is a known workaround.  Therefore, it could go for a whole release (10.04) lifecycle without a solid "fix".  There is a bug, but it's dormant.  As it stands, bugs that render a system completely unusable should be fixed prior to issues that have known workarounds.

---

### Post by diablo75 on 2010-06-06
> **ibe2fly4chu said:**
> Thanks for the advice diablo75. I shuffled through all the profiles provided ( there was but one lol) while playing an mp3 in the background. STill no luck though T.T..but i do think you are on to something about pulse audio...i am a bit affriad to uninstall it because i might not get it working like it supposed to be when i re install it. And by the way, your re-iteration of my problem is EXACTLY what is happening. Again, thanks for the adivice^^

I edited my post while you were replying so you might have missed something I added...  Try killing pulseaudio temporarily with the command I put near the bottom and experiment with it out of the way to see if ALSA works.  Best app for experimenting is probably VLC because it's easy to edit it's advanced output settings (e.g., force it to use ALSA instead of Pulse).

---

### Post by marcoftheknight on 2010-06-06
Sound is tough to get perfect actualy Im running my surround sound system off of ubuntu and its working perfectly with spdif but I do have one issue the other sound outputs stopped working like the headphone ouput not that it matters cause I can just plug my headphones into the reaceiver but my receiver is pretty how running.

So Ill have to figure that out at some points now to solve your problem:

thank you to the following user who created this sound guide excellent work
FOLLOW THIS:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

it worked like a charm for me all I had to do is make little effort and little hacking enjoy.

thanks

---

### Post by sdennie on 2010-06-06
If it's a bug that multiple people are having with a stock configuration, it's probably been reported on [https://launchpad.net/](https://launchpad.net/).  If it hasn't been reported, I encourage you to report it.  The forums are an official part of Ubuntu but, they aren't the part of Ubuntu that causes bug fixes to be issued.

---

### Post by ibe2fly4chu on 2010-06-06
That command indeed killed pulse audio. However vlc still didnt provide any output. As for the guide Spr i followed it like 2 times. I actually had all what i should have ( the correct output and all) that were refereed to in the guide. Il follow it one more time i guess just to see if i catch anything new. But yea...still no sound T.T

EDIT:
While playing an mp3 and streaming a youtube video i checked the application on the sound preferences. What shows up there is the ALSA plugin. However at the same time i was monitoring system montior and pulseaudio was still asleep. Just noting an observation, not sure if it is good info that changes anything

---

### Post by ibe2fly4chu on 2010-06-06
while searching i came across a thread that suggested to delete the ".pulse" file and reboot. Does anyone know where that specfic file is located?

---

### Post by tgm4883 on 2010-06-06
> **ibe2fly4chu said:**
> while searching i came across a thread that suggested to delete the ".pulse" file and reboot. Does anyone know where that specfic file is located?

It's a hidden file in your home directory. Have you opened a bug report?

---

### Post by Rubi1200 on 2010-06-06
Have you tried this?

[http://ubuntuforums.org/showpost.php?p=9315844&postcount=26](http://ubuntuforums.org/showpost.php?p=9315844&postcount=26)

---

### Post by ibe2fly4chu on 2010-06-06
Thanks i found it. Unfortunately it still didnt fix the problem. Also no i have no reported the bug yet..someone mentioned that if there is a known work arround (which everyone keeps telling me there is lol) then it most likely wont have any updates with a bug fix. At this point though i really am debating windows 7 or something...

Update: @ Rubi1200...yes i did try that. Numerous troubleshoot guides suggested it, and i did just now as you mentioned it as well. Everything in there is turned on and master and headphones are at maximum ( red )

---

### Post by Rubi1200 on 2010-06-06
Sorry to hear that. By the way, maybe I missed it but what version are you running?

Are you willing/do you think reinstalling might fix the problem?

I have found that a fresh install helps *sometimes*

---

### Post by ibe2fly4chu on 2010-06-06
oh i am on ubuntu 10.4. I did a fresh install about 5 times now. It does work at first, however after you run updates and install adobe flash (or somewhere in between doing all of that) the sound just completely stops working. I had a extra sound card just laying arround. i just installed it...still no sound. This just guarantees its not a hardware problem. I am virtually out of ideas.

Oh also: i am really trying not to reinstall everything one more time. I spent a good day custamizing/upgrading the system just the way i wanted it. Everything is perfect...except sound that is.

---

### Post by Mic[RSA] on 2010-06-06
You and me as well.

My windows had problems with a my headphones (blue scree), so I decided to use Linux Ubuntu as my main music players.

At first it worked (after I tried for a while to get it to work) then this weekend I (or a friend, can't remember :P ) Removed the USB headphones. After that it didn't work anymore. The main speakers (it is a laptop) still plays the music fine but not through the headphones. I also plugged it into a friends PC to see if it wasn't maybe the headphones that didn't work, but they do work. I also don't know what to do. I run Ubuntu, with KDE in the background, but haven't found a way to make it work again.

Last time I inserted my headphones I got a message stating that the usb headphones aren't working and its resetting to the back up sound device. I really don't know what to do. Is there a driver I should download maybe?

---

### Post by Rubi1200 on 2010-06-06
> **ibe2fly4chu said:**
> oh i am on ubuntu 10.4. I did a fresh install about 5 times now. It does work at first, however after you run updates and install adobe flash (or somewhere in between doing all of that) the sound just completely stops working. I had a extra sound card just laying arround. i just installed it...still no sound. This just guarantees its not a hardware problem. I am virtually out of ideas.

Oh also: i am really trying not to reinstall everything one more time. I spent a good day custamizing/upgrading the system just the way i wanted it. Everything is perfect...except sound that is.

I understand about not wanting to reinstall, especially once you have things set up the way you want. 

I hope you find a solution soon.

---

### Post by ibe2fly4chu on 2010-06-06
well its not a fix really but i did reformat and install for the 6th time. I did most of my customization WITHOUT running ubuntu updates. Sound is working fine so far..going to restart a couple times just to make sure. As far as ubuntu updates go...i think il just not run them.  lol at least till i can figure out which ones are individually for sound and deselect them. 

So just a recap: Clean install. Do whatever you want but DONT run updates (sudo apt-get update).

Update:
ok...so i restarted...sound stopped working again. siiiigggghhhhhh. so its not the updates after all. Thanks for all the help...lol back to windows!

---

### Post by ibe2fly4chu on 2010-06-06
Alright! I have been messing around with everything and finally found the problem. It isnt adobe flash or ubuntu updates. Its the graphic card!. you see, whenever i choose a driver that is suggested by "Hardware"...the driver becomes active however the sound vanishes. If i uninstall the all the video drivers (i am only given 2), the sound comes back and works perfectly. The thing is in doing so you cant use any desktop effects etc. Well now that we definately know what the problem is...any new suggestions or work arround?^^ oh yea, i did re-install ubuntu karmic, so now i am on 8.10. However i am alsmost sure this was the problem in 10.4 as well. I shall be re updateing (*stab myself*) to 10.4 to confirm.

UPDATE: Yes. Confirmed on 10.4. After installing graphic drivers from the "hardware menue", the sound stops working. If both suggested drivers are left unactivated..then the sound works fine. New question: lol does anyone know a work arround?

---

### Post by tgm4883 on 2010-06-07
> Re: **Why has their been no fix?**???????/

> **ibe2fly4chu said:**
> Thanks i found it. Unfortunately it still didnt fix the problem. Also **no i have no reported the bug yet**..someone mentioned that if there is a known work arround (which everyone keeps telling me there is lol) then it most likely wont have any updates with a bug fix. At this point though i really am debating windows 7 or something...

Update: @ Rubi1200...yes i did try that. Numerous troubleshoot guides suggested it, and i did just now as you mentioned it as well. Everything in there is turned on and master and headphones are at maximum ( red )

It's hard to fix bugs without knowing about them.

---

### Post by ibe2fly4chu on 2010-06-07
Yea. If my game works without those drivers il just call it and be happy. lol installing it right now to see. while listening to music :)

---

