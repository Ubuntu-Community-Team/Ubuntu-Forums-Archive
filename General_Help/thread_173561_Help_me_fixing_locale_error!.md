---
title: "Help me fixing locale error!"
date: 2006-05-10
forum: General Help
---

### Post by Isoss on 2006-05-10
Weird error given by terminal every time trying to install or open anything:
for example: I am trying to open bluefish:
```

(bluefish:17165): Gdk-WARNING **: locale not supported by Xlib

(bluefish:17165): Gdk-WARNING **: cannot set locale modifiers

```

Openeing source.list with gedit:
```
(gedit:17191): Gdk-WARNING **: locale not supported by Xlib

(gedit:17191): Gdk-WARNING **: cannot set locale modifiers

```
Or trying to open Automatic:
```
(zenity:17121): Gdk-WARNING **: locale not supported by Xlib

(zenity:17121): Gdk-WARNING **: cannot set locale modifiers

```
.......

WHAT THE HELL!!! 

These are my repositories:
```
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse

deb http://wine.lowvoice.nl/apt breezy main
deb-src http://wine.lowvoice.nl/apt breezy main

deb http://deb.opera.com/opera/ etch non-free

deb http://kubuntu.org/packages/kde351 breezy main

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://koti.mbnet.fi/~ots/ubuntu/ breezy/
deb-src http://koti.mbnet.fi/~ots/ubuntu/ breezy/

deb http://theli.free.fr/packages/breezy/ ./
## created by arniewinechanged

```

---

### Post by Isoss on 2006-05-10
I searched for my problem and found these:
[http://ubuntuforums.org/showthread.php?t=50040&highlight=locale+Xlib](http://ubuntuforums.org/showthread.php?t=50040&highlight=locale+Xlib)
[http://ubuntuforums.org/showthread.php?t=43467&highlight=locale+Xlib](http://ubuntuforums.org/showthread.php?t=43467&highlight=locale+Xlib)

in both, humina said:
```
This tells you that your locale is not set to en_US or en_GB or whatever. It is actually set to some language called C. You can see this by typing locale -a. The output shows your first locale is C. I don't know how to fix this, but this is where the problem lies.
```

he's right ... this is how it looks when I type locale -a:
```
C
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_IN.utf8
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
POSIX

```

Does any body know how to fix this?

---

### Post by Isoss on 2006-05-10
alright, you ppl might not know my problem cuz it seems complicated. at least, can you suggest something or direct me to something that might help?!

---

### Post by elamericano on 2006-05-10
You were expecting an answer in 3 hours? Patience.

locale -a shows all locales, not your current locale. I don't have this problem, but "C" is the first entry from locale -a for me too.

My locale output is:
> LANG=en_US.UTF-8
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


Is yours different?

---

### Post by Isoss on 2006-05-11
[QUOTE=elamericano]You were expecting an answer in 3 hours? Patience.
[/QUOTE]
:oops: actually ... ummmm ... well, ppl here are so helpful and very fast posting replies and solutions ... so I kinda got used to getting answers faster than a diarrhea (it's an expression in our country:mrgreen: ) ... but it's good ... but really, my problem isn't just this ... this problem is hulting a lotta other stuff
[QUOTE=elamericano]
Is yours different?[/QUOTE]
My locale looks like this
```
LANG=en_ZW.UTF-8
LC_CTYPE="en_ZW.UTF-8"
LC_NUMERIC="en_ZW.UTF-8"
LC_TIME="en_ZW.UTF-8"
LC_COLLATE="en_ZW.UTF-8"
LC_MONETARY="en_ZW.UTF-8"
LC_MESSAGES="en_ZW.UTF-8"
LC_PAPER="en_ZW.UTF-8"
LC_NAME="en_ZW.UTF-8"
LC_ADDRESS="en_ZW.UTF-8"
LC_TELEPHONE="en_ZW.UTF-8"
LC_MEASUREMENT="en_ZW.UTF-8"
LC_IDENTIFICATION="en_ZW.UTF-8"
LC_ALL=

```

I don't really understand what these are, I am still a newbie ... just started using linux a month ago. 

I really wish I can get a good explaination of what is locale and what does it exactly do and what does it have to do with package installations or starting?

Anyway ... Thank you for being patient with me, I just have a lotta things to learn and to do.

---

### Post by elamericano on 2006-05-11
A locale generally indicates what country you are in. Mostly, your system uses it to know what character set and keyboard layout you are using. See "man localedef" for what 12 rules can change by country (at the bottom). It's interesting.

Anyway, xlib must use it for something, but it doesn't recognize Zimbabwe. This is not an error. It's only "warning". It warns you that your locale might be misconfigured - but it's not. If your installs are failing, it's due to a different problem - but you didn't say anything was failing. It's just the messages that you were concerned about, right? xlib probably just uses a default, stable setting when it doesn't recognize your locale. No harm done.

If you really wanted to change your locale for an install, I don't know what to tell you, because "sudo dpkg-reconfigure locales" doesn't seem to work for me on Breezy. Maybe it requires a reboot.

Humina was trying to be helpful, but he misunderstood the situation - and the locale command.

---

### Post by Isoss on 2006-05-12
hmmmm .. alright, but there is something strange here. I don't live in Zimbabwe!! I live in Syria ... And I wonder where this en_ZW came from! I have never selected any option relating!

---

### Post by elamericano on 2006-05-12
Maybe it was an installer error. Did you select English as your language? Since there is no en_SY (English, Syria), maybe it went with the last English locale in the list.

So, you can either change it to ar_SY, if you want to use Arabic, or you'll need to pick an English locale that you like. Do you like any? ;) Seriously, it only matters that they use the same keyboard that you have.

Go to System->Administration->Language Selector and pick the Default Language (with location in parenthesis). That will be your new locale, but you won't see it take effect until you reboot.

Let me know what solution you went with.

---

### Post by Isoss on 2006-05-12
Problem Solved. Thanks a bunch. locale warning doesn't appear anymore. so I guess everything is ok. I think the default langage was set to English (Zimbabwe ) by a mistake and I just didn't notice it.

Anyway, still need an explaination concerning the C that appears in the top of the locale -a list. and also what is POSIX?

Thanks again,

---

### Post by elamericano on 2006-05-13
The default locale C corresponds to the 7-bit USASCII character set. This setting is the minimal locale needed to read and compile C programs.

POSIX is an IEEE standard equivalent to C. (because they want to be the ones who set the standards?)

Here's a link for some of the programming issues:
[http://jan.netcomp.monash.edu.au/i18n/locale/locale.html](http://jan.netcomp.monash.edu.au/i18n/locale/locale.html)

---

### Post by Isoss on 2006-05-13
Thanks buddy.

---

