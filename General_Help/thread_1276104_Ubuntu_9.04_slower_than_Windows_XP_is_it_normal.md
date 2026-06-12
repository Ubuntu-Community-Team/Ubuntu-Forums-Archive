---
title: "Ubuntu 9.04 slower than Windows XP is it normal?"
date: 2009-09-26
forum: General Help
---

### Post by UranUtan on 2009-09-26
Hi,

I am a committed Ubuntu user. This post is not a troll. The computer is Pentium 3, 1 GHz, 780 MB Ram. 120 GB hard drive, a mediocre video card (nVidia TNT2, 32 MB).

This same computer is used to run natively Windows XP SP3 and later reformatted to run Ubuntu 9.04 x32.

I don't do any benchmark to prove if one system is more optimized than the other. This is an old computer my wife was using for web surfing and typing office documents. The observation of responsiveness is just base on what we perceive when using each OS on the same computer. Here is what I have found:

- STEP 1: The computer is prepared to be ready for reasonable use: OS + system updates. (Ubuntu add nVidia driver, XP add Office, Firefox and a few freeware utilities)

- At this stage, Win XP feels more snappy than Ubuntu and also consume less resources. This is strange, I would expect the opposite.

- STEP 2: Install AnitVirus, Anti Spyware for WinXP. There is nothing to do for Ubuntu.

- At this stage, XP crawled in to a halt for any operation related to Internet (surfing or even downloading a simple file, no game, no P2P). Firefox become very slow. And the slowness of XP is increased over time.

So WinXP is dragged down by a bunch of unwanted crapwares and the anti-evarything to fight these craps. I understand perfectly. But before these craps occured, WinXP was faster than Ubuntu Desktop. Is it normal?

---

### Post by ninjapirate89 on 2009-09-26
I recently reinstalled XP and ubuntu on my laptop and a freshly installed XP does seem to be slightly faster. I only use XP for stuff that won't work in ubuntu (like my Zune software) so I didn't install anti-virus or anything, but in my past experiences with XP, the more you install on it, the slower it gets.

---

### Post by snowpine on 2009-09-26
> The minimum hardware requirements for Windows XP Home Edition are:

    * Pentium 233-megahertz (MHz) processor or faster (300 MHz is recommended)
    * At least 64 megabytes (MB) of RAM (128 MB is recommended)
    * At least 1.5 gigabytes (GB) of available space on the hard disk 

> Ubuntu should run reasonably well on a computer with the following minimum hardware specification. However, features such as visual effects may not run smoothly.

    * 700 MHz x86 processor
    * 384 MB of system memory (RAM)
    * 8 GB of disk space 

Conclusion: Windows XP is an older operating system (2001) than Ubuntu 9.04 (2009) and has lower system requirements, therefore it might run faster on some older hardware.

As you point out, however, a bare-bones install of Windows is not really usable; adding the necessary antivirus etc. slows it down considerably. Ubuntu is secure and ready to use in its basic configuration.

---

### Post by UranUtan on 2009-09-26
> **ninjapirate89 said:**
> I recently reinstalled XP and ubuntu on my laptop and a freshly installed XP does seem to be slightly faster.

I have also made a "proof of concept". On a Pentium 4, 2.8 GHz, 3 GB Ram running Ubuntu 9.04 x32. I create a virtual machine with WinXP SP3 + all updates. The VM is configured so that it cannot access the Internet. So I don't install any Anti Virus, Anti Spyware. And it runs indeed pretty fast. With all the hype about Win7 at the moment, few people realize that the best Windows you can find is WinXP ... with the condition that it must be disconnected from the Internet..

---

### Post by wojox on 2009-09-26
XP runs great when first loaded on your computer, but give it a month or two and compare it to Ubuntu. I had to reinstall XP every tree to four months  back in the day. Ubuntu, not yet in the six months I've been using it.

Ubuntu is actually faster due to the fact I can tweak it a lot easier than XP.

---

### Post by UranUtan on 2009-09-26
> **snowpine said:**
> The minimum hardware requirements for Windows XP Home Edition are:

* Pentium 233-megahertz (MHz) processor or faster (300 MHz is recommended)
* At least 64 megabytes (MB) of RAM (128 MB is recommended)
* At least 1.5 gigabytes (GB) of available space on the hard disk
Thank you for the reference. Just curious, where do you get this minimum requirement for Windows? If you get that from Microsoft then I don't trust the number. For me this means "minimum hardware requirements to display the login screen". That is why there is a lot of computers rated Vista ready. And indeed, when you see the laptops on the shelves, all you see is the login screen.

