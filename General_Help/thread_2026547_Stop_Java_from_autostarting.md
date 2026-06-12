---
title: "Stop Java from autostarting?"
date: 2012-07-15
forum: General Help
---

### Post by paul1149 on 2012-07-15
I'm running ubuntu 12.04 on some dated hardware, and I've noticed that java is using north of 250MB of memory, of 1.7GB. When I see this, I kill the process, with no adverse reactions I can see. I would like to remove java from autoruns, if not completely from the system. But it's not listed under autostarts. Any thoughts on advisability and methodology here? Thanks.

---

### Post by dino99 on 2012-07-15
use synaptic to know the java dependant apps, and remove it if you does not need it.

---

### Post by paul1149 on 2012-07-15
What a mess. To uninstall some element, others will be installed to take their place. And I lose libreoffice if I uninstall all of them.

---

### Post by ajgreeny on 2012-07-15
> **paul1149 said:**
> What a mess. To uninstall some element, others will be installed to take their place. And I lose libreoffice if I uninstall all of them.
?

I do not follow your argument; can you give more details please.

PS:  Do you know that you do not have to use any java apps in LibreOffice?  Go to Tools->Options->LibreOffice section and deselect the "Use a java runtime environment"

---

### Post by paul1149 on 2012-07-15
Thanks for that Libre office tip.

If I got to synaptics Package manager, and select all Installed "java" hits, and mark them for removal, the resulting list shows that Libreoffice, among many others, will be removed.

Then the irony is that a whole bunch of JRE stuff will be necessarily installed.

What I'd like to do is stop the big java stuff from autorunning. But I don't know how to do that in linux, since it's not on the autostart list.

---

### Post by spjackson on 2012-07-15
> **paul1149 said:**
> 
What I'd like to do is stop the big java stuff from autorunning. But I don't know how to do that in linux, since it's not on the autostart list.
```
ps -eF | fgrep java
```This should show the full command line, which may give a hint as to what it is, which may in turn give a clue about where it is being started.

---

### Post by paul1149 on 2012-07-15
Thanks. It looks like NixNote, which autostarts, is calling it. Heck of an overhead for a note-taking program. Might be better to access Evernote on the Web if it solves this problem.

---

### Post by paul1149 on 2012-07-16
Ok, I took Nixnote out of autostart, and with a fresh boot today no java is running. So I uninstalled nixnote and will use the Evernote Web interface. I would like a clean way to uninstall java itself, but at least if it's not autostarting it's not doing much harm.

Thanks.

---

