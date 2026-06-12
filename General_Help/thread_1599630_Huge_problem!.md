---
title: "Huge problem!"
date: 2010-10-18
forum: General Help
---

### Post by rudi246 on 2010-10-18
so I was trying to install the nvidia drivers then when I reboot all I get is a command line. Startx does not work, it says no screens found. I was dumb and uninstalled the nvidia drivers too not realizing my internet didn't work in the command line. I need to install the drivers from the live cd unless there is another way. I don't want to have to reinstall!

---

### Post by JackNocturne on 2010-10-18
Hello, you can have **networking** in command line:) , just connect your ethernet cable you should be good to go or do you connect using wireless?

---

### Post by rudi246 on 2010-10-18
nevermind fixed it with nano

---

### Post by JackNocturne on 2010-10-18
Please tell us how you fixed it, might help someone:)

---

### Post by salsaflick on 2010-10-18
Hello, you can have networking in command line. plz tell us how you solve it

[http://www.salsaflick.com]("http://www.salsaflick.com")

---

### Post by rudi246 on 2010-10-18
sudo nano /etc/X11/xorg.conf

and where it says Device change the word in quotes next to driver to vesa.

this brings back the GUI, but I still need the default drivers because it's very low resolution. Where can I get the default drivers?

edit: I have wireless internet. it wasn't working in the command prompt. I trioe sudo modprobe ndiswrapper but it doesn't matter now.

---

### Post by blackcobra on 2010-10-18
nm-applet
runs the network-manager

there are nvidia drivers in the synaptic, they might help
try, nvidia-common

gksudo synaptic

---

### Post by rudi246 on 2010-10-18
I actually downloaded nvidia-common from synaptic, that's what messed up my system. I have reinstalled Ubuntu because I had just installed it a couple days ago anyway. I still need drivers though so I can enable desktop effects. I have an NVIDIA GeForce4 420 Go graphics card on my Toshiba Satellite 2435-S255. Can anyone provide an alternate driver or instructions on how to fix this?

---

### Post by wfp on 2010-10-18
Try opening synaptic, and do a quick search for nvidia-173. Then install.

---

### Post by AoSteve on 2010-10-18
> **rudi246 said:**
> I actually downloaded nvidia-common from synaptic, that's what messed up my system. I have reinstalled Ubuntu because I had just installed it a couple days ago anyway. I still need drivers though so I can enable desktop effects. I have an NVIDIA GeForce4 420 Go graphics card on my Toshiba Satellite 2435-S255. Can anyone provide an alternate driver or instructions on how to fix this?

I actually had a similar problem with a friends laptop.  I tried the hardware (restricted) drivers and the synaptic available drivers; no go either way.

I'm not absolutely sure the location (it's been a while) but envy or envyNG something similar maybe someone can spread some light.   It's a text based installer for nVidia graphics.   It installed a legacy driver that worked with the GF4 series cards.  



Another idea (I did it on Karmic with an old system) is to actually recompile the kernel with the drivers.  There's a page on the wiki that explains the lot of it.  It's the "Not recommended method" of installation.   I didn't have a choice because I was stuck at a whopping 640x480 desktop with a GF4 Ti-4400.   It took a while to get it all correct but after it was all said and done; the thing flew like none other.  Hard to believe a GF4 and a 1.47ghz single core could push so much still LOL

---

### Post by rudi246 on 2010-10-18
@wfp: Ok, but just in case I lose the GUI again how can I get it back? Can I just uninstall nvidia-173? Last time I accidentally uninstalled the default driver too so I had no video drivers. I can do the nano thing again but the GUI is very low resolution and I never got it back to normal so I reinstalled it.

---

### Post by rudi246 on 2010-10-18
Hey aosteve do you have a link to that wiki?

---

### Post by AoSteve on 2010-10-18
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

It'll take a bit of time and you need to be patient.   But it has worked for me in the past.   I bet that system still has that thing installed...   I'd have to check!   I hope it helps.  Remember; you can't learn until you try.

---

### Post by AoSteve on 2010-10-18
I was reading through that wiki page; and it links to Envy as well!  LOL!  Make sure to take a look at that too.  I know it's all command line but it allowed me to easily install legacy drivers.

---

### Post by rudi246 on 2010-10-18
Thanks for the responses so far, I will have to check out envy because I have seen another post that it works with nvidia cards. I'm a little nervous about trying anything else from synaptic so I will leave nvidi-173 if nothing else works.

---

### Post by AoSteve on 2010-10-18
I hope envy works for you.   I know it's been a help when converting my "older computer using" friends in the past.   I know that one of the laptops I used Envy for is still running 8.04LTS.  LOL

---

### Post by rudi246 on 2010-10-19
Apparently envyng is for Ubuntu 8.04 and up, but when I try to install it says one of the dependancies not satisfiable is python. I have python but it said it needs an older version. I installed nvidia-173 and it took away my GUI again. I uninstalled nvidia-173 and rebooted. After the reboot the Ubuntu boot screen came up and it stayed on that screen. The computer wasn't frozen, I could press the power button and it would go through the shutdown process, it just stayed on that screen and the HDD indicator wasn't flashing so nothing was going on.

Anyway, I had made the unfortunate decision to go back to Windows XP. Good thing I had made a virtual hard disk of my entire hard drive before I installed Ubuntu. I like Ubuntu, but I was just having too many problems, plus I use Paint Shop Pro and Dreamweaver for doin eBay stuff and GIMP and Bluefish just didn't cut it for me. I will still use Ubuntu on my desktop dual booted with Vista, but Ubuntu just doesn't work for me as the only OS.

---

### Post by AoSteve on 2010-10-19
Here's what I say...  Linux isn't for everyone in any respect.  As a matter of fact; Linux isn't a quality choice for a lot of users out there.  Even though Ubuntu is probably the easiest Linux based OS out there; it just isn't for everyone.   

Personally I only have my Desktop and there's four different distro's of linux floating about on the 2TB worth of storage.   Windows just isn't my cup of tea anymore.    

At least you tried and the problem lies with Python yes.  I believe it requires Python 2.5 or earlier?  Not sure which, but I didn't even think of it at the time.

---

### Post by rudi246 on 2010-10-20
yea something like 2.5 or earlier. The problem is my laptop is kind of old so that's probably why the default drivers don't work right for a lot of my hardware. It runs great on my desktop though, the wireless adapter worked right away and my ATI Radeon card worked right away as well with desktop effects. If I had a newer laptop or a bigger hard drive I would definitely dual boot, but I only have a 40gb hdd so that kind of limits me a little bit.

---

### Post by AoSteve on 2010-10-21
In that case, you should grab up an older distro like 8.04...   While some of the features aren't the same; the hardware should work.  The fact that my OLD Athlon XP 1700+, Realtek onboard audio (one of the FIRST versions of it), nVidia GF4 Ti-4400, and weak hardware for today standards...   All works great, even with EnvyNG in 9.04!  :)

---

