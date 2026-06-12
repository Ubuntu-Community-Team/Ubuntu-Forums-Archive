---
title: "External Microphone Not Working"
date: 2010-03-11
forum: General Help
---

### Post by derekeverett on 2010-03-11
I have posted about this before, but not recently. I hope three times is a charm.

I have just re-installed Ubuntu 9.10 and I can still not get my external microphone working. Attached is screenshots of my Sound Preferences, I think everything is right. The documentation is a little out of date but I have done my best to follow those instructions.

I am plain getting no sound. Without making any hardware changes at all, the microphone works fine in Win7 on the same computer. So I know the problem is not hardware related. 

I am having no audio output troubles at all. System sounds play fine as do audio recordings.

Any help here would be appreciated. Thanks in advance!

---

### Post by derekeverett on 2010-03-13
Bump.

---

### Post by derekeverett on 2010-03-13
Bump again. I guess I could mention my sound card is a realtek ALC1200. Could this be a configuration problem of some kind that prevents input while allowing output?

---

### Post by derekeverett on 2010-03-14
Bump again. I would even be happy if I could find a source that says it's just not possible with my sound card or something but I can't seem to find that either...

---

### Post by derekeverett on 2010-03-15
Ok this will be my last bump for a while.

A bit upsetting though, my Ubuntu is set up just perfect for me. I've never been as happy with it as I am now. Just have this one issue that has been plaguing me for months.

If anybody has any ideas that would be great. And thank you.

---

### Post by derekeverett on 2010-03-22
Is there a limit to how many times one should bump these things?

---

### Post by blazemore on 2010-03-24
Try installing [Pavucontrol]("apt:pavucontrol"), then run it and see if you can find any sliders there that are muted.

---

### Post by derekeverett on 2010-03-24
Ok, I installed it.

I didn't fiddle with anything.. just took these screen shots for ya.

I should mention, just to be clear, that it is my external microphone coming in through the input jack of my sound card that I want to get working.

My monitor has a microphone built into it that works.. it just sounds like hell.

Thought that might make some of what your seeing more clear.

---

### Post by derekeverett on 2010-03-24
Sorry I forgot the screenshots. Here they are.

---

### Post by blazemore on 2010-03-24
What happens if you change the port on the Input tab?
It's fine to mess around in there. You have the screenshots if you need to set it back to default!

---

### Post by derekeverett on 2010-03-24
> **blazemore said:**
> What happens if you change the port on the Input tab?
It's fine to mess around in there. You have the screenshots if you need to set it back to default!

Thanks for the suggestion, I tried everything and still no dice.

I've spent literally hours on this now. I don't understand for the life of me what the problem can be.

I get audio output no problem at all. But I have never been able to get the input working with any version of Ubuntu. It's frustrating cause all I have to do is boot into Windows on this exact same machine and it records no problem. So I know I can't blame hardware. All I had to do in Windows was switch to "Line in" for input. Ubuntu gives me this same Line in option but doesn't work.

---

### Post by rahilm on 2010-03-24
> **derekeverett said:**
> Thanks for the suggestion, I tried everything and still no dice.

I've spent literally hours on this now. I don't understand for the life of me what the problem can be.

The problem is that ubuntu, like all other OS in the world, drops support for some hardware to give way for new hardware devices.  Also, the ubuntu devs are obssessed in fitting the entire OS on one 700mb CD.
I do not mean to discourage you. Please try on. If you get a solution, reply in this thread. It will help others like me.

It is obvious that none of the non-developers know how to fix this particular problem. If you want a reference, see this:
[http://ubuntuforums.org/showthread.php?t=1375598](http://ubuntuforums.org/showthread.php?t=1375598)

---

### Post by derekeverett on 2010-03-24
> **rahilm said:**
> The problem is that ubuntu, like all other OS in the world, drops support for some hardware to give way for new hardware devices.  Also, the ubuntu devs are obssessed in fitting the entire OS on one 700mb CD.
I do not mean to discourage you. Please try on. If you get a solution, reply in this thread. It will help others like me.

It is obvious that none of the non-developers know how to fix this particular problem. If you want a reference, see this:
[http://ubuntuforums.org/showthread.php?t=1375598](http://ubuntuforums.org/showthread.php?t=1375598)

Thanks for the encouragement.

As far as dropping support for hardware, this machine is only 9 months old! I've tried with 8.04, 9.04 and 9.10 - none of them work.

If I was getting no audio then I would just blame no audio support, but I get audio output no problem. Does it make sense that output works but input doesn't?

I don't know... maybe it does...

---

### Post by rahilm on 2010-03-24
> **derekeverett said:**
> Thanks for the encouragement.

As far as dropping support for hardware, this machine is only 9 months old! I've tried with 8.04, 9.04 and 9.10 - none of them work.

If I was getting no audio then I would just blame no audio support, but I get audio output no problem. Does it make sense that output works but input doesn't?

I don't know... maybe it does...
of course it does. 
but in my case the headphone audio output worked fine on all dsitros upto jaunty. Then suddenly no sound in karmic. and i am 100% sure that it will not in lucid.
My mic didn't work on all distros i have tried. Including XP and 7. So I guess it is a hardware issue. Interestingly, the headphones don't work in windows 7 too.

have you tried gettng rid of pulse audio and installing alsa?

---

### Post by derekeverett on 2010-03-24
> **rahilm said:**
> of course it does. 
but in my case the headphone audio output worked fine on all dsitros upto jaunty. Then suddenly no sound in karmic. and i am 100% sure that it will not in lucid.
My mic didn't work on all distros i have tried. Including XP and 7. So I guess it is a hardware issue. Interestingly, the headphones don't work in windows 7 too.

have you tried gettng rid of pulse audio and installing alsa?

I'm not sure I'm brave enough.. but I suppose I'm desperate enough. Are you aware of any guides etc. for me to take a look at?

---

### Post by rahilm on 2010-03-24
I am trying it now. I'll get back to you if it works..

---

### Post by rahilm on 2010-03-24
it screws up the sysytem..i recommend doing only if there is no choice
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=82842](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=82842)

in the second screenshot of your fist post.. what list shows up in connectors??

---

### Post by derekeverett on 2010-03-24
> **rahilm said:**
> it screws up the sysytem..i recommend doing only if there is no choice
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=82842](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=82842)

in the second screenshot of your fist post.. what list shows up in connectors??

Line-in, Microphone 1, and Microphone 2. I've tried all of them several times. No luck.

---

### Post by rahilm on 2010-03-24
I just realised that i had an old polaroid digtal camera with me and it had inbuilt mic. I plugged it in and poof. everything is detected (I reinstalled Pulseaudio) and the mic is actually extremely sensitive...unbelievable!!!

---

