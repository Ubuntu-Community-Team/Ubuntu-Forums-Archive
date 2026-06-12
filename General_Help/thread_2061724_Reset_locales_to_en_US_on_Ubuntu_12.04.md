---
title: "Reset locales to en_US on Ubuntu 12.04"
date: 2012-09-23
forum: General Help
---

### Post by fmmarzoa on 2012-09-23
Hi there,

I have installed Ubuntu 12.04 on a new machine. By mistake, I select Spanish as language during the install, so my whole system is in Spanish now. I rather like to have it in US English instead, so I have reconfigured locales, even generate them manually using locale-gen, but for some unknown reason my system is still in Spanish in both, terms and X-Window.

Even when my locale info is this:

$ locale
LANG=en_US.UTF-8
LANGUAGE=en_US:en_GB:es_ES:en
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC=en_US.UTF-8
LC_TIME=en_US.UTF-8
LC_COLLATE="en_US.UTF-8"
LC_MONETARY=en_US.UTF-8
LC_MESSAGES="en_US.UTF-8"
LC_PAPER=en_US.UTF-8
LC_NAME=en_US.UTF-8
LC_ADDRESS=en_US.UTF-8
LC_TELEPHONE=en_US.UTF-8
LC_MEASUREMENT=en_US.UTF-8
LC_IDENTIFICATION=en_US.UTF-8
LC_ALL=

I continue receiving system messages in Spanish instead of English. And so with X-Window menus and messages.

:confused::confused::confused:

Any hint?

Thanks a lot in advance!

---

### Post by germanix on 2012-09-23
Once you have changed the language to us-english on "sytem-settings" and "language support" you also go to the second tab on that window which is called "regional formats". Here you choose the country formats you want to use. On this tab you must also click the "apply-system-wide" button. At first you will see no changes taking place. You will have to log out and lock in again for the changes to take place. If that does not work then shut down and restart and at the log-in window make sure "english is selected.

---

