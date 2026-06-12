---
title: "Window frames"
date: 2009-08-21
forum: General Help
---

### Post by polt3r on 2009-08-21
I accidentall installed the KDE copmiz window messenger on Ubuntu 9.04, anyway as soon I noticed my mistake, I removed it, and now all the frames are goine. I can't resize windows, drag and drop them, close them from the usual top right cross etc. Also system > preferences > windows gives me the following error:

Windows manager "compiz" has not a registered configuration tool

So I want to restore everything to the way things were before I messed them up :D

---

### Post by tbluejeans on 2009-08-21
Try : 

```
metacity --replace
```I think that did the trick, when I had the same problem.

---

### Post by polt3r on 2009-08-21
Worked like a charm. Thanks dude

---

### Post by polt3r on 2009-08-22
ANy way to keep it saved after rebbot? :D

---

### Post by tbluejeans on 2009-08-22
Sorry for the late reply.  
Please try setting System->Preferences->Appearance->Visual Effects to [B]None.

[/B]I used to use gconf-editor to set it under gnome---applications---window-manager---default (from usr/bin/compiz to /usr/bin/metacity ) but it seems to be deprecated , so I don't think it will work anymore.

---

