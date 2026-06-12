---
title: "shutdown without closing all programs"
date: 2011-03-09
forum: General Help
---

### Post by ubu@ on 2011-03-09
Hi,

I tried **Kubuntu** and it have a nice function that not closing all programs when shutting down (*"not closing" *explicitly)  . So if I start the **Kubuntu** the next day, all the program will appear in the same state. in my **Ubuntu**, when pressing "shut-down", a message box pops asking : *"Are you sure you want to close all programs and shut down the computer?" *and I press *"yes"* (cause you are not leaving me any choice! [the other option is *"cancel"]* ).

can I add it some how to **Ubuntu**?

thanks,
Ubu.

---

### Post by veggen on 2011-03-09
Isn't that called *Hibernate* (or was it *Suspend*)? Anyway, it's one of those options other than *Shut down*.

---

### Post by Dutch70 on 2011-03-09
It also depends on the method you use to try and shut down Ubuntu. There are settings in your system for this, although I can't think of them off the top of my head, and I'm not currently logged into Ubuntu.

Veggen is correct, it's either hibernate or suspend. It's not "shutting down"

As a matter of fact, I think if you click the power button in the upper right hand corner of your panel (if you haven't moved it)...It will ask you if you want to shut down, log off, or
hibernate/suspend.

---

### Post by ubu@ on 2011-03-09
Hibernate gets an error: "btusb_bulk_complete... gailes to resubmit..."
Suspend is like "sleep", it's not shutting down the computer.

by the way,I tried the **K**ubuntu in the CS lab in the university (maybe it is an image with profile details???).
In **K**ubuntu i used "Log-off" without shutting down the computer, and the day after I entered again to my user in the lab (in different PC) and all the apps was in the same state (Kate, FIrefox and console...) . so I tried in my Ubuntu to use "logout" but it still asking "are u sure u want to close all program?" and using "switch from my_name_usr" it will not ask me this question, but when restating, all program are closed.

maybe I will compremise on "Suspend" (any way this semester won't let Ubuntu to rest in peace [shut-down]).

thanks,
Ubu.

---

### Post by ianp5a on 2011-05-12
There is a way in Ubuntu 10.10 to restart with all programs running as you left them.

1) Go to System-Preferences-"Startup Applications"
2) Choose the tab [Session Options]("https://help.ubuntu.com/community/AddingProgramToSessionStartup#Session Options") or Options.
3) Activate: "Automatically remember running applications when logging out"

Sadly this does not appear any more in Natty.

Does anyone know where this option is now?

Edit: [Solved for Natty here I think?]("http://askubuntu.com/questions/38517/how-to-add-programs-to-start-up")

Edit: [Sadly not]("http://www.linux-archive.org/ubuntu-desktop/478109-gnome-session-saving-dropped-natty.html").

---

