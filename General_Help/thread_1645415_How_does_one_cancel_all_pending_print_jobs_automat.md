---
title: "How does one cancel all pending print jobs automatically when loging out of a sessiou"
date: 2010-12-14
forum: General Help
---

### Post by melolontha-melolontha on 2010-12-14
Sometimes I want to keep something in PDF files, so I print to the PDF "printer". However, if I inadvertetnly forget to check the PDF creation and rather take the real printer (which is usually only powered up, when I really want to print something), printing goes to the real printers queue and nothing happens ... until, possibly some sessions later, I want to print something (on paper rather than PDF) and power up the printer.

Then all inadvertent garbage comes first and chances are big, that the printer gets junk during power up or reconnecting the cable to the computer and then the whole thing is wasting even more paper, since escape-sequences sent to the printer get chopped and misunderstood by the printer.

In order to stop this alltogether, I am looking for a mehtod, to automatically flush the whole printing queue every time when I log out of my ubuntu session.

I know, there is a command lpq to tell which print jobs are pending, I also know the command cancel -Umyname -a, but this requests for my password. I want to kill all those incomplete or pending print jobs automatically. 

And how do I hook such a command script into the logoff or shutdown sequence? 

Thanks in advance for helping with my - possibly stupid- question!

---

### Post by melolontha-melolontha on 2011-02-12
Meanwhile I have found out myself, how to get the desired effect - however flushing the queue automaticly after *starting* a session, rather than *when closing the actual sessio*n.

The first observation: the command

[INDENT][FONT="Courier New"]cancel -a[/FONT][/INDENT]

clears the whole printer queue (you can see what is in it using the command [FONT="Courier New"]lpq[/FONT], but that was not feasible to incorporate for the effect I was looking for: getting rid of all content of the queue, whatever is in it).

The second job is to find a way how to execute [FONT="Courier New"]cancel -a[/FONT] automatically. After long searching, I found that there is 

[INDENT][FONT="Courier New"]System > Einstellungen > Sitzungen[/FONT] (German version)

[FONT="Courier New"]system > settings > session[/FONT]s       (how I would translate it to English)[/INDENT] 

This is the right place to run things when a gnome session starts. A second menu shows up, where I was able to add a new item (I gave it the obvious name cancel-a) and in the second line of it, the command is 

[INDENT][FONT="Courier New"]/usr/bin/cancel -a[/FONT][/INDENT] 

Clicking on ok, and that's it - for this user account. In order to have the printer's queue being flushed for every user logging on on this computer, I had to repeat this for all user accounts.

I gave my fellow users on this PC the hint, not to start a new user session while a print job is advertently on the print queue just waiting to be completed.

Bingo!

---

