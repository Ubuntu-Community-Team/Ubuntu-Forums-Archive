---
title: "This is terrible: Update manager screws my desktop"
date: 2010-06-09
forum: General Help
---

### Post by Manuwash on 2010-06-09
This is seriously bringing my morale down. I just ran the update manager thinking it would be positive and the damn thing just screwed how I had everything set.

First of all compiz is not working at all. The settings are the same but it wont work. Im really pissed about this, everytime I restard ubuntu I feel its going to start up differently, something is not gonna work the way it did just a moment ago, its very stressing really. 

Whats the idea then, whenever the desktop is working fine dont touch anything? dont run any updates ever?

Anyways if anyone knows what could have happened to compiz please help :confused:

---

### Post by Manuwash on 2010-06-09
Oh to make matters worse, the cairo dock issue i had solved now is back, great update ubuntu, really great....

---

### Post by Manuwash on 2010-06-09
Is it possible that the update manager has wiped my ati drivers? I get the "no propietary drivers are in use on this system" message from the hardware driver preference.

How can an update be so unaccurate and damaging? I cant understand this, Im trying to download the ati drivers again. Happiness seems to be brief with linux.

---

### Post by Manuwash on 2010-06-09
Ok guys really i am desperate, I cant do one more google search I am exausted. I completely removed and reinstalled the ati drivers to no avail, I cant enable desktop effects, I tried booting both the new and old kernel, Im a noob I dont know what else to do and my patience is been drained. Give me a hand or im going back to the dark side of vista.

---

### Post by sgage on 2010-06-10
I have no idea what's going on with your installation. I have never experienced anything like it, and it's not something that happens all the time. 

But if I were you, I'd calm down, and just reinstall the whole thing from scratch.

---

### Post by stoneage on 2010-06-10
Are you using proprietary ATI drivers, or the ones from the repository?

If the former, and the installed updates included kernel updates, then reinstalling the drivers will be necessary - every time.

Essentially installing the proprietary driver means recompiling the kernel, so a new kernel means you have to recompile again.

---

### Post by philinux on 2010-06-10
> **Manuwash said:**
> This is seriously bringing my morale down. I just ran the update manager thinking it would be positive and the damn thing just screwed how I had everything set.

First of all compiz is not working at all. The settings are the same but it wont work. Im really pissed about this, everytime I restard ubuntu I feel its going to start up differently, something is not gonna work the way it did just a moment ago, its very stressing really. 

Whats the idea then, whenever the desktop is working fine dont touch anything? dont run any updates ever?

Anyways if anyone knows what could have happened to compiz please help :confused:

System specs and model of graphics card might help.

---

### Post by LoneWolfJack on 2010-06-10
did you upDATE or upGRADE ? big difference.

updates of the kernel will remove the restricted drives.

upgrades of heavily customized/adapted installs tend to break the entire system (it's impossible to test an upgrade against all possible adaptations the user may have made). I'm still for a "don't use upgrade with heavily customized systems" warning when somebody tries to upgrade, but what do I know...

---

### Post by cbrunhaver on 2010-06-10
I think Stoneage hit the nail on the head - if you separately install your proprietary video driver (ATI fglrx) outside of "hardware drivers", it will need to be reconfigured with each kernel update.

Either use the driver in "hardware drivers" (probably the best option based on your experience level) or carefully note any proposed kernel updates in update manager and configure your video appropriately.  

The open source ati drivers are making great strides (depending on the vintage of your video card) and so this may not be an issue for long, if you are just doing some desktop compositing  / cairo dock type stuff (not games).

---

### Post by Manuwash on 2010-06-10
Good news guys, I got as a present from a family member a desktop pc, a dual core 2.6 ghz machine with nvidia graphic card. I booted ubuntu from my external hdd and now the drivers auto configured and im back in track. Everything seems to be working flawlessly again.

I think the ati card from my laptop was simply not supported by the latest kernel the update manager installed. Whichever way it was, I dont care much to be honest, Im happy to be back on track .

Its true that now I have a dilemma because truly vista runs incredibly fast on this dual core, but i think, as long as ubuntu behaves well, ill stick to it for my normal surfing and entretainment needs.

Thanks to you all for the kind replies and excuse my previous desperation, i was quite pissed.

---

