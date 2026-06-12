---
title: "Bash color problem with &quot;ls -d */&quot;"
date: 2010-06-03
forum: General Help
---

### Post by RyanGT on 2010-06-03
I have a bash alias for "ls -d */" to list the directories in the current folder.  I find it very helpful.  I am having a problem with its color choices however.  The colors used for "ls -d */" are different from those of ls by itself (ls is an alias for "ls --color-auto").  For some reason, "ls -d */" uses blue text on a green background for folders on fat32 partitions.  This is almost impossible to read.  ls does not do this.  How do I fix this?

Thanks,

Ryan

---

### Post by Lampi on 2010-06-03
can you work around this with a different PS1 in bashrc?

For example I use this one on black background:

```

PS1='\[\033[31m\]\u\[\033[00m\]@\[\033[32m\]\h\[\033[00m\]:\[\033[1;34m\]\w\[\033[00m\] '
```

Notice the bold blue setting on "\w" - makes it more visible than the normal blue on black background

---

### Post by KayakJim on 2010-06-03
Have you tried modifying your alias to make the command the following?

```
ls --color=auto -d */
```

The reasoning behind my suggestion is that this alias is using the "base" ls command and not your alias ls and therefore losing the color option.

---

