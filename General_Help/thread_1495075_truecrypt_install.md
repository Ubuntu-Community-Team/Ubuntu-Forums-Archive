---
title: "truecrypt install"
date: 2010-05-27
forum: General Help
---

### Post by Achilles124 on 2010-05-27
I try to install truecrypt on my computer and I downloaded the program from the makers website. I untarred it and ran it. Now it is in my /usr/bin/ file. But it doesn´t run. 

It looks like this from the command line:

```
ecmpeek@ecmpeek-desktop:~$ /usr/bin/truecrypt
bash: /usr/bin/truecrypt: kan een binair bestand niet uitvoeren

```

It says: cannot execute a binary file.

What does that mean?

Another problem is that I cannot uninstall truecrypt either. It has installed an uninstall file in /usr/bin and it has a .sh extension. How do I unstall it?

---

### Post by alphaamanitin on 2010-05-28
have you tried just typing in truecrypt to the terminal, or going into /usr/bin and trying to open it from there?  If that does not work I would suggest trying "sudo truecrypt" in the terminal.  If you want to try to uninstall it at the command line try "sudo truecrypt-uninstall.sh"

I am a relatively new Linux user though perhaps you have tried these and it still does not work.  If that is the case good luck, and I hope a more experienced user helps out.

AlphaA

---

### Post by Achilles124 on 2010-05-29
Thank you for answering, alphaamanitin. I used bash truecryptuninstall.sh. That worked.

---

### Post by alphaamanitin on 2010-06-03
Glad to be of help.

AlphaA

---

### Post by Carlos_pe on 2011-01-21
Yeah!   To uninstall, it is also work for me. Here the resume: 

[COLOR=Navy][COLOR=Black]$ [COLOR=Navy]cd /usr/bin/[/COLOR]
/usr/bin$ [COLOR=Navy]sudo bash truecrypt-uninstall.sh [/COLOR]
[sudo] password for [user]: 
TrueCrypt uninstalled. [/COLOR]
[/COLOR]

Thanks

---

