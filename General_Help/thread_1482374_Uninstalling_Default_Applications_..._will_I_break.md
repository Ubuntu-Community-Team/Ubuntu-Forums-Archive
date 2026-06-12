---
title: "Uninstalling Default Applications ... will I break stuff?"
date: 2010-05-13
forum: General Help
---

### Post by sunshinecorp on 2010-05-13
This might be a rather silly question, which could be solved by trial and error I guess, but I simply don't have the time right now to go through the process of re-installing my OS. So...

I was wondering if I will cause instability/incompatibility issues to Ubuntu 10.04 if I remove certain features/applications that I never use or that I replace with alternatives. In particular:

[LIST]
[*]AisleRiot Solitaire
[*]Computer Janitor
[*]Dictionary
[*]Empathy IM Client
[*]F-Spot Photo Manager
[*]gbrainy
[*]Gwibber Social Client
[*]Mahjongg
[*]Mines
[*]Movie Player
[*]Pitivi Video Editor
[*]Quadrapassel
[*]Rhythmbox Music Player
[*]Sound Recorder
[*]System Testing
[*]Sudoku
[*]Tomboy Notes
[/LIST]

I guess removing the games won't cause any trouble, but how about the rest on that list? Also, I vaguely remember that by removing certain applications in the past caused the forced removal of ubuntu-desktop. Does that still happen on 10.04?

Before you flame me on why I want to do this, let's just say that *in addition* to preferring a clutter-free environment, every byte that I can save is precious to me right now. :)

I know about the minimal CD option, but I am asking about an existing install of Ubuntu Desktop 10.04.

Thank you in advance!

---

### Post by blueridgedog on 2010-05-13
The games can be removed.  I recommend keeping F-Spot as it is linked to in many ways.  The others you can try one at a time, but I would leave them if it were up to me unless you were struggling with space (which these will not offer much free space when removed).

---

### Post by howefield on 2010-05-13
The only one that looks as if it would do damage is System Testing, which would want to remove ubuntu-desktop also.

Seriously, if every byte really is important, you wouldn't be doing this. You would build from the ground up using the minimal install, which as you say, you are aware of.

---

### Post by Midnighter on 2010-05-13
No, it should not, but pay attention when you go to remove them, and see what else it wants to remove. If it wants to remove ubunutu-desktop (or whatever it's called), it should just be a "meta-package" which is nothing on it's own, and can be safely removed. It's more of an "umbrella" package, which drags in a bunch of other stuff if you install it again., but on it's own it's nothing, and can be safely removed. :)

---

### Post by joe26 on 2010-05-13
It does not hurt to remove them, but if it says something like, "must remove XX other packages" then you should not do it.

---

### Post by sunshinecorp on 2010-05-13
> **howefield said:**
> Seriously, if every byte really is important, you wouldn't be doing this. You would build from the ground up using the minimal install, which as you say, you are aware of.

Not wanting to quote myself, but:

> **sunshinecorp said:**
> but I simply don't have the time right now to go through the process of re-installing

...or even worse, the time to build from the ground up. I'm still a beginner, and it would require a lot of research on my part to pick the right packages to recreate a functional environment. I will have to try it, when my work schedule relaxes a bit. But sadly, that's not happening soon.

But thanks for the rest of your answer. :)

---

### Post by amite on 2010-05-13
If space really matters to u and u don't want messed up then it would be better u use miniimum cd option......but if don't want to this then u can uninstall games and other packages which hasn't dependecy on other. 
if u are using synaptic then don't select complete remove option,and uninstall package one by one after verifying it's dependency on other packages.

---

### Post by aysiu on 2010-05-13
> **howefield said:**
> 
Seriously, if every byte really is important, you wouldn't be doing this. You would build from the ground up using the minimal install, which as you say, you are aware of.

> **amite said:**
> If space really matters to u and u don't want messed up then it would be better u use miniimum cd option...... I agree with these recommendations.

Guide here:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by emarkay on 2010-05-13
> **aysiu said:**
> Guide here:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

Is that 100% correct for Lucid?

I remove on every install:
Bluetooth/Bluez, Britty, Evolution, Indicator-Messages, F-Spot, Gnome Games*, Gwibber, Mono*, Rhythmbox, Tomboy, Totem, UbuntuOne, Unneeded Fonts*, Vinagre, Vino
* Multiple files, as required. 

Also see:
[https://answers.launchpad.net/ubuntu-desktop-minimal/+question/110792](https://answers.launchpad.net/ubuntu-desktop-minimal/+question/110792)

---

### Post by aysiu on 2010-05-13
> **emarkay said:**
> Is that 100% correct for Lucid? Yes. I rebuilt the entire tutorial from the ground up with Lucid.

> I remove on every install:
Bluetooth/Bluez, Britty, Evolution, Indicator-Messages, F-Spot, Gnome Games*, Gwibber, Mono*, Rhythmbox, Tomboy, Totem, UbuntuOne, Unneeded Fonts*, Vinagre, Vino
* Multiple files, as required. 

Also see:
[https://answers.launchpad.net/ubuntu-desktop-minimal/+question/110792](https://answers.launchpad.net/ubuntu-desktop-minimal/+question/110792) That's a lot of what I get rid of as well.

The nice thing is that if you keep track of the packages you remove, you can always reinstall them, even if you're stuck at a command prompt.

---

### Post by sunshinecorp on 2010-05-13
The answers are very helpful so far. Has anyone had something broken by removing a certain application (on my list)? Experiences appreciated!

---

### Post by emarkay on 2010-05-13
> **sunshinecorp said:**
> The answers are very helpful so far. Has anyone had something broken by removing a certain application (on my list)? Experiences appreciated!

What I have removed in my list (a few there are on yours too) have not broken anything - and I have basically been getting rid of unwanted apps since the Dapper days...  :)

---

### Post by sunshinecorp on 2010-05-13
A google search revealed that I can get rid of Mono as well. That's good news. Not only don't I use Mono or any apps that depend on it, I didn't even know that it came installed by default...

[http://www.theopensourcerer.com/2010/04/29/how-to-remove-mono-from-ubuntu-10-04-lucid-lynx/](http://www.theopensourcerer.com/2010/04/29/how-to-remove-mono-from-ubuntu-10-04-lucid-lynx/)

```
sudo apt-get purge libmono* libgdiplus cli-common libglitz-glx1 libglitz1
```

Seems like it takes both F-Spot and Tomboy away with it... :)

---

### Post by emarkay on 2010-05-14
> **sunshinecorp said:**
> A google search revealed that I can get rid of Mono as well. That's good news. Not only don't I use Mono or any apps that depend on it, I didn't even know that it came installed by default...

Yup, all gone in my system as above... No Microsoft/CIA/FBI hooks in this system! :)

---

### Post by hxcobd on 2010-05-14
Whoa, the minimal install CD is only 20 megs? What on earth...

So tempting... But I don't know if I have the time or patience to build from the ground-up

---

