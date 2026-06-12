---
title: "Why is Audacity messed up?  Screenshots included."
date: 2006-06-17
forum: General Help
---

### Post by KillrBuckeye on 2006-06-17
I installed Audacity via Automatix, and it appears to be screwed up.  Look at the screnshots I attached.  If I go to Help => About Audacity, I can't even see any text.  The pull-down menu for the selected recording device (next to the record volume slider) is non-functional as well, meaning that I can't even make a multi-track recording project.  What is going on?

---

### Post by reclusivemonkey on 2006-06-17
[QUOTE=KillrBuckeye]I installed Audacity via Automatix, and it appears to be screwed up.  Look at the screnshots I attached.  If I go to Help => About Audacity, I can't even see any text.  The pull-down menu for the selected recording device (next to the record volume slider) is non-functional as well, meaning that I can't even make a multi-track recording project.  What is going on?[/QUOTE]

I installed Audacity via Synaptic and it works fine. My "About" looks like yours, but the rest is fine and I have had no trouble with multi-track recording projects;

[http://www.reclusivemonkey.com/images/Screenshot-24.png](http://www.reclusivemonkey.com/images/Screenshot-24.png)

---

### Post by maniacmusician on 2006-06-17
> **reclusivemonkey]I installed Audacity via Synaptic and it works fine. My "About" looks like yours, but the rest is fine and I have had no trouble with multi-track recording projects said:**
> http://www.reclusivemonkey.com/images/Screenshot-24.png[/url]

don't want to detract from the topic of the thread, but how did you get your bottom panel to look like that?

---

### Post by KillrBuckeye on 2006-06-17
Well, I think Audacity is actually working fine.  It's just that the SB Audigy drivers behave differently in Ubuntu.  I can't select a recording device in the application.  Instead, I need to manually adjust the record volumes in ALSA mixer.  The problem I have now is that I can't get the levels high enough even with everything maxed out (guitar, guitar preamp, Audigy record levels, Audacity record level).  :(  See this thread:

