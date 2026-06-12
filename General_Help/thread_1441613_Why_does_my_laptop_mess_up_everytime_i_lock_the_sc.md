---
title: "Why does my laptop mess up everytime i lock the screen?"
date: 2010-03-29
forum: General Help
---

### Post by JoeyF on 2010-03-29
First off, I have a Gateway MD2614U running Mint 8. But the problem happened with 9.10, Also. I'm using the proprietary driver. But it does it with the open source one, Too. Also whether or not I'm using Compiz, A custom theme, Or a Dock. 

When ever I lock the screen. Enter my password to unlock it. Reboot. The graphics mess up. And the only way I can fix it is to reinstall. I think it does it when I hard reboot, Also.

For example, One time when i turned it on and it went to the LM Leaf Logo. Underneath the logo was a green rectangle(Not the color green, Green as in part of the logo itself).

Another example:When it's loading the login box. You know with those two dots moving around. Once it's done spinning I get a black box behind them. It also does that after I have logged in. Before I get to the Desktop.

Am I the only one having this problem?

From what I heard on [http://brainstorm.ubuntu.com/idea/94/](http://brainstorm.ubuntu.com/idea/94/) it's AMD/ATI's fault. Is there any fixes?. I can go back to using the OS driver if I need to.


Thanks.

---

### Post by linden940 on 2010-03-29
that link you posted was for "Suspend and Hibernate"


so here is a fix for "Suspend and Hibernate" per that link 

well not really a fix but hey..it works...go into your power management preference and  if its a laptop change the "when laptop lid is closed" put it on "blank screen" and never spin down hdd and put it on no suspend/hibernate settings...

its a lazy cheap way to fix it...thats what i did..so when the screensaver comes up it will go into screensaver and THE screensaver HAS a password thing when i try to get back on..but it will open right up

---

### Post by JoeyF on 2010-03-29
I'm talking about when i lock it. Though.


Thanks.

---

### Post by linden940 on 2010-03-29
i know wht ur saying but that is something u can do so you can use your computer in the mean time as they fix it

---

### Post by JoeyF on 2010-03-29
No. I'm not talking about closing the lid. I am talking about System>Lock Screen or FN+F3.

---

### Post by JoeyF on 2010-03-30
Bump?

---

### Post by JoeyF on 2010-03-30
*deleted*

---

### Post by highfructose327 on 2010-03-31
looking at your model specs it looks like you are running a ATI Radeon HD 3200. 

you can check this by running 

```
lspci

```


if you are using fglrx drivers you could try to boot into recovery mode and run the following command:

Code:

```
sudo aticonfig --initial -f
```

that seemed to help others with graphics issues

here are a couple different post you might want to check out.

[http://ubuntuforums.org/showthread.php?t=1307041&page=2](http://ubuntuforums.org/showthread.php?t=1307041&page=2)

[http://ubuntuforums.org/showthread.php?t=1133950](http://ubuntuforums.org/showthread.php?t=1133950)

---

### Post by JoeyF on 2010-03-31
Thanks. I'll try that.

Two more things:Should i do that while i'm still having the problem to fix it  or after a reinstall to prevent it?. And does anybody have any more info about it/What could be causing it?.


Thanks.

---

### Post by JoeyF on 2010-04-01
Ok, So i tried the command but it didn't fix it. I'll try it after i reinstall the OS and install the Proprietary Driver.

2 things:
Is it better to do it from the Recovery Terminal or the Regular Terminal?.
And do you know anything about it doing it with the Open Source driver?.


Thanks. :)

---

### Post by JoeyF on 2010-04-02
Thank you so much!.

I got it working. After I installed the Proprietary Driver and before I rebooted I went to the terminal and did:
```
sudo aticonfig --initial -f
aticonfig --acpi-servces=off
```

:)

---

### Post by JoeyF on 2010-04-24
Sorry for reopening this.

I still have GNOME. And it's working fine.

But I went into Synaptic and installed Kubuntu-Desktop, Suspended/Locked the screen. Unlocked it and the graphics messed up(Staticy green bar at the top on resuming).

But GNOME's stil fine.

Any ideas?.

I'd figure doing the solution earlier would apply to that as well. I know I have the same driver on the KDE side because it had Desktop Effects on by default.


Grr. Can't wait till I go Nvidia :P


Thanks.

---

### Post by JoeyF on 2010-04-25
I went back to the default Open Source Driver because I was having problems with FGLRX.

Is there any fix for the Open Source Driver?.

Thanks.

---

