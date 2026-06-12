---
title: "Mass search and replace file renaming"
date: 2011-01-24
forum: General Help
---

### Post by xtheunknown0 on 2011-01-24
I've used fetchmail to download every message on my gMail account to ~/mail. When I run rsync on ~, I run into errors because a lot of the mail downloaded is has a '.' in its name.

~/mail contains [Gmail].All Mail, [Gmail].Bin, [Gmail].Drafts,[Gmail].Sent Mail, [Gmail].Spam, [Gmail].Starred and INBOX. In each of these directories are 3 folders: cur, new and tmp which each store text file version of every email.

I want to replace the '.' in file names with a '!' - how do I do this?

In vim, I understand ```
:% s/:/\?/g
``` and I can do for loops in bash.

TIA,
xtheunknown0

---

### Post by ajgreeny on 2011-01-24
```
find ~/mail -name '*' -exec rename -n 's/\./!/g' "{}" +
```should do it for all files in the ~/mail folder irrespective of any file suffix they may or may not have, but back up everything first, just in case I've got it wrong.

The one thing I'm not sure about is the need for the backslash after the s/ as the command I have used this for is to replace a space with an underscore.  I think, therefore that the \ is merely an escape for the space, and may not be needed if you are replacing a .

---

### Post by Vaphell on 2011-01-24
usually in regular expressions '.' is a symbol for 'any character', therefore you need to escape it to treat it literally as a plain dot.

---

### Post by ajgreeny on 2011-01-24
Thanks Vaphell, I wasn't sure.

How about the rest of the command?

---

### Post by Vaphell on 2011-01-24
i have no experience with rename, but that expression is identical to these used in sed and it looks legit (replaces dots with !).
**-name *** doesn't make too much sense (it doesn't narrow down anything), find matches everything without it either way, also i'd narrow down to files only (-type f)

---

### Post by sisco311 on 2011-01-24
If you want to rename directories too, then you need **-depth** (process each directory's  contents  before  the  directory  itself).

---

### Post by xtheunknown0 on 2011-01-24
> **ajgreeny said:**
> ```
find ~/mail -name '*' -exec rename -n 's/\./!/g' "{}" +
```<snip>

I had a read of the man page for find (and found parts of the discussion too technical). What are the last two bits

```
"{}" +
``` for?

I'm surprised that I was inconsistent in the OP. The vim regex searched for colons but I requested to replace '.'s. Thanks for a working command (and -name '*' is *not* needed).

TIA,
xtheunknown0

---

### Post by hawkmage on 2011-01-24
The "{}" in the -exec portion of a find command substitutes the path of the file that found.

If you are looking at only renaming the files with a '.' in name I would change the ```
-name '*'
``` to be ```
-name '*.*'
```

---

### Post by sisco311 on 2011-01-24
**-exec command {} ;** runs the command separately on each file found:
comannd file1
comamnd file2
command file3
...

**-exec command {} +** collects the filenames into groups or sets, and runs the command once per set:

command file1 file2 file3 file4 ... file999
command file1000 file1001 ...

---

