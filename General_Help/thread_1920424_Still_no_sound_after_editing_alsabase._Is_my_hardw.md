---
title: "Still no sound after editing alsabase. Is my hardware broken?"
date: 2012-02-04
forum: General Help
---

### Post by algar32 on 2012-02-04
I added this line to my alsa-base.conf code: options snd-hda-intl index=0 model=dell .
I dont understand. Do I need drivers or a clean install? Thanks.

I have a Dell mini 9

had to click on one of the buttons under speaker in the mixer section. Thanks.

---

### Post by Rodney9 on 2012-02-04
These two manuals give good advice for solving sound problems:

[Sound Troubleshooting Guide]("https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit")
(by Lkjoel and Wildmanne39)


[Sound Troubleshooting Procedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")
(by Mark Rijckenberg)


Rodney

---

### Post by Toz on 2012-02-04
> **algar32 said:**
>  options snd-hda-intl index=0 model=dell
I dont understand. Do I need drivers or a clean install? Thanks.

Do you mean...
```
options snd-hda-int[COLOR="Red"]e[/COLOR]l index=0 model=dell
```
...(note the e in intel)?

You might also want to try:
```
options snd-hda-intel model=dell
```
...as per [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/841308]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/841308").

---

