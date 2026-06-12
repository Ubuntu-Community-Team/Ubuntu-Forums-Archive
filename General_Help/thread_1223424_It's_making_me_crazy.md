---
title: "It's making me crazy"
date: 2009-07-26
forum: General Help
---

### Post by Gnusboy on 2009-07-26
I am new to Ubuntu and I used to believe I could read and understand English until I attempted to add driver programs (or anything else) from a CD.
10 HOURS later, I'm still trying to find a way to add all of the system drivers from the ASUS M3A78-EM CD.My ant-sized brain can seem to do this and I would appreciate some help.
I can copy the files from a CD to the desktop, but no matter what, I can not create a WORKING archive or install what I need. The tutorials are either out-of-date, or are in someway convolutedso that I can't find a step-by-step tutorial I can follow.
I had a similar problem with installing Flash 10, but somewhere found a script that handled is perfectly. I can't rediscover where I found that though.
The initial install of Ubuntu made everything function, but I'm not sure I'm getting the right performance from my new home-built system.
What do I need to do and can anyone help?

My System:
ASUS M3A78-EM mobo
AMD Quad core Phenom 9850 running in 64-bit mode
4 Gigs Ram
640 Gig Western dig HDD
Qwest DSL 3--5 mbps
Ubuntu 9.04 64-bit

I expected this machine would speed across the universe with me in tow, but it's more like a row boat with an anchor.
Any ideas to both get the software installed AND tweek the performance?
Thanks in advance.

---

### Post by Stenrad on 2009-07-26
Hi there!

There is a very simple solution to your problem - you don`t actually need that driver cd for Ubuntu. Besides, it`s for Windows only. I have a very similar setup to yours, when I installed 9.04 all I had to do was install the graphics card drivers which can be installed via the Administration --> Hardware Drivers menu. Which graphics card do you have?

---

### Post by Gnusboy on 2009-07-26
> **Stenrad said:**
> Hi there!

There is a very simple solution to your problem - you don`t actually need that driver cd for Ubuntu. Besides, it`s for Windows only. I have a very similar setup to yours, when I installed 9.04 all I had to do was install the graphics card drivers which can be installed via the Administration --> Hardware Drivers menu. Which graphics card do you have?

Thanks for the quick response. The ASUS mobo has integrated audio & video  and has an HDMI port
Vid is ATI Radeon HD 3200 GPU.
Audio is integrated Realtek ALC1200 Hi-Def Audio 8-channel CODEC
I installed the ALSA codec, but have not reallly tested it yet. Is there a better one?
I really want to connect my HDMI TV to the 'puter so I can watch all those free Netflix movies, etc.

Again Muchas Gracias

---

### Post by bodhi.zazen on 2009-07-26
Moved to General Help and Bump =)

Please keep in mind two things :

1. The FH&F , where you posted this thread, is not a support section. Please use GH, ABT, or other support sections.

2. Please try to use descriptive titles "It's making me crazy" is not the best title for a thread. While you may be frustrated, a better title may be "help with audio" and include a description of your hardware and what you have tried to get it working.

Welcome to the forums and best of luck :)

---

### Post by Firestem4 on 2009-07-26
Here are a few tips that can help you set up your machine properly (and make it easier for future reference).

Install the following packages: (You can do this from PackageKit.Just make sure to update the sources list, or refresh..whichever the button is to do that)
Ubuntu-restricted-extras   (this installs programs like java, flash, win32 codecs, other media codecs, TrueTypefonts, etc)

xserver-xorg-video-ati

Those two will take care of your baseline install for that.

Can I ask what it is that you needed from the driver-cd for your motherboard? Because truthfully most mobo driver cd's contain software for displaying the temp or voltage or whatever.(maybe a driver for the integrated NIC's)

Also to clarify. ALSA is not a codec. It is an extensible audio framework that programs interface with too deliver audio. You can try others and you may find more luck with them if you have audio problems. (Other Audio-Frameworks include GStreamer, Xine, and PulseAudio to name a few).

Any other questions feel free to ask.

---

