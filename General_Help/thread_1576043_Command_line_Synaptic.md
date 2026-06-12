---
title: "Command line Synaptic"
date: 2010-09-16
forum: General Help
---

### Post by lukemk1 on 2010-09-16
In Synaptic if you go Synaptic > File > Save Markings, that will save what has been installed from repositories. My question is, is there a way to save this file via the command line so that way I can integrate this into a back up script?

---

### Post by sandyd on 2010-09-16
> **lukemk1 said:**
> In Synaptic if you go Synaptic > File > Save Markings, that will save what has been installed from repositories. My question is, is there a way to save this file via the command line so that way I can integrate this into a back up script?
```

dpkg -l
```

or...
```

dpkg --get-selections > [FONT=Verdana]path/to/file[/FONT]

```
and to restore all the selections...
```

dpkg --set-selections < path/to/file
dselect

```

---

### Post by solar george on 2010-09-16
```

dpkg --get-selections > *filename*.txt

```

---

### Post by lukemk1 on 2010-09-16
Does this do the same as checking the box that says "Save full state, not only changes" in Synaptic?

---

### Post by sandyd on 2010-09-16
> **lukemk1 said:**
> Does this do the same as checking the box that says "Save full state, not only changes" in Synaptic?
yea.
The instructions after the part where I said 'or' does that.

---

### Post by lukemk1 on 2010-09-17
Alright, thanks for the help guys!

---

