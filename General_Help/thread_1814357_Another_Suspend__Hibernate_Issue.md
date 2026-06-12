---
title: "Another Suspend / Hibernate Issue"
date: 2011-07-29
forum: General Help
---

### Post by telseth on 2011-07-29
I have a Dell Latitude E6500.  Recently, my suspend and hibernate just stopped working.  It did work in the past I know, but I cannot remember when it stopped so it would be hard for me to pinpoint a cause.  I have 11.04 installed.

What happens is when I put my computer into suspend, it starts shutting down things and about 5 seconds later just drops everything (power off).  The pm-suspend log doesn't have anything of note except sleeping NetworkManager Fails.  The last log message is this, so maybe knowing what should come next could be helpful:

> /usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.

Hibernate is even more fun, the screen blanks and then the fan starts churning, the keyboard backlight turns on and the numberlock and scroll lock lights start blinking.  And that is where it stays until I perform a hard reset.

Has anyone else run across anything like this?  I can live without these features, but they are handy and I hate when things don't work.

---

### Post by royer10r on 2011-08-15
i am about to buy a e6500 and was wondering if you figured this out

also do you have the integrated graphics or the nvidia?

---

### Post by telseth on 2011-08-16
I have the nvidia chipset, and I wouldn't worry.  It used to work, it just started to fail.  I'm sure if I did a fresh install I would be fine.

---