[http://ubuntuforums.org/showthread.php?t=198626]("http://ubuntuforums.org/showthread.php?t=198626")

Any help you could provide would be greatly appreciated!

---

### Post by reclusivemonkey on 2006-06-18
[QUOTE=maniacmusician]don't want to detract from the topic of the thread, but how did you get your bottom panel to look like that?[/QUOTE]

I removed everything from the bottom panel, made it totally transparent, increased the size to 48 pixels, unticked "Expand" and then just added the applets/applications I wanted.

---

### Post by reclusivemonkey on 2006-06-18
[QUOTE=KillrBuckeye]It's just that the SB Audigy drivers behave differently in Ubuntu.[/QUOTE]

Differently into Ubuntu to what? Have you tried and other Linux distros? There are several that are specifically geared towards music recording, if this is all you use this computer for, you may want to take a look at those.

[QUOTE=KillrBuckeye]I can't select a recording device in the application.  Instead, I need to manually adjust the record volumes in ALSA mixer.  The problem I have now is that I can't get the levels high enough even with everything maxed out (guitar, guitar preamp, Audigy record levels, Audacity record level).[/QUOTE]

Firstly you need to work out whether its just Audacity which isn't working correctly. You can record directly from your soundcard using "arecord", which is a basic command line recording tool from alsa. I would take a look at "man arecord", amd use the example they give at the bottom ; 

```

arecord -d 10 -f cd -t wav -D copy foobar.wav
              will  record  foobar.wav  as  a 10-second, CD-quality wave file,
              using the PCM "copy" (which  might  be  defined  in  the  user’s
              .asoundrc file as:
              pcm.copy {
                type plug
                slave {
                  pcm hw
                }
                route_policy copy
              }

```

You can then play this with aplay and see how the levels are. I'm no sound/Ubuntu expert (I have come from Slackware for this release of Dapper), but I have been recording some simple podcasts for the world cup with Audacity and a Sound Blaster Live and not had any trouble.

---

### Post by KillrBuckeye on 2006-06-18
Through my searching, I have found others who had complaints about the Audigy 2 card for multitrack recording in Ubuntu.  For some reason in Ubuntu, there is no way to choose which channel you want to record, i.e. line in, mic, analog, etc.  Instead, you have to completely turn down the capture volumes on everything except the channel you want to capture.  If this is not done, then any recording application will capture *everything* that is going through the card.  So if I am doing a multitrack recording project, the previously-recorded channels that I use for "cue" will be copied to a new channel that I am trying to record.  This is different than in Windows, which allows me to select the channel to capture and it will only recorded that signal to disk.  I presume it is the Creative driver that allows me to do this.  That is my understanding at this point.

Here is a blurb taken from UbuntuStudio.com about the Audigy 2 card:
Source: [http://http://ubuntustudio.com/wiki/index.php/Audio_Hardware#Creative_Audigy2_ZS_PCI_Sound_Card]("http://ubuntustudio.com/wiki/index.php/Audio_Hardware#Creative_Audigy2_ZS_PCI_Sound_Card")
> Creative Audigy2 ZS PCI Sound Card

The ALSA Mixer for this card is frustrating because of how the analog sources are mixed together. I've contemplated pulling the card and putting in the SB Live! 5.1 again for the decent mixer controls. Otherwise, this card has been great. Every time I start Audacity, I need to change the PCM capture level back to 0, otherwise I get a bouncing effect where any audible tracks get recorded into the new one when I hit Record (and as you know, you don't need the "bounce" feature with PC-based digital multitracks). 

I am very new to Linux, and I use this computer for a bit of everything, including gaming, multimedia, and recording.  I really like what I've seen of Ubuntu so far, and I'd like to believe that it can do just about everything that Windows can do.  That's why it's really bothering me that I can't figure out how to resolve this problem.

---

### Post by reclusivemonkey on 2006-06-18
Did you try arecord as I suggested?

---

### Post by KillrBuckeye on 2006-06-18
[QUOTE=reclusivemonkey]Did you try arecord as I suggested?[/QUOTE]I get the following error when I try the command you suggested:

```
ALSA lib pcm.c:2090:(snd_pcm_open_noupdate) Unknown PCM copy
arecord: main:533: audio open error: No such file or directory
```

---

### Post by reclusivemonkey on 2006-06-18
[QUOTE=KillrBuckeye]I get the following error when I try the command you suggested:

```
ALSA lib pcm.c:2090:(snd_pcm_open_noupdate) Unknown PCM copy
arecord: main:533: audio open error: No such file or directory
```[/QUOTE]

Did you create the .asoundrc file?

---

### Post by KillrBuckeye on 2006-06-18
You'll have to forgive me as I'm still a Linux noob.  I created a file called .asoundrc with the following text:

pcm.copy {
                type plug
                slave {
                  pcm hw
                }
                route_policy copy
              }

Now if I run the arecord command, it just sits there.  I waited more than 10 seconds, but it still didn't respond.  I pressed to Ctrl+C to cancel, but I didn't see any .wav file in my home directory.

---

### Post by reclusivemonkey on 2006-06-18
[QUOTE=KillrBuckeye]
Now if I run the arecord command, it just sits there.  I waited more than 10 seconds, but it still didn't respond.  I pressed to Ctrl+C to cancel, but I didn't see any .wav file in my home directory.[/QUOTE]

If everything is correct, you should see arecord report that it is working;

```

luke@mother:~$ arecord -d 10 -f cd -t wav -D copy foobar.wav
Recording WAVE 'foobar.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
```

---

### Post by KillrBuckeye on 2006-06-19
Well I don't know what's going on with "arecord", but Audacity works fine in terms of recording signals.  I can record any system sounds, or an internet radio feed for example, and the levels are just fine.  The problem seems to be only with the volumes I can achieve using the analog inputs of the Audigy 2 Platinum ZS front panel.

I posted on the Creative forum, and somebody found this bug tracker item for ALSA.  It's still an open issue, so it appears I'm not going crazy.  Looks like I'll need to stick with Windows for recording until this issue is resolved or I get some different audio hardware.

FYI: You can just use the "Guest login" to view the following page without signing up.
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=324]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=324")

---

### Post by arphe_el on 2006-06-19
it's good you have installed it please let me know how do you install it from the scratch including saving audio to mp3s.

thank you and GODspeed!

Best regards,


arphe_el

---

