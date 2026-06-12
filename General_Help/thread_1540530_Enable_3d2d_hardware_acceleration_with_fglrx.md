---
title: "Enable 3d/2d hardware acceleration with fglrx"
date: 2010-07-27
forum: General Help
---

### Post by jxtreme on 2010-07-27
I am trying to figure out how to enable 2d/3d hardware acceleration, but I really don't know how. Can someone who has know-how help? I have the proprietary ati (fglrx) driver.

---

### Post by Zorgoth on 2010-07-27
How did you install it?

If you got it from "Hardware Drivers" it should just work.

If you got it from the ATI website you would need to run "aticonfig --initial" and reboot your computer (as described in the pdfs the download page links to).

I believe you would also need to reinstall the drivers for every update of Ubuntu if you got them from the ATI website.  If you have a 5xxx series, at least a Mobility 5xxx series, it is definitely worth it for the newer drivers though.

---

### Post by lizzibet on 2010-07-28
likely, you updated your drivers with ubuntu-tweak and now playonlinux isn't  working so well now?  disable the nvidia ppa uninstall the hardware drivers then reinstall them, be sure to have cleared out your package manager's cache to....

---

### Post by jxtreme on 2010-07-28
Ah, I see. I installed from the ATI website, but I could never aticonfig --initial because it outputed this:
```
Found fglrx primary device section
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-3
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.

```But I didn't think anything of it. I have a Mobility 4500, so whatever it is about 5xxx doesn't apply here. Don't use ubuntu-tweak/playonlinux. What version is the driver from Hardware Drivers? I want 10.6.

EDIT: Ooops, realized I have to run as superuser. Restarting now.
EDIT2: Success!
```
john@john-laptop:~$ glxinfo | grep direct
direct rendering: Yes

```

---

