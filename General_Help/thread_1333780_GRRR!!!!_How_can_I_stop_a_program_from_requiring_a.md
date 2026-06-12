---
title: "GRRR!!!! How can I stop a program from requiring a library that's too old!"
date: 2009-11-21
forum: General Help
---

### Post by rolandixor on 2009-11-21
I've tried everything. Been bitten hard by karmic's stupid (yes, stupid, and I hope the developers read this, it's utterly stupid) problems with audio. Why is gnome-volume-control looking for libpulsecommon-0.9.15.so???????? it's not the right .so!!!!! and no matter what I do, reinstall, uninstall, purge merge and splurge it won't go away.

I've had it.

Is there a way to make the program look for it's dependencies again???

---

### Post by michy99 on 2009-11-21
Try making a symbolic link named libpulsecommon-0.9.15.so which points to the new library. I have had success with that tactic before.

---

### Post by rolandixor on 2009-11-21
I tried copying... no luck. I need to update their dependencies.

---

### Post by rolandixor on 2009-11-21
I did the link, did not work

---

### Post by rolandixor on 2009-11-21
btw, I won't go back to vista, and I need this fixed soon please. It's also stopping my multimedia keys from working, my volume control from working, and any music from playing.

---

### Post by rolandixor on 2009-11-21
wonderful. create a link, get back the good old segmentation fault that I had from the start... -___-

---

### Post by HeadHunter00 on 2009-11-21
You go to synaptic package manager, search the package and force version it to an older version. If, you're talking about something as old as beryl, then too bad, you can't.

---

### Post by HeadHunter00 on 2009-11-21
What dependency do you need anyway?

---

### Post by rolandixor on 2009-11-21
okay, basically, I need to get pulseaudio and gnome-volume-control to stop trying to load libpulsecommon-0.9.15.so ... it's obsolete, and there already is a 0.9.19.so there anyway! they load both for some reason. the first one does not exist in any package, nor is it recommended by anything, so why try to load it?

basically, until they stop this nonsense, my computer is muted :(

---

### Post by rolandixor on 2009-11-21
okay, basically, I need to get pulseaudio and gnome-volume-control to stop trying to load libpulsecommon-0.9.15.so ... it's obsolete, and there already is a 0.9.19.so there anyway! they load both for some reason. the first one does not exist in any package, nor is it recommended by anything, so why try to load it?

basically, until they stop this nonsense, my computer is muted :(


I should also add, I need my sound back by tomorrow, as I need to use the laptop to playback some stuff. So please, someone help me!!!

---

### Post by rolandixor on 2009-11-21
> **HeadHunter00 said:**
> You go to synaptic package manager, search the package and force version it to an older version. If, you're talking about something as old as beryl, then too bad, you can't.

I'm a bit of an advanced user, so that won't help, I've tried a lot. All I need is an answer that says what command to run to make a program look for dependencies sensibly again. Would preload make things worse?

---

### Post by steveneddy on 2009-11-21
> **rolandixor said:**
> **[COLOR="Red"]I'm a bit of an advanced user[/COLOR]**, so that won't help, I've tried a lot. All I need is an answer that says what command to run to make a program look for dependencies sensibly again. Would preload make things worse?

:rolleyes:

OK - maybe a total reinstall will solve the issue?

**Locate** the file you don't want and delete it manually?

The developer make the application dependent on certain software packages.

Install the application version that used the version of the .so that you already have.

There - three answers in one post.

---

### Post by rolandixor on 2009-11-21
very funny. -_- but I've done all that. next -_-

---

### Post by steveneddy on 2009-11-21
> **rolandixor said:**
> very funny. -_- but I've done all that. next -_-

You already did a total reinstall?

---

### Post by Dark9204 on 2009-11-21
> **rolandixor said:**
> okay, basically, I need to get pulseaudio and gnome-volume-control to stop trying to load libpulsecommon-0.9.15.so ... it's obsolete, and there already is a 0.9.19.so there anyway! they load both for some reason. the first one does not exist in any package, nor is it recommended by anything, so why try to load it?

basically, until they stop this nonsense, my computer is muted :(

Ok, there are some things that you should know.
1. Pulseaudio is just a sound server, it has nothing to do with your drivers.
2. You have not stated WHY you so desperately need that .so.
3. If Pulseaudio is a problem for you, simply kill it (pulseaudio -k).
If you get no sound, i would try to kill pulseaudio and update ALSA drivers and Linux Kernel.

---

### Post by rolandixor on 2009-11-21
not of my system but almost everything on it. I thought I was getting somewhere just now because I managed to trick the two offenders that the needed .so was there, but now that they load it, it's missing symbols. Seems to me like there has to be some cache or something that's forcing them to load the lib, cause there is no other reason they should. Nothing on my system needs such an old version of pulseaudio, yet pulseaudio itself won't load. I hope the ubuntu devs quite acting like microsoft and right their wrongs or we will lose a lot of people.

To be honest I was one of the ones who defended the whole pulseaudio deal and some of the stupid decisions, but I've had it now. I have an assignment to complete for Operating Systems, and I can't even get aa proper working system with music to keep my calm. 

oh and yes, I am a bit angry sorry if I've been rude in any way.

---

### Post by rolandixor on 2009-11-21
not of my system but almost everything on it. I thought I was getting somewhere just now because I managed to trick the two offenders that the needed .so was there, but now that they load it, it's missing symbols. Seems to me like there has to be some cache or something that's forcing them to load the lib, cause there is no other reason they should. Nothing on my system needs such an old version of pulseaudio, yet pulseaudio itself won't load. I hope the ubuntu devs quite acting like microsoft and right their wrongs or we will lose a lot of people.

To be honest I was one of the ones who defended the whole pulseaudio deal and some of the stupid decisions, but I've had it now. I have an assignment to complete for Operating Systems, and I can't even get aa proper working system with music to keep my calm. 

oh and yes, I am a bit angry sorry if I've been rude in any way.

---

### Post by rolandixor on 2009-11-21
oh great a double post now. Why are the forums gone nuts? my apologies for the double post.

to explain... I don't NEED the .so, I wish pulseaudio would stop asking for it. In fact, I want pulseaudio working cause when it does, things go smoothly.

---

### Post by renkinjutsu on 2009-11-21
i ditched pulseaudio completely in 9.10, so i don't know of any pulseaudio problems.. why don't you just uninstall pulseaudio? All you need is ALSA anyway.

---

### Post by rolandixor on 2009-11-21
because it's so tightly integrated now. And please, don't tell me to uninstall it. I tried and got no where. I need a solution, not more head aches :'( I'm at the point of crying and giving up. And I mean that literally :S

If I had money I'd just get a new hard drive as I wanted, but I'll have to wait to long.

---

### Post by Dark9204 on 2009-11-21
> **rolandixor said:**
> oh great a double post now. Why are the forums gone nuts? my apologies for the double post.

to explain... I don't NEED the .so, I wish pulseaudio would stop asking for it. In fact, I want pulseaudio working cause when it does, things go smoothly.

How about compiling from source?
As i see it, you have three options
1. Compile from source.
2. Report it as a bug. [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu). If so, you will have to be very precise and tell them what does not work. 
3. Live with it, is it really that crucial?

The first thing that really annoys me with your post is that you haven't described your problem! Make the post informal and structured!

---

### Post by michy99 on 2009-11-21
What version of pulseaudio are you running? According to the bug report at 

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=528405](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=528405)

it should have been fixed with version 0.9.15-2.

---

### Post by rolandixor on 2009-11-24
thanks to all who helped. I got it fixed on my own. turns out pulseaudio had installed to /usr/local from a previous compilation I did. I removed that and everything is working.

I hope this can help someone in the future. In fact, I might post a warning message to newer users never to compile without doing ./configure --prefix /usr ! Not doing that == fail on ubuntu.

---

