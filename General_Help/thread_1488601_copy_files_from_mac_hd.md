---
title: "copy files from mac hd"
date: 2010-05-20
forum: General Help
---

### Post by fjsimpkins on 2010-05-20
this is my situation. i have a macbook that wont boot. i want to copy the picture and music from the hd. i took the hd out and put it into my dell inspiron. i booted up with a live cd and im able to view the files. i can play the music. i just cant copy anything to my external hd. its telling me i dont have premissions. i tried to change that in the properties but it wont let me. does anyone have any suggestions? im still looking around but im not finding much. thanks 

jim

---

### Post by dino99 on 2010-05-20
with synaptic, install mountmanager and tweak the devices and partitions settings as you need (system admin mountmanager)

---

### Post by bobcollard on 2010-05-20
> **fjsimpkins said:**
> this is my situation. i have a macbook that wont boot. i want to copy the picture and music from the hd. i took the hd out and put it into my dell inspiron. i booted up with a live cd and im able to view the files. i can play the music. i just cant copy anything to my external hd. its telling me i dont have premissions. i tried to change that in the properties but it wont let me. does anyone have any suggestions? im still looking around but im not finding much. thanks 

jim
Try this in Terminal:  gksu "file manager"   Where "file manager" is whatever you are using to access the files.  It will give you root access.  Don't use the quotes.

---

### Post by fjsimpkins on 2010-05-20
> **dino99 said:**
> with synaptic, install mountmanager and tweak the devices and partitions settings as you need (system admin mountmanager)

i tried this but im not really sure what to tweak and how to tweak it. ive tried formatting the external but im still not allowed to copy any files.

---

### Post by fjsimpkins on 2010-05-20
> **bobcollard said:**
> Try this in Terminal:  gksu "file manager"   Where "file manager" is whatever you are using to access the files.  It will give you root access.  Don't use the quotes.

thanks but its not giving me the permissions to access the mac hardrive? im still checking google and forums trying to find an answer.

---

