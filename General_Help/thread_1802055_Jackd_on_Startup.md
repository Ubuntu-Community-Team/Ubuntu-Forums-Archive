---
title: "Jackd on Startup"
date: 2011-07-11
forum: General Help
---

### Post by swiftoid on 2011-07-11
Hi everyone. I've finally got jack to work with my sound card without having to sudo everything.! Yay!

So I thought, let's run it at startup to save me having to do it manually every time.
I put in /etc/rc.local:
jackd -d firewire

and the server starts on boot as expected. The only trouble is, I now have to sudo anything that uses jack, where as if I don't put it in rc.local and start it manualy through a terminal programs can access it normally. Can anyone help me figure out how to make it work without suding?

Thanks

Jamie

---

### Post by swiftoid on 2011-07-12
Anyone...?

---

### Post by CatKiller on 2011-07-12
Can't you just launch jackd when you log in?

System -> Preferences -> Startup Applications

EDIT: Just saw you were using KDE. I know that KDE has a similar option, but I can't remember where it is off the top of my head. You'll find it, though.

---

### Post by swiftoid on 2011-07-12
Thanks. I already tried that, but the kde version doesn't allow you to add new programs to startup. Just disable existing ones. 
I'd prefer it to be at boot if possible anyway.

---

### Post by CatKiller on 2011-07-12
> **swiftoid said:**
> Thanks. I already tried that, but the kde version doesn't allow you to add new programs to startup. Just disable existing ones. 

Nasty. An appropriate [.desktop file]("http://standards.freedesktop.org/desktop-entry-spec/latest/") in ~/.config/autostart should still work, though.

Something like this might work.
```

[Desktop Entry]
Type=Application
Name=Starting JACK with a text file because KDE won't let me add an entry to startup
Exec=jackd -d firewire
```It's also possible that KDE are extending the Desktop specification with their own startup method, in which case you might need to put in some of [this information]("http://l10n.kde.org/docs/admin/autostart-and-runonce.html") from the KDE docs. I've not used KDE in a long time, so I can't do any testing for you to give a definitive answer. The last time I used it, it did pick up ~/.config/autostart entries. You might need to put it somewhere else if they've made big changes since then.

> I'd prefer it to be at boot if possible anyway.So you can route the login sound through your EQ? :D

Seriously, I do understand the itch-to-scratch thing, but getting the JACK server running as a non-root user before any user has logged in requires much manpage-reading and doesn't (to me) appear to offer any benefit over the fairly easy method of starting it as a user when that user logs in.

---

### Post by swiftoid on 2011-07-12
Thanks for your help. I'm actually switching to  plain old ubuntu anyway as we speak, I was getting sick of the slow jerky KDE interface. While I prefer the KDE form factor, Gnome is just so much smoother and more developed.

So I'm going to wile away a few hours getting my card to work on ubuntu then I'll be back to this problem again. 

The reason I want jackd to start on boot, is to make linking it with alsa easier. All my attempts to do so on kubuntu failed, and I was begining to suspect it was because when alsa loaded, it checked for jack, couldn't connect, and so just ignored my settings.

My end goal is to have my firewire audio interface be my primary sound card for all linux programs. You'd think this would be easy and intuitive... it really isn't! Windows has spoiled me.

If you have any advice on how to link alsa with jack (making jack the default audio device system wide), I would really appreciate it.

Thanks

---

### Post by CatKiller on 2011-07-12
> **swiftoid said:**
> If you have any advice on how to link alsa with  jack (making jack the default audio device system wide), I would really  appreciate it.

'Fraid not. ALSA configuration makes me cry. When I need to use JACK I  just run qjackctl. It suspends PulseAudio and somehow magically makes  normal ALSA calls go through JACK. The rest of the time I just use  PulseAudio.

As for the startup process, that makes me cry for largely the same  reasons; very configurable, with multiple approaches over the years that all hang around for legacy reasons. It's a thicket.

The Ubuntu Studio project documentation might have something useful  about getting JACK started system-wide with appropriate permissions.

