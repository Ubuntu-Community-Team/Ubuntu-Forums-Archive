---
title: "HP EliteBook 8540w"
date: 2010-07-09
forum: General Help
---

### Post by aeon.flux on 2010-07-09
hi there, i'm going to but a new notebook, i wanted alienware m11x, but it looks like i will buy HP EliteBook 8540w ( some specs can be found here - [http://www.alza.sk/hp-elitebook-8540w-d162490.htm](http://www.alza.sk/hp-elitebook-8540w-d162490.htm) )

so i just wanted to know, if there is somebody, who tried to use ubuntu on it, of some notebook that have the same parts (CPU, GPU...) i mean, that if it will be posible to use ubuntu on this one, if will wifi work etc... 

can somebody give me some answers?

---

### Post by krazyd on 2010-07-11
Hi

I've got the 8440p elitebook, and it works very well with a couple of exceptions:
[LIST]
[*]fingerprint reader doesn't work
[*]Suspend/Hibernate doesn't work - it seems to be a display problem though, and I'm on integrated graphics so it may not affect you.
[*]Ambient light sensor and screen brightness keys don't work properly, however screen brightness is adjustable in "power settings", and it automatically dims when going to battery.
[*]Wimax support is a little patchy ([though it's being worked on]("http://ubuntuforums.org/showthread.php?t=1008200")). I haven't actually tried it myself.
[/LIST]

Basically, this is very new hardware and I expect most of these bugs to be ironed out quickly. All the above points relate to Kubuntu 10.04 which is otherwise very stable and a pleasure to use. Elitebooks are very nice machines :D.

Edit: [Here is the suspend bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/570604"). There are some reports of suspend working on Maverick, though I haven't tried it.

---

### Post by aeon.flux on 2010-07-13
thanx a lot for answers : )

i've used ubuntu for the first time (and still using it) one year ago on my HP Pavilion dv6000. Some things don't work, like card reader 5in1 or wireless control, but i can live with that. 

But i have problem with cooling or something, because when i turn on pc, it's HOT in few minutes(then i have wet hands and my keyboard is dirty). I had the same problem with windows Vista that was preinstalled, and Windows 7 too, so I think that it's the hardware problem(not dirt). That's why i don't like HP notebooks, i really wanted Alienware or Lenovo Thinkpad, because my friends has these and it's really awesome. But the HP Elitebook looks like the best for me right now(price&hardware), but i'm afraid that i will have the same problems with Elitebook. I don't even know anybody who would tell me, that Elitebooks don't have these problems.

...help.. : (

---

### Post by aeon.flux on 2010-07-27
...so i bought that HP Epitebook..

nice piece of work. there are some details that i dont like, but in fact, its ok. 

here is the best part - when i fist started windows, i took almost 1 hour of installing, and after that i finaly saw a logon screen. when i pluged in my USB Flash with ubuntu installed (32bit ubuntu into 64bit pc) i just started up and everything works :D 
full resolution, all programs, touch sensitive buttons, touch pad, track point, wifi, webcam, new nVidia Quadro FX GPU, some things work better than in windows :D

ubuntu RULZ!!!! :KS :KS :KS :KS :KS

---

### Post by krazyd on 2010-07-27
congratulations! :D

did you get the 8540w? and how does suspend work for you?

---

### Post by aeon.flux on 2010-07-28
yes, i get exactly that model that i mentioned in link. looks like i will use windows only for playing games like assassins creed 2 and working with rhinoceros, maya, and ubuntu for everything else..

---

### Post by arsenix on 2010-08-30
Are any of you 8540w users using the docking station?  So far the only "non correctable" issue I am having under Ubuntu is that the notebook fails to resume when I dock or undock while it is asleep.  Machine just does not wake up properly... anyone else seeing this?


James

---

### Post by charon79m on 2010-10-03
I too have the 8540w and am very impressed with the overall performance for the price.

I used the suggestions on this page to fix the suspend/hibernate bug with USB3 and the Function keys for screen brightness:

[http://www.linlap.com/wiki/hp+elitebook+8540w](http://www.linlap.com/wiki/hp+elitebook+8540w)

Only two complaints I have are that the fingerprint reader doens't work and the "mute" button is reversed.  It's red when playing and blue when muted.  I've not yet found a way to correct either of the above issues, but they're pretty minor.

I got my laptop from HP's refurbished stock.  I got an i7-620m processor, 4GB RAM, 250GB HDD, HD display, WebCam, NVidia Display w/ 1GB Vid memory, etc for about $1200 including a 3 year accidental damage warranty.  The only issue, physically, with the laptop was that all the stickers seem to have been put on by a blind monkey... but that hardly hinders performance.

I love the feel of the laptop.  The base has almost no flex to it and the hinges feel good.  I love the feel of the keyboard and was actually surprised to find the 10-key on the side.The latch that holds the monitor closed seems very strong, and the brushed aluminum outside feels good to the touch and seems to be pretty rugged.  

My goal for the laptop is to use it as a podcasting platform.  I've got VirtualBox running with 4 VMs without issue; though, I've moved two of the VMs off to an eSATA drive to help with drive access.  Performance is quite good even when running all four machines and recording the screen.

Yep, quite happy!

---

### Post by arsenix on 2010-11-29
I still haven't fixed the docking issue.  I just deal with it by ejecting before sleeping, waking before docking.

The main issue with this computer has been terrible battery life.  I have the QuadroFX 1800 and the i7-Q820.  I barely get over an hour, even under light usage.  I have not tried it under Windows but may just to separate hardware vs software issue.  I am wondering if I have some type of hardware issue on the machine.

Anyone else experiencing this issue?


James

---

### Post by Priyantha Bleeker on 2011-01-03
Can someone please help me with getting my graphics up and running ?
I have a Elitebook 8540w with a Nvidia Quadro FX1800 with a Dreamcolor(ips 10bit) display.
And I get 'No screens found' errors in my /var/log/Xorg.5.log.

---

### Post by chralg on 2011-02-22
> **Priyantha Bleeker said:**
> Can someone please help me with getting my graphics up and running ?
I have a Elitebook 8540w with a Nvidia Quadro FX1800 with a Dreamcolor(ips 10bit) display.
And I get 'No screens found' errors in my /var/log/Xorg.5.log.
 
 
Hi. Try using a framebuffer. I struggled with no graphics on my 8540W(fx1800 / dreamcolor2) for four days!! and ended up in a framebuffer setup.
 
Steps
 
1) remove 'nomodeset' kernel setting if any (edit /etc/default/grub and update-grub2)
2) apt-get install v86d
3) use a minor xorg.conf looking like this;
 
```

chralg@8ball:~$ cat /etc/X11/xorg.conf 
# Minimal xorg.conf 
Section "Device"
        Identifier      "Default screen"
        Driver          "fbdev"
EndSection
chralg@8ball:~$ 

```
 
4) reboot
 
 
/Christofer

