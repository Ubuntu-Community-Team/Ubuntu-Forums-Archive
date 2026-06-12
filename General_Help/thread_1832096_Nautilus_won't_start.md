---
title: "Nautilus won't start"
date: 2011-08-24
forum: General Help
---

### Post by mr_raider on 2011-08-24
I'm using Natty x64 on an Lenovo Thinkpad x120e.

as of yesterday, I am unable to launch Nautilus by any means, whether command line or from desktop icons for my computer. I've tried in Unity as well as classic desktop. Here is the message from command line


```
nabeel@x120e:~$ gksu nautilus
Initializing nautilus-gdu extension
Initializing nautilus-open-terminal extension
```


The desktop flickers, then no nautilus

I am able to run and use file manager with no problems. I already tried re-installing nautilus in synaptic.

---

### Post by searchfgold6789 on 2011-08-24
That's because nautilus takes care of the desktop as well as the file manager, kind of like Windows Explorer. 
Try:
```
gksu nautilus ~
```

---

### Post by mr_raider on 2011-08-24
Same issue:


```
nabeel@x120e:~$ gksu nautilus ~
Initializing nautilus-gdu extension
Initializing nautilus-open-terminal extension

(nautilus:1716): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

```

---

