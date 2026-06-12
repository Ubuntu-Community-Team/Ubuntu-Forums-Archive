---
title: "system slow down when on docking station"
date: 2010-06-01
forum: General Help
---

### Post by g.a. on 2010-06-01
Hi,

my laptop (a Dell Precision M2400) works just fine alone.

When I put it on the docking station, after a while it starts slowing down the performance, the current open applications take all the CPU, the temperature raises and soon it is not possible to do anything but switch off the laptop, undock and switch it on again.

I'm using this laptop since one year, from 8.04 until the current 9.10, and I always had those problems. They occurred quite rarely, however, now it is systematic.

Is there any hint? how can I verify if it is an hardwrae or software problem (maybe the Nvidia driver?).

Thanks in advance,
g.

---

### Post by dustinmarlowe56 on 2010-06-01
I haven't heard of anything like this before, if you have always had the issues but they are just now becoming constant then I would suggest reverting back to 8.04 and see if the problem still persists as badly. This would at least let us know if it was an issue with the OS or a system hardware malfuction.

---

### Post by g.a. on 2010-06-07
well, I have not tried yet with a former version since in the last days I made a kernel upgrade (2.6.31-22) and I tried by changing some settings related to the power management.

unfortunately today, after 3 hours of fine work, it happened again and even after a shutdown.

currently I restarted on the laptop without docking station, the temperature is down to 46 degrees (it was 53 when happened) and the machine is working fine.

I'm wondering about maybe upgrading to 10.04 and check if it happens again...

g.

---

### Post by jeruzzzzzzzz on 2010-06-07
I have the same problem with the same machine. I just tried to install the latest nvidia driver... and no help ... I changed my RAM, I changed the motherboard... nothing... (and I have 10.04)...

---

### Post by Smart Viking on 2010-06-07
Can it be because the docking station somehow stops airflow?

---

### Post by jeruzzzzzzzz on 2010-06-07
have been tracking the temperature... and everything seems normal...
Actually I did not know this could be the dock station...  

Temperature of the CPUs stay around 45/47 C, HDDs stay around 50C and nvidia stay around 68/70C but the DELL people told me it was all good... 
I really don't know

Correction: I tried without the dock, and it seems to work well... additionally, the GPU reaches max 63C ... that might be as simple as this.
I will try putting some kind of cooler under the dock+laptop

---

### Post by g.a. on 2010-06-11
well, here is the positive end of the story.

I had put an external strong fan to the laptop+docking and, via conky, monitored a 6-8 degrees celsius less than the previosu steady state temperature. The system perfectly worked for hours.

I then called Dell assistance and today they changed me the cooling device (well also the motherboard but the technician told it was only to be sure and avoid an additional travel).

Now I'm working at almost 20 degrees less than the "critical" temperature that blocked my system.

For the moment everything is ok.

best,
g.

---

### Post by jeruzzzzzzzz on 2010-06-14
hum, I also bought a fan to slide underneath, and it seems it works well... what temperatures for the GPU, CPUS and HDD? (before and after) just to see if I can call Dell and ask them to change the ventilation system.

Thanks!

---

### Post by LinuPP on 2010-06-14
most hdd dock can be compatible with windows and mac os. From your state, it's not the hardware problem.. More infor about [hard drive dock]("http://www.espow.com/wholesale-sata-hdd-docking-station-for-mac-support-1394b-1394a-firewire-port.html"), you can read this post:
[http://www.techsupportforum.com/hardware-support/hard-drive-support/405380-sata-sata-ii-hard-drive-dock-compatibility.html](http://www.techsupportforum.com/hardware-support/hard-drive-support/405380-sata-sata-ii-hard-drive-dock-compatibility.html) , you need to log in.. 

Also have a read through:
[http://ezinearticles.com/?Issues-About-Choosing-a-Hard-Drive-Dock-Station&id=4391552](http://ezinearticles.com/?Issues-About-Choosing-a-Hard-Drive-Dock-Station&id=4391552)

---

### Post by jeruzzzzzzzz on 2010-06-14
Hi there, we are talking about a laptop dock

---

### Post by g.a. on 2010-06-15
Hi,

I used to check the temperature with the variable temp of the software conky.

I'm not sure 100% what kind of temperature I was monitoring but after the hardware change now the temperature fallen down of almost 10 degrees celsius.

Even the keyboard is not warm anymore.

Hope this help, feel free to make specific question

Best
g.

---

### Post by jeruzzzzzzzz on 2010-06-15
Well I am actually thinking asking Dell to change the cooling system (I actually did not know it could be changed independently of the motherboard). But before doing so I would like to compare the temperature I get with the one you have, now that they changed it. Would you mind checking it? Thanks!

---

### Post by g.a. on 2010-06-16
first let me precise that the technician DID change also the motherboard. he said that, according to the symptoms of my laptop, it was useless but it prevents the possibility to an additional intervention (i'm 100 km away from the nearest interventaiton center).

the temperature used to be around 45-48 degrees celsius and became critical after 50.

currently it stays always under 40.

again, i'm not sure what kind of temperature i'm monitoring, i can give you my conky.conf and you can just run on your machine.

btw the keyboard was some kind of warm and now this feelings is gone too.

best,
g.

---

### Post by jeruzzzzzzzz on 2012-02-07
Actually, I ended up adding a cooling system underneath the dock+laptop and that solved the problem... Doing a bit of research you can read around that the GPU is not cooled on this laptop (as opposed to the CPU). So having other monitors to work with makes the GPU temperature go up... Some not so good design details I guess...

---

### Post by mbelladonna on 2012-03-14
> **jeruzzzzzzzz said:**
> Actually I ended up adding a cooling system under the dock and that solved my problem! The GPU on this latop is actually not being cooled as the CPU is... some design glitch!

I have the exact same problem with the exact same equipment. My GPU temp raises up to 68C when docked making my computer almost unusable. I wonder which cooling system you placed under the dock and how did you do it (I see not much space to place a cooling system there). Can yo send me a link or pictures of the cooling system itself and how you placed it?

Much appreciated.

---

### Post by howefield on 2012-03-14
Old thread closed.

---

