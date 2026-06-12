---
title: "Virtual Machine: Windows XP or 7?"
date: 2010-01-29
forum: General Help
---

### Post by JesterDev on 2010-01-29
Just curious what would be faster. Windows 7 seems faster, and less ram intensive then XP, but on a VM which would be better?

I just need it for my ipod touch. 

Intel T8300 2.40Ghz (dual core)
2 Gigs Ram

---

### Post by UranUtan on 2010-01-29
I am not sure that Win7 is faster nor less RAM intensive than XP. May be you meant the opposite.
 
In anyway, the VM with Win7 will have triple the size of the one with XP (in terms of VM file size). In my experience, a VM with WinXP is far more economic in resource and take less disk space. Win7 after some system updates and software install has the tendency to bloat disk usage which is very hard to reclaim.
 
Once installed, you can run the VM with XP on any host. While the VM with Win7 will reset the activation status if the host has different CPU. For example, you had activated Win7 when running the VM with your laptop. When you run this VM with your desktop it might reset the activation status (but if you run it again with the laptop, then Win7 remains activated).

I recommend Virtualbox 3.12. Do you need Internet when you connect your iTouch to the VM? If not, then you can even disconnect the VM from the internet by setting a blank IP in the Gateway property in WinXP Network settings. The VM can still communicate with the LAN but is disconnected from the Internet. This would make your Windows unattackable.

Good lucks.

---

### Post by howefield on 2010-01-29
> **JesterDev said:**
> Just curious what would be faster. Windows 7 seems faster, and less ram intensive then XP, but on a VM which would be better?

I just need it for my ipod touch. 

Intel T8300 2.40Ghz (dual core)
2 Gigs Ram

They say perception is reality, but in this case, I'd say it was dreaming.

Any XP install I've seen or used boots up in a couple of hundred megabytes of RAM, give or take. Whilst Windows 7 is at least triple that.

Likewise disk space usage.

As for speed, I have no issues with either but I'm not putting a stopwatch on them. If the overall experience is good, I am not bothered by a few milliseconds here or there.

---

### Post by Objekt on 2010-01-29
I'd go with Win XP.  It's simply less resource-intensive.  Since you really only need it for one app, why bother with all the extra stuff in Win 7?  Win 7 is pretty, but is overkill for running iTunes (or whatever it is that the Touch requires).

Also, as UranUtan pointed out above, with Win 7 there's the "activation" nonsense to deal with.  Product "activation" is a neutral-sounding word for a very ugly thing: being forced to obtain Microsoft's permission to use software you paid for.  That kind of crap, and others, prompted me to deprecate use of Microsoft operating systems for good.

Win XP may or may not require activation (VLK and OEM versions don't), but you will only have to activate the virtual install once.  I've never moved virtual machines between physical host systems, but one ought to be able to do so without issue.

---

