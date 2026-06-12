---
title: "Terminal Tab-completion, but on steroids?"
date: 2011-02-21
forum: General Help
---

### Post by Ranko Kohime on 2011-02-21
Is there an easy way to put all of the current directory's files on the command line, without tab-completing each individual one?

---

### Post by fabricator4 on 2011-02-21
> **Ranko Kohime said:**
> Is there an easy way to put all of the current directory's files on the command line, without tab-completing each individual one?

[Yes]("http://www.cyberciti.biz/faq/bash-loop-over-file/")

This was just one example from the results of a google search on "bash read filenames list"

Many variants work by sending the output of ls to a file, then using the contents of this file as an array.

I haven't written anything like this myself yet, but it's on the todo list.

Chris

---

### Post by whatthefunk on 2011-02-21
Have you checked out the program "tree?"

EDIT:  crap, I didnt read the OP very well.  Tree will show you the files but not put them in the command line for you.

---

### Post by DaithiF on 2011-02-21
if you want to expand the list of files before executing the command, then see
[http://superuser.com/questions/215950/how-to-expand-on-bash-command-line](http://superuser.com/questions/215950/how-to-expand-on-bash-command-line)

---

### Post by Habitual on 2011-02-21
in terminal:

```
echo *
```

but it lists directories too.

---

### Post by hugmenot on 2011-02-21
No, no, no.

Here&#8217;s how to do it with bash:

```
ls *<ctrl-x>*
```

You will get all glob matches of asterisk on one line.

Similarly, if you want to insert the possible completions (the above is for files only) just use <alt-*>

```
sudo aptitude purge linux-headers<alt-*>
```

---

### Post by Ranko Kohime on 2011-02-21
Oh well duh.

* Slaps forehead

I don't know why I didn't think of using an asterisk.  I tried Google, but with search terms along the lines of tab-completion, which didn't give the desired results.

---

### Post by Habitual on 2011-02-21
yeah, sometimes Google makes it difficult to find even basic elements of a search.

'echo *' sorta works for your requirement but the output requires further processing?

Maybe someone else will have a more elegant solution...

Good Luck.

---

### Post by deconstrained on 2011-02-21
> **hugmenot said:**
> 
Here’s how to do it with bash:

```
ls *<ctrl-x>*
```
Holy moley that's awesome. I never knew ^X was a metachar in bash that expanded globs. I just learned something new!

---

### Post by Habitual on 2011-02-21
doesn't work for me here, but that's not surprising.
I'm not even using Ubuntu.

It does work here. Ima dork. :)

---

