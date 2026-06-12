---
title: "FireFox mouse wheel scrolling up problem"
date: 2010-05-15
forum: General Help
---

### Post by xmsft on 2010-05-15
I just finished installing 10.04. When I use the mouse wheel to scroll up, Firefox loads previous pages in my history.  I had the same problem in 9.10.  I've searched through the net looking for solutions.  Most solutions talk about adjusting mousewheel.withnokey options.  However, everything I try doesn't stop it from loading previous pages when using the mouse wheel to scroll up.  My current settings are as follows:

mousewheel.withnokey.action = 0
mousewheel.withnokey.numlines = 6
mousewheel.withnokey.sysnumlines = true

Using the mouse wheel to scroll down works fine.  It's only when scrolling up.  Has anyone else experienced this problem.  I'm using a Microsoft Optical Intellimouse.

Any assistance would be appreciated.

Thanks,
Dale

---

### Post by lovinglinux on 2010-05-16
Is your mouse wireless? Do you have a wireless router? I'm asking this because I had a wireless mouse that was affected by the router signal, making it do strange things like that.

Have you tested if it affects other browser?

Also test if this problem happens with a clean Firefox profile so we can rule out some possible culprits.

To create a new profile run the profile manager. Close Firefox and run it with the command below:

```
firefox -P
```

---

### Post by xmsft on 2010-05-17
I just installed Chrome and experience the exact same behavior.  The command Firefox -p has no affect.

Any ideas?

Thanks.

---

### Post by lovinglinux on 2010-05-17
> **xmsft said:**
> I just installed Chrome and experience the exact same behavior.  The command Firefox -p has no affect.

Any ideas?

Thanks.

It must be a Gnome issue then or a hardware/driver issue.

Try to create a new Ubuntu user and login in to that account to see if the problem persists. If yes, then is probably a hardware/driver issue.

---

### Post by xmsft on 2010-05-17
Well, you got me to thinking....This mouse is a wired Microsoft optical mouse, which is a pretty simplistic mouse.  However, it is a USB mouse using a PS/2 adapter plugged into a Cybex KVM switch which then plugs into the machine's PS/2 port.  So, I bypassed the KVM and plugged the mouse directly into a USB port on the machine and boom, it's started working correctly.

Interestingly, I've never had a problem with this KVM before or the adapter.  Windows always worked fine as well as "older" versions of Ubuntu.  I think the last time it worked was 8.04, but I couldn't swear to that.  It's been a while since I've used this machine.  I normally use my laptop which has never had any issues.  Anyways, this narrows it down.  It's either the KVM or the PS/2 adapter in conjunction with the driver.

Thank you very much for pointing me in the right direction.

---

### Post by lovinglinux on 2010-05-18
> **xmsft said:**
> Thank you very much for pointing me in the right direction.

You are welcome. I'm glad you solved the problem.

---

