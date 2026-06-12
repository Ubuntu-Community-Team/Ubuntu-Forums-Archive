---
title: "Bash script to toggle config file"
date: 2006-04-03
forum: General Help
---

### Post by FlakJacket on 2006-04-03
I would like to make a script of some kind to change a certain value in a config file from true to false and vice versa. Could someone point me to a good resource for how to do this, or tell me the necessary commands?

Thanks,
Flak

---

### Post by ltmon on 2006-04-03
I think the quickest and easiest way would be to make two copies of the config file.  One with the value as "true", another as "false".

Your bash script would then look something like:

```

#!/bin/bash
cp real_config_file /tmp/tmpconfig
cp my_config_file real_config_file
cp /tmp/tmpconfig my_config_file

```

Hope it makes sense,

Cheers,

L.

---

### Post by FlakJacket on 2006-04-03
That works marvelously! Thank you very much.  Do you happen to know a command I could add to the end to refresh the desktop without restarting X?

Thanks,
Flak

---

### Post by ltmon on 2006-04-04
[QUOTE=FlakJacket]That works marvelously! Thank you very much.  Do you happen to know a command I could add to the end to refresh the desktop without restarting X?

Thanks,
Flak[/QUOTE]

Hi,

KDE has a system of inter-process calls called "dcop".

To invoke a dcop call from bash you type:

```

dcop <application> <object> <function> [arguments]

```

for example, with amarok running I can do:
```

dcop amarok player next

```
to skip to the next track.

Of course we now need to find which objects/functions are available in each application.

I'm not at my Kubuntu PC now, so I can't really tell you exactly.  To find out for yourself, type:

```

kdcop

```

This will bring up a "dcop browser" with all the applications running at the moment and the functions you can call on them.

If you search through the list of applications for "kwin" or "kdesktop" there might be a function inside one of them to refresh the desktop.

I'll have a look myself when I get home tonight.

Cheers,

L.

---

### Post by ltmon on 2006-04-05
Now I'm home I can give you the exact command to refresh your desktop:

```

dcop kdesktop KDesktopIface refresh

```

Add it to the bottom of your script and voila!

L.

---

