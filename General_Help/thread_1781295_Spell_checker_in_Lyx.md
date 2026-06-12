---
title: "Spell checker in Lyx"
date: 2011-06-13
forum: General Help
---

### Post by Ariya243 on 2011-06-13
Does anyone know how to activate spell checker in Lyx 2.0?
There is Aspell and Hunspell installed in Ubuntu 11.04

---

### Post by Frogs Hair on 2011-06-13
According to this page , spell checking is toggled on or off in preferences.
[http://wiki.lyx.org/LyX/NewInLyX20/#inline-spelling](http://wiki.lyx.org/LyX/NewInLyX20/#inline-spelling)

---

### Post by Ariya243 on 2011-06-14
The problem is that this feature is switched off, grayed out

---

### Post by 334455 on 2011-06-14
You need the package:
myspell-xx-xx
where xx is the code for your language and country.

This should be fairly automatic in LyX and the package "should" be installed as standard. You could check if your language support is complete and check if the the package:
language-support-xx
(xx=your language code) is installed.

---

### Post by Ariya243 on 2011-06-15
I have myspell-en-us installed, but Lyx 2.0 doesn't see it. Spell checker is grayed out.
language-support-en is installed too
I re-installed Lyx 2.0 too, but still the spel checker is grayed out

---

### Post by 334455 on 2011-06-15
LyX has a mailing list for support: [http://www.lyx.org/MailingLists#toc4](http://www.lyx.org/MailingLists#toc4). You could ask there. The spell checking has gone through changes in LyX 2 and there can be bugs or settings to adjust. 
Are you using LyX 2.0RC3 from the standard repo? If you are, you could test LyX 2.0 final. If you don't want to build it yourself, you could get it from the getdeb repo: [http://www.getdeb.net/welcome/](http://www.getdeb.net/welcome/).

---

### Post by Ariya243 on 2011-06-15
Thanks!
I'll try the Lyx mailing list

---

### Post by linas on 2012-09-09
FWIW, this is still a problem in "precise pangolin".  Am trying to figure it out, again...

According to this thread: [http://comments.gmane.org/gmane.editors.lyx.general/70372](http://comments.gmane.org/gmane.editors.lyx.general/70372)  the issue is that the ubuntu version of lyx was not compiled with spell-checking... hmmm...

---

### Post by linas on 2012-09-09
I found teh answer here: Yayyyy!

[http://ubuntuforums.org/showthread.php?t=1929675](http://ubuntuforums.org/showthread.php?t=1929675)

I have now got the answer to this problem from the LinuxFormat Forum.

Check in the Software Centre to see if ENCHANT is installed. If not, install it.  Then start Lyx,select TOOLS, PREFERENCES, LANGUAGE SETTINGS, SPELLCHECKER.  Then at SPELLCHECKER ENGINE, select ENCHANT, press ENTER KEY, and click on SAVE.

You should now have a spell checker!

:KS:KS:KS:KS:KS

---

### Post by wildmanne39 on 2012-09-09
thanks

---

