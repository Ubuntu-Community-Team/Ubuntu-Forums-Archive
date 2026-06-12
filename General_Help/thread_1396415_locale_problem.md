---
title: "locale problem"
date: 2010-02-02
forum: General Help
---

### Post by Norami on 2010-02-02
On my Ubuntu Server 9.10 box, the locale is messed up. I have 4 other boxes running 9.10, have set them up the same way as this one, and they don't have this problem. Only this box is.

```
$ locale
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
```

I think this is having an effect on my bash scripts. Every time I try to run a script, it says:

```
-bash: ./script.sh: /bin/bash^M: bad interpreter: No such file or directory
```

Any idea on how to set the locale? I've looked it up on google, and through here, but none of the fixes seem to have an effect on anything. I've never encountered this before. Perl also gives me a warning about the locales, saying that LANGUAGE and LC_ALL are unset.

---

### Post by rnerwein on 2010-02-02
hi
run your script: dos2unix your_file

you got ^M dos line feeds in it
ciao

---

