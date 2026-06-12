---
title: "Gcompris - fails to start"
date: 2009-09-22
forum: General Help
---

### Post by Andyc709292 on 2009-09-22
Hi,
Recent re-installation of 9.04 and previously working (before format and re-install) Gcompris now fails to start.
I get the timer, and system monitor shows it starting but timer stops, and application in system monitor disappears!

I've uninstalled using add/remove and then uninstalled and installed edubuntu suite, but no luck.

Any help appreciated as a 3 year old is pretty p*ssed at the moment... :)

Cheers
Andrew

---

### Post by P4man on 2009-09-22
try starting it from a terminal, you may get an error message that sheds some light on the issue.

---

### Post by Andyc709292 on 2009-09-23
Thanks for the tip.
I get this:

exec_prefix NULL
XF86VidMode: Compiled with XF86VidMode.
If you have problems starting GCompris in fullscreen, try the -x option to disable XF86VidMode.

** (process:4393): WARNING **: Binary relocation disabled
package_data_dir         = /usr/share/gcompris/boards
package_locale_dir       = /usr/share/locale
package_plugin_dir       = /usr/lib/gcompris
package_python_plugin_dir= /usr/share/gcompris/python
Infos:
   Config dir '/home/home/.config/gcompris'
   Users dir '/home/home/My GCompris'
   Database '/home/home/.config/gcompris/gcompris_sqlite.db'
Exception ImportError: 'No module named Numeric' in 'garbage collection' ignored
Fatal Python error: unexpected exception during garbage collection
Aborted


--
Any advice appreciated. Oh, and just tried the -x option, no luck

---

### Post by nikhilk on 2009-09-23
> **Andyc709292 said:**
> Exception ImportError: 'No module named Numeric' in 'garbage collection' ignored
Fatal Python error: unexpected exception during garbage collection
Aborted

It seems python package "numeric" is missing. See if installing the package "python-numeric" resolves the error.

---

### Post by Jorgel on 2009-09-23
Don't know if it worked for Andy but it worked like a charm for me ( installing 'python-numeric' ) . Thank You **nikhilk**

---

### Post by Andyc709292 on 2009-09-24
Marvellous.
Worked for me too!

Perhaps something that should be included in the original install eh.

Thanks **nikhilk**

---

### Post by nikhilk on 2009-09-24
> **Jorgel said:**
> Don't know if it worked for Andy but it worked like a charm for me ( installing 'python-numeric' ) . Thank You **nikhilk**

> **Andyc709292 said:**
> Marvellous.
Worked for me too!

Perhaps something that should be included in the original install eh.

Thanks **nikhilk**

You are welcome!

---

### Post by trellis2 on 2009-10-03
The version of Gcompris in the repos is only a demo version. To compile the latest version see [http://ubuntuforums.org/showthread.php?t=1280450]("http://ubuntuforums.org/showthread.php?t=1280450")

---

