---
title: "Help computer freezing"
date: 2011-10-10
forum: General Help
---

### Post by Noamo30 on 2011-10-10
I am having a problem with my desktop PC, It seems as if my processor cant handle the simplest of tasks, for instance i would open up google chrome and go to a website and after about a minute or so the screen would become lightly pixelated, freezes and then becomes unpixelated, my guess is the processor because just waving around my mouse brings it up to about 20 load on both cores.



3 gb ddr2 4200 Ram
nividia Geforce 8500gt
AMD phemnom 2 dual core

---

### Post by An Sanct on 2011-10-11
Welcome to the forums!

The first thing, that came to my mind was - Is it maybe overheating? If you can, try opening the case, make sure, that you do not void the warranty, doing so!

If the problem goes away, then it is overheating.

If you do so, make sure, that no children or pets have access to your machine ;) nobody should touch anything inside - specially when running (under voltage/plugged in).

The second guess would be the RAM. So while booting, hold down the shift key and in GRUB select the memtest86 option to check the health of your RAM.

---

### Post by sanderd17 on 2011-10-11
And if it is over heating, try vacuum cleaning your computer (while unplugged).

---

### Post by An Sanct on 2011-10-11
> **sanderd17 said:**
> And if it is over heating, try vacuum cleaning your computer (while unplugged).

Yes, if there is a lot of dust, vacuume it, specially the ventilators.

Whilst vacuuing, they will spin - do not overdo that, they might get damaged and that will create really bad overheating.

PS. Let me note one more time, to be careful with an open machine, there is a high risk of injury or complete computer failure, if one would touch the insides while it is operating/plugged in! (I almost feel sorry for ever mentioning that possible solution ...)

---

### Post by Johnb0y on 2011-10-11
> **sanderd17 said:**
> And if it is over heating, try vacuum cleaning your computer (while unplugged).

just a bit of advice, do not Vacum your PC... use compressed air if possible... vacum can create static and **** you PC totally if not careful.

p.s. make sure you PC is up-to-date will all software and try doing the mem test as [An Sanct]("http://ubuntuforums.org/member.php?u=1241936") suggested. sounds like it could be RAM... possible HDD...

cheers :D

---

### Post by mörgæs on 2011-10-11
Try having **top** run in the background while doing normal tasks. This will show which application(s) is heavy on the system.

---

### Post by Noamo30 on 2011-10-11
thanks in advance. but i dont think that it is the HDD or the overheating, it is an ultra computer and has four fans on it, the biggest of which is on the prcoessor, one fan is out however, the fan on the power supply could this be the problem, i used system tests and benchmark, and i cant find a way to upload the results, as for running top i dont see anything out of the ordinary

---

