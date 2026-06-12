---
title: "Need assistance with ATI drivers"
date: 2011-11-17
forum: General Help
---

### Post by Broodwich, The on 2011-11-17
I'm not driven toward any Distro atm, however Ubuntu and other Debian derivatives fancy my blouse... that is, if I wore a blouse. In which case, I'd have to be utterly insane or pinned in a drag movie set in the old, old west. Now that'd be humoring for a change... Wait, oh, back on topic - Anyway, I love Ubuntu/Mint/et cetera. However, I'm having a constant conundrum - Getting my ATI CCC/Driver to work. I'm going mad!!!!

So, here's some specs -

HP Pavilion DV6QTE
i7 2720QM
Radeon HD 6770M
8 GB DDR3 RAM
640 Toshiba 7200RPM HDD

Not that the latter two really mattered I suppose, seeing as the problem more than likely (obvious, one is) pertains to the i7 and the Radeon card. I've run through several different Ubuntu/Ubuntu Spin offs/Mint installations with an attempt in each to get the ATI Driver to run. At all. All the way from my introduction into Wubi and into my big scary step into an individual partition. Suffice to say, I'm not a novice in the Computer game - but as far as Linux is concerned, I'm still a greenhorn. Honest - I love it, I love freedom from M$ Windows, and I would love to altogether replace my Windows installation... it's just I game. Way too much - and admittedly can't get past the mental block the difficulty I seem to be having with the ATI driver is causing me.

So, I called this beating a dead horse because I'm sure it's a "problem" that's been complained of a lot before if not recently. I certainly hope, yet at the same time wish it not to be true, that it's just my hardware not agreeing with what I want to do with Linux/ATI. If anything, I can live with Ubuntu/Derivative/or even continue experimenting in other Distros (Fedora, Gentoo, CentOS, and Arch just to name a few) for casual use while booting up Windows for my gaming. Ultimately, I hope someone however can help me come up with a solution that'll hopefully work across most Distros (but most definitely in Ubuntu/Mint). If not, like stated - I'll live with it... and if it is a hardware issue, then at least once I build my new Desktop rig I'll have a much smoother set up with video drivers/Linux.

Sorry that this one is a bit wordy/lengthy - TL;DR is HAAAAAALP ME I NEED TO GET ATI DRIVERS TO WORRRRRKKKK!!! AND I HAS AN I7 AND AN AMD RADEON HD 6770M AHHHHHH LAPTOPS.

Thanks.

-Broodles, the satanic little 'wich.

---

### Post by Broodwich, The on 2011-11-17
[Though as a latter thought, I wouldn't be surprised at how silly it was to post this in the wrong area. I sort of just attached Gaming & Leisure to the ATI Driver, and thought someone here would know... that's not to say the correct area of the forum wouldn't know... I feel silly now.]

---

### Post by sffvba[e0rt on 2011-11-17
*Thread moved to **General Help**.*

Title changed to assist in getting relevant help.

Welcome to the forum :)



404

---

### Post by alphacrucis2 on 2011-11-17
Did you try installing the Catalyst driver via typing **[COLOR="Lime"]add[/COLOR]**itional drivers in the dash. Run the additional drivers program and install that way.


Edit: Ubuntu is a good distro for ATI cards as Ubuntu and AMD seem to cooperate on releases of the Catalyst driver. You didn't say what distro you are currently running. Above assumes Ubuntu 11.04 or 11.10,

---

### Post by Dlambert on 2011-11-19
Use sabayon:0 Drivers built in!

---

### Post by Mark Phelps on 2011-11-19
Is yours one of the Infamous HP laptops that has switchable graphics?  IF so, it's going to be very hard to get the ATI graphics to work because Ubuntu doesn't see the card.

To see what video card/chip you're actually using, open a terminal, enter "lspci" -- and look for the line containing "VGA".  Post that result back here.

---

### Post by Broodwich, The on 2011-12-01
I know my first post sort of sucked, or at least that's my self conscious speaking. I have done additional drivers, thank you - multiple times. I even did it as "manual as it gets", not sure if you'd consider compiling it, but even had to show a friend here in Lincoln that it just wouldn't work no matter which way you try.

Mark, yes it is the switchable graphics kind - but I was under the impression that only mattered to Windows. (The ATI specific driver used on the Windows side is HP-developed, ergo modified to utilize a switchable option. I can't even update those drivers unless I do it through HP's website, as AMD's update manager won't recognize it. Another thing I noticed was reinstalling Windows will actually disable this altogether, so I don't believe that switchable has much to do with it. Hopefully, at least.)

I'm actually getting around to installing 11.10 atm here at ze verk, so I shall use this terminal command to see what it says. I do know when I used 11.04 back in around July or so all that happened was Unity took a dump, went back to Gnome, and basically said I had no Accelerated 3D Support in my chipset. I can only assume this is because it somehow is defaulting to the Sandy Bridge APU, which then if what you meant by switchable was that it had the APU + GPU then yes and I do see how that's an issue...

And I heavily, sighfully cry now.

Anyway, is Sabayon is Distro or some sort of a manager? I'll keep my head up in this little adventure, and I thank you all who helps and welcome whatever help and advice I can get from the community.

Hopefully, too, I can find a workaround and be somewhat of a help to anyone in the future with this similar HP model.

Which, btw, rocks... I just want to use Linux. :(

PS - On my Windows side, I have that somewhat awesome Beats Audio. I know HP doesn't have a Linux 'version' of this, but does anyone know short of a google search what I could get for some decent audio control?

EDIT: Also, Mark, I hope you'll remember this thread! I know it's been a week, but once I have 11.10 going again I'll post the result you were seeking.

---

### Post by Broodwich, The on 2011-12-01
> **Mark Phelps said:**
> Is yours one of the Infamous HP laptops that has switchable graphics?  IF so, it's going to be very hard to get the ATI graphics to work because Ubuntu doesn't see the card.

To see what video card/chip you're actually using, open a terminal, enter "lspci" -- and look for the line containing "VGA".  Post that result back here.

ATI Technologies Inc Whistler XT [AMD Radeon HD 6700M Series]

Seems to detect it... now... whereas before it seemed not to be... going to run additional drivers, and if somehow that does the tricky trick trick this time around (unlike in 11.04 for me) then yay... problem solved.

---

