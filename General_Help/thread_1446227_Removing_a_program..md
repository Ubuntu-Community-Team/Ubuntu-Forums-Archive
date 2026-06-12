---
title: "Removing a program."
date: 2010-04-03
forum: General Help
---

### Post by themarker0 on 2010-04-03
I need to remove a program. I cannot find it with sudo apt-get remove WhatPulse. It is bugged and i need to remove anyways. So can anyone help me out? :D

It shows up in the applications under other, thats what bugs me :/

---

### Post by Revolutionary101 on 2010-04-03
Open Synaptic from System>Administration>Synaptic Package Manager. Search for WhatPlus in Synaptic and find the package that you were looking for and click on the filled in box. Then you can mark it for removal and hit apply on the top of the window.

After that the program will be removed.

---

### Post by themarker0 on 2010-04-03
> **Revolutionary101 said:**
> Open Synaptic from System>Administration>Synaptic Package Manager. Search for WhatPlus in Synaptic and find the package that you were looking for and click on the filled in box. Then you can mark it for removal and hit apply on the top of the window.

After that the program will be removed.

It doesn't find it. :/

---

### Post by Revolutionary101 on 2010-04-03
Narrow your search by clicking on Installed in the left side of the Synaptic Package Manager.

---

### Post by mechro on 2010-04-03
If you didn't install it with apt-get, synaptic or debian installer I don't think apt will find it.

Are there any uninstall instructions with the package you downloaded?

Perhaps you could reverse your install procedure to uninstall it.

---

### Post by themarker0 on 2010-04-03
> **Revolutionary101 said:**
> Narrow your search by clicking on Installed in the left side of the Synaptic Package Manager.

Still nada

> **mechro said:**
> If you didn't install it with apt-get, synaptic or debian installer I don't think apt will find it.

Are there any uninstall instructions with the package you downloaded?

Perhaps you could reverse your install procedure to uninstall it.

It was installed with a .deb. Then i sorta screwed it up and installed it again, and that broke it.

---

### Post by mechro on 2010-04-03
Hmm... OK. Try sudo apt-get remove whatpulse (no capital letters).

---

### Post by themarker0 on 2010-04-03
> **mechro said:**
> Hmm... OK. Try sudo apt-get remove whatpulse (no capital letters).

E: Couldn't find package whatpulse

---

### Post by mechro on 2010-04-03
In Synaptic, is it listed as a broken package?

---

### Post by linden940 on 2010-04-03
how is it buggy? it may have somthing 2 do with how u installed it

---

### Post by oldos2er on 2010-04-03
```
sudo dpkg -r whatpulse
```

---

### Post by themarker0 on 2010-04-03
> **mechro said:**
> In Synaptic, is it listed as a broken package?

Its not listed at all.


> **linden940 said:**
> how is it buggy? it may have somthing 2 do with how u installed it

Its because i installed it the right way once, but it didn't work, then merged a good install of it with it.

> **oldos2er said:**
> ```
sudo dpkg -r whatpulse
```

Will try. Didn't work, says whatpulse isn't installed. But it is O.o

---

### Post by oldos2er on 2010-04-03
> **themarker0 said:**
> Its not listed at all.




Its because i installed it the right way once, but it didn't work, then merged a good install of it with it.



Will try. Didn't work, says whatpulse isn't installed. But it is O.o

Whatever the name of the deb file you installed was, try it with **sudo dpkg -r <package name>**

---

### Post by themarker0 on 2010-04-04
> **oldos2er said:**
> Whatever the name of the deb file you installed was, try it with **sudo dpkg -r <package name>**

Nothing doing, it is still there. :/

---

### Post by mechro on 2010-04-05
> **themarker0 said:**
> 

It shows up in the applications under other, thats what bugs me :/

Perhaps you are only left with the menu entry? Edit the menu?

---

### Post by themarker0 on 2010-04-05
> **mechro said:**
> Perhaps you are only left with the menu entry? Edit the menu?

I didn't know you could do that.

Thank you very much :)

---

### Post by themarker0 on 2010-04-06
Edit: Its still here :S

---

