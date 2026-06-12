---
title: "No Audio with: SoundMAX Integrated HD Audio"
date: 2006-05-19
forum: General Help
---

### Post by ilektriksky on 2006-05-19
I seem to just be having tons of problems with this new computer.
](*,) 

It has utilizes a SoundMAX Integrated HD Audio, and I cant seem to get any sound to play within Ubuntu.

If anyone has run into this problem and/or knows a solution or any ideas, I would be most grateful if you would share it.


Thanks

Ilektrik

---

### Post by xdefconx on 2006-06-08
Yeargh! i'm also looking for this solutions

-newbies-

---

### Post by toniti on 2006-06-16
Same here. HELP!

---

### Post by tuanway on 2006-06-21
I have this problem also, i have a asus w3j laptop, and it detects it as a analog device ad1986a and there is also an intel hda audio. im also using the newest version of ubuntu. while the card is detected, there is no noise coming out of either the laptop speakers or headphones. not sure whats wrong really.

---

### Post by s10case on 2006-06-25
I am having the same problem as well, except I am getting a high pitched noise when I try to use audio programs, and sometimes when I do other things. I have an asus M2NPV-VM.

According to the manual, this motherboard has:

Southbridge: - NVIDIA nForce 430 MCP
High Definition Audio - "soundMAX ADI AD1986A 5.1 channel CODEC"

When I run
 
[COLOR="Blue"]
cat /proc/interrupts
[/COLOR]

I get the following output:

[COLOR="Blue"]
           CPU0
  0:     471293          XT-PIC  timer
  1:       3592          XT-PIC  i8042
  2:          0          XT-PIC  cascade
  5:      47476          XT-PIC  libata, libata, ohci_hcd:usb1, ohci1394, HDA Intel
  7:          3          XT-PIC  parport0
  8:          0          XT-PIC  rtc
  9:          0          XT-PIC  acpi
10:          0          XT-PIC  MPU401 UART
11:     195821          XT-PIC  ehci_hcd:usb2, eth0
15:      32703          XT-PIC  ide1
NMI:        273
LOC:     471163
ERR:          0
MIS:          0
[/COLOR]

I see that a lot of things are using IRQ 5, I don't know if that is a problem or not, but I have read on various posts that sometimes audio and network don't like to use a shared irq.

This begs another question: what device in that list is my audio card? Is it "HDA Intel"? If so, why isn't it called soundMax?

I tried installing the nvidia chipset driver that came with my motherboard and updating the module configs as the readme described, but it made no difference.

Any help would be awesome, seemingly for alot of us.

TIA

Mike

---

### Post by hotani on 2006-07-04
no word on this? I'm building a system and up to this moment I had the M2NPV-VM MB on my list, but no sound means it's not going to be on there for long. Alternatives?

---

### Post by axxs on 2006-07-12
tuanway, I have this problem also, i have a asus w2jc laptop, everything seems to work, just no sound. Nothing is set muted. There's no error messages trying to run any sound app, it shows it running .. just no sound.

---

### Post by dhon on 2006-07-13
I've got the ASUS W3J and had to add the model=laptop-eapd to get it to work.

---

### Post by chumba on 2006-07-16
I have found a solution for my **M2NPV-VM** mobo. 

Not sure how that could apply to laptop cases but as I can see people are looking for generic High Definition audio "soundMAX ADI AD1986A" fixes.
Here is my case description and solution [details]("http://www.planetamd64.com/index.php?showtopic=23938&st=0&gopid=243353&#entry243353").

Basically everything is simple (after I spent almost a week looking for answers :) ).

-Update BIOS (not even sure if that is required step, but it generally always good idea to do that).
-Get latest [ALSA drivers]("http://www.alsa-project.org/"). I got "**1.0.12rc1**" but "**1.0.11 final**" should also do.
-Put "**options snd-hda-intel position_fix=1 model=3stack**" to "**/etc/modprobe.d/alsa-base**".
-Worked for me after **reboot**.

Good luck.
-Chumba

---

### Post by hansie2k on 2006-07-19
chumba's suggestion works even without the alsa upgrade. Just update the options in /etc/modprobe.d/alsa-base, reboot, and boom, sound works. Thanks chumba!

I still have one problem. The front mic does not work...any suggestions?

---

### Post by thomasr on 2006-07-19
Thanks, chumba. Worked a treat.

---

### Post by fredricsolstad on 2006-08-12
Hi, 
just wanted to let you know that your fix works great in SuSE 10.1 aswell!
I might not use your dist any more, but I still think your community is great

---

### Post by danik on 2006-09-09
Hi everybody

I'm italian student.
I installed ubuntu three days ago, and until now I've looked for any solution to my problem with soundmax audio card all over the web.
I only wanna say thank to chumba, you're great.

danik

---

### Post by cobanik on 2006-12-28
Hello
I have some questio ns:
How do I do that??because ie probing lots of thing but... do i have to do this?? cd /etc/modprobe(enter) and then cd alsa-base?? because i can do that. it says that the directory does not exists (the last one)
or do i have to put this directly?? /etc/modprobe.d/alsa-base?? because it says denied access but i typed it with sudo -s
I am lost.
can anybody help me?? i hope you're good to me as i am a litle newbie

thank u.

---

### Post by fredricsolstad on 2006-12-29
> **cobanik said:**
> Hello
I have some questio ns:
How do I do that??because ie probing lots of thing but... do i have to do this?? cd /etc/modprobe(enter) and then cd alsa-base?? because i can do that. it says that the directory does not exists (the last one)
or do i have to put this directly?? /etc/modprobe.d/alsa-base?? because it says denied access but i typed it with sudo -s
I am lost.
can anybody help me?? i hope you're good to me as i am a litle newbie

