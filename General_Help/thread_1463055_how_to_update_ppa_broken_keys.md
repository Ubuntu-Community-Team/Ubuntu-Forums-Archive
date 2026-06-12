---
title: "how to update ppa broken keys?"
date: 2010-04-26
forum: General Help
---

### Post by Elie-M on 2010-04-26
I want to fix this annoying thing with ppa keys broken and having to fix them. there was a script named launchpad-update that used to do that for you, but everything I find is for pre karmic.. is there any alternative to that script? anyway to do it manually? please help me.. cz some programs I installed are not getting updated and I'm having to add new ppas manually..

---

### Post by cariboo on 2010-04-26
If you go to the ppa page you should see a green link saying Technical details about this PPA, click the link, then select your version from the drop down. You should see a link under Signing Key, click the link, it should take you to a keyserver page, click the link that looks similar to this:

```
1024R/[COLOR="Blue"]_E549B1AC_[/COLOR]
```

Copy and paste gpg public code block to your favorite text editor, and save it.

Next go to System->Administration->Software Sources->Authentication, click the Import Key File button, select the file you just saved, click OK and your done. You may have to update the sources.

---

### Post by Elie-M on 2010-05-01
thx man appreciated

---

