---
title: "Ubuntu 12.04 is a mess.  Help me help you."
date: 2012-06-15
forum: General Help
---

### Post by pepsifx357 on 2012-06-15
Consider this my bug report since the bug reporting system refuses to work. :mad:

Initially, my first problem was that Ubuntu would not install on an external USB hard drive because GRUB failed to install.  So I used an SSD.  No big deal, just small detail.

I've been using Ubuntu for about 5 years now and thought the 9.10 release was the most broken release, for me, but 12.04 at this point takes the cake.  I don't know what's going on in Ubuntu land, or in my computer, but this thing is very broken.  I just recovered from a combined X restart and Nautilus failure.  I had to restart the whole computer because the X restart wouldn't allow me to login anymore. :confused:

I'm having random X restarts while watching videos.  It completely freezes the computer when playing 3D games(After a while).  Initially the Nvidia driver in the repo slowed my computer to a halt.  I am currently using driver 295.59 from Nvidia's website.  32bit.

Nautilus failures keep poping up, however, I don't know why.

The network just stops working after a while.  Again, I don't know why.

Automtic remote NFS connections via fstab freeze nautilus for about a minute before they connect, upon system startup.

I can't use CTRL+ALT F1-F6 to get to the prompts.  At all.  My monitor just shuts off until I hit CTRL+ALT+F7 to get back to X.

The bug reports won't report the bugs they find, because it says they are out of date or something.  I have no clue why.

Unity shows up when playing Minecraft "fullscreen."  I moded my copy of Unity to include the window dodging feature so it would go away when in "fullscreen."

Also, I have an RME HDSP MADI sound card, that when used with ALSA, makes videos playback super fast.  Pulse audio doesn't recognize it so I'm currently stuck with onboard sound.  I have a 24 track recording studio and that kinda sucks not being able to use my sound card.

I don't mean to bitch, because I could just go back to 10.04. BUT...I really, really like Unity and the new features and I want to help.  So please, help me help you.  Tell me what you need from me.

Thanks,

Ben

---

### Post by pepsifx357 on 2012-06-17
This is driving me crazy.  If I do anything realted to video 2d or 3D, it freezes my computer or retarts X.  I had been working on a presentation for 2 hours and it froze.  I lost the first one, because it got corrupted, but this one, I was able to resalvage.  I quit playing minecraft because when it would freeze, I would have to restart my computer.  Doing that corrupted my world everytime, so I would have to start over.

I've seen about 3 kernel updates and numerous X updates, but it still hasn't fixed the problem.

---

### Post by mardybear on 2012-06-17
> **pepsifx357 said:**
> This is driving me crazy.  If I do anything realted to video 2d or 3D, it freezes my computer or retarts X.  I had been working on a presentation for 2 hours and it froze.  I lost the first one, because it got corrupted, but this one, I was able to resalvage.  I quit playing minecraft because when it would freeze, I would have to restart my computer.  Doing that corrupted my world everytime, so I would have to start over.

I've seen about 3 kernel updates and numerous X updates, but it still hasn't fixed the problem.
Wow...lots of problems. My first impression would be either a hardware problem, possibly graphic card/drivers, or a corrupt/unsuccessful Ubuntu install. If it's a dual boot system, does the hardware run fine with another operating system? Through the Grub boot menu, have you tried booting from 'safe' mode kernel (or whatever Grub calls it).

I'm sure others will be able to provide more expertise and will probably request additional info, such as your system specs, log reports, etc.

Good luck, sorry i'm not much help.

marty

---

### Post by Shadius on 2012-06-17
Lots of problems for sure. I can relate to your frustrations. Going on what mardybear said, have you tried to log in using Recovery Mode, or perhaps using a LiveCD to see if that reproduces the problems? I can't offer any solid solutions myself. I'm suspecting it has to do with the drivers for NVIDIA. What graphics card do you have? 

You could run this from the Terminal:

```
lspci | grep VGA
```

Post back the results.

---

### Post by sky5564 on 2012-06-17
Sounds like a hardware issue, 12.04 is the most stable and snappy release i have ever used and it works flawlessly on my amd laptop,Nvidia is known to cause problems with linux, In fact about 90% of the threads on this forum about graphical issues are Nvidia related.

Do you have any other computers you can try ubuntu on? Keep in mind ubuntu 12.04 is going to need at least 1 GB of ram and a dual core processor wouldent hurt either.

---

### Post by Jimmyfj on 2012-06-17
> **sky5564 said:**
> Sounds like a hardware issue, 12.04 is the most stable and snappy release i have ever used and it works flawlessly on my amd laptop,Nvidia is known to cause problems with linux, In fact about 90% of the threads on this forum about graphical issues are Nvidia related.

