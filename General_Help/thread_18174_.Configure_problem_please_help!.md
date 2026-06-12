---
title: "./Configure problem please help!"
date: 2005-03-05
forum: General Help
---

### Post by nal on 2005-03-05
I am trying to install a mudlib but I am having a problem this is the comment I get, please tell me what i need to do to fix this.

root@visper:/home/nal/Desktop/mud/Nightmare-3.3.1 # ./Configure
bash: ./Configure: /usr/local/bin/perl: bad interpreter: No such file or directory

---

### Post by alastair on 2005-03-05
Well, it is often "./configure" not "./Configure" (note the case of the 'c') but - if you have "Configure" then it looks like it is looking for Perl in the wrong place i.e.

/usr/local/bin/perl

Perl is in :

/usr/bin/perl

You - you can probably just edit the "Configure" file (assume it is a script?) and change the location.

---

