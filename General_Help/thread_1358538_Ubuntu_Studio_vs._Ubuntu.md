---
title: "Ubuntu Studio vs. Ubuntu"
date: 2009-12-18
forum: General Help
---

### Post by wbm on 2009-12-18
Hello, could someone please fill me in if I can use Ubuntu Studio as my main operating system?
I am currently using Ubuntu in a dual boot with Vista machine.
The whole family is using Ubuntu for e-mail, web, homework etc.

Specifically, can Ubuntu Studio - which I'll use for home music recording - also do e-mail, Flash on web pages, YouTube etc. etc.
I understand that it uses a different kernel and that may pose some problems for regular day to day use.

Thanks for any input.

---

### Post by Soapy.Illusions on 2009-12-18
I have personally never tried Ubuntu-Studio, but I think it would be perfect for your situation

Yes you can use it to do e-mail flash and all the rest, the main difference is it comes default with a lot more multimedia programs, and most importantly has JACK pre-configured which can be a hassle in Ubuntu

So yes I would advise it, try the live CD first if you want to be sure

---

### Post by audiomick on 2009-12-18
Hi.
No live CD for Ubuntu Studio the last time I looked.

I have been using Ubuntu Studio 64 bit as my main system for about 2 years. I haven't had any problems relating to it being Studio and not "standard" that I am aware of.

You will have to add a couple of things that are standard in Ubuntu, I think Evolution and I think Open Office only has the writer on Ubuntu Studio. Both versions access the same repositories, so you can install anything that is on standard Ubuntu.

---

### Post by wbm on 2009-12-18
Thanks!
I am running it semi-sucesfully in Virtual Box and noticed that a bunch of "standard" programs are missing by default, e.g. Open Office and Evolution.
But that can easily be added.
SO no problem with YouTube etc.? I had read that the real time kernel would have problems with all kinds of "regular" things like e.g. Flash.

---

### Post by Darael on 2009-12-18
You could add the Studio elements to a standard Ubuntu install by installing the "ubuntustudio-desktop" package, and then if you had any issues with Flash on the realtime kernel just selecting the other at boot time for that sort of task... or something like that!

---

### Post by wbm on 2009-12-18
> **Darael said:**
> You could add the Studio elements to a standard Ubuntu install by installing the "ubuntustudio-desktop" package, and then if you had any issues with Flash on the realtime kernel just selecting the other at boot time for that sort of task... or something like that!

I looked into that, but that would then also require doing a lot of manual configurations for e.g. audio.

---

### Post by wbm on 2009-12-18
I had started a separate thread, but maybe I can ask this here too then:

I have a PC that currently dual boots Vista and Ubuntu from one internal 200gb drive.
Ubuntu is the main OS used by the family for e-mail, games, web, homework etc.

I want to add a second 500 gb SATA hard drive and install Ubuntu Studio on it for my music stuff.

When I add the second drive, can I just install Ubuntu Studio on it and have it show up as a third option on boot up? Currently I can choose between Ubuntu and Vista on boot.
Will Ubuntu Studio then show up as a third option?

Is there anything else I have to be aware of before I do this? E.g. where does the bootloader actually sit? E.g. in case the first drive dies some day?
Thanks!!!

---

### Post by Darael on 2009-12-18
You'll need to do two things:
1) make sure the Ubuntu Studio install process puts GRUB on the 500gig drive
2) boot into the 200gig drive's Ubuntu and run "sudo update-grub"
After that, Studio should show up as another boot option in your normal GRUB menu.

---

### Post by audiomick on 2009-12-18
Ha, thought that was you!

You tube works for me, and these days I rarely have a web site that doesn't work.

I have to say though, that my attitude is if a site has so much flash crap on it that I can't see it, I boycott it.

---

### Post by wbm on 2009-12-18
> **Darael said:**
> You'll need to do two things:
1) make sure the Ubuntu Studio install process puts GRUB on the 500gig drive
2) boot into the 200gig drive's Ubuntu and run "sudo update-grub"
After that, Studio should show up as another boot option in your normal GRUB menu.

Darael, I take you up on "If anything I say is unclear, don't hesitate to ask for a breakdown."

Step 1: put new hard drive in machine

Step 2: Stick Ubuntu Studio DVD in computer and boot to installer

Where do I tell it to put Grub on the 500 Gig drive? During install? After install?

When all is installed, how do I then boot into the 200 gig drive Ubuntu? Do you mean from the BIOS startup disk order? Don't I have Grub then on both drives? Then when I update Grub on the 200 Gig drive to show both Ubuntus and Vista, do I then have a "spare" unused Grup on the 500 Gig drive?

Thanks!

---

### Post by wbm on 2009-12-18
> **audiomick said:**
> Ha, thought that was you!

You tube works for me, and these days I rarely have a web site that doesn't work.

I have to say though, that my attitude is if a site has so much flash crap on it that I can't see it, I boycott it.

I take it you don't have kids then - addicted to Club Penguin? 
:(

---

### Post by audiomick on 2009-12-18
> **wbm said:**
> I take it you don't have kids then - addicted to Club Penguin? 
:(
No, no kids, and I am old enough to remeber the world before there were computers in every house.

Yes, you could say that...:)

---

### Post by garyed on 2009-12-18
There really isn't much difference between the two. 
Studio has a lot of audio & video programs installed.
Studio has Jack setup (communicates & syncs music programs)  
Studio has real time kernel for better audio latency
Getting around is virtually the same.
I don't think Studio comes with Open Office or much graphic programs.
It's Grub didn't do well for me.
I haven't had a good experience recording wise so far with U-studio 9.10 
but U-studio 7.10 Gusty worked great.

---

