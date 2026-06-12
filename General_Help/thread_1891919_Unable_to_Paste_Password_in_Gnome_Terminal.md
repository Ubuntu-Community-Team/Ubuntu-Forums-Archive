---
title: "Unable to Paste Password in Gnome Terminal"
date: 2011-12-06
forum: General Help
---

### Post by tleish on 2011-12-06
OS: Ubuntu 11.10
App: Gnome Terminal 3.0.1

When terminal commands like ssh or mysql require a password, I am unable to paste a password.  I have passwords saved in an encrypted file which I copy from and paste into other applications.  

When a password entry is requested, Both Edit > Paste and Right Click > Paste are both grayed out.  Shift+Ctrl+V or middle mouse button click do not work either.

I have done this on other versions of Ubuntu and other terminals, but I am unable to on the latest.  I'm sure this is for some security reason, but after searching the internet I can't find a way to enable this.

Any ideas?

-tleish

---

### Post by bluexrider on 2011-12-06
don't think the shell will allow that.

---

### Post by no2498 on 2011-12-07
? have you tried clicking enter 
as we can not see the pass word as we type it

---

### Post by snowpine on 2011-12-07
If Edit -> Paste is grayed out then there's nothing in your clipboard. You need to highlight the text in the source document and Edit -> Copy or Ctrl + C before you can paste into the terminal.

---

### Post by tleish on 2011-12-09
I learned it's a combination of multiple Linux clipboards and the KeePass password manager.  The passwords are copied to a clipboard that I can paste into any application other than a terminal.

[http://www.sparrowtail.com/linux-and-its-schizophrenic-clipboards](http://www.sparrowtail.com/linux-and-its-schizophrenic-clipboards)

---

