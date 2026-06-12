---
title: "Compiz won't autostart??"
date: 2010-02-21
forum: General Help
---

### Post by nowhere@cox.net on 2010-02-21
Hey,

I had my system working fine with compiz and the rotating cube and all. I went and demoed the wobbly windows to someone but I did it by going to System/Preferences/Appearance and enabled extas. I also use the fusion icon to switch between compiz and metacity but now whenever I restart, compiz is disabled even tho the fusion icon says it's enabled. If I click the already enabled compiz it starts working again.

Whats up? How can I get compiz to be enabled by default again?

Thanks!

---

### Post by kid1000002000 on 2010-02-21
Go to system>preferences>startup applications and add a start up application.  the command to open compiz-fusion upon startup is "compiz-gnome".

Hope this helps!

---

### Post by Greenwidth on 2010-02-21
..

---

### Post by Mr_Freez3 on 2010-02-21
Try going to "System>Preferences>Appearance>Visual Effects" again...make sure "Extra" is ticked (activated).

---

### Post by nowhere@cox.net on 2010-02-22
Thanks for the reply. But if I enable extra effects, Compiz is no longer in effect. If I re-enable Compiz using the fusion icon, then the extra effect radio button is empty (in fact all three are empty).

The problem is when I reboot, the rotate cube isn't working, docky isn't working (basically all compositing). But when I check compiz fusion icon it says Compiz is selected. Clicking on it again even tho it's selected already activates compiz and all the compositing features work. 

It's not working every time I reboot.

So, anyone know?

Thanks a ton!

---

### Post by hawthornso23 on 2010-02-22
Clicking extra effects is not a good way to enable compiz. Although I was happily using compiz after upgrading to Karmic, I noted this wasn't ticked once so ... I very foolishly ... ticked it. It took me a couple of days to get everything working again. 

Be aware that clicking "extra effects" can lead to a less than optimal experience.

```
compiz --replace
```

does it for me, and I have a key combination set up to do this.

---

### Post by nowhere@cox.net on 2010-02-23
So you're telling me that compiz will not autostart for you and you have a key sequence to enable it?

I too seem to have this exact problem in that compiz was starting up just fine until I stupidly click extra effect to show off wobbly windows instead of using the compiz setting. Now I can't get compiz to autostart regardless of what I do, even compiz --replace.

=(

---

### Post by Mr_Freez3 on 2010-02-23
I agree with hawthornso23, I did the very same thing once and I can't remember how I fixed it.  But I did get it back to where compiz was default after a reboot.

When I do an Ubuntu installation, I install the ATI Catalyst driver from their site, then enable "Extra" effects.  The only reason I use ATI's proprietary driver is because "Extra" effects cannot be enabled at the present time with my GPU using OS driver on a clean Ubuntu install.  And I'm not comfortable with modifying (upgrading to Lucid's kernel) stuff just to get compiz working. 

Once I tick "Extra" effects...I never fool with it again (lesson learned).  If I want compiz off, I use the Compiz Fusion Icon to do it.

---

### Post by nowhere@cox.net on 2010-02-23
Well, I seem to have fixed it. After many, many different trials this is SPECIFICALLY what did it:
[LIST=1]
[*]Use Compiz-Fusion icon to set to metacity (compiz was already selected remember but not active).
[*]Use Compiz-Fusion icon to set back to compiz
[*]Kill Compiz-Fusion icon
[*]Type compiz --replace in the ALT-F2 run dialog (terminal would not stick)
[/LIST]

---

