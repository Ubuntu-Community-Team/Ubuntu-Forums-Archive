---
title: "Weird permission issue"
date: 2010-04-27
forum: General Help
---

### Post by cpa on 2010-04-27
Hi there,

I'm experiencing some weird issues in my home directory.
I can't ls it (permission denied), and nautilus only shows empty folders.

But if I do "chmod 777 -R *", everything is back.
I don't want my stuff to be executable so I tried "chmod oag-x -R *" and then back to my issue : permission denied.

I've already done some stuff like "chown me -R * ; chgrp me -R *"

Any ideas ?
-- Cp

---

### Post by sisco311 on 2010-04-27
You need execute permission on the directories in order to be able to list their contents. Try something like:
```
find ~ -type d -exec chmod 0755 '{}' \+
find ~ -type f -exec chmod 0644 '{}' \+
```

To set a *private home*:
```
chmod 0700 ~
```

---

### Post by cpa on 2010-04-27
It works, now, thanks.

But I don't get the commands.
In find ~ -type d -exec chmod 0755 '{}' \+, what does '{}' \+ mean ?

---

### Post by sisco311 on 2010-04-27
**'{}'** is replaced by the current file name being processed;

**-exec command '{}' \;**  runs the command on each file;

For example, if the *find ~ -type f* returns file1, file2 and file3:

[I]command file1
command file2
command file3[/I]

**-exec command '{}' \+** runs the specified command on the selected files, but the command line is built  by  appending each  selected file name at the end:

*command file1 file2 file3*

[uhelp]community/find[/uhelp]
```
man find | less +/"-exec command"
```

---

