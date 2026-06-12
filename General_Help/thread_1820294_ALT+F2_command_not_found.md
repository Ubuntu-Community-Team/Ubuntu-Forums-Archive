---
title: "ALT+F2 command not found"
date: 2011-08-07
forum: General Help
---

### Post by MetalMASK on 2011-08-07
Hi All,

I am running gNatty ubuntu 11.04. before yesterday, the Alt+F2 then type in gnome-tweak-tool would successfully open the Advanced Settings in application. But now it shows "command not found", same thing for gnome-terminal...

Is there anyway to fix this? What package is the ALT+F2 related to?

Thanks in advance

---

### Post by SalHelder on 2011-08-07
Have you done any updates?

---

### Post by MetalMASK on 2011-08-07
Yes I have. For installing fixes that are specific to the machine (lenovo T420, thinkfan fix), I have to.

The compiz setting is setup correctly as I just checked. still "command not found" for everything i type in there.

---

### Post by SalHelder on 2011-08-07
Are you sure the package is still installed? Just saying, since even in the terminal it won't run.

---

### Post by MetalMASK on 2011-08-07
I assume you meant the compiz package? Yes it is still installed. I did uninstall it for some reason and have reinstalled it (that might be the reason?) The compiz setting looks fine to me.

Sorry I meant gnome-terminal cannot be called from ALT+F2. If I type gnome-tweak-tool in the terminal, it will open fine.

All application (terminal, advanced setting) can be called from the application tab, but not from ALT+F2....

---

### Post by MetalMASK on 2011-08-07
Found the bug being reported by others as well:
(in German) [http://forum.ubuntuusers.de/topic/alt-f2-zeigt-command-not-found/#post-3191077](http://forum.ubuntuusers.de/topic/alt-f2-zeigt-command-not-found/#post-3191077)

and a bug report: [https://bugzilla.redhat.com/show_bug.cgi?id=719675](https://bugzilla.redhat.com/show_bug.cgi?id=719675)

---

### Post by SalHelder on 2011-08-07
I was talking about the gnome-tweak-tool package. And if I get you right, Alt+F2 is not working at all right? Not only for that one, all others don't work right?

---

### Post by MetalMASK on 2011-08-07
correct. The situation is (same as reported in the post in ubuntu.de) 
once I press ALT+F2, the interface for typing command shows up, but besides "r", calling any other command would give "command not found"

---

### Post by SalHelder on 2011-08-07
Are you using version 3.1.3? Apparently they fixed it with 3.1.4:

"I retested on Fedora 16 and Alt+F2 works there so I think this was fixed by
Gnome Shell 3.1.4. I'm going to go ahead and mark this fixed then."

Found here: [https://bugzilla.gnome.org/show_bug.cgi?id=656054](https://bugzilla.gnome.org/show_bug.cgi?id=656054)

Anyway as a workaround if you need I guess you could use kupfer or gnome-do.

---

