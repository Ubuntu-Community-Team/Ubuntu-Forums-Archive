---
title: "grep command"
date: 2009-11-10
forum: General Help
---

### Post by mo.reina on 2009-11-10
can anyone help me out here, this displays the location of the files that have the string "shell".  it also includes the name of the file, which i don't want, i only want the location.  i used the -l option because i didn't know any other option that would only give me the location instead of showing me the matched lines.

```
grep -rl '\<shell' /usr/share/doc
```

---

### Post by lloyd_b on 2009-11-10
> **mo.reina said:**
> can anyone help me out here, this displays the location of the files that have the string "shell".  it also includes the name of the file, which i don't want, i only want the location.  i used the -l option because i didn't know any other option that would only give me the location instead of showing me the matched lines.

```
grep -rl '\<shell' /usr/share/doc
```

Just to make sure I understand you - you want a list of directories that contain files that have words that start with "shell" in them?
(if you want *just* the word "shell", you'd need '/<shell/>')

If so ```
for FILE in `grep -rls "/<shell" /usr/share/doc`; do echo ${FILE%/*}; done
```will do the trick.  Note: those are "backtics" around the grep command, not single quotes.  The backtic is located above the <tab> key on US keyboards.  This command will NOT work if you use single quotes!

What this does is execute the 'grep' command, and loops through the results, stripping of the last slash and everything after it.

Note: the "-s" option for 'grep' suppresses any "file not found" error messages.  I got some when I tried your command on my machine...

Lloyd B.

---

### Post by mo.reina on 2009-11-10
yep that's what i'm trying to get.  is there a way to do it in a one line command rather than through a script.  i tried the above code on the command line and there was no output

---

### Post by lloyd_b on 2009-11-11
> **mo.reina said:**
> yep that's what i'm trying to get.  is there a way to do it in a one line command rather than through a script.  i tried the above code on the command line and there was no output

Not that I know of.  'grep' does NOT have any capabilities for string manipulation, which is what's required to strip off that file name.

As for the no output - there's a typo on the command I gave you.  I used a slash where it should be a backslash.  Here's the correct command:```
for FILE in `grep -rls "\<shell" /usr/share/doc`; do echo ${FILE%/*}; done
```

Lloyd B.

---

### Post by mo.reina on 2009-11-12
yeah i'm beginning to see that, i've been at this for 3 days and still nothing.  thanks for the help

---

