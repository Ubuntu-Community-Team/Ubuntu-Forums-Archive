---
title: "Problem burning dvd with brasero..."
date: 2009-09-25
forum: General Help
---

### Post by gismo93 on 2009-09-25
Hi.

I tried burning a dvd with brasero earlier but had a bit of trouble.

i obviously had the dvd in and it had enough free space cuz it hasnt been used before.

anyway i selected the movie i wanted to burn, clicked burn and then the dialogue box comes up where you have to select what you want to burn it to, but the burn button was greyed out and there was a message there aswel saying:

"Please replace the disc with a supported cd or dvd"
"it is not possible to burn with the current set of plugins"

so the first part is obvious but these dvd's have never given me problems before?

ideas? thanx

---

### Post by XDevHald on 2009-09-25
Hi gismo,

Welcome to the Ubuntu Forums. Open Brasero and look at the top menu where it shows Project - Edit - Tools - Help and click on "Edit" then select "Plugins" and uncheck "File Downloader". Be sure everything else is unchecked as well besides the "Image Checksum".

Check back with us.

---

### Post by gismo93 on 2009-09-25
thanx for the reply xdev, ive done that but still getting the same message?

---

### Post by XDevHald on 2009-09-25
Hey gismo,

Sorry to see this did not work as it was just a small test checkup. This bug has been reported for 8.10 which has carried over to 9.04, odd.: [https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/322769](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/322769)

The above is a display of others having the exact same issue. However with others they have installed dvdauthor (which is in the reposority list by **apt-get install dvdauthor**.

Please try this while brasero is closed, then open it after dvdauthor has been installed and try again.

P.S My username on this forum has changed, just an FYI.

---

### Post by gismo93 on 2009-09-25
well, just installed dvdauthor but still hasn't fixed the problem?

maybe restarting may help?

thanx for your help xdev i really appreciate it!

---

### Post by XDevHald on 2009-09-25
If this did not work, go ahead and uninstall **apt-get autoremove dvdauthor** and remove brasero the same way and re-install it. With linux you don't have to reboot, it makes the system changes automatically.

You are VERY welcome, just trying my best.

---

### Post by philinux on 2009-09-25
Personally I would install k3b.

---

### Post by cgroza on 2009-09-25
Install "gnomebaker" it is in the repositories...

---

### Post by gismo93 on 2009-09-25
tried using gnomebaker didnt work either, im beginning to think its a problem with my cd/dvd drive?

---

### Post by XDevHald on 2009-09-25
Hey gismo,

It's a possibility. If the other applications that everyone has recommended have not worked, then you should check your drives for any errors.

---

### Post by delukard on 2009-09-25
i have also failed 3 atempts at burning an iso(ironically ubuntu 64 iso) and it always failed. (i was using ubuntu 32) i just booted to my xp64 and burn it with nero7 and it burned with no problems.

---

