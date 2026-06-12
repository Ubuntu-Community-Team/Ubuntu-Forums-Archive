---
title: "Startup Hotplug Subsytem Freeze &amp; ATI Radeon 9250 PCI Problems"
date: 2006-04-15
forum: General Help
---

### Post by Danny-O on 2006-04-15
Hi there, I know this is my first post on the forums and I kinda feel bad that it's a request for help.

I've been using Ubuntu (Hoary) on my laptop for a while now, and I really liked it, so I decided to install it on a seperate drive on my PC.  The installation went fine, but when I booted ubuntu up for the first time, my computer froze on "Starting hotplug subsystem."

Here are my specs, really quickly.
Intel Celeron 2.8 gHz
512 mb RAM
1 80gig HD, 1 20gig HD (Running ubuntu 5.10)
Intel integrated graphics (If you need specs on this I'll find them and post them)
ATI RADEON 9250 PCI graphics card 256mb

Now I read somewhere that this is because I was using my radeon to start up instead of my integrated graphics.  So I went into the BIOS and switched them around, and started up again.  And it worked, but often there are graphical glitches and such, so I really want to get my Radeon working.

So my problem is, how do I install drivers for my Radeon whilst using my Integrated graphics?  I've read a couple of tutorials but they seemed like they would only work if I was using my Radeon to begin with - which I can't because it won't start up (obviously)

Sorry if this is a n00b question, or in the wrong forum.  I did read the rules, but I didn't know which subforum to put this question in.

Thanks in advance.

**EDIT:** I think this is in the wrong forum. I clicked Hardware>Video from the index, but it put it in the Live CD area for some reason?

---

### Post by meegs on 2007-05-22
Hey I think I am having a similar problem.

did you resolve your issues with the ATI Radeon9250?

---

### Post by Githlar on 2007-07-24
I, too, am having this problem (and I also have an Intel Celeron [2.9Ghz] with Intel integrated graphics). Only, when I try to boot with PCI as the video adapter, loading crashes with a flood of errors.

---

### Post by TRDownShift on 2007-08-31
im also having the same prob, im runin a dell dimension 2350 with a P4 1.7 1gig of RAM and i cant get ANY linux OS to boot at all with my ATI(radeon 9250 PCI 256MB), live CD or not, there all doing to same thing T.T 

im about to cry becus im fliping sick of windows, and linuxs runs sooooooo much better but theres really not much point to moving over to linux if i cant take my radeon with me. >.>

---

### Post by Githlar on 2007-09-02
As far as I have found, the ATI Radeon 9250 PCI is not supported by the proprietary drivers, nor have I been provided or have I found a workaround to make the 9250 work in Linux. The card is a bit dated, so I can see why it wouldn't be supported. Looks like you'll have to stick with *shivers* Windows or you could try to use your onboard video if you have it, but it won't be near as good as if you were able to use your video card of course. Unfortunately, that's all the advice I can give you =(

---

### Post by TRDownShift on 2007-09-03
yeah, i've ben useing the onboard card.. T.T it's so slow, the only thing i can play is stepmania >.> and i dont even have APG slots, this liddle dell only has PCI. untill i get a new computer i think im just about F'ed ~.~

oh well, thanks for the input, i've ben trying to find simple yes or no somewhere, finely got it.

as for winsh*t i think i'll stick with linux, although my gaming is going to get put on hold till i can buy a new computer or if you guys can point me to a PCI video card that is supported maybe i'll pick that up.

anyway, later guys, thanks for the help.

---

### Post by Githlar on 2007-09-03
Yeah, my HP computer is the same way. It only has PCI slots =(. But, it has a 3Ghz processor and I got the whole thing for $75, so I can't complain haha.

---

### Post by triplebootfan on 2007-10-16
You can use the ATI Radeon by going into recovery mode while booting up.  When the prompt comes up type in:

sudo dpkg-reconfigure xserver-xorg

Select the ati driver type.  Uncheck dri.  If you don't know where your card your card's address, i.e. 1:11:0, type in:

lspci

Do that before you type in sudo dpkg-reconfigure xserver-xorg.  Remember your card's address for later.

Most options are self explanatory.  Anyway, when it gets to the screen resolution options, I ran into trouble by trying to select my own.  It always booted into a black screen.  It worked fine if I leave the screen resolutions at the default options.  In other words, just click your way through all the monitor options.  Once you're done, type in:

startx

The card now works.  However, as far as I know these options still won't work for playing many linux games, I did find some references to another driver, but I haven't used it.  I'm just glad I eventually got the card to work.  As for using both the card and the integrated, huh?  I was able to keep the integrated graphics enabled in the bios, but as for still using it in linux, the only way I know (extreme linux novice that I am) to siill use the integrated is to remove the card.  Everytime you remove or reinstall the card though you have to type in sudo dpkg-recofigure xserver-xorg again.

Hope this has been helpful.

---

### Post by Githlar on 2007-11-21
I finally fixed my problem! I got rid of my Radeon 9250 after finally giving up on it. I got an nVidia GeForce 6200 256MB PCI card and I installed it and I GOT THE SAME PROBLEM! So, I figured this was not a card issue, it was a motherboard issue more than likely. I did a little sniffing around and found a post regarding an entirely different video card, but the same problem - and the person had onboard Intel graphics also.

Long story short, here's the solution:

sudo gedit /etc/modprobe.d/blacklist

Append to the end of the file:
```
blacklist agpgart
blacklist intel_agp
```

---

