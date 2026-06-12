---
title: "Did this command mess my system up?"
date: 2009-11-02
forum: General Help
---

### Post by viking_maniac on 2009-11-02
Ok, don't laugh now!

I used a command in the Terminal to uninstall TOR:

$ sudo apt-get remove tor*.*

But then I got something like 1 zillion lines of info rolling down, and at the bottom something failed so the uninstall process stopped. Incredibly enough, my system still works!

Do you think this has messed things up? Does this qualifies for a new install?

---

### Post by mac9416 on 2009-11-02
Do you still have the output of the command to post here? That way we could see what succeeded and what failed. After running that command on my machine up to the confirmation (I said "no"), I would say that would break your system unless something failed before it got a chance to wreak havoc.

---

### Post by coffeecat on 2009-11-02
Have a look in System > Administration > Log File Viewer. Drop down dpkg.log.1 and select today's date. You can see what has been installed or uninstalled when you ran the command.

By the way....

> **viking_maniac said:**
> tor*.*

This *.* business is only necessary in Windows. Unix OSs see the '.' as just another character, so you could have typed 'tor*' and done just as much damage. :p

For instance, say you have a bunch of files, fred1.txt, fred2.txt, fred3.txt, and so. Then 'rm fred*' would be as effective as 'rm fred*.*' and 'rm fred*txt'.

---

