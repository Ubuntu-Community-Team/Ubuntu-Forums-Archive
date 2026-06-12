---
title: "Serial terminal?"
date: 2011-03-15
forum: General Help
---

### Post by 5149.5 on 2011-03-15
All I need is a simple dumb terminal to talk to a serial port. I started out trying GKermit. I installed it from the software center but I could not find it in apps or the main menu program. 

I removed it and tried CKermit. Same story. It showed as installed in software center, but I could not find it any where else. 

I removed it and tried Cutecom and then minicom. It was the same story with both of those. If any body knows of a serial terminal app that actually installs properly, I would be grateful.

---

### Post by mcduck on 2011-03-15
Most likely *all of them* installed properly, but are command-line applications and thus don't appear in your menus. Just open a terminal and execute them from there.

---

### Post by antaios256 on 2011-03-15
I regularily connect to cisco/nortel console ports via serial port/dumpterminal using

GTKTerm

note if it is a usb serial device, gtkterm needs to have teh adapter plugged in before you luanch the program.

---

### Post by 5149.5 on 2011-03-15
> **mcduck said:**
> Most likely *all of them* installed properly, but are command-line applications and thus don't appear in your menus. Just open a terminal and execute them from there.

Thanks for the answer. I'll give it another try. There should be something to let you know that is the case. I'll look for a clue as I go. :lolflag:

---

### Post by 5149.5 on 2011-03-15
> **mcduck said:**
> Most likely *all of them* installed properly, but are command-line applications and thus don't appear in your menus. Just open a terminal and execute them from there.

You were right. It did execute from the command line but it is an awfully skinny app. The help screen didn't even indicate a switch for setting line parameters. I assume this has to be done with stty before calling the terminal. I looked at the description and info in software center and there wasn't anything to tip me off that it was executed from the command line.

Thanks for the tip. That's the first command line application I've encountered on Ubuntu and now I know they still exist in this age of everything GUI. :D

---

### Post by 5149.5 on 2011-03-15
> **antaios256 said:**
> I regularily connect to cisco/nortel console ports via serial port/dumpterminal using

GTKTerm

note if it is a usb serial device, gtkterm needs to have teh adapter plugged in before you luanch the program.


Thanks.That one will work fine.

---

### Post by mcduck on 2011-03-15
> **5149.5 said:**
> You were right. It did execute from the command line but it is an awfully skinny app. The help screen didn't even indicate a switch for setting line parameters. I assume this has to be done with stty before calling the terminal. I looked at the description and info in software center and there wasn't anything to tip me off that it was executed from the command line.

Thanks for the tip. That's the first command line application I've encountered on Ubuntu and now I know they still exist in this age of everything GUI. :D

There's plenty of those around, for all things don't need a GUI, and some things are better done through command-line interfaces.

(plus the ability to create scripts using various command-line applications, which gives you powers beyond the imagination of people used to only running graphical applications, without even requiring much of programming skills or anything like that... ;)

Anyway, there usually isn't any "warning" about an app being a CLI application. Although not having a screenshot in the Software Center might serve as a hint, as might the programs description. But usually it's just assumed that people either already now what they are installing or check the manual.

(For example I don't know which one of those programs you tried, but if it's help screen didn't help a lot, probably it's manual page would have bee more helpful... You can run "man *nameofprogram*" to view a program's manual)

---

### Post by antaios256 on 2011-03-15
> **5149.5 said:**
> Thanks.That one will work fine.

No problem, just rember that each time you launch the application you may have to set your bit rates and select your device port (ive found the default config save doesnt work well)

---

