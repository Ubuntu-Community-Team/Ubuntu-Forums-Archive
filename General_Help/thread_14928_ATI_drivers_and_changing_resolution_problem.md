---
title: "ATI drivers and changing resolution problem"
date: 2005-02-10
forum: General Help
---

### Post by pagefault on 2005-02-10
First of all let me appologize if this is a duplicate of another question but I can't seem to find my answer. I am running hoary and I have installed the latest fglrx packages from apt but I am unable to get resolution changing working while the server is running. I have tried looking over the forum for an answer and some people have got this working but I have not found a clear answer as to how that was done. I have 3d and everything else working. Any help is appreciated.

---

### Post by pagefault on 2005-02-10
Ok nevermind I finally managed to fix my problem. Apparently the XRandR extension doesn't work unless the DGA extension is disabled. How strange. Anyway if anyone else is having this problem just copy over the lines that omit it from the original configuration file fglrxconfig creates.

---

### Post by mdr on 2005-02-21
ta muchly pagefault for pointing me in the right direction.
got that sorted now.

---

### Post by clparker on 2005-02-28
OK, somebody please explain to me how I can raise my resolution higher than 640 x 480 in Hoary. The Option wont go higher in the system configuration.

---

### Post by dell500 on 2005-05-05
[QUOTE=pagefault]Ok nevermind I finally managed to fix my problem. Apparently the XRandR extension doesn't work unless the DGA extension is disabled. How strange. Anyway if anyone else is having this problem just copy over the lines that omit it from the original configuration file fglrxconfig creates.[/QUOTE]

Does this mean this part of the XF86Config-4 file:

```
# This loads the miscellaneous extensions module, and disables
# initialisation of the XFree86-DGA extension within that module.
    SubSection  "extmod"
      Option    "omit xfree86-dga"   # don't initialise the DGA extension
    EndSubSection
``` 

Configure to:

```
# This loads the miscellaneous extensions module, and disables
# initialisation of the XFree86-DGA extension within that module.
#    SubSection  "extmod"
#      Option    "omit xfree86-dga"   # don't initialise the DGA extension
#    EndSubSection
``` 

Is this correct?

I've got Ubuntu Hoary 5.04 and i'm running an ATI 9600XT.  After I installed the fglrx drivers the change in resolution stopped working.  Hopefully this works, i'm going to restart x and see what happens.

---

