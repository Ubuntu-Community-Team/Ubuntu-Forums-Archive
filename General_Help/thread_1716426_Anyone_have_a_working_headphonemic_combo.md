---
title: "Anyone have a working headphone/mic combo?"
date: 2011-03-28
forum: General Help
---

### Post by Duke_N on 2011-03-28
If yes , please consider replying to this post. I'm got 2 hairs left trying to get my friggin headet working. My machine multi-boots into various OSs - headphones works in XP no problems. Also on PC-BSD.

I prefer Xubuntu, but what a PITA setting sound up!! :)

Would be much obliged for any help/
--
Duke

---

### Post by Lateralis on 2011-03-28
I think you may need to be more descriptive of your problem.  Headphones and microphones should just work as they are not exactly technical pieces of kit.  (Technically they are transducers which converts one signal into another, i.e. electrical pulses into sound or sound into electrical pulses.)  If you are having trouble listening to sounds through headphones or recording sounds through a microphone then in all probability there is a problem with either your hardware or the drivers.

---

### Post by Duke_N on 2011-03-28
> **Lateralis said:**
> I think you may need to be more descriptive of your problem.  Headphones and microphones should just work as they are not exactly technical pieces of kit.  (Technically they are transducers which converts one signal into another, i.e. electrical pulses into sound or sound into electrical pulses.)  If you are having trouble listening to sounds through headphones or recording sounds through a microphone then in all probability there is a problem with either your hardware or the drivers.

You missed the part of my original post where I state that my headphone/mic combo WORK in Windows XP.  So, the problem is not with the hardware, soundcard, or anything like that. It's an Xubuntu hardware config issue.

Do you have a  working headphone/mic combo? My headphones emit sound, OK in Xubuntu, The mic does not work with any of the settings that I've tried.
--
duke

---

### Post by Lateralis on 2011-03-28
I didn't miss that part of your post, but I may have misinterpreted the point of your post.  That is, I originally read your post as you saying Ubuntu doesn't agree with your headphones or microphone, which is not possible.  The problem will be with your computer's sound card/hardware.  So, what hardware do you have?  What is the make and model of your sound card?

---

### Post by Duke_N on 2011-03-28
> **Lateralis said:**
>   The problem will be with your computer's sound card/hardware.  So, what hardware do you have?  What is the make and model of your sound card?

There is NO problem with my sound card! :) It works perfectly with 2 other Operating Systems.

It is a built-in VIA3059. 

Windows XP reports the following as well: 

AC97 Codec: ALC650

That's all I know about it. So far ...
--
Duke

---

### Post by vivek.pandey on 2011-03-28
so you dont get sound from your headphones?
have you tried system->preferences->sound->output->analog headphoes?
though it should work with speakers too but try this

---

### Post by Duke_N on 2011-03-28
> **vivek.pandey said:**
> so you dont get sound from your headphones?
have you tried system->preferences->sound->output->analog headphoes?
though it should work with speakers too but try this

I DO GET  sounds from the headphones! The mic on the headphone set does NOT work under Xubuntu.  The MIC!
--
Duke

---

### Post by Solarlease001 on 2011-03-28
I have almost same type of issue.May be I got solution Sticking this thread about mic

---

### Post by Duke_N on 2011-03-28
> **vivek.pandey said:**
> so you dont get sound from your headphones?
have you tried system->preferences->sound->output->analog headphoes?
though it should work with speakers too but try this

BTW, I don't see

system->preferences

on my system!  I'm running Xububtu 10.10

---

### Post by LostFarmer on 2011-03-28
Had the same problem till I noticed a switch on the head set cord that had the mic off.  I am using Ubuntu and under sound preferences /hardware "Analog Stereo Duplex" and for Input have "Analog Microphone/Microphone 1"  . Clicked on the sound Icon in top bar to get sound preferences.  I am using it for skype.  Hope info helps, I know different desktops will be different.

---

### Post by Duke_N on 2011-03-28
> **LostFarmer said:**
> Had the same problem till I noticed a switch on the head set cord that had the mic off.  I am using Ubuntu and under sound preferences /hardware "Analog Stereo Duplex" and for Input have "Analog Microphone/Microphone 1"  . Clicked on the sound Icon in top bar to get sound preferences.  I am using it for skype.  Hope info helps, I know different desktops will be different.

I wish it was as easy as forgetting a MIC switch ;) Don't have one of those on the cord. Onlly a volume control and mute for the earphones.