Well I am almost joking there, but I hope to get the ironic point. Back to the topic, I am still a little bit disappointed that Ubuntu is not as snappy as I was hoping. I wonder if Xubuntu would be better for this low specs computer.

---

### Post by kerry_s on 2009-09-26
[http://library.gnome.org/admin/system-admin-guide/stable/performance-0.html.en](http://library.gnome.org/admin/system-admin-guide/stable/performance-0.html.en)

check the performance tips, with some tweaking you can get it up to speed. i ran jaunty on 450mhz 256mb ram, so i know it can be done.

i switched to debian lenny & did a base install build up, the programs are older, but run much better on the old stuff.

---

### Post by blueridgedog on 2009-09-26
> **UranUtan said:**
> I am still a little bit disappointed that Ubuntu is not as snappy as I was hoping. I wonder if Xubuntu would be better for this low specs computer.

You could tune Ubuntu for better performance, disabling services that you don't need and removing modules that you can do without (there are many guides for this and one posted in this thread). 

Also, keep in mind that Linux is pitched not as a faster way to do something, but a more open way to do the task.  Linux in many areas can be sluggish, but that stems from its interaction with closed source hardware and software.  I have a quad core system with gigs and gigs of ram, but flash and some animated gifs in firefox will hit my system hard.  

Linux IS faster than windows, when looking exclusively at the processing of the kernel, the act of computing and doing work.  However the GUI is often hit with the closed source software/hardware issues and can appear sluggish in certain lights.  The lack of vendor provided graphics card acceleration is a big factor as well as reversed engineered code for many network devices.

Hang in there and keep in mind that it is not a race, but a journey.

---

### Post by kerry_s on 2009-09-26
> Hang in there and keep in mind that it is not a race, but a journey.

love that, best of this year. :lolflag:

---

### Post by Timothy Benton on 2009-09-26
Windows has better hardware support, things like DirectX acceleration, mature drivers, etc. Hardware is kind of built to work with Windows. Ubuntu is "cleaner" and smarter, but hardware is tailor-made to run fast on Windows. Graphics cards are not built to run Gnome, X, Xfce, or whatever, they are made for DirectX. OpenGL is not used by many programs, even on Linux. MANY Windows apps use DirectX. Sound cards are not designed for OSS or ALSA, they are made for DirectSound.

At least that is what I think.

---

### Post by cos85 on 2009-09-27
The problem is possibly with the graphics card: nvidia discontinued support for TNT2 in Ubuntu 9.04+. The binary driver you have isn't actually being used -- you probably fell back onto the non-accelerated nv or nouveau drivers. That makes your system *a lot* less responsive (I had the same problem with an older pc).

You need to either roll back to 8.10 or install an older version of xserver (the latter might be preferable; see if there are tutorials online).

---

### Post by Lukios on 2009-09-27
I work on alot of older computers myself, and simply put, XP is faster then Ubuntu Jaunty. Like one said before, XP is older and is meant to run on older systems, but given a little time and a few programs like antivirus, it will be running like crap very soon. I personally have found it better to build my Ubuntu from a mini.iso only adding what I want, that does not include Ubuntu-desktop. I would suggest using LXDE. From my experience LXDE worsk great on PIII and I have been told that it works fine on PII as well.

---

### Post by blueridgedog on 2009-09-27
And I was remiss in not suggesting xubuntu as an alternative on your system.

---

### Post by Elcid247 on 2009-09-27
maybe compare xubuntu next time? :D

a very very feature rich OS like ubuntu cant be compared to win xp lacking loads of stuff ubuntu has, its like comparing windows xp to windows 98 n saying hey 98 is faster :D yea it sure is, but try having more features :D

im sure if u use metacity instead of compiz, turn off all graphic effects just like xp it would end up just the same speed :D cause ram n CPU usage r almost always less on ubuntu for me atleast.

btw for me i dont have any anti software installed cause ubuntu is my main OS, but um still ubuntu is faster, or atleast i can do my stuff faster, i so miss gnome-do, terminal and all my hotkeys that i set myself when im on windows, so yea ubuntu is always faster to get my stuff done... atleast for me :D

and really without antieverything ud be reinstalling windows every week or two so yea practically, ubuntu IS faster.

---

### Post by Lukios on 2009-09-27
Even xubuntu is a beast . . .

---

