---
title: "command used by admin to find hidden files????"
date: 2010-08-15
forum: General Help
---

### Post by rahulburra on 2010-08-15
hi everyone,

What linux command would an administrator use to find all hidden files on a Unix/Linux server that were generated during the last week?

can anyone please answer the question

Thankyou
Rahul

---

### Post by kiridude on 2010-08-15
ctrl h

---

### Post by JustinR on 2010-08-15
Hi,

If your using a GUI, such as nautilus, go to 'View' and check 'Show Hidden Files'.

If your using CLI, type the command 'dir -a' into the correct folder directory to see all hidden files.

---

### Post by J V on 2010-08-15
Lol... I'd go for some combination of find and grep... Any files beginning with . or ending with ~ are hidden, so you can just search the home folders (Or the whole system) for files created in the last... and then filter out ones without ^. or ~$

---

### Post by rahulburra on 2010-08-15
thnx for reply guys but im looking for the **hidden files in the unix/linux server that are generated in the last week using command prompt not a GUI**

---

### Post by drs305 on 2010-08-15
I'm no command line expert, but start with something like this:
```

sudo find / -type f -mtime -7 -iname ".*"

```

Take a look at "man find" to see what the options are and how to further tweak the results.

---

### Post by Nervouswreck on 2010-08-15
Or, if you want more information on the files, try ls -al .* in the appropriate directories.

(all files beginning with a dot are hidden; the asterisk is a wildcard.)

---

### Post by surfer on 2010-08-15
```
find . -atime 1 -name ".*"

```

or something alike. [FONT="Courier New"]man find[/FONT] will give you all the necessary info.

---

