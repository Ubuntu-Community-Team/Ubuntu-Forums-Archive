---
title: "hardware detection"
date: 2010-02-11
forum: General Help
---

### Post by rbutler480 on 2010-02-11
Hello all
This is probably too general a question, so I appologize in advance. I am running karmic and have run into some problems getting some usb hardware recognized at boot-up. I have been wanting to understand the whole process of hardware detection and am finding it quite difficult, not because of the concepts involved but because I am hardly ever sure that the info I am reading applies to 9.10. 
( for example:If I am reading an article that says to use udevtest to check a rule instead of devadm how much other information is out of date? I have no way of knowing)

So question 1. Would I be better off using an older release where information is more readily availiable? Hate to do that as I've spent a lot of time getting 9.10 set up as I like it.

I have become familiar with things I am pretty sure are deprecated and others I am not so sure of :
Is HAL completely deprecated in 9.10 or is it partialy  still used used ?
Is Hotplug still used ?

 Ideally since I tend to think graphically I'd like to draw the sequence of hardware detection. 
Step one leds to step 2, which branches to steps 3 and 4 etc. I don't need a deep understanding of each step at this time but there is no way I can feel I understand my system unless I have such a basic understanding.
 I've tried posting this in various versions on various forums and no one has responded. So I am not sure if my questions are too general, or whatever. I have looked at some sites suggested as well as download a great pdf book, but either information is for earlier releases of Ubuntu or too basic, ( how to manage your desktop etc.). I am begining to feel like a persona non grata and am not sure why. Are these not valid questions for forums ? Real new at all this stuff so sorry if that is the case.

---

### Post by MooPi on 2010-02-11
Which hardware is not being detected ?

---

### Post by rbutler480 on 2010-02-12
> **MooPi said:**
> Which hardware is not being detected ?

A usb hub that is plugged into a usb pci card, but I'm more interested in getting a good basic understanding of how things fit together than in solving a particular problem. I thought some linux guru might be able to recommend something, was worth a shot;)

---

### Post by falconindy on 2010-02-12
All hardware is detected at bootup. If a kernel module exists to drive the hardware, it's installed via modprobe and resources are allocated for it. This is separate from the abstraction that occurs when loading an Xserver. 

It's (usually) flawed to think that an older release may have a better chance of supporting your hardware. Unlike Windows, where hardware support wavers with every release, Linux's support only improves.

As you've only provided anecdotal remarks about your hardware, let's see some hard evidence. What's the output of 'lspci'? Does your PCI USB card show up there? What happens when you plug a device into the hub? Does it show up in 'lsusb'?

---

