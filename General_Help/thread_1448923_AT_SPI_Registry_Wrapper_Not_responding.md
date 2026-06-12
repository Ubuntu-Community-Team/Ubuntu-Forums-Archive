---
title: "AT SPI Registry Wrapper Not responding"
date: 2010-04-07
forum: General Help
---

### Post by wellington7 on 2010-04-07
Hello! I'm new to Ubuntu (to Linux, actually).
After a month of use, always I click to shut down the system I get the message "AT SPI Registry Wrapper Not responding".

There is a screenshot attached. What is this program, and any idea how to solve this?

---

### Post by ajgreeny on 2010-04-07
There have been bugs posted about this in the past, which I admit I haven't searched in detail, but if you don't actually use any screen-readers or assistive technology applications, such as orca, you can disable the **at-spi registry wrapper** in the startup applications list in *System ->Preferences ->Startup Applications*.

---

### Post by mkarnicki on 2010-09-23
I'm running 10.04, what if I have the same problem and no trace of at-spi registry wrapper in the Startup Applications window? See attached screenshot (pops sometimes after Shutdown is selected from the menu).

EDIT: I just read that removing at-spi might help. Since I'm not using accessibility thingy's, that'll probably help.

---

### Post by fisch246 on 2011-05-20
anyone have any idea how to fix this in 11.04? i can't find it in the Startup Application unfortunately, and i don't use accessibility apps, so if there's a way to disable it for good in 11.04 please let me know.

---

### Post by linuxinstalledfromhdd on 2011-05-20
disable Assistive Technologies (System / Preferences / Assistive Technologies),

---

### Post by mkarnicki on 2011-07-26
wellington7, could you please mark this thread as 'solved'?
linuxinstalledfromhdd's solution does the trick :)

---

