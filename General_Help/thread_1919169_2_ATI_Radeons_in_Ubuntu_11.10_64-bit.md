---
title: "2 ATI Radeons in Ubuntu 11.10 64-bit"
date: 2012-02-02
forum: General Help
---

### Post by hapticdata on 2012-02-02
Hello!

I'm new to Ubuntu and am really excited by it so far. There has just been this one part thats causing me a great deal of frustration and that's my multi-display setup with two ATI Radeons. I have been trying to follow posts through google that are taking me to various solutions and using xinerama and editing my xorg.conf file. They all seem to have a lot of risky leg-work without a very clear promise that it is even the right solution, or that I have what is necessary already installed, so I am hoping to get some clarity.

Here are the relevant bits from running "lspci":

01:00.0 VGA compatible controller: ATI Technologies Inc Juniper [Radeon HD 5700 Series]

05:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5670]


I have 3 monitors, 2 23" LG IPS Monitors that run 1920x1080 and one 26" Samsung that runs 1920x1200.

The 2 LG's are connected to my Radeon 5700 over DVI and the Samsung is connected to the Radeon 5670 over HDMI.

I have managed to get the 2 LG monitors to extend, they appear in System Settings->Displays as a blue and a green ' Goldstar Company Ltd 23" '

At this point I have done the following:
[LIST=1]
[*]installed ubuntu from inside windows (Wubi)
[*]booted into ubuntu and installed the 300+ updates
[*]tried fixing my problem by installing the proprietary ATI drivers (one of which would not install)
[*]began reading posts describing those drivers as problematic
[*]followed a wiki on "RadeonDrivers" to remove "fglrx"
[*]
[/LIST]

I have not installed any other drivers for anything.

I have been looking at this wiki: [https://help.ubuntu.com/community/XineramaHowTo](https://help.ubuntu.com/community/XineramaHowTo)
in conjunction with this post:
[http://web.archive.org/web/20090228203550/http://www.paralipsis.org/2006/01/enabling-xinerama-in-ubuntu/](http://web.archive.org/web/20090228203550/http://www.paralipsis.org/2006/01/enabling-xinerama-in-ubuntu/)

both seem a little hard to trust, as far as being the right solution and whether or not they are up to date. 

I am a developer, but not so much c/c++ and I am brand new to linux, I'm comfortable with command-line but not to the extent that the average person in this forum probably is.

I would love to get a clear explanation as to what I need to do and have some confidence that it is the right process. Still holding on to a hope that maybe there is just an installer I can double-click :)

thanks!

---

### Post by hapticdata on 2012-02-03
Can someone please point me in the right direction here?

Is this what I should follow? [http://web.archive.org/web/20090228203550/http://www.paralipsis.org/2006/01/enabling-xinerama-in-ubuntu/](http://web.archive.org/web/20090228203550/http://www.paralipsis.org/2006/01/enabling-xinerama-in-ubuntu/)

---

