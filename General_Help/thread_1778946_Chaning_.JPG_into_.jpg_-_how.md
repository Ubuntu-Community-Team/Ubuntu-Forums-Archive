---
title: "Chaning .JPG into .jpg - how?"
date: 2011-06-09
forum: General Help
---

### Post by zozza on 2011-06-09
There's got to be an easy way to do this and I can't find it:

I have 50 files with the extension .JPG.  I want to change the extensions into lower case with one command.

How?  Thanks.

---

### Post by sisco311 on 2011-06-09
In Ubuntu, you can use the Perl based rename command:
```
cd path/to/dir
rename --no-act 's/.JPG$/.jpg/' *.JPG

```

See: ```
man rename
```

---

### Post by AlphaLexman on 2011-06-09
> **sisco311 said:**
> ```
rename --no-act 's/.JPG$/.jpg/' *.JPG
```
@ sisco311: Could you explain the dollar sign '$' in there?

It doesn't look like variable expansion. Or at least point me to an explanation.

Thanks.

---

### Post by sisco311 on 2011-06-09
> **AlphaLexman said:**
> @ sisco311: Could you explain the dollar sign '$' in there?

It doesn't look like variable expansion. Or at least point me to an explanation.

Thanks.

It's part of a [regular expression]("http://en.wikipedia.org/wiki/Regular_expression").

As you can see *s/foo/bar/* is quoted with single quotes, because it shouldn't be interpreted by the shell (bash). It must be passed to the command (rename) as it is.

Where *foo* is a perlexpr (Perl regular expression).

See:
```
perldoc perlre
```

In most regular expressions $ matches the ending position of the string.

---

### Post by jim_deadlock on 2011-06-09
There are several mass renaming packages in the software center, just search for 'rename', I'm sure most of them will do the job.

---

### Post by sisco311 on 2011-06-09
> **jim_deadlock said:**
> There are several mass renaming packages in the software center, just search for 'rename', I'm sure most of them will do the job.

Yep.

Incomplete list of GUI tools:

[list]
[*]thunar (file manager)
[*]**gprename** 
[*]gnome-commander (file manager)
[*]purrr 
[*]pyrenamer 
[*]gwenrename 
[*]**krename** 
[/list]

---

### Post by jim_deadlock on 2011-06-09
I've just been trying metamorphose it's very nice:

[http://file-folder-ren.sourceforge.net/]("http://file-folder-ren.sourceforge.net/")

---

### Post by sisco311 on 2011-06-09
> **jim_deadlock said:**
> I've just been trying metamorphose it's very nice:

[http://file-folder-ren.sourceforge.net/]("http://file-folder-ren.sourceforge.net/")

It looks cool. I will try it and eventually add it to my list.

Thanks, jim_deadlock.

---

