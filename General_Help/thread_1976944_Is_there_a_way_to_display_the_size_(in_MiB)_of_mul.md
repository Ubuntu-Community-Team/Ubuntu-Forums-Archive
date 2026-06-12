---
title: "Is there a way to display the size (in MiB) of multiple folders in a directory?"
date: 2012-05-09
forum: General Help
---

### Post by redvenomweb on 2012-05-09
I'm trying to find the sizes of several folders within a directory.  There are ~100 folders, so I don't want to manually right-click->Properties on each one; I'm looking for an application that can display folder size within the directory listing.  Nautilus only displays the number of files, not the size.

I've used applications that perform this task in Windows, but that doesn't do me much good.  Any suggestions?  I'm on 10.04/11.10/12.04.

---

### Post by steeldriver on 2012-05-09
have you looked at the du command?

---

### Post by redvenomweb on 2012-05-09
I was able to use du for my needs.  Thanks for the suggestion.

---

### Post by practic on 2012-05-10
If you want a GUI approach, Disk Usage Analyzer. Run it, type Ctrl-O (to analyze the folder you want), and you get a nice visual display of the results.

---

### Post by ntu on 2012-05-11
> **practic said:**
> If you want a GUI approach, Disk Usage Analyzer. Run it, type Ctrl-O (to analyze the folder you want), and you get a nice visual display of the results.

And how do you get to the Disk Usage Analyzer please?

---

### Post by MG&amp;TL on 2012-05-11
Installed by default on *buntu, unless I'm mistaken. Find it in the Unity dash or your equivalent menu system.

---

### Post by ntu on 2012-05-11
Thanks, but in my 12.04 was not in Dash and looked in the Software centre for download and it did not appear there either.

---

### Post by MG&amp;TL on 2012-05-11
Okay, try:

```
sudo apt-get install baobab
```

Must have got removed somehow.

---

### Post by ntu on 2012-05-11
Thanks. Will try that later.

---

