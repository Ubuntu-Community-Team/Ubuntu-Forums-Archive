---
title: "Microphone not working, works under Windows"
date: 2011-07-15
forum: General Help
---

### Post by K1251 on 2011-07-15
I have an Acer Aspire One D255E netbook dual-booting Win7 and Kubuntu Natty, and basically the inbuilt microphone works in Windows but not in Kubuntu. 

I've tried running alsamixer, it's not muted. I installed pavucontrol and under input devices there are 2 options: Analogue Input and Analogue Microphone. Both of them show the volume level hovering round about nothing. But slightly above, so I dunno, noise I guess.

Any ideas how to get Kubuntu to recognise the microphone?

- K

---

### Post by dabl on 2011-07-15
With alsamixergui and pavucontrol both open, use pavucontrol to slide the volume up and down.  On alsamixergui you should be able to determine which "capture" or "front mic" channel is also moving up and down.  You might also need to use the "front mic boost", if it uses the front mic channel.

---

### Post by bodhi.zazen on 2011-07-15
Sometimes it helps to search the forums =)

[http://ubuntuforums.org/showpost.php?&p=10394028&postcount=1](http://ubuntuforums.org/showpost.php?&p=10394028&postcount=1)

---

### Post by K1251 on 2011-07-15
> **dabl said:**
> With alsamixergui and pavucontrol both open, use pavucontrol to slide the volume up and down.  On alsamixergui you should be able to determine which "capture" or "front mic" channel is also moving up and down.  You might also need to use the "front mic boost", if it uses the front mic channel.

alsamixergui only shows 2 things, 'master' and 'capture'. When the volume is changed in pavucontrol the 'capture' level moves with it. Somehow I don't think this is what you meant. Is alsamixergui meant to be displaying more than just two volume bars?

---

### Post by K1251 on 2011-07-15
> **bodhi.zazen said:**
> Sometimes it helps to search the forums =)

[http://ubuntuforums.org/showpost.php?&p=10394028&postcount=1](http://ubuntuforums.org/showpost.php?&p=10394028&postcount=1)

I did search, didn't find that. Also, the problem mentioned in that thread is completely different, so I don't see the relevance. That guy is talking about speaker output.

---

### Post by dabl on 2011-07-15
> **K1251 said:**
> alsamixergui only shows 2 things, 'master' and 'capture'. When the volume is changed in pavucontrol the 'capture' level moves with it. Somehow I don't think this is what you meant. Is alsamixergui meant to be displaying more than just two volume bars?

Right, that is what I meant.  Wow, well that's a pretty simple audio system, or else your driver might need an "option".

Try clicking the little "lock" under the "capture" channel, in alsamixergui.  In pavucontrol, make sure the "internal audio" is not muted, and click the "set as fallback" button.

Regarding driver options, see this:  [http://ubuntuforums.org/showthread.php?t=1043568&highlight=intel+sound+database](http://ubuntuforums.org/showthread.php?t=1043568&highlight=intel+sound+database)

and this: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by K1251 on 2011-07-15
> **dabl said:**
> Right, that is what I meant.  Wow, well that's a pretty simple audio system, or else your driver might need an "option".

Try clicking the little "lock" under the "capture" channel, in alsamixergui.  In pavucontrol, make sure the "internal audio" is not muted, and click the "set as fallback" button.

Regarding driver options, see this:  [http://ubuntuforums.org/showthread.php?t=1043568&highlight=intel+sound+database](http://ubuntuforums.org/showthread.php?t=1043568&highlight=intel+sound+database)

and this: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Ok, I did that, opened Audacity and there's an option in there that I don't think was there before under input device. I have 'pulseaudio', which detects no input, and now I have Intel HDA, which works.

Thing is, when I open Skype (the whole reason I want the mic to work) the only option is pulseaudio server. So, is there any way to force pulseaudio to recognise the Intel HDA input so that skype will, in turn, recognise it?

I realise this is a whole different question.

---

### Post by dabl on 2011-07-15
I can use skype with either my Logitech USB webcam or a plug in audio microphone.  The webcam is simplest (once I cracked how to preload the video part of it).  The key is, in pavucontrol, to mute the "internal audio" and then make sure to press the "set as fallback" button on the webcam.  If I don't do that, skype won't get my audio.

The plug in audio mic is different.  On that one, before every skype session, it is necessary to go into alsamixergui and click the lock on "front mic" and also click the "front mic boost" and turn it up 1/3 of the way.  Then I can launch pavucontrol and verify the volume or turn it up to about 80%, and then launch skype and I've got audio. As far as I can tell, skype will not permit you to use other than pulseaudio, if you have pulseaudio installed on your system.

You can read posts from folks claiming how helpful it is to remove pulseaudio, but that has never worked for me -- I've got it working on 2 desktops and 1 netbook, with skype on all 3 of them.  The netboook uses audio headphones and that works too.

---

### Post by enimeizoo on 2011-07-16
Removing pulseaudio did work for me, giving it a try would be cheap. It gave me a lot of options in skype, wich would only show 'pulse' option for mic, speakers and ringing. After removing pulseaudio, I could choose any jack, mic or speaker on the computer.

That said, I don't know a lot about pusleaudio, so it might have been a misconfiguration or something. So if you get it to work without removing, it is probably better.

---

### Post by K1251 on 2011-07-16
> **enimeizoo said:**
> Removing pulseaudio did work for me, giving it a try would be cheap. It gave me a lot of options in skype, wich would only show 'pulse' option for mic, speakers and ringing. After removing pulseaudio, I could choose any jack, mic or speaker on the computer.

That said, I don't know a lot about pusleaudio, so it might have been a misconfiguration or something. So if you get it to work without removing, it is probably better.

Removing pulseaudio worked, thank you! Skype now has all the options for different inputs etc.

Thanks guys, I'll mark this little mystery as solved :D

- K

---

### Post by K1251 on 2011-07-16
Actually, hold on. Having rebooted, I now have no sound. At all. Do I need an alternative to pulseaudio or something?

EDIT: I think it's because it asked me if I wanted to forget the old devices, and I pressed yes. Don't think I should have. Any way to get them back after 'permanently forgetting' them?

2nd EDIT: False alarm. What the hell is going on with this? Every time I log in my sound configuration changes, now I have like 20 different sound card options. Oh well, never mind. *marks as solved... for now*

---

### Post by LalithW on 2011-07-16
> **K1251 said:**
> Actually, hold on. Having rebooted, I now have no sound. At all. Do I need an alternative to pulseaudio or something?

EDIT: I think it's because it asked me if I wanted to forget the old devices, and I pressed yes. Don't think I should have. Any way to get them back after 'permanently forgetting' them?

2nd EDIT: False alarm. What the hell is going on with this? Every time I log in my sound configuration changes, now I have like 20 different sound card options. Oh well, never mind. *marks as solved... for now*

Try installing Default Sound Card.. you can download this from Ubuntu Software Centre.... I had the same problem on my Dell Aspire One. It worked for me.

---

### Post by K1251 on 2011-07-16
> **LalithW said:**
> Try installing Default Sound Card.. you can download this from Ubuntu Software Centre.... I had the same problem on my Dell Aspire One. It worked for me.

Thanks, I'll have a look :)

---

