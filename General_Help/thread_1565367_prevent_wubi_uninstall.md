---
title: "prevent wubi uninstall?"
date: 2010-08-31
forum: General Help
---

### Post by jakerman999 on 2010-08-31
I'm looking for a way to make wubi unable to be uninstalled.  Or possibly require a password before uninstall.  Just something to stop my roommate from deleting ubuntu(again).  I've tried the polite option and that didn't work, so this is my last peaceful resort.  If this isn't possible, just let me know.

---

### Post by bcbc on 2010-08-31
Lock down your computer with a decent password and open up a guest account for your roommate (if you feel that's the polite thing to do).

---

### Post by Rasa1111 on 2010-08-31
what bcbc said.
only *I* feel that it *would* be polite.
much more so than him deleting it. (again). 

Be admin, and keep him as a guest. 
Then he can't remove or change/add things without password.
He wants to act like a child
treat him as one.

---

### Post by rockager on 2010-08-31
> **Rasa1111 said:**
> what bcbc said.
only *I* feel that it *would* be polite.
much more so than him deleting it. (again). 
 
Be admin, and keep him as a guest. 
Then he can't remove or change/add things without password.
He wants to act like a child
treat him as one.
and don't forget to put a password for the hidden admin log (if you are using xp)
or lock your computer by installing a password on the BIOS.

---

### Post by bcbc on 2010-09-01
I suppose you can also delete c:\ubuntu\wubi-uninstall.exe and the [registry key]("https://wiki.ubuntu.com/WubiGuide#How do I manually uninstall Wubi?"):
> To remove Wubi from the add/remove list, delete the registry key:
  HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi

It's a little more subtle. Might even work :)

---

