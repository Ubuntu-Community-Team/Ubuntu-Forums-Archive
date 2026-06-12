---
title: "ubuntu 10.10 and SIS672 graphic card driver"
date: 2010-11-09
forum: General Help
---

### Post by Teclas on 2010-11-09
Hello. I'm new to linux (I actually only installed it yesterday to give it a try) and the first thing I noticed was the 800x600 resolution that came by default (due to the lack of drivers, of course).

I immediately searched the forums for more info and prayed that someone had the same problem and could solve it. Unfortunately, some people had, I tried to do what they did and nothing...

Anyway, is there someone that can help me and my crappy (for real) Fujitsu-Siemens Esprimo Mobile 5515 Notebook?

Thanks in advance from a desperate person

---

### Post by hblv33 on 2010-11-11
hi, do not speak English most want to help you with the help of a translator on line just like I'm doing now, see the following sites:

for 32 bits

[http://diversosassuntosbrasil.blogspot.com/2010/10/sis-671-no-ubuntu-maverick-1010-32-bits.html]("http://diversosassuntosbrasil.blogspot.com/2010/10/sis-671-no-ubuntu-maverick-1010-32-bits.html")

for 64 bits

[http://diversosassuntosbrasil.blogspot.com/2010/09/driver-mandriva-2011-0-para-uso-em-sis.html]("http://diversosassuntosbrasil.blogspot.com/2010/09/driver-mandriva-2011-0-para-uso-em-sis.html")

vesa with 3D effects 1280x768

[http://diversosassuntosbrasil.blogspot.com/2010/10/sis671-no-ubuntu-com-driver-vesa-e.html]("http://diversosassuntosbrasil.blogspot.com/2010/10/sis671-no-ubuntu-com-driver-vesa-e.html")

---

### Post by timpool on 2010-11-17
[FONT=Courier New]I do have the same situation. Since some sleepless nights i tried so many drivers, changed countless xorg.conf files and nothing did happen.
I got the fujitsu siemens esprimo mobile V5535 with an SIS Mirage 3+

I found some links they say, the vesa driver schould work - not for 3D - but it works at its best. Might be enough for office and movies etc. I would be fine with that as well.
Is the vesa driver already installed within the dis - running Maverick 10.10? Or do i have to download?

Can i use two drivers in the section "Device" i.e. : #Driver   "vesa"   and
                                                     #Driver   "sis"

Is someone out there who can help me / us?[/FONT]

...waiting here while tipping F5 any second...

---

### Post by stuarttanner on 2010-11-22
the v5535 issue was sorted with ubuntu 10.10 back in august and this fix really works though you will never get your sis graphic to run 3d.
follow this link

[http://ubuntuforums.org/showthread.php?t=1548547](http://ubuntuforums.org/showthread.php?t=1548547)


good luck

---

### Post by Teclas on 2010-12-02
thank you all for your replies.
I'm going to try them.
I'll change the topic title to [SOLVED] if it worked.

---

