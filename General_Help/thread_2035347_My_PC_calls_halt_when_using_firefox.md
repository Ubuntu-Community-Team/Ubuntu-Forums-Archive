---
title: "My PC calls halt when using firefox?"
date: 2012-07-30
forum: General Help
---

### Post by telac on 2012-07-30
I'm using Ubuntu 12.04 64 bit, 3.2.0-27-generic kernel.

Basically when I'm using Firefox (14.0.1) I randomly have my PC shutdown entirely and during this shutdown its writing "will now halt" so it looks like a legit shutdown.
Text on shutdown screen is: "Broadcast message from root: System is going down for halt now!"

I think its in some form related to me pressing ENTER in firefox, as it often happens when I'm visiting a new page, but currently running Chrome to see if its related in any way.
EDIT: It happens in Chrome also, so its not browser dependent.

I'm running dual screens (separate xsessions) using Gnome3 as shell. Using NVIDIA driver which previously have been reported for crashing when using ENTER button but for me it simply calls a shutdown of PC, not just freezing. I see a normal shutdown procedure of closing down services and eventually power off. It shows on screen among the log lines: "will now halt".

I tried disabling the powerbtn.sh script in /etc/acpi/ but it seems its not that, and /var/log contains nothing, there is no indication of what is calling the shutdown.
I'm running out of things to check for anymore, and have no clue if its really a shutdown command being called or an internal process due to a crash etc?

Anyone experienced something similar that maybe can shed some light on this or give me more clues where to solve this mystery?

---

### Post by telac on 2012-08-08
SOLVED!

Turns out its was an issue with a Gnome extension that set the shutdown menu to "power down" instead of suspend.

That, in combination with multiple desktops could sometimes cause my keyboard to control the other desktop and in a certain combo, call that event. After I disabled the extension, the problem disappeared. It makes sense also with browsers because those are programs where ENTER + DOWN buttons are heavily used..

Phew! That was a tough nugget to crack ;-)

---

