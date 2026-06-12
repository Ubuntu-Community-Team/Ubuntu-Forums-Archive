---
title: "When Close Lid, Computer Won't Sleep"
date: 2010-05-01
forum: General Help
---

### Post by emagine on 2010-05-01
Hello everyone,

I just installed ubuntu 10.4 and when I close my laptop, it does not go to sleep.  The hard drive is still on and the computer is still working even after I have closed it. Any ideas on how to fix?

Thank you.

---

### Post by jaybok on 2010-05-02
may be a silly suggestion, take a look at System ->Power Management.  My settings from 9.10 did not transfer correctly after upgrading.

---

### Post by Nick43092 on 2010-05-02
Any chance you're using Wubi? Wubi doesn't seem to support that at all.. I close my lid and it does the same...

---

### Post by emagine on 2010-05-02
> **jaybok said:**
> may be a silly suggestion, take a look at System ->Power Management.  My settings from 9.10 did not transfer correctly after upgrading.
yes, I have tried that.  For "When laptop lid is closed" the only option I get is "blank screen", I cannot remember if in 9.10 I was offered "sleep" as an option.

---

### Post by emagine on 2010-05-02
> **Nick43092 said:**
> Any chance you're using Wubi? Wubi doesn't seem to support that at all.. I close my lid and it does the same...
No, I am not using Wubi. I just upgraded from 9.10.

---

### Post by rfindler on 2010-05-07
I'm having this problem. In 9.0x I closed my lid and it went to sleep. In 10.4, I see the preference is set to suspend, but when I close the lid, it does not suspend.

I'm using an hp 2140 if that matters. Is there some way I can try to diagnose this?

---

### Post by emagine on 2010-05-07
> **rfindler said:**
> I'm having this problem. In 9.0x I closed my lid and it went to sleep. In 10.4, I see the preference is set to suspend, but when I close the lid, it does not suspend.

I'm using an hp 2140 if that matters. Is there some way I can try to diagnose this?
I figured it out.  You should have a battery icon in the top right.  Left click it and go to preferences.  Just set it to suspend.  For some reason this option was not there before.  I don't know if this matters, but it might help to put a battery in your laptop, instead of just leaving it plugged in without a battery.  It might activate the option.  Try it and report back.

---

### Post by 0ziris on 2010-05-08
> **rfindler said:**
> I'm having this problem. In 9.0x I closed my lid and it went to sleep. In 10.4, I see the preference is set to suspend, but when I close the lid, it does not suspend.

I'm using an hp 2140 if that matters. Is there some way I can try to diagnose this?

I have the same problem on my HP mini 5101. After upgrade it won't go to sleep if the lid is closed. Is this a HP issue?

---

### Post by 0ziris on 2010-05-10
I tried a fresh install and it makes no difference, the problem still persists. Anyone knows how to diagnose such a problem?

---

### Post by emagine on 2010-05-10
> **0ziris said:**
> I tried a fresh install and it makes no difference, the problem still persists. Anyone knows how to diagnose such a problem?
You tried click the battery icon and changing it in the preferences?

---

### Post by 0ziris on 2010-05-11
> **emagine said:**
> You tried click the battery icon and changing it in the preferences?

By clicking the battery icon you mean setting the Power Management Preferences in System Preferences. The battery is just a notification icon and a shortcut. So the real problem is with the Power Management.

---

### Post by emagine on 2010-05-11
> **0ziris said:**
> By clicking the battery icon you mean setting the Power Management Preferences in System Preferences. The battery is just a notification icon and a shortcut. So the real problem is with the Power Management.
Yes, I was just recommending one way of getting to it.  Send me a screenshot of what you see under the power management, I have attached a screen shot of what you should see.

---

### Post by efflandt on 2010-05-11
I have an older HP desktop (from 2004), but that is not the issue.

10.04 uses a new kernel mode (KMS) video driver that can interfere with suspend, or at least it does with my ATI X1300 video.  I could not suspend or hibernate with the default kernel mode radeon driver, and it also seemed to slow up video on my system (glxgears was not moving, just jerking occasionally).

So I disabled KMS to use the user space module.  That seems faster (glxgears runs smoothly "much" faster) and suspend and hibernate work.

So try that and see if that helps.  To do that from the grub menu, press e, and then after **quiet splash** add a space and **nomodeset**.  If that helps add it to /etc/default/grub (use sudo prefix on your editor) and **sudo update-grub**.  Putting it on the 2nd line like below would use it for all kernels including (recovery).

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="nomodeset"

---

### Post by martintremblay on 2010-06-10
I have the same problem on Compaq/HP notebook worked fine on Ubuntu 9.10, but closing lid no longer makes system suspend or hibernates on 10.04.

I have attempted to make changes to "System-Preferences-Power Management".

Selecting either "blank screen" or "suspend" or "hibernate" on bat power or ac power has no effect. 

Attempting to make default also has no effect

Appears to be a possible bug.

I have attached shot of Battery PMP screen (my AC is pretty much the same)

---

### Post by martintremblay on 2010-06-10
I tried changing "**nomodeset" **but it made no difference.

(I have Intel 945 Video - also not well supported by Intel on Linux/Ubuntu)

---

### Post by macrules on 2010-07-17
I have the same problem on my mivvy G310 netbook.
it is a default N450 config netbook.
Did anyone file a bug for this?

---

### Post by rdzrdz on 2011-01-15
bump....

anyone?  Same problem with my mini and no solutions seen sofar

---

### Post by Mr Nemo on 2011-06-20
bump

---