I finally discovered how to get at the sound preferences => right clicking on the speaker or mic icon(s) in the "Notification Area".  No joy! BTW, that is exactly the kind of feedback I was looking for. Thanks.  Could you tell me what settings you see when you run "alsamixer" from a Terminal window - or its GUI?  Much obliged!
--
Duke

---

### Post by LostFarmer on 2011-03-28
> Onlly a volume control and mute for the earphones. That what I was thinking about the switch till I change it.

As for 'alsamixer'  "what ever it is" :
Card: Intel ICH5
Chip: Analog Devices AD1985
Then it has some upright colored displays with MASTER at 100, Master M at 0, Master s at 0, Headphone as "mm" , Pcm=84, Surround=100 ,center=100.  Have no idea what I'm looking at.

I did have to try different setting for hardware.  My Motherboard is a ANUS P4P800

---

### Post by Duke_N on 2011-03-28
> **LostFarmer said:**
> That what I was thinking about the switch till I change it.

As for 'alsamixer'  "what ever it is" :

[snip]

Then it has some upright colored displays with MASTER at 100, Master M at 0, Master s at 0, Headphone as "mm" , Pcm=84, Surround=100 ,center=100.  Have no idea what I'm looking at.


Mine is almost the same, except that "Headphone" is not showing up. Just  "mic".

Did you have to install the headphone anywhere?

BTW, I'm in Alberta - not too far from Idaho :) Thanks.
--
Duke

---

### Post by Duke_N on 2011-03-28
> **hollandmonster said:**
> this what I want to say.
This is what I have:
[http://www.google.com/search?q=headphone+mic+combo&num=20&hl=en&newwindow=1&client=mozilla&prmd=ivns&source=univ&tbs=shop:1&tbo=u&sa=X&ei=zFaRTbyEPYm-tgfnsMxn&ved=0CC0QrQQ](http://www.google.com/search?q=headphone+mic+combo&num=20&hl=en&newwindow=1&client=mozilla&prmd=ivns&source=univ&tbs=shop:1&tbo=u&sa=X&ei=zFaRTbyEPYm-tgfnsMxn&ved=0CC0QrQQ)

Do you see that there is a Microphone as well as earphones?

The output to earphones  => work OK
The input from Microphone =>  NOT work

I do NOT HAVE:

system->preferences->sound

in Xubuntu.  No where does "analog headphones" show up!

Does **anybody** use Xubuntu here on this forum????

---

### Post by bodhi.zazen on 2011-03-29
xubuntu (xfce) uses xfce4-mixer =)

[http://www.xfce.org/projects/xfce4-mixer](http://www.xfce.org/projects/xfce4-mixer)

[img]http://www.xfce.org/images/projects/screenshots/xfce4-mixer.png[/img]

You can add it to your panel or you can call it from the command line.

I use headphone / microphone often and in general, what you have been told in this tread is often the case.

In general the problem tends to be either :

1. Your microphone is muted or not active. You can activate it in a mixer, alsamixer if needed.

2. Linux does not recognize your sound card.

3. Some applications, skype for one, can have a problem.

It would be rare that the microphone itself, and not the sound card, or one of the other 3 items above, is the problem.

Can you try another sound card ? Can you try another microphone ?

Another potential problem, although it sounds unlikely, is your microphone connected properly ? 

Don't laugh, but I once spent a few hours trying to debug a sound issue and it turned out my 2 year old had "re wired" the connections.

---

### Post by d3v1150m471c on 2011-03-29
how does the device actually connect to the computer. like, do the headphones go into the output jack and the mic in the input, or is this usb...? if they don't connect like i mentioned you'll probably need a driver for them for linux if it's even made.

---

### Post by Duke_N on 2011-03-29
> **bodhi.zazen said:**
> xubuntu (xfce) uses xfce4-mixer =)

[snip]

You can add it to your panel or you can call it from the command line.

What is curious is that the alsamixer **does not** show "Headphone" as it does on your system

> 
I use headphone / microphone often and in general, what you have been told in this tread is often the case.

In general the problem tends to be either :

1. Your microphone is muted or not active. You can activate it in a mixer, alsamixer if needed.Microphone is not muted when used with  Windows XP or PC-BSD. Doesn't show up in alsamixer.


> 2. Linux does not recognize your sound card.The earphones on my combo work just fine! I can listen to music all day long. I agree that Linux is not detecting the headphones, or they are not installed properly.

> 3. Some applications, skype for one, can have a problem.I don't use Skype! I've been testing with:

gnome-sound-recorder 2.31.6


> It would be rare that the microphone itself, and not the sound card, or one of the other 3 items above, is the problem.

Can you try another sound card ? Can you try another microphone ? The sound card is built into the mobo. I have no other. Microphone  works - for sure!

> Another potential problem, although it sounds unlikely, is your microphone connected properly ? 

Don't laugh, but I once spent a few hours trying to debug a sound issue and it turned out my 2 year old had "re wired" the connections.As I've said, the microphone works just fine in XP and PC-BSD. Somehow, Linux is not detecting the headphone. Is their a way to nuke **all** the sound support in Xubuntu, and then re-install it again? Thanks for the great input!
--
Duke

---

### Post by Duke_N on 2011-03-29
Update:

I've managed to get to the point of being able to hear in the earphones, what I say into the mic. Could it be then, that this Gnome Sound Recorder app is hosed?
--
Duke

---

### Post by bodhi.zazen on 2011-03-29
You keep saying the hardware is working in other OS (windows / BSD) but that information does not really help us to help you.

You need to tell us exactly what hardware you are using, specifically what sound card and what headphone / microphone.

Does it help you if I tell you my microphone is working here ? No, we need to know your hardware.

---

### Post by Duke_N on 2011-03-29
> **bodhi.zazen said:**
> You keep saying the hardware is working in other OS (windows / BSD) but that information does not really help us to help you.

You need to tell us exactly what hardware you are using, specifically what sound card and what headphone / microphone.

Does it help you if I tell you my microphone is working here ? No, we need to know your hardware.

Re-read the thread - especially post #5!

Telling you that my hardware works is all other OSs, **should** give you a clue that it's not a hardware problem! Do you see that? I have a multi-booting machine!! All the same hardware!!
**Sounds works perfect - both input and output - in windows/bsd**.

The headset I'm using is a "Cyber Acoustics" brand. How does** that** help?
Is there any specific commands that I can issue at a terminal, that would help you get a better picture?
--
Duke

---

### Post by Lateralis on 2011-03-29
OK.  You've said that the hardware is fine, but it could be a Linux driver issue.  Or your hardware may not be fully compatible with Linux.  From what you said in your post #5 I don't think that is the case as I believe your chipset is supported.  But you can help us out by providing the output of the following command:

```

sudo lshw -C multimedia

```

---

### Post by Duke_N on 2011-03-29
> **Lateralis said:**
> OK.  You've said that the hardware is fine, but it could be a Linux driver issue.  Or your hardware may not be fully compatible with Linux.  From what you said in your post #5 I don't think that is the case as I believe your chipset is supported.  But you can help us out by providing the output of the following command:

```

sudo lshw -C multimedia

```

```

dnormandin@select-man:~$
sudo lshw -C multimedia
  *-multimedia            
       description: Multimedia audio controller
       product: VT8233/A/8235/8237 AC97 Audio Controller
       vendor: VIA Technologies, Inc.
       physical id: 11.5
       bus info: pci@0000:00:11.5
       version: 50
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: driver=VIA 82xx Audio latency=0
       resources: irq:22 ioport:e000(size=256)
```

---

### Post by bodhi.zazen on 2011-03-29
> **Duke_N said:**
> Re-read the thread - especially post #5!

Telling you that my hardware works is all other OSs, **should** give you a clue that it's not a hardware problem! Do you see that? I have a multi-booting machine!! All the same hardware!!
**Sounds works perfect - both input and output - in windows/bsd**.

The headset I'm using is a "Cyber Acoustics" brand. How does** that** help?
Is there any specific commands that I can issue at a terminal, that would help you get a better picture?
--
Duke

We are going in circles. We all understand your hardware "works", and that it works in Windows and BSD.

You probably need to load a module, but we can not tell you how without additional information.

Here is a link that goes through the "basics" of how to solve these kinds of problems.

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by Duke_N on 2011-03-29
> **bodhi.zazen said:**
> 
[snip]
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

This is the best advice that you could have given! :) It solved my problem immediately. There should be an automatic referral to this site **for all** sound questions/problems.

Thanks again, for that link
--
Duke

---

### Post by bodhi.zazen on 2011-03-29
Glad you got it sorted, do you mind posting the solution (in case it help others searching the forums with a similar problem) ?

---

### Post by Duke_N on 2011-03-29
The solution is described in the link below:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

under the only microphone topic.

Anyone having trouble with trouble shooting their Sound problems should** read the above document first.**
--
Duke

---

