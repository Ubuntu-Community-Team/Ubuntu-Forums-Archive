---
title: "time --output=log.txt --append"
date: 2006-05-22
forum: General Help
---

### Post by SadaraX on 2006-05-22
This should be pretty simple, but I just cannot figure out how to use the time command to output to a text file. The 'time' command should be able to use the --output=log.txt option but I keep gettting errors.

Here's the command I want to run

$ time --append --output=log.txt avidemux2 --run script.js --quit

Everything after the log.txt is the actual command. I get messages like "bash: --append: command not found" or "bash: --output: command not found". I have looked over the man pages and even their examples do not work right. Can anyone help?

I have tried pipe the output to another command or sending it to a text file, but the final time output will not pipe or send properly. For example:

$ time `avidemux2 --run script.js --quit &>/dev/null` > log.txt prints nothing
$ time `avidemux2 --run script.js --quit &>/dev/null` > grep "real" shows nothing

---

### Post by tonyr on 2006-05-22
**time** has many incarnations. It is a **keyword** (built-in) command in
(at least) **bash** (sh) and **tcsh** (csh). which has created confusion for many.  The
man page you are reading is for **/usr/bin/time**, so your command line should
be
```

$ /usr/bin/time --append --output=log.txt avidemux2 --run script.js --quit

```

---

### Post by zebog13 on 2008-03-11
> **tonyr said:**
> **time** has many incarnations. It is a **keyword** (built-in) command in
(at least) **bash** (sh) and **tcsh** (csh). which has created confusion for many.  The
man page you are reading is for **/usr/bin/time**, so your command line should
be
```

$ /usr/bin/time --append --output=log.txt avidemux2 --run script.js --quit

```

THank you for this, it was exactly what I needed. Although it ruined many a jokes that included; "NEVER TRUST THE MAN {page}" and "DON'T LISTEN TO THE MAN {page}"

---

