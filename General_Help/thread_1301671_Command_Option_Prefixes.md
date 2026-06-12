---
title: "Command Option Prefixes"
date: 2009-10-26
forum: General Help
---

### Post by timjohn7 on 2009-10-26
A newb question.  Having copied and pasted thousands of commands, and learnt hundreds in the process, I would like to know the definition of the following command option prefixes.  I've looked at man pages, lots of User Guides, Bash Beginners Guides etc but have not found a definitive list.

What exactly do these mean?  Please add any more of the same ilk and I'd appreciate any links to a manual where I can read the info for myself:

a.  -
b.  --
c.  &
d.  &&

---

### Post by TenPlus1 on 2009-10-26
This may explain it better: [http://www.livefirelabs.com/unix_tip_trick_shell_script/june_2003/06232003.htm](http://www.livefirelabs.com/unix_tip_trick_shell_script/june_2003/06232003.htm)

---

### Post by timjohn7 on 2009-10-26
Thanks... that does explain things well.

---

### Post by sisco311 on 2009-10-26
A -- signals the end of options and disables  further  option processing. Any arguments after the -- are treated as filenames and arguments.  An argument of - is equivalent to --


It's useful when a filename begins with a -
i.e. 
```
sisco@acme:~$ touch -i
sisco@acme:~$ rm -i
rm: missing operand
Try `rm --help' for more information.
sisco@acme:~$ rm "-i"
rm: missing operand
Try `rm --help' for more information.
sisco@acme:~$ rm \-i
rm: missing operand
Try `rm --help' for more information.
sisco@acme:~$ rm -- -i

```

If a command is terminated by the control operator &,  the  shell  executes  the command in the background in a subshell.  The shell does not wait for the command to finish, and the return status is  0.

---

### Post by timjohn7 on 2009-10-26
Thanks sisco311, but I'm afraid that your advice is a bit over my head.  It makes me look a bit like your avatar!
In the code snippet, the lines containing "See rm --help" are my problem.  Why is there a "--" before help and not just a "-"?

---

### Post by sisco311 on 2009-10-26
> **timjohn7 said:**
> Thanks sisco311, but I'm afraid that your advice is a bit over my head.  It makes me look a bit like your avatar!
In the code snippet, the lines containing "See rm --help" are my problem.  Why is there a "--" before help and not just a "-"?

--help is the long option form.

i.e.:
```
ls -a
```does the same thing as:
```
ls --all
```

after a single dash you can write more than one short options:
```
ls -al
```does the same thing as:
```
ls -a -l
```

EDIT:
*-help* would be interpreted as *-h -e -l -p*

---

### Post by timjohn7 on 2009-10-26
> **sisco311 said:**
> --help is the long option form.

i.e.:
```
ls -a
```does the same thing as:
```
ls --all
```

after a single dash you can write more than one short options:
```
ls -al
```does the same thing as:
```
ls -a -l
```

EDIT:
*-help* would be interpreted as *-h -e -l -p*

Thanks sisco... that does make it clear... especially the final edit.

---

