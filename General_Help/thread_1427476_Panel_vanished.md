---
title: "Panel vanished"
date: 2010-03-11
forum: General Help
---

### Post by XR171 on 2010-03-11
A friend of mine (doesn't have an account here yet) booted up his computer today and the top panel that he uses for launching applications, places,  system, and other functions of it was gone.  He rebooted but it was still gone.  He tried accessing the setting for it but nothing happened.  He removed the bottom panel manually some time beforehand.

Desktop icons still work.  Xubuntu is installed alongside Windows ME.   Machine has about 400 Mb RAM, 40 Gb HD, 1.4 ghz AMD Athlon.  Any ideas or help would be greatly appreciated.

Thank you.

---

### Post by J_Stanton on 2010-03-11
just go into system settings and you will be able to add panels.

---

### Post by CaptainWraith on 2010-03-11
its not letting me add a panel at all. i went to settings and tried to do it that way but nothing happened when i clicked on the panel option.

---

### Post by onyxvu on 2010-03-11
i am having this exact same problem on xubuntu. i have not removed the other panel though, but i cannot access the panel settings from any direction...

edit- i forgot to add that the panel only appears to missing in the xfce session, my gnome panels appear to be ok

---

### Post by CaptainWraith on 2010-03-12
i also just found that i don't have sound anymore

---

### Post by onyxvu on 2010-03-12
my sound has never worked, though my system sound works, so does that make it a driver issue? im more concerned about getting my panel back...

---

### Post by fisheater on 2010-03-12
Check the last post on this thread.

[http://ubuntuforums.org/showthread.php?t=1318353&page=2](http://ubuntuforums.org/showthread.php?t=1318353&page=2)

good luck!

FE

---

### Post by denham2010 on 2010-03-13
> **fisheater said:**
> Check the last post on this thread.

[http://ubuntuforums.org/showthread.php?t=1318353&page=2](http://ubuntuforums.org/showthread.php?t=1318353&page=2)

good luck!

FE

The above is a Gnome solution. For Xfce, open a terminal or press CTRL + F2 and enter:

```
xfce4-panel &
```

This will restart your panels. You should now be able to open the settings manager for panels and re-configure them.

Cheers.

---

### Post by onyxvu on 2010-03-13
thank you denham! this worked perfect. now is the some code for checking the sound drivers? i will turn the sound on, then restart and the sound is auto muted. the sound works fine in my bios so i know that it is a OS problem... any ideas?

---