> My end goal is to have my firewire audio interface be my primary sound card for all linux programs. You'd think this would be easy and intuitive... it really isn't! Windows has spoiled me.If ALSA (hardware side) knows about your FireWire interface, you don't necessarily need to use ALSA (software side) to access it. Unless you need low-latency audio and pipelining, you don't necessarily need to use JACK either. If ALSA knows about it, PulseAudio can access it, which means that it should be able to work fairly easily. "Should" is often a loaded word when it comes to Linux audio, though :)

Good luck!

EDIT: Don't know if [this]("http://ubuntuforums.org/showthread.php?t=1761178") is helpful?

---

### Post by swiftoid on 2011-07-12
Wait a minute, maybe I'm getting a little confused here. What program controls audio in linux? Pulse audio or alsa? I've been going on what little useful info I can garner from forums on t'interweb, but maybe I've got this wrong.

I really wish there was a "HowTo: Firewire as default audio device", it would make life so much easier. Better yet, I wish linux would just detect my firewire interface and add it as a sound device in the mixer. FFADO detects it an adds it into it's mixer, but how does that help anyone?

I thought ffado's website would be helpful, but there's very little info on how to use ffado in the real world on there.

Thanks

Jamie

---

### Post by CatKiller on 2011-07-12
> **swiftoid said:**
> Wait a minute, maybe I'm getting a little confused here. What program controls audio in linux? Pulse audio or alsa?

Yes.

