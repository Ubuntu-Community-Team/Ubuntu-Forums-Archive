---
title: "Pipe to clipboard"
date: 2011-10-05
forum: General Help
---

### Post by ofnuts on 2011-10-05
Is there a way to pipe the output of CLI commands to the clipboard (instead of creating a temp file, or mousing a potentially large ouput), something like
```

ls -al >/dev/clipboard
or
ls -al | clipboard

```

---

### Post by Pynalysis on 2011-10-05
> **ofnuts said:**
> Is there a way to pipe the output of CLI commands to the clipboard (instead of creating a temp file, or mousing a potentially large ouput), something like
```

ls -al >/dev/clipboard
or
ls -al | clipboard

```

Check this out: [http://stackoverflow.com/questions/749544/pipe-to-from-clipboard](http://stackoverflow.com/questions/749544/pipe-to-from-clipboard)

---

### Post by WorMzy on 2011-10-05
I use xsel:

```
command | xsel -ib
```

Transfers the output of "command" _i_nto the clip_b_oard.

To copy into the primary buffer, use:

```
command | xsel -ip
```

To paste the contents of the clipboard or primary buffer, use

```
xsel -ob
#OR#
xsel -op
```

---

### Post by SecretCode on 2011-10-05
For me, xclip is the solution.

Read the man page for the difference between "primary", "secondary" and "clipboard" selections.

---

### Post by ofnuts on 2011-10-05
Wunnerful, thanks all.

---

