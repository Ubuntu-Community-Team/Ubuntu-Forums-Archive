---
title: "Unity Toolbar icons missing"
date: 2012-05-17
forum: General Help
---

### Post by Cardale on 2012-05-17
I had this problem before I upgraded from 11.10 and it looks like it is still present in 12.04.

Sometimes when I login the icons are visible, and I do nothing different when it happens verses when it doesn't.

---

### Post by Frogs Hair on 2012-05-17
I'm thinking there is a conflict with the dock . Remove the dock from startup applications and see if Unity starts normally. I saw similar post and the person just changed dock applications to solve the problem , but the cause was unknown.

---

### Post by Cardale on 2012-05-17
Thanks for the tip, but it didn't help. 

Unity 2D works just fine...

The dock did work perfectly.. I'm not sure what update or setting changed screwed it up.  Any way to reinstall Unity maybe?

---

### Post by Frogs Hair on 2012-05-17
You can reinstall unity from the synaptic package manager if installed . Try the following command first .```
unity --reset-icons
```  You will have to add your favorites again after using this command.

---

### Post by Cardale on 2012-05-17
Not sure if this is related, but maybe.... I am getting this error in my kernel log.

17/05/12 04:50:49 PM    NVRM    API mismatch: the client has the version 290.10, but
17/05/12 04:50:49 PM    NVRM    this kernel module has the version 295.40. Please
17/05/12 04:50:49 PM    NVRM    make sure that this kernel module and all NVIDIA driver
17/05/12 04:50:49 PM    NVRM    components have the same version.

Any idea how I can repair the mismatch?


Reinstalling didn't work and neither did your command.

---

### Post by Frogs Hair on 2012-05-17
It may not be related .Check synaptic to see if both Nvidia drivers are installed if you upgraded the old driver should be removed but something may have gone wrong.  I use Nvidia current because I am a bit afraid of the post release update drivers and my graphics card is not powerful enough to notice a difference anyway .

You may want to look at Xsession errors in home / hidden folders also .

---

### Post by Cardale on 2012-05-17
It does appear there is some mismatches I believe.

Which ones should I go with?

---

### Post by Frogs Hair on 2012-05-17
The Nividia settings should have a different number. You have the same packages as I do .

---

### Post by Cardale on 2012-05-17
Reinstalled and still didn't help.  I still have no toolbar icons.

Any other ideas?

---

### Post by Cardale on 2012-05-18
Solved the problem it was actually the API mismatch that was the cause.  For some reason once I fixed the API mismatch the icons returned.

So if your having this issue then you might need to look in your kernel logs.

---

### Post by Frogs Hair on 2012-05-18
> **Cardale said:**
> Solved the problem it was actually the API mismatch that was the cause.  For some reason once I fixed the API mismatch the icons returned.

So if your having this issue then you might need to look in your kernel logs.

Glad your up and running !  ):P

---

### Post by Cardale on 2012-05-19
Yeah thanks man. :lolflag:

---