### Post by Noamo30 on 2011-10-11
[https://www.dropbox.com/home#:name-sorter,0::](https://www.dropbox.com/home#:name-sorter,0::)
i uploaded the results to dropbox in the folder computer

---

### Post by An Sanct on 2011-10-12
> **Noamo30 said:**
> ...one fan is out however, the fan on the power supply...

That would mean, that basically the PSU is overheating.

This could mean: (examples)
3,7V instead of 3,0V for RAM, the result RAM corruption, resulting in random pixelation on the monitor and overall strange computer behavior...

10,3V instead of 12,0V for HDD, the result would be strange read/write operations ...

I skipped the current stuff (Amperes), the voltage part is explanatory enough. But just to inform you (I apologize, if you already know), that electric "Power" equals voltage (u) times current (i) square. Giving p = u * i * i.

So **get a new PSU - ASAP** as excessive voltage or current can actually kill/fry any of the components!

*note: read edit, below*. At worst, if you really need to use the computer, keep the machine opened, allowing cool air to flow from outside.
edit: Actually, removing the side of the computer helps only if it is a "static" side, so it has no fans. If the side plate has fans on it, it would actually be better to leave it on, as it cools down the system.
PS. there is a "go advanced" button left below and by clicking it, you are given more options with editing - amongst them is "attachments" or a paper clip symbol, there you can attach files.

---

### Post by Noamo30 on 2011-10-12
thank you an sanct, i do have a fan on the open side of the computer but i could take off the back panel if it helps ive attached the file now

---

### Post by Noamo30 on 2011-10-12
ok sorry id didnt upload the last time, here is the file

[COLOR="Blue"]Removed the attachment as it contained some personal info - CharlesA[/COLOR]

---

### Post by Noamo30 on 2011-10-12
ok here is some screenshots of the pcu going wierd

An Sanct what power supply would you suggest, im trying to stay cheap

---

### Post by An Sanct on 2011-10-12
Looking at that pictures, the thing I notice is "plugin-containe" eating more than 90%.

With an uptime of cca 20 minutes and "plugin-containe" having cca 40 minutes run time (two processors, double the time)

I also noticed, that you have firefox in the background (I guessed it was FF) where "plugin-containe" is one of the plugins you have installed. So, my proposal is to try to run FireFox without any plugins or addons.

edit II. Oh and at this moment, What FireFox and Flash version are you using???

PSU...
To make sure, that we are talking about the same thing, here is a link:
[http://en.wikipedia.org/wiki/File:PSU-Open1.jpg](http://en.wikipedia.org/wiki/File:PSU-Open1.jpg)
Please confirm, that this is the component with the dead fan.

edit: I checked, PSUs are from 15&#8364; (roughly 20$) upwards, I'd propose not to be too cheap here :) as it is not expensive. Also consult someone from the store & don't buy the most expensive one ... you don't need it ;). Also I asked an admin to remove the odt file, you uploaded since it is not needed and contains too much data :)

---

### Post by Noamo30 on 2011-10-12
im running a pretty new version maybe one or two behind current

yes that is what im talking about for PSU

even with taking out the plugins it doesnt make sense that it should be running that slow, i used to use the hard drive in an external drive and had no problems whatsoever. 

it doesnt make sense that it would be running so slow with a computer of these specs as shown on the odt file, which is why i uploaded it.

i was running firefox ad playing a flash game, and it didnt run slow at all, so i dont know why it doesnt freeze then but it tends to freeze more when i open up a program like firefox, change tabs or open up more than one program

---

### Post by Noamo30 on 2011-10-12
this is the one in my pc all of the parts are ultra
[http://www.xoxide.com/ultra-x-finity-600w-psu.html](http://www.xoxide.com/ultra-x-finity-600w-psu.html)

---

### Post by An Sanct on 2011-10-12
For flash, I recommend the use of the FlashAid plugin for firefox and the use of the latest version, same goes for FireFox.

Thats a great PSU, go with something in that category (powerful enough)

It has two ventilators? I googled for that PSU and some have two ... so one is not working?

PS. If the PSU performs okay otherwise, than the ventilator might be stuck - physically.

---

### Post by Noamo30 on 2011-10-12
if you mean fans then yes it has two and they both dont spin, and how do i find out if the psu performs okay otherwise

edit: the fans spin ok by moving them with something, they dont seem to be blocked at all

---

### Post by An Sanct on 2011-10-13
With performing 'okay' I meant, the computer has no other power problems other than those fans.

Considering, this is a more powerful (advanced) PSU and I don't know how it behaves, the fans could be automatic, so they spin only when needed ... If that is so, then my whole overheating theory is wrong.

I wouldn't want you to throw a perfectly good working PSU away, buy another and still be stuck with the same problems :)

Can you please type 'sensosrs' in the terminal, it should produce an output similar to this one (mine)

```
an@drak:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +46.0°C  (high = +83.0°C, crit = +99.0°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:       +35.0°C  (high = +83.0°C, crit = +99.0°C)

coretemp-isa-0002
Adapter: ISA adapter
Core 2:       +37.0°C  (high = +83.0°C, crit = +99.0°C)

coretemp-isa-0003
Adapter: ISA adapter
Core 3:       +34.0°C  (high = +83.0°C, crit = +99.0°C)

atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:       +0.00 V  (min =  +0.80 V, max =  +1.60 V)
+3.3V Voltage:       +0.00 V  (min =  +2.97 V, max =  +3.63 V)
+5V Voltage:         +0.00 V  (min =  +4.50 V, max =  +5.50 V)
+12V Voltage:        +0.00 V  (min = +10.20 V, max = +13.80 V)
CPU Fan Speed:      65504 RPM  (min =  600 RPM)
Chassis1 Fan Speed:    0 RPM  (min =  600 RPM)
Chassis2 Fan Speed: 65504 RPM  (min =  600 RPM)
Power Fan Speed:    65504 RPM  (min =    0 RPM)
CPU Temperature:      +0.0°C  (high = +45.0°C, crit = +45.5°C)
MB Temperature:       +0.0°C  (high = +45.0°C, crit = +46.0°C)

an@drak:~$ 

```(note, that all odd numbers, like 0 and 655504 are extremes, meaning that the sensor in my case is not working, but thinks that it is...)

---

### Post by Noamo30 on 2011-10-13
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +58.0°C                                    
Core1 Temp:  +60.0°C   

this is what i got nothing about fans

---

### Post by An Sanct on 2011-10-14
That looks fairly normal ...

Have you updated the browser yet?

---

### Post by Noamo30 on 2011-10-14
yes it has nothing to do with the browser it isnt a software issue i have used it with the new ubuntu cd and it still gets messed up with any program

---

### Post by Noamo30 on 2011-10-15
i discovered that my heatsink's thermal paste has started to chip away, it has barely any left and in splotches. This seems like a likely candidate for the problem

---

