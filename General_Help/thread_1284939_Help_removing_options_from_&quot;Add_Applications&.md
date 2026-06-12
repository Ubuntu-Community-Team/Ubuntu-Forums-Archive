---
title: "Help removing options from &quot;Add Applications&quot; dialogue"
date: 2009-10-07
forum: General Help
---

### Post by praveenmarkandu on 2009-10-07
i used wine to install Microsoft Office 2007. it works beautifully. however an unwanted side effect is that it puts a bunch of crap in my "Add Applications" dialog(when you right click a file and choose open with --> other application)

to show you what im talking about i've attached a screenshot

---

### Post by gwydionwaters on 2009-10-07
so remove them?

---

### Post by praveenmarkandu on 2009-10-07
the remove is GRAYED out

---

### Post by gwydionwaters on 2009-10-07
yes well it was not in the OP

---

### Post by gwydionwaters on 2009-10-07
perhaps, there may be a file in /usr/share/application-registry/<office 2007 ish name>
if there are many duplicate entries in here you could try removing them and restarting. be sure to back up the file first, in case of disaster. [code]cp <office 2007 ish name> <office 2007 ish name.bak>
you may need to be root to view and/or edit these files

* there are also some mime files in /home/USER/.local/share/applications

* i think i found it, well i found the list of available mime types, this may be where yor system has duplicate entries. /usr/shar/applications/mimeinfo.cache
hope some of this helps with your problem

---

### Post by praveenmarkandu on 2009-10-07
> **gwydionwaters said:**
> 

* i think i found it, well i found the list of available mime types, this may be where yor system has duplicate entries. /usr/shar/applications/mimeinfo.cache
hope some of this helps with your problem

thank you. that did the trick. made a backup just in case.

---

