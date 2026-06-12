---
title: "Skip Black Screen on Startup"
date: 2011-08-27
forum: General Help
---

### Post by freshaslupe on 2011-08-27
I am running Ubuntu 11.04 on my eee pc along with Windows XP. After picking Ubuntu from the Windows boot screen there's the Ubuntu boot screen that's timed out to 10 seconds. Then there is a black screen with a line flashing in the upper corner before the Ubuntu logo and logon screen. How can I skip all the screens completely on startup and go straight to the Ubuntu logo like in Windows.

---

### Post by searchfgold6789 on 2011-08-27
[See the Grub 2 Guide.]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by kyletstrand on 2011-08-27
Check this thread specifically.  You should then be able to get a different splash screen.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by freshaslupe on 2011-08-27
> **searchfgold6789 said:**
> [See the Grub 2 Guide.]("http://ubuntuforums.org/showthread.php?t=1195275")

I am not having a black screen error I just want to skip all the screens like in Windows so Ubuntu will boot faster. Ubuntu boots up fine it's just that the black screen stays there for a while making the boot take longer.

---

### Post by freshaslupe on 2011-08-27
> **kyletstrand said:**
> Check this thread specifically.  You should then be able to get a different splash screen.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

I am not having a black screen error I just want to skip all the screens  like in Windows so Ubuntu will boot faster. Ubuntu boots up fine it's  just that the black screen stays there for a while making the boot take  longer.

---

### Post by searchfgold6789 on 2011-08-29
If this black screen is the Grub screen, then simply set the countdown to 0 using the guide.

---

### Post by freshaslupe on 2011-08-30
> **searchfgold6789 said:**
> If this black screen is the Grub screen, then simply set the countdown to 0 using the guide.

It is not the grub screen. It is a black screen after the grub screen with a flashing cursor in the upper corner.

---

### Post by Mark Phelps on 2011-08-30
Do you have the following sequence:
1) Start the PC
2) Get a bunch of boot messages
3) Screen goes blank -- but not black
4) Some time later (minute or more), screen goes black
5) Some time later, Ubuntu login screen appears.

If that's the case, the "black" screen is Ubuntu loading -- and since your GRUB file is probably configured with the "quiet" option, nothing is being displayed.

In that case, there is nothing you can do -- because it takes time for all the processes to load before you see a desktop.

---

### Post by notgary on 2011-08-30
> **freshaslupe said:**
> It is not the grub screen. It is a black screen after the grub screen with a flashing cursor in the upper corner.

Unfortunately there's nothing you can do about that since it's a part of the boot up process.

---

### Post by notgary on 2011-08-30
I've submitted this as a paper cut [here]("https://bugs.launchpad.net/ubuntu/+source/grub/+bug/837581"). If you want you can head over there and add your two cents.

---

### Post by freshaslupe on 2011-08-30
> **notgary said:**
> I've submitted this as a paper cut [here]("https://bugs.launchpad.net/ubuntu/+source/grub/+bug/837581"). If you want you can head over there and add your two cents.

Okay, thank you.:)

---

