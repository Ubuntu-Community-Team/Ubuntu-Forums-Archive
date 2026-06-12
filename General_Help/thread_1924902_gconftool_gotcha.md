---
title: "gconftool gotcha?"
date: 2012-02-13
forum: General Help
---

### Post by Thorsen V on 2012-02-13
I have a script where I want to do this:

gconftool-2 --set /desktop/gnome/thumbnail_cache/maximum_age -1

(-1 is a meaningful value to assign)

the problem is gconftool-2  assumes it's a switch:

Error while parsing options: Unknown option -1.
Run 'gconftool-2 --help' to see a full list of available command line options.

I can't think of a way round this ...

---

### Post by bluexrider on 2012-02-13
Did you need help with this because it is now marked (SOLVED)

---

### Post by Thorsen V on 2012-02-13
> **bluexrider said:**
> Did you need help with this because it is now marked (SOLVED)
I clicked on the wrong thread tools option (meant to click on subscribe) :D
Yes, help would be nice ...

---

### Post by bluexrider on 2012-02-13
as an example 

```
gconftool-2 --type int --set /desktop/gnome/thumbnail_cache/maximum_age "60"
```you were missing the --type which is int.

However I also tried the "-1" configuration but couldn't get it past "0" so I really haven't helped except correcting some code.

I am going to subscribe as to follow the issue

Posted on Ask Ubuntu 2-13-2012 02:16

Like to know the answer too

---

### Post by bluexrider on 2012-02-14
here is the answer and I tested it:


it's a little tricky setting negative vialues with  gconftool, you need to prepend with --
```
gconftool --set --type int  /desktop/gnome/thumbnail_cache/maximum_age -- -1
```

---

### Post by Thorsen V on 2012-02-14
> **bluexrider said:**
> as an example 

```
gconftool-2 --type int --set /desktop/gnome/thumbnail_cache/maximum_age "60"
```you were missing the --type which is int.

However I also tried the "-1" configuration but couldn't get it past "0" so I really haven't helped except correcting some code.

I am going to subscribe as to follow the issue

Posted on Ask Ubuntu 2-13-2012 02:16

Like to know the answer too
Thanks. Actually I did have the --type bit in my script but it got lost in translation to a forum question.... :)

---

### Post by Thorsen V on 2012-02-14
> **bluexrider said:**
> here is the answer and I tested it:


it's a little tricky setting negative vialues with  gconftool, you need to prepend with --
```
gconftool --set --type int  /desktop/gnome/thumbnail_cache/maximum_age -- -1
```
Thanks bluexrider!
 Pity the man page doesn't seem to mention it :)

ETA: gconftool uses g_option_context_parse() to read command line args:[ http://www.gtk.org/api/2.6/glib/glib-Commandline-option-parser.html]("http://www.gtk.org/api/2.6/glib/glib-Commandline-option-parser.html")

---

### Post by bluexrider on 2012-02-14
Glad to help while I learned something too. Mark this one
(SOLVED)

---