---

### Post by chralg on 2011-02-22
... forgot to mention that I'm on Ubuntu 10.10 and 2.6.38-3-generic (to get rid of the acpi bug).
 
:)
Christofer

---

### Post by thwint on 2011-02-22
Thx Chris. With this workaround I'm able to use the full resolution.

Just to mention it is necessary to install a newer kernel than the default (2.6.35.X). I installed a 2.6.38 and got it working with this kernel.

---

### Post by mpsii on 2011-03-09
> **arsenix said:**
> I still haven't fixed the docking issue.  I just deal with it by ejecting before sleeping, waking before docking.

The main issue with this computer has been terrible battery life.  I have the QuadroFX 1800 and the i7-Q820.  I barely get over an hour, even under light usage.  I have not tried it under Windows but may just to separate hardware vs software issue.  I am wondering if I have some type of hardware issue on the machine.

Anyone else experiencing this issue?


James

Um... it's a Core i7 with an nVidia Quadro FX card. This != good battery life. If you wanted battery life, you would not have gotten a desktop replacement laptop. Or, choose the Core i5. Personally, I have the Core i7QM version with the 880M. I have not tried to use it for an extended period on battery alone. I tend to think of the battery as more of a built-in UPS.

Michael

---

### Post by zinadork on 2011-06-10
I have an HP DV6 and I can't get the Clickpad to work properly.  I have seen workarounds, but either they don't work at all, or they leave gaping holes in functionality, like I can now double to to right click but not drag and drop.

---

### Post by arsenix on 2011-07-14
Overall the Elitebook 8540w is the worst linux notebook I've ever had.  Excessive power consumption and heat may be a current linux problem (unclear), but it is also plagued with random failures to suspend/resume.  I can't stand resume failures but it seems like their bios is just buggy so it is unlikely there will be any workarounds at any point.  I get around 10% resume failure.

My suggestion is if you want to run Linux buy a competing model... all of which seem to work perfectly.



James

---

### Post by gk_blr on 2011-09-12
> **arsenix said:**
> Overall the Elitebook 8540w is the worst linux notebook I've ever had.  Excessive power consumption and heat may be a current linux problem (unclear), but it is also plagued with random failures to suspend/resume.  I can't stand resume failures but it seems like their bios is just buggy so it is unlikely there will be any workarounds at any point.  I get around 10% resume failure.

James

Hi, were you able to solve the battery backup issue? It's terrible under Ubuntu 10.04.
I barely get an hour of backup. And also the laptop gets very HOT!

BTW, I get more than 2 and half hours of battery back up for Win7 on the same machine!

---

### Post by arsenix on 2011-09-13
Nope... never fixed it.  Machine still uses gobs of power.  It seems that not enough people use this notebook (especially under Linux) to care about it (HP included).  According to some sources the issues stem from bios bugs which of course are worked around under Windows.

Very well made machine... it just sucks under Linux.


James

---

### Post by arsenix on 2011-11-01
I have found that power consumption is improved somewhat with Ubuntu 11.10.  The updated powertop in the new release also enabled me to identify some power consumption issues (webcam was using a lot of power, etc).  I can now get around 90 minutes... better.

  Suspend/resume still sucks on this notebook though, and lately it has been hard crashing every day or two.  I definitely will not buy an HP again.


James

---

