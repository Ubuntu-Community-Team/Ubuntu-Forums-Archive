---
title: "Rectangles instead of text"
date: 2011-08-18
forum: General Help
---

### Post by nestorpan on 2011-08-18
Hi.
I have this problem:
I see rectangles in the places where should be text. This happens, for example in Code::Blocks in the build log tab, in the warning lines, the rest of the text is ok.
This also happens in certain message boxes of Ubuntu. And in the subtitles text in the default video player.

Mi version of Ubuntu is 11.04.

Thanks in advance.

---

### Post by SoFl W on 2011-08-18
This might be a language or font problem.  Did you make any changes to the language or font settings?  What is your default language.

---

### Post by nestorpan on 2011-08-18
No, I didn't make any change to the language nor font settings.

This is my locale output:

LANG=en_US.UTF-8
LANGUAGE=en_US:en
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

---

### Post by tredegar on 2011-08-18
My **locale**```
LANG=en_GB.utf8
LC_CTYPE="en_GB.utf8"
LC_NUMERIC="en_GB.utf8"
LC_TIME="en_GB.utf8"
LC_COLLATE="en_GB.utf8"
LC_MONETARY="en_GB.utf8"
LC_MESSAGES="en_GB.utf8"
LC_PAPER="en_GB.utf8"
LC_NAME="en_GB.utf8"
LC_ADDRESS="en_GB.utf8"
LC_TELEPHONE="en_GB.utf8"
LC_MEASUREMENT="en_GB.utf8"
LC_IDENTIFICATION="en_GB.utf8"
LC_ALL=

```
So what is different  (apart from *GB*) is your line:
[COLOR="Red"]*LANGUAGE*=en_US:en[/COLOR]
which does not refer to UTF-8, and I don't have a **LANGUAGE=** entry at all (I'm using 10,04).

I'm unsure as how to fix this for you, but it points out the possible mis-configuration.

Maybe **grep** your filesystem ( you could start in **/etc/** ) for **LANGUAGE=en_US:en** ?

---

