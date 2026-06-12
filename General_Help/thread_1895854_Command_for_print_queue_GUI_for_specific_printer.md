---
title: "Command for print queue GUI for *specific printer*??"
date: 2011-12-15
forum: General Help
---

### Post by ethanay on 2011-12-15
I've searched and searched online and in forums for an answer to this, and haven't found one:

I've set up an Ubuntu computer in the lab I manage as a print server to accept/deny print jobs from all the other computers (mostly P4 Windows XP/Linux, with four shiny newish iMacs thrown in for good measure).

I want the print queue manager to startup automatically on login.  In order to do this, I need to know the command for it.  No, it's not ```
system-config-printer-applet --no-tray-icon
``` That only shows the print queue for jobs from the current, local user.  I need to see the queue for all jobs on a specific printer from ANY user.  To do this via GUI, I invoke:

```
system-config-printer
```
then I right click on the printer, and select "View Print Queue Ctrl+F"

This is the ONLY window that will automatically update and display print jobs sent from client computers.  My question is:  what is the command to invoke this window directly, so I can add it to the startup programs?  I can't find anything in --help or man pages...

---

### Post by lechien73 on 2011-12-15
I've taken a look around, and it doesn't seem like there is a way of launching the single queue window that you want.

The system-config-printer command is a python script, and a brief look shows the function that's called to display the queue window (self.on_view_print_queue_activate) - along with the printer index number.

I suppose it wouldn't be too complex to copy the script to a new name, and modify it so that it could accept a printer index number as a command-line argument and display its queue.

---

### Post by ethanay on 2011-12-15
Hi Matt, thank you for snooping around!  I don't have the capacity even to do scripting.  However, even if I can't find a solution, it's nice to know I'm not crazy and continuing to overlook something obvious!

I could file a bug report against it as a feature request.  It seems like that's an important (but missing) management feature for an ad-hoc print server handling jobs from many clients...thoughts?

---

### Post by lechien73 on 2011-12-15
You could request it as a feature enhancement. It does seem like one of those options I never realised I needed, but now seems vitally important :)

I started to take a look at adding that functionality myself, but the fact that it's now midnight here in Dublin and my beer is starting to take effect probably hampered my efforts somewhat!

If I manage to get something knocked together over the next couple of days, I'll drop you a note.

Thanks for the support on the membership thread, btw :D

---

### Post by ethanay on 2011-12-16
FYI, the feature request:
[https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/905528](https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/905528)

please add or modify anything you believe is pertinent.  I added the following optional resolution:

> Another option to add this functionality is to add an option in the system-config-printer-applet --no-tray-icon GUI to display jobs from any users (including those submitted to the server from client computers), which is what I believe the web-based interface does by default.

Here's to beer-induced ingenuity!

---

### Post by ethanay on 2012-09-24
Marking this thread as solved since the requested feature has been implemented!

---

