---
title: "Nano charset problem"
date: 2006-05-01
forum: General Help
---

### Post by jarmake on 2006-05-01
I have problem with nano (in terminal) not using correct charset . Instead of äö I get garbage letters  Ã¤ and Ã¶.
Everything else seems to work pretty much. I have my locale set like
LANG=fi_FI.UTF-8
LC_CTYPE="fi_FI.UTF-8"
LC_NUMERIC="fi_FI.UTF-8"
LC_TIME="fi_FI.UTF-8"
LC_COLLATE="fi_FI.UTF-8"
LC_MONETARY="fi_FI.UTF-8"
LC_MESSAGES="fi_FI.UTF-8"
LC_PAPER="fi_FI.UTF-8"
LC_NAME="fi_FI.UTF-8"
LC_ADDRESS="fi_FI.UTF-8"
LC_TELEPHONE="fi_FI.UTF-8"
LC_MEASUREMENT="fi_FI.UTF-8"
LC_IDENTIFICATION="fi_FI.UTF-8"
LC_ALL=

I've tried setting it to en_US.UTF-8 as well but it has no effect. I cannot find any configuartion options for Nano to set this. I am using Ubuntu Breezy.
Any ideas?

---

### Post by duality on 2006-05-01
use another editor..... kwrite/kate/gedit

---

### Post by duality on 2006-05-01
try another editor..... kwrite/kate/gedit

---

### Post by jarmake on 2006-05-01
When I am locally on my ubuntu I use gedit without problems. But now I am connecting via ssh shell remotely, so I cannot use any graphical editors. 

I've tried to install pico to see if that would make any difference. However I am unable to do this as Ubuntu won't allow me to install pico.

Typing: apt-get install pico results in:
Package pico is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  nano
E: Package pico has no installation candidate

And indeed entering command pico launches nano. And trying to uninstall nano is no-go becuse it will uninstall ubuntu-standard as well which leads to problems...

---

### Post by jarmake on 2006-05-02
The problem was Putty that had ISO -charset set as default and as my Ubuntu had UTF-8 in use, these two didn't communicate correctly.
Yes, the problem was between the chair and the desk....

---

