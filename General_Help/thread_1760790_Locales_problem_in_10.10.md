---
title: "Locales problem in 10.10"
date: 2011-05-17
forum: General Help
---

### Post by timgood on 2011-05-17
Running locale from terminal gives me:

```
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_GB-UTF8
LC_CTYPE="en_GB-UTF8"
LC_NUMERIC="en_GB-UTF8"
LC_TIME="en_GB-UTF8"
LC_COLLATE="en_GB-UTF8"
LC_MONETARY="en_GB-UTF8"
LC_MESSAGES="en_GB-UTF8"
LC_PAPER="en_GB-UTF8"
LC_NAME="en_GB-UTF8"
LC_ADDRESS="en_GB-UTF8"
LC_TELEPHONE="en_GB-UTF8"
LC_MEASUREMENT="en_GB-UTF8"
LC_IDENTIFICATION="en_GB-UTF8"
LC_ALL=en_GB-UTF8

```

How can I fix this? I've tried 

```
sudo dpkg-reconfigure locale
```

but it doesn't work.

```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = "en_GB-UTF8",
	LANG = "en_GB-UTF8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
/bin/bash: warning: setlocale: LC_ALL: cannot change locale (en_GB-UTF8)
Generating locales...
  en_AG.UTF-8... done
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... done
  en_DK.UTF-8... done
  en_GB.ISO-8859-1... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... done
  en_IE.UTF-8... done
  en_IN.UTF-8... done
  en_NG.UTF-8... done
  en_NZ.UTF-8... done
  en_PH.UTF-8... done
  en_SG.UTF-8... done
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... done
  en_ZW.UTF-8... done
Generation complete.

```

Any ideas?

---

### Post by timgood on 2011-05-17
Also noticed that when I start a terminal:

```
bash: warning: setlocale: LC_ALL: cannot change locale (en_GB-UTF8): No such file or directory

```

So where is the missing directory located?

---

### Post by timgood on 2011-05-18
Bump...

---

### Post by Kzin on 2011-05-30
[http://blog.andrewbeacock.com/2007/01/how-to-change-your-default-locale-on.html](http://blog.andrewbeacock.com/2007/01/how-to-change-your-default-locale-on.html)

Just check that out.  Make sure your locale is in the /var/lib/locales/supported.d/local file and then do a dpkg-reconfigure

---

