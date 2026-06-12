---
title: "Quit applet"
date: 2010-07-28
forum: General Help
---

### Post by bouncingwilf on 2010-07-28
One of the many reasons I switched to Linux was that I was fed up of Windows asking me to confirm every action. Having once been (many years ago) a system administrator on a Unix system, one of the things I liked best was that you could issue a command and the system silently did exactly what you told it, now it seems, we have slipped into the nanny Windows world.

My current problem is that my boat computer is wired to the boat's ignition system and when I switch the engine off, I'd like the computer to shut itself down (flat batteries on boats are very bad news!) However, despite receiving a valid "shutdown" command from the computer PSU, Lucid insists on putting a message on the screen and continues to remain up until the command is confirmed. This is NOT the behaviour I want. Is there any way please of disabling this annoying feature and getting the PC to automatically shutdown?

Bouncingwilf.

---

### Post by aeiah on 2010-07-28
take a look at /etc/acpi/powerbtn.sh

this seems to bring up the menu if you havent got suspend/hibernate/resume set up to use the power button. perhaps you'd prefer to use suspend on power off rather than shutdown? if that's the case, you'll have to look into gnome-power-preferences.

if you do want it to send the shutdown signal, you'll see from the powerbtn.sh script that it does this as a last resort once it checks for suspend/hibernate options, and when it can't open the menu thing for you.

i assume just replacing powerbtn.sh with a script that does ```
/sbin/shutdown -h now 
```
will be sufficient.

unless we're talking about a different menu or something, of course. pressing the power button and your shutdown method may be different. when i press my power button it looks like this:

[img]http://img830.imageshack.us/img830/5518/screenshotmp.png[/img]

---

### Post by bouncingwilf on 2010-07-28
Many thanks - 10 years retired and I though I'd left scripting behind - I seem to remember shutdown -g0 -i0 used to work! I'll give it a try when I get to the boat and take it from there.


Bouncingwilf

---

