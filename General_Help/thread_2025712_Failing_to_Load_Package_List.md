---
title: "Failing to Load Package List"
date: 2012-07-14
forum: General Help
---

### Post by Eric Oblepias on 2012-07-14
I'm recieving this error report every time I try to run any updates.  I'm not sure what to do in order to fix this.

[B]Could not initialize the package information
An unresolvable problem occurred while initializing the package information.[/B] [B]
Please report this bug against the 'update-manager' package and include the following error message:[/B] [B]
'E:Malformed line 1 in source list /etc/apt/sources.list.d/spotify.list (dist parse)'[/B]

---

### Post by plucky on 2012-07-14
> **Eric Oblepias said:**
> I'm recieving this error report every time I try to run any updates.  I'm not sure what to do in order to fix this.

[B]Could not initialize the package information
An unresolvable problem occurred while initializing the package information.[/B] [B]
Please report this bug against the 'update-manager' package and include the following error message:[/B] [B]
'E:Malformed line 1 in source list /etc/apt/sources.list.d/spotify.list (dist parse)'[/B]

Open Software Sources and disable spotify.list as a source.


Then post the output for ```
cat etc/apt/sources.list.d/spotify.list
```

and someone might be able to tell you how to edit the .list file

Good luck

---

### Post by Eric Oblepias on 2012-07-14
> **plucky said:**
> Open Software Sources and disable spotify.list as a source

How exactly do I go about doing this?

---

### Post by plucky on 2012-07-15
> **Eric Oblepias said:**
> How exactly do I go about doing this?

Open Software Updater and select the **Settings** button.This will open **Software Sources**.Find the line with spotify under the **Other Software** tab and un-tick the boxes.

Also please post the output for the **cat** command in the previous post.

Good Luck

---