Do you have any other computers you can try ubuntu on? Keep in mind ubuntu 12.04 is going to need at least 1 GB of ram and a dual core processor wouldent hurt either.

Your statement about nVidia drivers simply isn't true. Every nVidia-driver I've used since Ubuntu 7.04 has been really great. You might confuse the driver issue with some of the problems conserning the ATI-drivers.

I use Ubuntu 12-10a1 AND have the nVidia driver installed. My system is snappy and rock solid.

I thing his problems sounds alot more like a faulty power supply, which doesn't have enough power to keep all parts of the system running at peak level.

---

### Post by steve7777777 on 2012-06-19
> **Jimmyfj said:**
> Your statement about nVidia drivers simply isn't true. Every nVidia-driver I've used since Ubuntu 7.04 has been really great. You might confuse the driver issue with some of the problems conserning the ATI-drivers.

I use Ubuntu 12-10a1 AND have the nVidia driver installed. My system is snappy and rock solid.

I thing his problems sounds alot more like a faulty power supply, which doesn't have enough power to keep all parts of the system running at peak level.

Linux founder blasts Nvidia
Torvalds calls chip designer 'the single worst company' working with Linux
By Carly Page
Mon **Jun 18 2012**, 11:43

LINUX FOUNDER Linus Torvalds has blasted chip designer Nvidia, naming it "the single worst company" he's ever had to deal with working with Linux.

Torvalds was speaking at a forum in Finland for Entrepreneurship in Otaniemi when he made the remarks in response to a question from the audience.

A women explained that she was trying, unsuccessfully, to get Linux working on a laptop that uses an Optimus chip from Nvidia, saying, "I was expecting that Nvidia would kind of chip in and do something...[but] they said flat out 'no' they're not doing any support."

The question obviously got Torvalds a bit riled up, as he responded, "I know exactly what you're talking about and I'm very happy to say that it's the exception rather than the rule.

"And, I am also happy to very publicly point out that **Nvidia has been one of the worst trouble spots we've had with hardware manufacturers **and that is really sad because Nvidia tries to sell chips, a lot of chips, into the Android market and Nvidia has been the single worst company we've ever dealt with. So Nvidia, f**k you!"

You can watch Torvalds' express his remarks about Nvidia in the video below, at approximately 48 minutes in. µ

Source: The Inquirer ([http://s.tt/1eTD0](http://s.tt/1eTD0))

---

### Post by SeijiSensei on 2012-06-19
I think Linus is full of hot-air on this subject myself.  Certainly his issues about whether NVIDIA has met his standard of cooperation with Linux hasn't translated into observable problems for me as an NVIDIA user for about a decade now.  Other than a problem with the EDID for my Sony TV not providing the correct dot pitch, I've had zero issues with the proprietary drivers when installed via the Additional Drivers application in Ubuntu.

NVIDIA cards include a bunch of proprietary features including implementations of Windows DRM that limit the company's ability to provide an open-source driver.  Since NVIDIA reports that Windows constitutes well over 90% of its driver shipments, I'm not holding my breath for them to dance to Linus's tune in this matter.

For his part, Linus has continously refused to implement an "application binary interface" for Linux drivers which would avoid the need for recompiling kernel modules every time the kernel is updated.

---

### Post by pepsifx357 on 2012-06-21
I've got an 8800 GTS.

Thanks for the reponse guys, I'm going to trouble shoot hardware now.

---

### Post by cybergalvez on 2012-06-21
> **pepsifx357 said:**
> I've got an 8800 GTS.

Thanks for the reponse guys, I'm going to trouble shoot hardware now.

Check your memory, I was having lots of issues random restarts, crashes, freezing etc. Ended up being bad ram.

---

### Post by pepsifx357 on 2012-07-02
> **cybergalvez said:**
> Check your memory, I was having lots of issues random restarts, crashes, freezing etc. Ended up being bad ram.

Yes, I agree.  I have had trouble with my memory in the past, but I know what my RAM likes and doesn't like at this point.  After a while of the computer being turned off, I usually have to wiggle 'em around a bit to get the electrons to connect.  Once it's on, RAM usually isn't a problem.

Things have calmed down quite a bit after a few updates, regarding the random Xorg restarts, but there have been problems that have come up from the updates.  It still restarts Xorg every once in a while, but now it's once a day maybe.

I still can't use CTRL+ALT F1 or any of the other F keys to get to the TTYs.  I've lost my ability to snap windows to the edges of the screen now.  My notification area has stopped working with rhythm box.  My RME HDSP MADI card still plays youtube videos at light speed.  Google Earth doesn't work with my card now, might have been a kernel upgrade that I wasn't paying attention to though.

I probably should have waited a year before starting to use 12.04, but I was getting tired of 10.04 and the old Gnome.  I like Unity and the GUI flow quite a bit and wanted to jump into it.

---