thank u.

I would suggest that you use the following command to edit it in Ubuntu.. 

```
sudo gedit /etc/modprobe.d/alsa-base
```hit enter (return) and enter your password.. in a few seconds you'll be able to just copy and paste the entry :) 

Hope that clears things out for you :)

---

### Post by ken21032002 on 2007-01-06
Hallo.
I have tried the setting, "options snd-hda-intel position_fix=1 model=3stack", and the sound of my M2NPV-VM has got working.
However, the microphone does not seem to work.   Is there anybody who has also microphone got working?

---

### Post by karimjguirimkarim on 2007-01-06
many thanks, working great now

Karim jguirim karim

---

### Post by german hamster on 2007-04-12
knowing that I'm digging out a rather old thread (in germany we call such people necrophile) I wanna thank chumba/hansie2k! I am totally new to Linux and just could not solve that problem until I found this thread. I have absolutely no Idea how this solution works and why I have to do this, but it works. I'm so happy, Bob Marley makes working so much nicer:D

---

### Post by damaged1 on 2007-04-16
Hi,
I've had the same problem as above...

so far i've:
updated my alsa drivers and alsa lib to 1.0.14rc3 ( had to download the bzip'd packages coz they weren't in the feisty packages yet)
added the line "options snd-hda-intel position_fix=1 model=3stack" to /etc/modprobe.d/alsa-base

this gave me sound out of the front right speaker (note these speakers work fine with my laptop)

added "noapic" to the kernel line in /boot/grub/menu.lst

still can't get sound working in anything but the front right speaker... help?

Oh and I'm running feisty kubuntu beta.

also: if i run alsamixer sound dies until i restart alsa

---

### Post by bricin on 2007-05-09
Update: um... nevermind. It just starting working. I cannot tell if this was the option line in alsa-base or messing with the UI to make sure everything was unmuted or what, but the sound is definitely working now. Thanks to all.
---
I'm running Ubuntu 7.04. I tried adding the option and rebooting, still no sound.

Any other places to look? I have tried:
[LIST=1]
[*]alsamixer
[*]the ui in the upper right corner (sound icon)
[*]updating alsa
[/LIST]

Nothing works as yet. The system appears to detect the card properly and the card is known to work under Windows XP (dual boot laptop, Toshiba Portege M200 if that is helpful).

---

### Post by kaykfrink on 2007-05-13
> **damaged1 said:**
> Hi,
I've had the same problem as above...

so far i've:
updated my alsa drivers and alsa lib to 1.0.14rc3 ( had to download the bzip'd packages coz they weren't in the feisty packages yet)
added the line "options snd-hda-intel position_fix=1 model=3stack" to /etc/modprobe.d/alsa-base

this gave me sound out of the front right speaker (note these speakers work fine with my laptop)

added "noapic" to the kernel line in /boot/grub/menu.lst

still can't get sound working in anything but the front right speaker... help?

Oh and I'm running feisty kubuntu beta.

also: if i run alsamixer sound dies until i restart alsa

damaged1, I am having the same exact problem (sound out of the front right speaker, sound dieing if I make any changes with alsamixer.) I was wondering if you had any success fixing it.

---

### Post by kurrrt on 2007-05-15
I have the same problem with microphone. Neither integrated nor external mic is working.  Has anyone fixed this?


> **ken21032002 said:**
> Hallo.
I have tried the setting, "options snd-hda-intel position_fix=1 model=3stack", and the sound of my M2NPV-VM has got working.
However, the microphone does not seem to work.   Is there anybody who has also microphone got working?

---

### Post by acmarfil31 on 2007-06-04
Hi, I'm also having the same problem.  The microphone doesn't seem to be detected by SKYPE, but I can hear my voice coming out.

Is it a device problem, or any setting I need to to?  I'm having Feisty Fawn with updated kernel.  Skype1.3 or 1.4alpha neither works, even the Sound recorder also doesn't work at all.

Any help would be appreciated much.

Regards

---

### Post by Ancient1 on 2007-07-12
Me too .. 

P5B Deluxe , SoundSux  ( NOT a mistake) 
HDA Intel / Alsa  Mixer 
Feisty AMD64, latest everything .. just installed a week ago 

No Mic Recording , [COLOR="Red"]even though[/COLOR]  the mic IS working i.e I can hear the mic ,  

Alsa Mixer , and every mixer I tried, doesn't show MIC in recording , only Capture - select device . and Capture 1 & 2 ..  

Tried alsa conf setting mentioned in the documentation and on the net .  

^&%*$^#   :confused:

---

### Post by kuffi on 2007-08-12
Wow - the Asus webpage has a linux driver "ZIP" for the Asus M2N-SLI Deluxe.
It the drivers are not like expected in the normal sections like "audio, etc..." is in the "other" section. I didn't tried the drivers so far. 

Here is the link:
[http://dlsvr03.asus.com/pub/ASUS/misc/LinuxDrivers.zip](http://dlsvr03.asus.com/pub/ASUS/misc/LinuxDrivers.zip)

pfiertie
kuffi

---

### Post by wrx230 on 2007-10-23
Has anyone gotten their digital out (fiber optic) to work? My headphones work fine, but nothing seems to be coming out - and I have a nice sound system I used to use when I used winblows :/. Maybe its just something I am doing wrong? I have an asus p5b mobo, but it looks like they use the same sound. Thanks!

---

### Post by Nxx on 2008-06-10
This advice did not help me.

---

### Post by abdu_mka on 2008-07-24
can any one give us the steps i'm new in linux , please the steps , in a simple way, 

thanx in advanced

---

