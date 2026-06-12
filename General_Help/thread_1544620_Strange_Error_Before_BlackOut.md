---
title: "Strange Error Before BlackOut"
date: 2010-08-02
forum: General Help
---

### Post by Unknown-Demon on 2010-08-02
I'm very sorry for the second post.
But My Screen blacked out a few minutes ago and in the black screen there were some words in there
That I can barely remember but I do remember seeing cupsd
and then it goes to the blinking bars.
How can this be corrected? :/

  - Andrew

---

### Post by TheNerdAL on 2010-08-02
We'll need more information, like what version of Ubuntu, if you are using Ubuntu, are you using and are you using a graphics card and what model is it if you can remember?

---

### Post by Unknown-Demon on 2010-08-02
I'm using Xubuntu 10.04 
Graphic Card:  VGA compatible controller: Intel Corporation  82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

---

### Post by TheNerdAL on 2010-08-02
> **Unknown-Demon said:**
> I'm using Xubuntu 10.04 
Graphic Card:  VGA compatible controller: Intel Corporation  82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

Did you install the drivers? And when you are in the black screen, do you see a blinking underscore?

---

### Post by Unknown-Demon on 2010-08-02
I thought it installed the driver's during the installation.
And yes, I did see a blinking underscore before the blinking bar's came up.

---

### Post by TheNerdAL on 2010-08-02
Try this" 
1) At the grub menu, press 'e'.
2) After "quiet splash" type "nomodeset".
3) Ctrl+x to boot.

Does it work after you tried it?

---

### Post by Unknown-Demon on 2010-08-02
Nope.

---

### Post by TheNerdAL on 2010-08-02
How did you install Xubuntu 10.04?

---

### Post by Unknown-Demon on 2010-08-02
I ordered a Xubuntu 10.04 Alternate install disk.

---

### Post by TheNerdAL on 2010-08-02
Okay, try to add the noapic and acpi=off arguments in addition to the nomodeset flag. 

That should work.

---

### Post by Unknown-Demon on 2010-08-02
i'm kinda new to linux, were would I put it?

---

### Post by kaj on 2010-08-03
I am having the same problem.

I have installed Ubuntu 10.04 LTS server on an elder HP Compaq EVO desktop computer. On top of the server I have installed the Ubuntu-desktop and everything seems to be working fine.

After some time, half an hour or an hour or so, the screen suddenly blacks out, then it is blinking with some white bars or figures. After some seconds, 10 or 20 or something like that, it is flashing some error messages for a short time and blacks out totally.

Now, that is not a good behaviour for a server.

The graphics driver is just the standard one.

---

### Post by dvdntwrk on 2010-08-18
I'm running pretty much the same config hardware and Ubuntu 10.4. In my case I've removed (at separate times) the Power Management and Screen saver code. Every time I touch the preferences on the screen saver the "lock-up" begins so I tried by removing any software that Synaptic identified with Power of Screen and the lockup still occurs.

There is some messages displayed before and the most I can see if something about Pulse audio. I have installed the Ubuntu Studio packages trying to get Jack operational - but the hang up keeps me screwed up.

The initial description sounds exactly like what i see before my machine locks up.

---

