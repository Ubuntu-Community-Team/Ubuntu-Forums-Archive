---
title: "Installing KGpg and gpgdir (to encrypt directories)"
date: 2012-08-24
forum: General Help
---

### Post by dragonfly41 on 2012-08-24
I'm still using Ubuntu 10.10

installed KGpg
got it to work and manage key in the GUI

then installed gpgdir (to encrypt directories)

[http://www.ghacks.net/2009/06/03/recursively-encrypt-directories-with-gpgdir/](http://www.ghacks.net/2009/06/03/recursively-encrypt-directories-with-gpgdir/)

this installation does not fully work yet

this error is shown ..

[COLOR=Blue]/usr/bin/perl: symbol lookup error: /usr/lib/gpgdir/i386-linux-thread-multi/auto/Class/MethodMaker/MethodMaker.so: undefined symbol: Perl_Tstack_sp_ptr[/COLOR]

test file shows the above error.

but when I go back to launch KGpg it will not launch the agent.

So neither KGpg or gpgdir is working.   KGpg seemed to stop launching after I installed gpgdir (but that might be coincidence).

Any advice?


[COLOR=DarkRed]**[1st Edit]**

I can now launch kgpg from command line

kgpg -d

Options:
  -e                        Encrypt file
  -k                        Open key manager
  -d                        Open editor
  -s                        Show encrypted file
  -S                        Sign file
  -V                        Verify signature


But will not launch from Applications menu.

And gpgdir still refuses to work.

[B]
[2nd Edit][/B]

The KGpg problem is solved.

I went into Applications (right click) > Edit Menus

and changed the properties of KGpg link

from kgpg %U
to kgpg -d
which launches editor

So it is gpgdir perl error above which remains to be solved.


[/COLOR]

---

### Post by dragonfly41 on 2012-08-25
gpgdir problem solved.

The developer of gpgdir (Michael Rash) suggested 

[LIST]
[*]installing libclass-methodmaker-perl package (Synaptic Package Manager)
[*]delete old installation files in /usr/lib/gpgdir
[*]reinstall from gdrdir source with "./install.pl --Exclude Maker"
[/LIST]
and this worked .. all tests in  test suite passed.

---

