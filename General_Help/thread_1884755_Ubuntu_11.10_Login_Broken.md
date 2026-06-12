---
title: "Ubuntu 11.10 Login Broken?"
date: 2011-11-21
forum: General Help
---

### Post by Masmidow on 2011-11-21
Hey,

    After having Ubuntu 11.10 for some time, I suddenly can't get into my computer. It keeps telling me that it 

[FONT="Courier New"]"Could not connect to session bus: //bin/dbus-launch terminated abnormally without any error message"[/FONT]

This happened after I restarted it. I have turned it off and back on multiple times since then, and still have the same error. I need to get back in to my account very badly. Can anyone help me?

Michael

---

### Post by efflandt on 2011-11-22
I have not seen that error, but did have a problem where I would totally lose video signal somewhere between grub menu and login screen and I was at least able to get into text console to uninstall/reinstall different video drivers by doing the following:

In grub menu select your Linux if not the default, then press **e** to edit and at end of linux line after ro change **quiet splash vt.handoff=7** to **nosplash --verbose text** (doing this is just temporary, not permanent), then Ctrl+x to boot.

If that gets you to a text console, login and see if you can get X to run with **startx** command.  If not, you may at least be able to **sudo mount** something (different partition or USB flash) and copy (cp) files if you know your way around a text terminal.

---

### Post by mandim on 2011-11-25
Hello to all. I'm new to forum and Ubuntu and I would like to report that the same problem is appearing to me. The problem started when I have some open programs and then tried to log-out. After that I couldn't manage to log-in again. Instead I get the same error:

> "Could not connect to  session bus: //bin/dbus-launch terminated abnormally without any error message"

I have the 11.10 version. I will try to do the above solution and report back for the results.

---

### Post by mxndrwgrdnr on 2011-12-11
Same thing is happening to me. Came out of nowhere. I believe it happened after I left my laptop out and on and the battery died. After plugging it in and logging on I get "Could not connect to  session bus: //bin/dbus-launch terminated abnormally without any error". can't make any sense of it and i can't log onto my own desktop! can't access my files!
need help!
thanks

---