Or OSS. Or JACK. Or ESD. Or aRts (although I don't think many people use that).

It's all frightfully complicated.

The basic problem is that one sound system didn't do everything that everyone wanted. So people wrote a different one. Then the first one got better, so people had to support two. Then neither did everything that everyone wanted. So people wrote a different one. You can see where this is going...

Each one is geared to a particular purpose. Nothing natively supports them all. As things have progressed, some of the features of the new-and-shiny have been implemented in the old-and-crufty. Different approaches fall in and out of favour as feature-sets and philosophies change.

The current default Ubuntu approach is to use PulseAudio. It was incredibly controversial at the time it was introduced, but it's settled down into something quite sensible. You may see much wailing and gnashing of teeth on the Internet about Pulse, but the criticisms are largely out of date. It has some very nice user-friendly features, like being able to route audio from more than one application (which vanilla ALSA lacked without hardware support), per-application volume settings, on-the-fly resampling of audio streams, and the ability to stream audio over a network. It's a good fit for a general Ubuntu user.

All of that user-friendliness comes with some overhead. If you have an aggressive resampling regime, it can use a reasonable amount of CPU. If you're routing audio all over the place, you sometimes get some latency.

Professional audio work demands raw performance over everything. If you have significant latency, you can't play in time. Even the kernel can be too slow for some people, so there's been work on realtime kernels to get the absolute maximum performance. This makes PulseAudio not a good fit for those users. JACK's very low latency and arbitrary connections make that a much better fit for those users. Different feature-set, you see?

Neither of those actually output any sound at all. To do that, they'd need to duplicate all the work that has already been done in getting hardware specs and writing drivers for all the sound devices there are out there. Since ALSA and OSS are mature projects, all of the hardware work has already been done by those projects. PulseAudio and JACK both use either ALSA or OSS as a back-end to actually talk to the hardware. Ubuntu uses ALSA, but I'd imagine that other distros might use OSS. Either is fine.

The bit that makes things complicated is that each sound system generally assumes that it has full control over the hardware. In order to make more than one application make noise, this isn't generally the case. So different plugins have been developed that allow each of the sound systems to think that they have total control over a piece of hardware, when actually the sound is routed through something else entirely. Which means that you might end up with a signal path that goes

Application -> OSS -> ALSA -> PulseAudio -> ALSA -> Hardware

and that not be crazy.

PulseAudio has plugins for most things, so PulseAudio will often just work, pretending to be whatever it is that an application asks for. JACK has plugins for ALSA and OSS, so if you're running a stripped-down pro-audio machine, that will generally just work, provided your application speaks JACK (which pro-audio applications do). With some tweaking, general ALSA outputs will also turn up in JACK. With some more tweaking, you can get really low latency audio. Neither PulseAudio nor JACK understand the other, but users like me - that occasionally do pro-audio stuff, but most of the time don't - benefit from a script that turns off PulseAudio when JACK starts and then turns it back on again when JACK stops. I think that comes with Pulse, but it could just as easily come from JACK. Doesn't matter either way.

So to answer your implied question, as long as ALSA understands the hardware, either JACK or PulseAudio should work OK as a front-end without too much work. They don't work at the same time, but that's OK. PulseAudio is probably less work, provided you don't want really low latencies.

---

### Post by swiftoid on 2011-07-13
Wow! Thanks for all the help. I really appreciate you're taking the time to write all that. I'm now only slightly more confused :-(

I've managed to get jack to run ok on ubuntu natty, I don't even need to sudo it. And I'm using aqualung to play back music through my firewire devices! Score! This link was very helpful: [http://www.chrisbaume.co.uk/?tag=ubuntu](http://www.chrisbaume.co.uk/?tag=ubuntu)

Now, my next goal is to make all of ubuntu play back through my firewire device. From reading your last post, I think what I need to do is make pulse audio output to jack instead of straight to the (unused) sound card. Is that correct?

If so (please let it be that simple), how do I get pulse audio to route to jack instead of the onboard sound card?

Thanks for all your help once again. I really am very grateful. 


Jamie

---

### Post by CatKiller on 2011-07-13
> **swiftoid said:**
> Now, my next goal is to make all of ubuntu play back through my firewire device. From reading your last post, I think what I need to do is make pulse audio output to jack instead of straight to the (unused) sound card. Is that correct?

Not necessarily. In Natty you can use the volume widget on the panel to tell PulseAudio which device to use. Pretty simple, really. In older versions, I think you needed to use padevchooser to set the default sink to whichever device you want as shown in paman's Devices tab.

> If so (please let it be that simple), how do I get pulse audio to route to jack instead of the onboard sound card?I realised subsequently that I was incorrect in my assertion that PulseAudio and JACK can't talk to each other. That used to be the case, but PulseAudio now has a module that will let it output to JACK, called pulseaudio-module-jack (in the repositories from Lucid onwards). I think it just shows up as a stereo pair that you can connect in JACK the same as you would any other application.

---

### Post by swiftoid on 2011-07-13
Hey. would you believe it... I got it working! It only took me about 5 hours, but I did it. :D

Very convoluted, but it works. I even had to write my own SH script to switch the pulse audio input/outputs automatically to JACK (as they default to actual cards).

Thanks for all your help. One last question. I'm trying to install the linux-rt kernal onto ubuntu 11.04 natty narwhal, but when I try I get this:
```
jamie@jamie-linux:~$ sudo apt-get install linux-rt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-rt

```

Any ideas how I can switch? Audio is still a bit jerky with the standard kernal.

Jamie

---

### Post by CatKiller on 2011-07-13
> **swiftoid said:**
> I'm trying to install the linux-rt kernal onto ubuntu 11.04 natty narwhal

AFAIK, most of the things that the realtime kernel did have been integrated into the mainline generic kernel and the external project has kind of died. I could be mistaken, though. You should still be able to start JACK in realtime mode, though. ISTR that there are some security setting tweaks that are recommended to make that more likely to work.

In terms of your performance, it might be worth checking that you aren't resampling twice; once from whatever the file is at to whatever PulseAudio's using and again from that to whatever JACK's using. Setting both of them to match whatever your hardware uses natively is probably a good place to start.

 JACK also has a bunch of options that you can tweak until you've eliminated xruns. I never quite managed it: always got an xrun whenever I opened something new or rotated the cube, so I stopped doing those things when I was doing srs bsns.

Glad you've got it sorted, and I'm sure you've learned quite a lot along the way :)

---

