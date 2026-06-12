---
title: "Can't open terminal and other apps! Problems after automatic update and reboot"
date: 2010-09-24
forum: General Help
---

### Post by kenny99 on 2010-09-24
Hi, I did an automatic update and rebooted this morning and I now have a bit of a nightmare situation where I can't open the majority of applications, including the terminal. When I rebooted, my desktop loaded as normal, but then when I try to open the terminal (from Applications -> Accessories or from my quick launch panel), nothing happens other than the quick launch panel disappears for a second then reappears. This is the case for most other apps, but not for Chrome (obviously).

Does anyone know of this issue or how I could go about fixing it? Really grateful for any help as stuck at work and can't actually do anything until I get this fixed!

EDIT: Used Alt+F2 to open the terminal, ran safe upgrade and then rebooted, but still having the same issue. As Ubuntu was booting, there was a "Broken pipe" message, which didn't stop the boot process but is still a bit worrying. I've run a file system check but this hasn't resolved the problem either.

---

### Post by kenny99 on 2010-09-24
Anyone?

---

### Post by stlsaint on 2010-09-24
Try re-installing an application that isn't working. This will help in aid in troubleshooting.

---

### Post by kenny99 on 2010-09-24
Thanks for the reply. It seems I can launch all applications via Alt+F2, but, for example, I can't launch anything at all from the System menu. When I try to do this, the top panel disappears then fades back in, and nothing else happens. I'm running the 64 bit version of Lucid. All very strange! Any ideas?

---

### Post by kenny99 on 2010-10-05
I still haven't been able to resolve this issue. Can anyone help? I also can no longer access my local server on my work LAN - I get the error: Nautilus cannot handle "smb" locations.

---

### Post by SPr on 2010-10-05
Launch a terminal with alt+f2 and from the terminal try and launch other programs. What errors are given?

Look in the System log viewer for errors. Use 
```

gksu gnome-system-log

```
from a terminal to open it.
```

dmesg|grep broken
dmesg|grep error

```

They might reveal a few clues.

---

### Post by kenny99 on 2010-10-06
Thanks for the pointers @SPr, here are the results:

dmesg|grep broken - returns no results
dmesg|grep error - all errors are libflashplayer.so related, which I'm pretty sure is nothing to do with my current issue. 

In the system log, I'm trying to find any relevant issues - the problem I mentioned in my last post, about trying to connect to a local server with Samba, seems to be generating this error:

gnome-screensaver-dialog: pam_smbpass(gnome-screensaver:auth): Cannot access samba password database, not running as root.

Apart from that, I can't see anything obvious in the logs which would be causing the issues I've mentioned.

---

### Post by waperboy on 2010-10-06
Right click on the application menu, select to edit the menu. Then go select an app that does not work and edit it, and see how the commandline to start the app looks. Try start the terminal from alt-f2 and paste that commandline in the terminal and watch for error messages.

---

### Post by kenny99 on 2010-10-06
I can right click on the Application menu, but when I select "Edit Menus", nothing happens. All very strange! Anything else I can try?

---

### Post by kenny99 on 2010-10-07
Ok I've run update and upgrade from the terminal and then rebooted to see if that would correct the problem I'm having, but alas no joy :( However, it does get rid of the broken pipe message I was getting previously.

Anyone any ideas what's going on with this? Thanks for the help so far.

---

### Post by SPr on 2010-10-08
Have you tried opening any of the offending programs from the terminal yet?

---

