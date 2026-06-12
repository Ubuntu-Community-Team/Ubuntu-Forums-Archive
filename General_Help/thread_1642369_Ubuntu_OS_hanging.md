---
title: "Ubuntu OS hanging"
date: 2010-12-10
forum: General Help
---

### Post by stayahead on 2010-12-10
Hello,

I'm having a bit of a problem with Linux apparently hanging usually when using Chrome browser, although I haven't determined if it happens exclusively when using Chrome, but this appears to be the case at the moment. The screen locks entirely and the mouse pointer does not move. The OS does not respond to any key or mouse presses. The only thing to do is hard-reboot the laptop.

I've installed Ubuntu 10.10 from a CD image. Its not installed alongside another OS. Linux is the only OS I am using on this laptop.

Its a DELL Inspiron 6400, with 120 GB hard drive and 1 GB RAM.

CPU: Intel(R) Core(TM)2 CPU T5500  @ 1.66GHz
Graphics card: ATI Technologies Inc M52 [Mobility Radeon X1300]

No custom drivers.

Does anyone have any suggestions?

---

### Post by tajiknomi on 2010-12-10
> **stayahead said:**
> Hello,

I'm having a bit of a problem with Linux apparently hanging usually when using Chrome browser, although I haven't determined if it happens exclusively when using Chrome, but this appears to be the case at the moment. The screen locks entirely and the mouse pointer does not move. The OS does not respond to any key or mouse presses. The only thing to do is hard-reboot the laptop.

I've installed Ubuntu 10.10 from a CD image. Its not installed alongside another OS. Linux is the only OS I am using on this laptop.

Its a DELL Inspiron 6400, with 120 GB hard drive and 1 GB RAM.

CPU: Intel(R) Core(TM)2 CPU T5500  @ 1.66GHz
Graphics card: ATI Technologies Inc M52 [Mobility Radeon X1300]
[SIZE=2]
[/SIZE]No custom drivers.

Does anyone have any suggestions?

[SIZE=2]I am not sure , may be this is Graphics Problem,
[/SIZE]
[SIZE=2]Go to Sytem > Administration > Additional-Drivers and check out whether it Find out some drivers for you or not..?
If it finds out.....you just has to ***enable*** it...[/SIZE]

---

### Post by kanishkdudeja on 2010-12-10
umm..just when its starting to hang..

run ```
top
``` in the terminal and post its output..

you have to install ati radeon drivers for ur graphic card..

[http://ubuntuguide.org/wiki/Ubuntu:Maverick#Install_Latest_Nvidia.2FATI_drivers](http://ubuntuguide.org/wiki/Ubuntu:Maverick#Install_Latest_Nvidia.2FATI_drivers)

---

