---
title: "Random Freezes"
date: 2006-06-12
forum: General Help
---

### Post by kairu0 on 2006-06-12
My computer freezes very randomly. There is no pattern to the applications that are open when it happens. (Sometimes, it freezes when nothing is open at all.) The frequency varies, but it seems to happen a maximum of 3 or 4 times per day.

This happened in Breezy, too, by the way. (By the way, this is a fresh install of Dapper.) It doesn't happen in XP, which makes me believe that it's not bad memory in the computer.

I am using the i810 video driver, and rt2500 driver for my wifi pcmcia card. This is a Vaio VGN-FS21. I have installed all the latest updates.

Can anyone help me?

---

### Post by johnc4510 on 2006-06-12
If you type: top  in a terminal, it will show you what processes are running and how much memory and cpu they are using. You can leave this running, and maybe see what is causing the problem.

---

### Post by HeavyAl on 2006-06-12
While I realize you say that it does not happen in XP, random freezes can almost always be traced to faulty memory or overheating issues. I would check to make sure that the heat sink on your cpu is firmly attached and that none of your ram has pulled away from the board as can often happen under higher temperatures. I'm not saying that there isnt something else at work here but its best to double check the basics first.

---

### Post by nanotube on 2006-06-12
[QUOTE=kairu0]My computer freezes very randomly. There is no pattern to the applications that are open when it happens. (Sometimes, it freezes when nothing is open at all.) The frequency varies, but it seems to happen a maximum of 3 or 4 times per day.

This happened in Breezy, too, by the way. (By the way, this is a fresh install of Dapper.) It doesn't happen in XP, which makes me believe that it's not bad memory in the computer.

I am using the i810 video driver, and rt2500 driver for my wifi pcmcia card. This is a Vaio VGN-FS21. I have installed all the latest updates.

Can anyone help me?[/QUOTE]
frequently these freezes are due to video driver problems. try switching your video driver to vesa, and see if the freezes keep happening.

to switch to vesa, just edit your /etc/X11/xorg.conf, and change your Driver line to look like
```
Driver "vesa"
```

---

### Post by kairu0 on 2006-06-17
[QUOTE=johnc4510]
If you type: top in a terminal, it will show you what processes are running and how much memory and cpu they are using. You can leave this running, and maybe see what is causing the problem.[/QUOTE]

I left top open until it froze. No process was really hogging the system.

[QUOTE=nanotube]frequently these freezes are due to video driver problems. try switching your video driver to vesa, and see if the freezes keep happening.[/QUOTE]

I switched to vesa driver and the system still froze.

What should I try next?

---

### Post by kairu0 on 2006-06-18
The problem still continues. At this point, I think it might be heat-related. My processor seems to be operating between 52-60 celcius.

Does anyone have any ideas?

---

### Post by kairu0 on 2006-06-23
I have tried the following so far, but still no cake:

[LIST]
[*]Removing gnome-screensaver
[*]Disabling DRI
[*]Using the VESA driver
[*]Checking CPU + HDD temperature
[*]Memtest
[/LIST]

What can I still try?

---

### Post by nanotube on 2006-06-25
start disabling services that run on startup. start with the stuff you don't need, like bluetooth crap, fetchmail, etc. there was a guide on these forums somewhere about speeding up ubuntu by disabling unneeded startup services, find it, and follow it. maybe one of those processes has a problem with your hardware, so if you disable it, your problem might go away.

---

### Post by kairu0 on 2006-06-25
Nanotube: Thanks for the idea. I've disabled a few things and we'll see within the next few days if it still feels inclined to freeze ;)

I think the problem might be that the rt2500 driver (for my pcmcia wifi card) does not support SMP and I was using the vanilla 686 kernel from the repos that has SMP built in.

I'll try with the 386 kernel and my reduced services load and see what happens...

---

### Post by Quirky on 2006-06-25
In Dapper, the problem with SMP and rt2500 is solved. I'm using the rt2500 driver now on the 686 SMP-enabled kernel with no problem, but it hung immediately after bringing the network up under Breezy. The rt2500 driver hang wasn't an isolated, once-a-day kind of problem, but a 100% reproducible, happened-every-time thing.

---

### Post by kairu0 on 2006-07-02
Problem was solved by reinstalling. I suspect that the culprit was either the 686 kernel (I'm now using 386) or not enough swap space.

---

### Post by davro on 2006-07-02
I have been crashing out regular, twice this morning and its not even 7.30

I have done memory test also Tryed kernels 
2.6.15-25-386 locked
2.6.15-23-386 locked
2.6.15-22-386 locked
2.6.15-20-386 locked

Tryed different window managers all locked up
Gnome
Kde
Fluxbox
Blackbox

Tryed running the vesa driver, but x did not even run/work so that was not a brilliant suggestion.

This is becoming a bit of a joke now.
If reinstalling is the only answer then i am seriously looking at another OS

---

### Post by nanotube on 2006-07-02
have you tried the 686 kernel?
have you tried disabling screensaver?
also try going through your startup services list and disabling the unneeded ones (like bluetooth and stuff). there is a thread out there somewhere about "speeding up ubuntu" that goes through all the services and which ones you can safely turn off...

---

### Post by kairu0 on 2006-07-12
> **davro said:**
> I have been crashing out regular, twice this morning and its not even 7.30

I have done memory test also Tryed kernels 
2.6.15-25-386 locked
2.6.15-23-386 locked
2.6.15-22-386 locked
2.6.15-20-386 locked

Tryed different window managers all locked up
Gnome
Kde
Fluxbox
Blackbox

Tryed running the vesa driver, but x did not even run/work so that was not a brilliant suggestion.

Since X does not work, you can probably bet that the window managers are not the problem. You must have a device conflict or some other hardware issue (overheating, faulty power supply, etc.)

I also suggest that you try the 686 kernel to see if the kernel is your problem.

---

