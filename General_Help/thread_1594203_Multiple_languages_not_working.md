---
title: "Multiple languages not working"
date: 2010-10-12
forum: General Help
---

### Post by kallekn on 2010-10-12
I'd like to be able to use the Gnome desktop and programs in several languages, as far as I can see I have installed the necessary language support for the desired languages, but only my default language (Finnish) is working the way it should.

When I select any other language when I check into a new session I still get most everything in Finnish, except that the date is in the selected language, but with Finnish endings. Weird! The language change seems to affect some programs, but not the Gnome interface.

I had this problem in 10.04 and was hoping it might disappear in 10.10, but there is no change. What am I doing wrong? Do I need to upgrade or reinstall the language files in some way, or what?

---

### Post by myro21 on 2011-03-20
> **kallekn said:**
> I'd like to be able to use the Gnome desktop and programs in several languages, as far as I can see I have installed the necessary language support for the desired languages, but only my default language (Finnish) is working the way it should.

When I select any other language when I check into a new session I still get most everything in Finnish, except that the date is in the selected language, but with Finnish endings. Weird! The language change seems to affect some programs, but not the Gnome interface.

I had this problem in 10.04 and was hoping it might disappear in 10.10, but there is no change. What am I doing wrong? Do I need to upgrade or reinstall the language files in some way, or what?

Has there any solution been found to that problem? I am experiencing the same thing:
I installed in language support English and German. If I select English with the highest priority in the language support window and then choose German on the login screen, every menu is in English (only the date is in German). 
If I select in language support German with the highest priority, everything is in German, even if I select English on the login screen (only the date is in English then).

Do I have to reinstall something?
Thanks for reading

PS.: I already posted this issue a couple of days ago on the german ubuntu forums, but no one knew an answer.
PPS.: I started using ubuntu one week ago, thus I am not really familiar with the system.

---

### Post by myro21 on 2011-03-23
bump, problem still persists. my locale looks like this:
```

LANG=de_DE.utf8
LANGUAGE=en
LC_CTYPE="de_DE.utf8"
LC_NUMERIC="de_DE.utf8"
LC_TIME="de_DE.utf8"
LC_COLLATE="de_DE.utf8"
LC_MONETARY="de_DE.utf8"
LC_MESSAGES="de_DE.utf8"
LC_PAPER="de_DE.utf8"
LC_NAME="de_DE.utf8"
LC_ADDRESS="de_DE.utf8"
LC_TELEPHONE="de_DE.utf8"
LC_MEASUREMENT="de_DE.utf8"
LC_IDENTIFICATION="de_DE.utf8"
LC_ALL=

```
is that alright like that?

---

