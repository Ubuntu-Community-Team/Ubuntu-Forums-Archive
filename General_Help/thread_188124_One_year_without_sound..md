---
title: "One year without sound."
date: 2006-06-03
forum: General Help
---

### Post by iAlta on 2006-06-03
A(lmost) year has now passed, since I took my first steps into the world of Linux. It has been amazing, I just switched to Kubuntu on a brand new PC(well, new for me), and it looks supery good. 

But I don't know how Kununtu sounds... come to think about it, I don't know how Ubuntu sounds eighter. Not untill resently(i.e. today), I heard the first sound of Linux, unfortunretly, it wasn't on my PC. 

I have never tried to get the sounds working, thinking you would need some codexes I didn't have, and I never boutherd finding them, but now I know you can have sound out-of-the-box, or in this case out-of-the-disk, but "you" != "me". 

So could anyone tell me, how can I get the sounds working? I would like that.
What do I have to do? What configurations, what specification? How can I hear this awsome operating system? 

*Thanks in advance iAlta*

---

### Post by jocko on 2006-06-03
Could you tell us what soundcard you have? Most likely someone on this forum have the same card and know how to help you...

---

### Post by jdong on 2006-06-03
To help identify your sound chipset, the output of the following two commands would be appreciated:

```

lspci -v

```

```

lsmod | grep snd

```

---

### Post by iAlta on 2006-06-03
Thanks for the replys.

lscpsi -v said:
```

0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
        Subsystem: Quantum Designs (H.K.) Inc: Unknown device 0645
        Flags: bus master, medium devsel, latency 32, IRQ 209
        I/O ports at cc00 [size=256]
        I/O ports at d000 [size=128]
        Capabilities: <available only to root>
```
and
```
0000:00:0b.0 Multimedia audio controller: Ensoniq ES1370 [AudioPCI]
        Subsystem: Unknown device 4942:4c4c
        Flags: bus master, slow devsel, latency 32, IRQ 225
        I/O ports at e400 [size=64]
```

lsmod | grep snd said:
```
snd_mpu401              6728  0
snd_mpu401_uart         7808  1 snd_mpu401
snd_ens1370            19552  1
gameport               15496  2 analog,snd_ens1370
snd_rawmidi            25504  2 snd_mpu401_uart,snd_ens1370
snd_seq_device          8716  1 snd_rawmidi
snd_ak4531_codec        7936  1 snd_ens1370
snd_intel8x0           33692  1
snd_ac97_codec         92704  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  4 snd_ens1370,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd_page_alloc         10632  3 snd_ens1370,snd_intel8x0,snd_pcm
snd                    55268  16 snd_mpu401,snd_mpu401_uart,snd_ens1370,snd_rawmidi,snd_seq_device,snd_ak4531_codec,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
```

Any help?

---

### Post by todak on 2006-06-03
I have the same sound card (Ensoniq audio PCI 1370). It appears I also have the same chipset as you (SiS).
Your lspci shows both the onboard and pci card being used. Go into the BIOS and disable the onboard sound. Then you should be able to hear sound through the 1370 pci card. I have always had every version of Linux I have tried, recognize this particular card.

---

### Post by iAlta on 2006-06-04
Wow thanks, I'll do that now...:p 

Thanks...

---

### Post by Lord Illidan on 2006-06-04
I have a wierd soundcard (genius, ugh), that is never detected in Mandrake... never works in it. Even Mandriva 2006 doesn't work with it. And after 1 hour of installation, if it doesn't work, I just remove it.. 
How could you remain for 1 year without sound, then???

---

### Post by OffHand on 2006-06-04
[QUOTE=Lord Illidan]
How could you remain for 1 year without sound, then???[/QUOTE]
Haha I was wondering about the same.

---

### Post by iAlta on 2006-06-04
Lazyness I guess...

Now back to topic, I don't know how to disable the onboard sound. What should I be looking for? What typicle words are used for this?

I found only one option with the word "sound" changed that from "EDB" to "PCI" but with no luck...

---

### Post by Ocxic on 2006-06-04
the option would be in the advanced or chipset section of your bios. look for onboard audio. if you can't find theses options try changing your "sound" option to PCI and see what happens.

---

### Post by todak on 2006-06-04
[QUOTE=iAlta]
Now back to topic, I don't know how to disable the onboard sound. What should I be looking for? What typicle words are used for this?[/QUOTE]

On my particular BIOS I go to the "Integrated Peripherals" heading and enter.
Next, I go to the "SiS 730 on chip PCI device" heading and enter.
Then, I go to the "SiS 7018 ac97 audio" setting and press the Page up or Page down key to change the setting from enabled to disabled.
Then I press F10 and enter to save the settings and reboot.
Your chipset numbers will probably be different than what mine are, however, the particular words should be the same or at least very similar.
Hope this will help you!:p

---

### Post by iAlta on 2006-06-04
Integrated Peripheral - SIS OnChip PCI Device - SIS AC97 Audio.
That was my phath, I give you my thanks for guiding me to the right one.*

It now works! Finally, now I just have to install wine, then I can kick back with some good'ol fasion Diablo II.

On a side note, what is BIOS and what does it stand for?


* doesn't this sound epic?

---

### Post by jdong on 2006-06-04
[QUOTE=iAlta]
On a side note, what is BIOS and what does it stand for?
[/QUOTE]

[http://en.wikipedia.org/wiki/BIOS](http://en.wikipedia.org/wiki/BIOS) (good information, if you're really curious)

It stands for Basic Input Output System, provides a basic interface for your operating system to talk to your computer's hardware. The role of the BIOS has extended to configuring the numerous devices that are integrated onto your motherboard.

The BIOS is somewhat considered dated/legacy now, and there's been movement towards reducing the dependency on BIOS and moving to something a lot more software-malleable. For example, ACPI allows the operating system to control the power and other aspects of lots of the hardware in your computer, and there will be more standards to follow. Eventually in the future, the OS will be able to do everything the BIOS supports at a software level.

As a testament to that, if you go to a computer store and take a look at the BIOS setup program on modern systems (especially laptops), you'll see a great reduction in the number of BIOS options. They've all been migrated to various software control methods.

---

### Post by todak on 2006-06-04
[QUOTE=iAlta]Integrated Peripheral - SIS OnChip PCI Device - SIS AC97 Audio.
That was my phath, I give you my thanks for guiding me to the right one.

It now works! [/QUOTE]

Glad to know I could help solve your problem! =D>

---

### Post by iAlta on 2006-06-05
Thanks.:)

---

