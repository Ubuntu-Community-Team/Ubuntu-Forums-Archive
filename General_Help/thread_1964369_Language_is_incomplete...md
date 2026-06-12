---
title: "Language is incomplete.."
date: 2012-04-23
forum: General Help
---

### Post by GameX2 on 2012-04-23
Hi,


I'm French, so I installed the French language on Ubuntu, and removed English; pretty obvious.  The problem is, I can't understand why Ubuntu is not *perfectly* in French?  There is one message that keep appearing in English for some reason, and it's "Authentification is required to run GRUB-Customizer/GParted ...".  Shouldn't that be in French as well?  I deleted the English language!
When I check the languages settings, English is not installed.  Only French is there, oh and Chinese as well (??).  Can't remove it, don't know why.


Why this message still display in English?
Not a big issue, but anyways, still would be better to have a fully French Ubuntu for me.


Thanks for the reply!

---

### Post by dniMretsaM on 2012-04-23
It's probably the program itself that's in English. There might be a language setting inside the app. Or you might have to download something extra. If there isn't a French translation, you could help translate the program if you contact the developers. I'm sure they would appreciate it.

---

### Post by GameX2 on 2012-04-23
Thanks for replying that fast;

Both GParted Partition Editor and GRUB-Customizer are availible in French; actually, here a screenshot of the language problem:

[http://img337.imageshack.us/img337/8489/language.png](http://img337.imageshack.us/img337/8489/language.png)

Shouldn't "Authentification is required to run the GParted Partition Editor" be in French as well?

EDIT: Exactly the same thing when I'm trying to add a PPA, as well.

---

### Post by 3rdalbum on 2012-04-24
File a bug report. Either the string in the Policykit window is hardcoded in (which it shouldn't be!) or nobody has translated that string to French yet and the English string has been put into the French language pack in the meanwhile. Either case, it is a bug and needs reporting.

Submitting a translation would be much appreciated, I'm sure.

---

### Post by GameX2 on 2012-04-24
Perhaps this is a bug with Ubuntu 11.10, since I never had a similar problem using Ubuntu 11.04.
It seems it's not a bug with the applications, but with the Unity environnement itself, since I also get this bug while opening system applications, such as adding a PPA.

I'll try to install English, and then reinstall French next; if that doesn't work, this is probably a bug as you say.

---

