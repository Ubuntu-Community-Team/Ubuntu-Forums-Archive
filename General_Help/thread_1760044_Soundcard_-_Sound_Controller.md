---
title: "Soundcard - Sound Controller"
date: 2011-05-16
forum: General Help
---

### Post by longreacher on 2011-05-16
This is probably a dumb question, but is a soundcard the same thing as a sound controller?
When I type:
```
aplay -l
```
 
I'm getting:
```
 
aplay: device_list:221: no soundcard found...

```
 
But when I type:
```
 
lspci -v

```
I'm getting:
 
```
 
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
        Subsystem: IBM Device 0287
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at e8080c00 (32-bit, non-prefetchable) [size=512]
        Memory at e8080800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2
        Kernel driver in use: Intel ICH
        Kernel modules: snd-intel8x0
 

```
 
I've been following Lordraiden's "Comprehensive Sound Problem Solutions Guide ", but after completing it I still get the no soundcard found message.

---

### Post by tredegar on 2011-05-16
> is a soundcard the same thing as a sound controller?
Yes.

Your sound card/controller is by Intel, which is generally well supported by linux, so I am surprised you have problems.

Is the required module loaded? You can check to see if it is listed by **lsmod | grep snd-intel8x0**

Is there anything in your BIOS to enable/disable your sound? Please check.

Are you running a non-standard install of ubuntu (Eg A virtual machine, "wubi", something else)? If so, please tell us the details.

Which version of ubuntu have you installed?

> I've been following Lordraiden's "Comprehensive Sound Problem Solutions Guide " A link would be helful. When you follow the guide, do you receive any errors? 

If so, what are they?

---

### Post by longreacher on 2011-05-16
I'm running Ubuntu server 10.10 (headless).  Nothing weird about the install.

The Guide I was following is _**[here]("http://ubuntuforums.org/showthread.php?t=205449&highlight=Comprehensive+Sound+Problem+Solutions+Guide")**_  (now that i look at it again, it's probably fairly outdated.)

I was able to follow until I got to the command to use module-assistant in alsa-source.  I got error messages and things went off the rails at that point.

I'll check the bios tonight.  I'll have to round up a monitor somewhere.  (No way to do that remotely, right?)

Thanks.  As you can probably tell, I'm fairly new to Linux

---

### Post by tredegar on 2011-05-16
> I'm running Ubuntu server 10.10 (headless).
That might be where the problem lies. Servers are just that (generally hidden in the attic/basement, or just a rack in a datacentre). They serve data. If you think about it, they aren't *required* to make any noises (because nobody will be listening). 

Servers are usually configured with the minimum of services running (this reduces the number of security issues you need to consider). I can't think of any server configuration that would/should start up sound services by default. If you want sound, and USB sticks and all to work, maybe install a desktop version of linux. 

So the reason your sound isn't working is perhaps because your installation was (rightly) designed that way.
> The Guide I was following is here
It is way out of date. Ubuntu is using **pulseaudio** now. **alsa** might still apply, but ....
> I'll check the bios tonight. I'll have to round up a monitor somewhere. (No way to do that remotely, right?)
AFAIK there is no way to check the BIOS remotely.

But if the PC is remote, why do you need it to make sound? Perhaps if you explained your situation/problem better, we could offer better advice.

Best wishes.

---

### Post by longreacher on 2011-05-16
OK, so I checked the BIOS, everything seems to be enabled at that end.

Insofar as what I'm hoping to accomplish, I want to be able to stream audio out to the web via the microphone port.  I'm looking to take our local fire department radio transmissions and port them through to [_www.radioreference.com_]("http://www.radioreference.com/").I can do it on my windows machine, but since my server is on all the time it makes sense to port it out through there.

---

### Post by longreacher on 2011-05-17
OK.. I solved it, the problem that I had not added myself to the audio group.  When I tried aplay -l as root, my soundcard came up fine.
 
Adding myself to the audio group solved the problem

---

### Post by tredegar on 2011-05-17
> Adding myself to the audio group solved the problem
Well done, and thanks for the follow-up.

---

