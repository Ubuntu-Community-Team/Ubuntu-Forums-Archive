---
title: "Installed Wubi but doesn't run and windows slowed right down"
date: 2010-09-07
forum: General Help
---

### Post by whity4420 on 2010-09-07
Hi, new to all this so sorry in advance if some patience is needed!

Basically I set Wubi installing and it went through its restart. I selected it from the menu and it carried on with the installation. At the end a load of text ran through very quickly and the computer restarted.

Now when I selected ububtu a menu appears with a choice of 3 versions of windows, and just loads that.

Im lost and more than a little bit confused, any help would be appreciated!

Oh, also windows takes about 10 minutes to load up now.

---

### Post by bcbc on 2010-09-07
> **whity4420 said:**
> Hi, new to all this so sorry in advance if some patience is needed!

Basically I set Wubi installing and it went through its restart. I selected it from the menu and it carried on with the installation. At the end a load of text ran through very quickly and the computer restarted.

Now when I selected ububtu a menu appears with a choice of 3 versions of windows, and just loads that.

Im lost and more than a little bit confused, any help would be appreciated!

Oh, also windows takes about 10 minutes to load up now.
There's no reason windows should take longer to boot. That I know of.

Did you press the SKIP button during the install? This is not good for wubi installs as it bypasses a very important package (lupin-support) that is required for wubi. One of the symptoms is a grub menu with no Ubuntu entries, just windows. 
If you did you should reinstall wubi.

---

### Post by whity4420 on 2010-09-07
Well there's a definite change in windows. It took 5 minutes or so for the uninstaller to start [though it ran fine once it opened] and I'm waiting now for the installer.

Thanks for the reply though. I shall let you know how the reinstall ends up (:

Maybe a system restore will help windows? If not I can always reinstall that I guess.

---

### Post by garvinrick4 on 2010-09-07
What version of Wubi did you use 10.04 or 10.10

---

### Post by whity4420 on 2010-09-07
10.04

I have windows back to normal speed through a system restore, and am currently reinstalling Wubi. Shall see how it goes.

---

### Post by bcbc on 2010-09-07
> **whity4420 said:**
> 10.04

I have windows back to normal speed through a system restore, and am currently reinstalling Wubi. Shall see how it goes.

Just make sure you're not using your remaining disk space for wubi. That'll kill windows for sure. Other than that I can't think of any reason that windows will slow down.

---

