---
title: "Broken packages synaptic can not find. Please help!"
date: 2011-11-27
forum: General Help
---

### Post by colobix on 2011-11-27
IN synaptic when I try to upgrade a package, it says that I need to fix broken packages first.
So when I click "fix broken packages", I get this error message:

E: Unable to correct problems, some broken packages are held back.
E: Error, pkgProblemResolver:: Resolve generated a breach, it may be due to packages held back.
E: Unable to correct dependencies
E: Error, pkgProblemResolver:: Resolve generated a breach, it may be due to packages held back.

E: Unable to correct dependencies

How do I fix this?

---

### Post by azertyh on 2011-11-27
hello,
in synaptic, look at custom filters/broken, reinstall ou remove the packages listed there.

---

### Post by BC59 on 2011-11-27
You can do as well 


```
sudo dpkg --configure -a
```

and then

```
sudo apt-get -f install
```

---

### Post by colobix on 2011-11-27
Thanks but none of that worked.
The terminal way said there was nothing to upgrade, install or remove.
The synaptic way doesn't work because I can't do changes in synaptic when I have broken packages.

Now what do I do?

---

### Post by oldtimer7777 on 2011-11-27
> **colobix said:**
> Thanks but none of that worked.
The terminal way said there was nothing to upgrade, install or remove.
The synaptic way doesn't work because I can't do changes in synaptic when I have broken packages.

Now what do I do?

power-cycle your entire system

After you power cycle your system, run those commands above in your Terminal, and cut and paste what it says please..

---

### Post by colobix on 2011-11-27
Power cycle?
What's that?

If it means reinstall, I'm not gonna do that.
If it means restart, I just did, and nothing new happened.

---

### Post by oldtimer7777 on 2011-11-27
Use Google to look up unfamiliar terms you find here..

Power Cycle means to reboot your system, and then use the above posted commands in your Terminal.

> **colobix said:**
> Power cycle?
What's that?

If it means reinstall, I'm not gonna do that.
If it means restart, I just did, and nothing new happened.

Reboot your system and run this in terminal:

```

sudo dpkg --configure -a 
sudo apt-get -f install
sudo apt-get -f update
sudo apt-get upgrade
```

---

### Post by colobix on 2011-11-27
Wow. I think that last one worked for some magic reason.
Thanks:)
But when repairing the system is that easy, why can it not do these things automatically?
It would give linux a way more user friendly image.
Instead of now when it says "broken" every time there's something installed the wrong way.
It scares people away, you know.

---

### Post by oldtimer7777 on 2011-11-27
> **colobix said:**
> I told you I just did that.
Still says there's nothing to remove, install or upgrade.

Did you reboot?

You may have to do things more than once here..... if you want help

Also cutting and pasting your results in terminal would be good so we can see the errors.

---

### Post by colobix on 2011-11-27
oh NO it still says I have to fix the broken packages first, now when I try to use synaptic.

---

### Post by oldtimer7777 on 2011-11-27
> **colobix said:**
> oh NO it still says I have to fix the broken packages first, now when I try to use synaptic.

Stop trying to use synaptic for a minute.  And use Terminal for now..  You can do everything Synaptic does from terminal for now. Use those commands to try to fix your broken packages.   Do you know what Terminal is?

---

### Post by colobix on 2011-11-27
Thanks. I think it works now.
I did a restart, and now I believe everything is fine.
The thing about the terminal is that it's more risky.
I mean it's scarier than synaptic.
Oh well. Thanks for your help.
I really wish these things could be done automatically.
It shouldn't be necessarily for a regular pc user to go though all this scary frustrationness.

---

