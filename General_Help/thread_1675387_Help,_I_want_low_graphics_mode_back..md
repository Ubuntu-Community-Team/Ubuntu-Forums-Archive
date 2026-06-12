---
title: "Help, I want low graphics mode back."
date: 2011-01-25
forum: General Help
---

### Post by /bee/ on 2011-01-25
Specs:
Gigabyte GA-MA770T-UD3P mobo
Unlocked 3rd and 4th cores in my dual-core AMD Phenom II X2, to make it a quad-core AMD Phenom II X4 B50 Processor, stable overclock
4 GB DDR3 Ram
nVidia GeForce 8500 GT, custom overclock
Ubuntu 10.10

[I've posted a bit in the past about my gfx problems](http://ubuntuforums.org/search.php?searchid=78998270).  I still can't get my graphics card to play nicely with Ubuntu.  I have tried every version of every available driver and none of them work.  Every proposed suggestion ends with me reformatting and reinstalling Ubuntu.  I know everyone's mileage may vary and what has been suggested may work for other's problems, but I'm thinking about putting windows xp on my machine (after 2 *mostly* wonderful windows-free years) if I can't get low graphics mode back.

**This is the important part:**

I want to get my computer to give me this dialog box when I'm about to enter Ubuntu so I can choose low graphics mode.  As it currently stands, my computer locked up twice while I was trying to write this.  I just want a stable machine, and in low gfx mode, it is.  Help!

[img]http://i.imgur.com/PbWEl.png[/img]

---

### Post by pl@yer on 2011-01-25
On boot up instead of logging into the graphical environment try hitting ctrl+alt+f2 and logging in there. Then run these commands.
```

sudo -s
cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bkup
cat /etc/X11/xorg.conf_bkup|sed -e 's/nvidia/vesa/g'>/etc/X11/xorg.conf
init 6

```
Your system should reboot. This should set your system to use a standard svga driver for your card. 

I would then undo your over clocking stuff and hope that the card itself isn't messed up.

---

### Post by /bee/ on 2011-01-25
> **pl@yer said:**
> I would then undo your over clocking stuff and hope that the card itself isn't messed up.
That's something that honestly didn't even occur to me until just now.  I should have thought of that before.  I know the card is able to handle overclocking like a champ (tested extensively in win xp and vista and ubuntu) and it's not messed up, but I wonder if overclocking might be a part of the problem.  I'll give NV Clock a chance to lower the gfx card back down and see where that takes me.  If it's still screwy, I'll look into your first suggestion.

Thanks for the very quick reply.

---

### Post by asmoore82 on 2011-01-25
> **/bee/ said:**
> Specs:
Gigabyte GA-MA770T-UD3P mobo
Unlocked 3rd and 4th cores in my dual-core AMD Phenom II X2, to make it a quad-core AMD Phenom II X4 B50 Processor

I wasn't aware that AMD was using that manufacturing process, but if they are,
there is a very, very good reason that those other cores were locked.

You can't make the fabrication process for Quad Core chips perfect.
Some chips right off of the assembly line are going to be "duds."
But with a Quad Core, even if it's a "dud" it's still very likely that
at least 2 or maybe 3 of the cores are good. So you seal up the cores
that fail the first testing phase and sell it as a Dual Core.

There's absolutely no way that AMD would sell a perfectly working Quad Core
chip at a Dual Core price - that's just burning money.

---

### Post by /bee/ on 2011-01-25
Actually I read somewhere that AMD was literally burning money to keep the lights on in their factories.  LOL... Regardless of what the case may be, I built this computer several years ago with full intentions of OC'ing and was able to unlock them and get them stable even through the most vigorous stress-testing I could manage in xp, vista and ubuntu.  I'll grant you that is becoming more rare to find a cpu with good 3rd and 4th cores that can achieve noticeable results, but I got lucky.  Not to mention, nowadays it's ludicrously easy to find a quad-core and then some.

---

### Post by cascade9 on 2011-01-25
It try putting the video card back to stock speeds..it cant hurt. Anything is better than wanting to go back to low graphics mode... 

Or just buy a new card. The 8500GT shouldnt be that hard to get a replacement/upgrade, and it should be cheap to do. 

> **asmoore82 said:**
> I wasn't aware that AMD was using that manufacturing process, but if they are,
there is a very, very good reason that those other cores were locked.

You can't make the fabrication process for Quad Core chips perfect.
Some chips right off of the assembly line are going to be "duds."
But with a Quad Core, even if it's a "dud" it's still very likely that
at least 2 or maybe 3 of the cores are good. So you seal up the cores
that fail the first testing phase and sell it as a Dual Core.

There's absolutely no way that AMD would sell a perfectly working Quad Core
chip at a Dual Core price - that's just burning money.

As the production process goes on, the fab plants get better and better at it. Processes improve, yields increase, errors drop. That is part of how CPUs (within a family) tend to get increasing clock speed over time. 

To use the example of the Phenom II, what happens is that all the X2, X3 and X4 CPUs come from the same wafer. During the production process, they are tested. Chips that fail at 3.6GHz are knocked back, and tried on 3.5GHz, untill they hit the lowest clockspeed that AMD is producing for that chip. If they fail there, they are binned. 

Soem chips will fail core test, but make the speed test. Those will be marked down to X3 or X2. During the early production  runs, that would have been fairly common but as time goes on it happens less and less. 

The thing is that there is always far geater demand for lower end chips, the top end chips dont sell so well. So you might get from a batch of 1,000 chips there might be orders for 50 X4 975s, 75 X4 970s, 125 X4 965s and so on. AMD (and intel) really dont want to have to check chips more than they have to, so once the quota for X4 975s is filled, they just test for X4 970s. Once the X4 970 quota is filled, they make X4 960s. There ends up being a point where they are just testing for X2, and not bothering to even test for X4. 

So you can get a X2 that can have 4 perfect cores. Sure, you will also get some that have 'bad' cores, but just because its been sold as an X2 doesnt mean that the cores are automatically bad.

---

### Post by Herman on 2011-01-25
:D 
On the subject of returning to low graphics mode:

@ pl@yer, Thanks for posting those commands, I always like to learn the  command line ways of doing things just in case the other way doesn't  solve the problem. I will give those a try myself some time when the need arises.

@ /bee/, Another idea would be to just go down one line in your GRUB Menu at boot time and boot into 'Recovery Mode'. 
In recovery mode you should see an option called 'failsafeX - run in low-graphics mode'. 
From there you can choose from several options, and I'm pretty sure you should be able to get your graphics configuration reset in there somehow without too much trouble, and probably avoid the need to re-install. 
At least it worked a couple of times for me when using USB external drives and moving from one machine to another (after installing drivers to get googleearth working properly). :D

EDIT: 
That's one way to get to see a sign similar to the one displayed in the original post 'Ubuntu is running in low graphics mode'.
The list of options subsequent to the 'Ubuntu is running in low graphics mode' sign is:
* run in low graphics mode just for one session
* reconfigure graphics
* troubleshoot the error
* exit to console login
* restart X

---

### Post by /bee/ on 2011-01-25
> **pl@yer said:**
> On boot up instead of logging into the graphical environment try hitting ctrl+alt+f2 and logging in there. Then run these commands.
```

sudo -s
cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bkup
cat /etc/X11/xorg.conf_bkup|sed -e 's/nvidia/vesa/g'>/etc/X11/xorg.conf
init 6

```
Your system should reboot. This should set your system to use a standard svga driver for your card.

My computer is freezing up again and so I thought I would just go and do this.  However, I don't have a xorg.conf file.  Furthermore, is this going to put me into the low graphics mode that comes as a result of the dialog I posted before?  Any help (that doesn't end with me reinstalling) is appreciated.

---

### Post by pl@yer on 2011-01-26
Okay you should make one with Xorg -configure. 
```

sudo -s
Xorg -configure
cat ~/xorg.conf.new|sed -e 's/nvidia/vesa/g'>/etc/X11/xorg.conf
init 6

```

---

### Post by AlexanderDGreat on 2011-01-27
> but I wonder if overclocking might be a part of the problem - May I just butt in,

I'm running a Desktop-Server Ubuntu 10.04, it's a pain in the ***, because I'm running a fax server in a VirtualBox Machine.

I need that thing for the office, but since Ubuntu from time to time, 3x in 1 month, stays on the message

UBUNTU IS RUNNING IN LOW GRAPHICS MODE - the damn server won't boot, and office fax don't get transmitted,

I wish it would go away!

/bee - you're not the only one with this problem.

I don't have a videocard, I'm thinking of installing one so I will use a Proprietary Driver which in my opinion would be stable enough.

But a videocard on a server? That's really annoying.

:(

PS Good thing someone answered my question, here: I'm just about to try. [http://ubuntuforums.org/showthread.php?t=1663847]("http://ubuntuforums.org/showthread.php?t=1663847")

---

