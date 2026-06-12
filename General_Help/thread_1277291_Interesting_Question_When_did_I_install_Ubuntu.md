---
title: "Interesting Question: When did I install Ubuntu?"
date: 2009-09-28
forum: General Help
---

### Post by PeEllAvaj on 2009-09-28
This isn't a real issue, more a point of curiosity.

I'm trying to figure out when I first installed ubuntu on this machine, or what release I started with.  Are there any files that would be left around untouched with the original date or version number?

Thanks!

---

### Post by sideaway on 2009-09-28
closest I can get is uname -a. Just general information about kernel etc.

---

### Post by alienclone on 2009-09-28
> **sideaway said:**
> closest I can get is uname -a. Just general information about kernel etc.

im sure that would just give the date of your last kernel install/upgrade.

---

### Post by Jose Catre-Vandis on 2009-09-28
Have a look at history in synaptic

---

### Post by t0p on 2009-09-28
> **PeEllAvaj said:**
> This isn't a real issue, more a point of curiosity.

I'm trying to figure out when I first installed ubuntu on this machine, or what release I started with.  Are there any files that would be left around untouched with the original date or version number?

Thanks!

You're currently using Jaunty.  Do you mean you want to know when you first installed an *earlier* version of Ubuntu?  Like Hardy, or Dapper or something?

Have you done clean installs?  If so, you will have installed one version over the other, and files from the earlier version will no longer exist.

If you've always done upgrades rather than clean installs, I don't know of any files that will have survived in this way.  Someone else may know more than me, but I don't think what you want is available.

---

### Post by credobyte on 2009-09-28
```
ls -al /sbin

```

In most cases, these files shouldn't have been replaced/modified, so .. [COLOR=RoyalBlue]last modified[/COLOR] would be your installation data/time :-\"

---

