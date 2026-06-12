---
title: "Evince Failure: dconf?"
date: 2011-08-17
forum: General Help
---

### Post by ackey on 2011-08-17
Hi Everyone,

I *was* running 10.04 on a laptop and had problems with evince.   Usually it would not open a document, either from nautilus or terminal.  It would just say "loading" indefinitely.  I could use xpdf or gv or acroread on these files, so it was an evince problem.

I did a "fresh install" to 11.04, but kept my home partition the same.  Evince still will not work, but now it won't even open and gives me this error message:
```

ackey@whobuntu:~$ evince
**
ERROR:dconfcontext.c:29:dconf_context_get: assertion failed: (thread != NULL)
Aborted

```

I have spent some time debugging this, but have seen nothing change:
[LIST=1]
[*]A new account on the same computer: Evince works
[*]installing dconf or dconf-tools: no change
[*]Removing the folder .gnome2/evince : no change
[/LIST]

I'm pretty sure this has to be a configuration file somewhere, given that the problem persisted through a "fresh" install and the new user sees a working evince.

What can I try next?  I prefer evince to other options, but really don't want to start with a fresh user account and lose all of my settings.

---

### Post by ackey on 2011-08-17
Double clicking on a document WILL open it (this is an improvement over how it was behaving on the previous Ubuntu install) but I get the same error from a terminal - with it not opening.

So what would cause evince to not open from the terminal (with or without a file passed to it) when it WILL open from double clicking on a file or typing "evince" in the alt-f2 dialog?

---

