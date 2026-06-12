---
title: "Flash &quot;click-to-play&quot; no go"
date: 2009-12-06
forum: General Help
---

### Post by cpeachey on 2009-12-06
Karmic/Firefox 3.5.5./amd64bit
Flash video clips do not run when "click to play" is pressed.
Flash/about says I had 10.0.32.18 but is this 32bit or 64bit?
I have tried some of the flash install suggestions but the instructions seem mostly to be incomplete!
this one for example....
# Inside the folder that extracts is a "Get64bitFlash" file, double click on it.
# Select "Run in Terminal"
# When the terminal closes, restart your browser.

Terminal opens with lots of instructions but does not actually do anything!
Can anyone help please?
Chris

---

### Post by IllegalCharacter on 2009-12-06
This is a common issue, I had the same problem when upgrading to Karmic.

Try this from a terminal (Applications->Accessories->Terminal):
```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

Right before the last line put:
```
export GDK_NATIVE_WINDOWS=1
```

Save it and restart Firefox. See if that helps.

---

### Post by cpeachey on 2009-12-06
What a star!
I did not see this solution when I was searching so many thanks.
I have been using Ubuntu for most of the year and each time I re-install it everything seems to work first time except Adobe Air and Flash which both seem to need commands entering into Terminal. (not something "average" users want to do).
Thanks again
Chris

---

