---
title: "Permanent resolution settings"
date: 2010-05-13
forum: General Help
---

### Post by Rhaspun on 2010-05-13
Every time I start my computer Ubuntu will start with a resolution
of 1280x960. I go into the Administration setting and click the Nvidia X server settings and change it to 1280x1024. Next time I start it starts in 1280x960. Is there a way to make the changes I click on my permanent setting? Thanks for any help. BTW I am using 
10.04.

---

### Post by fooman on 2010-05-13
you must configure the settings as "root" (sudo) and save to x configuration file to make them "stick".

open a terminal (applications > accessories > terminal) and type or copy/paste the following:

     
```
gksudo nvidia-settings 
```when it opens, set the resolution,  press "apply",  then press "save to x configuration file"

that should work.

---

