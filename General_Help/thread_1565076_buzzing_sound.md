---
title: "buzzing sound"
date: 2010-08-31
forum: General Help
---

### Post by dagame on 2010-08-31
hi, im having a problem with the sound, most of the times i play anything with sound, it turns to a very bothering buzzing noise. Please watch the video i uploaded to see if anyone can diagnose this problem, let me know how to fix it. I have very little experience with ubuntu so please be as descriptive as possible. Thanks in advance.


[http://www.youtube.com/watch?v=DKoYab7yvYE]("http://www.youtube.com/watch?v=DKoYab7yvYE")

---

### Post by gvernold on 2010-08-31
Which netbook are you running this on?

---

### Post by dagame on 2010-08-31
> **gvernold said:**
> Which netbook are you running this on?

msi l2100-036US

specs are:
x1250 ati chipset
alC888 sound??? not really sure, is what it said on the alsa mixer

---

### Post by gvernold on 2010-08-31
Right then, I've got a Lenovo X100e with a similar (if not the same processor in it) and I've been having the same problems with some music tracks and internet radio but not with video soundtracks. I'm also running on Ubuntu 10.04 netbook remix. I'm just wondering if there is an incompatibility somewhere but I'm afraid I'm pretty new at this diagnostics thing and it could take me a while to sort out.

I'll update as soon as I know something more, sorry I can't give an immediate solution.

---

### Post by juil on 2010-08-31
Try this thread:

[http://ubuntuforums.org/showthread.php?t=1522103&highlight=sound+buzz](http://ubuntuforums.org/showthread.php?t=1522103&highlight=sound+buzz)

I was too busy to read the whole thread to see if it will actually help you...

---

### Post by dagame on 2010-08-31
> **juil said:**
> Try this thread:

[http://ubuntuforums.org/showthread.php?t=1522103&highlight=sound+buzz](http://ubuntuforums.org/showthread.php?t=1522103&highlight=sound+buzz)

I was too busy to read the whole thread to see if it will actually help you...

wel,l i looked at that thread before, and it didn't help. He's also been looking for a solution but hasn't been able to solve it either.  I had tried lowering the pcm as you can see on that video to see if it had worked and it still kept making that buzz sound.

It all started right when i was trying to solve another issue that i had when my cpu was always running at 100% because of kacpi_notify, i had disable it & after that i updated my grub, and is being doing that ever since then. Could that had something to do with it?

---

### Post by JC Cheloven on 2010-09-01
Hi dagame, I can't be sure whether your new problem is related or not to the kacpi one you posted [here]("http://ubuntuforums.org/showthread.php?p=9795227"). It could be. The best I have to offer by now is trying to find a combination of boot parameters that suit your system (ie, that don't produce high kacpi cpu usage, and don't interfere with your sound). 

You already know how to modify /etc/default/grub (update-grub included LOL), but i'd suggest to set the parameters at boot time, and edit the grub file to make changes permanent only when you (eventually) find a working combination. To do so, at boot time, when the grub menu appears, press 'e'. Look for that 'quiet splash' (or rather 'acpi=off apm=on' in your case), and replace it for one of these combinations (only one at a time). Then ctrl-x to boot only this time with these parameters. 

Suggested combinations to try out:

```
noapic nolapic
```
```
pci=routeirq
```
```
pci=noacpi
```

note.- acpi is kind of a standard to control power management and configuration of interfaces between the OS and the bios. For recent computers (after 2000), acpi=off may not be suitable.

---

### Post by dagame on 2010-09-02
> **JC Cheloven said:**
> Hi dagame, I can't be sure whether your new problem is related or not to the kacpi one you posted [here]("http://ubuntuforums.org/showthread.php?p=9795227"). It could be. The best I have to offer by now is trying to find a combination of boot parameters that suit your system (ie, that don't produce high kacpi cpu usage, and don't interfere with your sound). 

You already know how to modify /etc/default/grub (update-grub included LOL), but i'd suggest to set the parameters at boot time, and edit the grub file to make changes permanent only when you (eventually) find a working combination. To do so, at boot time, when the grub menu appears, press 'e'. Look for that 'quiet splash' (or rather 'acpi=off apm=on' in your case), and replace it for one of these combinations (only one at a time). Then ctrl-x to boot only this time with these parameters. 

Suggested combinations to try out:

```
noapic nolapic
```
```
pci=routeirq
```
```
pci=noacpi
```

note.- acpi is kind of a standard to control power management and configuration of interfaces between the OS and the bios. For recent computers (after 2000), acpi=off may not be suitable.
finally, I got it fixed. The noapic nolapic seemed to have fix it, so did pci=noapi. Are there any differences between those two, if so which one do you recommend? anyways thanks a lot JC, i couldn't have done it without your help. :D

---

### Post by JC Cheloven on 2010-09-03
Hi, glad it worked. 

As for your question, not an easy one to explain, and I've not much knowkedge about that anyway. 
[LIST]
[*]In short, pci=noacpi tells the kernel to not use acpi to route pci interrupts. 
[*]Some quick info about interrupt controllers (apics) can be found [here]("http://en.wikipedia.org/wiki/Intel_APIC_Architecture").
[/LIST]
The only advice I have is: use that works better for you in practice. For example, cpu temperature and fan activity may help you to judge. If you want to monitor these, there are tools in the repos ...

Cheers
JC

---

