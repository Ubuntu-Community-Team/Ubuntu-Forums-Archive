---
title: "mv + double quotes = messed up file name"
date: 2010-02-01
forum: General Help
---

### Post by rnelson0 on 2010-02-01
So I was SSH'd into my box at home and I was moving files around using the mv command. I rename somethings with spaces and use double quotes to do so.

e.g.
```

~$ mv fileOne.txt "File One.txt"

```

My problem is I got a little too speedy hit enter before I put the final double quote in. This prompted me with an arrow to complete the command, so I just typed in the final quote and hit enter again. The console looked like this:

```

~$ mv fileOne "File One.txt
>"
~$ 

```

Here is my problem, when I perform an ls on the directory the file name shows up like this:

```

File One.txt?

```

And now it won't let me move it or copy it. I get this:

```

mv: cannot stat `File One.txt': No such file or directory

```

Any ideas?

---

### Post by SoFl W on 2010-02-01
Did you try mv "file one.txt?" "file one.txt"

---

### Post by rnelson0 on 2010-02-01
Yes, that was the first thing I tried. It didn't work. I was able to VNC into my computer and use the GUI to rename the file which worked. In the GUI, the file name showed an invalid character block. 
When I would use tab to autocomplete the name on the command line it wouldn't put in that character.

I'm still curious if there is a way to fix that via command line.

---

### Post by jamesisin on 2010-02-01
The ? represents a problematic character (obviously).  You could use:

```
mv File\ One.txt* File\ One.txt
```

I think that will fix your issue.

---

### Post by falconindy on 2010-02-01
You can fix it the same way you made the mistake. Type the opening quote, end with the newline and a double quote and then the new filename. Or, just type the first few letters and let tab completion do the rest.

---

### Post by jamesisin on 2010-02-01
> **falconindy said:**
> just type the first few letters and let tab completion do the rest.

Please note:

> **rnelson0 said:**
> When I would use tab to autocomplete the name on the command line it wouldn't put in that character.

---

### Post by falconindy on 2010-02-01
> **jamesisin said:**
> Please note:
Mmm it would seem I skipped over that part. Also, shame on me for using ZSH (rather than Bash), which happily completes the newline char.

My second suggestion of recreating the same goof to undo it works on Dash, Bash, and ZSH. I suppose the tricky part comes in understanding what char the ? really is, if you didn't realize what you did to create it.

---

### Post by jamesisin on 2010-02-01
> **falconindy said:**
> I suppose the tricky part comes in understanding what char the ? really is, if you didn't realize what you did to create it.

You don't have to know the character.

> **jamesisin said:**
> ```
mv File\ One.txt* File\ One.txt
```

The asterisk is a wildcard for any number of any character.  I tested it.  Works perfectly.

---

