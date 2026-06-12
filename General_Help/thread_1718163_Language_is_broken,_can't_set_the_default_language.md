---
title: "Language is broken, can't set the default language"
date: 2011-03-30
forum: General Help
---

### Post by WesleyWex on 2011-03-30
I'm using Ubuntu Desktop with some daemons (like Apache and MySQL), and wanted to install a new locale. I tried a lot of things but it seems that everything was removed from Ubuntu 10.10 that could do this on the command line, so I gave up and used Language & Format.

The problem is that now I can't uninstall the new language (pt_BR) because it not only is stuck on my settings (when I print my locale, everything is using it, even if it is not installed), but the behaviour of the system is weird. If I reinstall the language and say English should be the preferred one, some applications like CompizConfig gets partially on English, partially on Portuguese.

I tried a lot of stuff:
[LIST]
[*]locale -a does not show pt_BR
[*]locale shows this:```
wesley@Jupiter:~$ locale
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=pt_BR.utf8
LANGUAGE=en
LC_CTYPE="pt_BR.utf8"
LC_NUMERIC="pt_BR.utf8"
LC_TIME="pt_BR.utf8"
LC_COLLATE="pt_BR.utf8"
LC_MONETARY="pt_BR.utf8"
LC_MESSAGES=en_GB.UTF-8
LC_PAPER="pt_BR.utf8"
LC_NAME="pt_BR.utf8"
LC_ADDRESS="pt_BR.utf8"
LC_TELEPHONE="pt_BR.utf8"
LC_MEASUREMENT="pt_BR.utf8"
LC_IDENTIFICATION="pt_BR.utf8"
LC_ALL=

```
[*]tried running the old dpkg-reconfigure localeconf (installed manually)
[*]/etc/environment do not mention pt_BR
[/LIST]

I wonder if I'm going to get any help for this or this issue will fall into oblivion like all issues I had in the past and the only solution is format and reinstall, like before.

---

### Post by Zatta on 2011-03-31
I had a similar issue today, see [https://bugs.launchpad.net/ubuntu/+source/language-pack-pt/+bug/746576](https://bugs.launchpad.net/ubuntu/+source/language-pack-pt/+bug/746576) , after updating some language packs.

I tried a lot of things. Eventually, I added the following 3 lines to /etc/profile with 
```

$ sudo gedit /etc/profile

```
 in an attempt to "force" a solution:

```

#inserted into /etc/profile:
export LANG="pt_BR.UTF-8"
export LANGUAGE="pt_BR:en"
export LC_MESSAGES="pt_BR.UTF-8"

```

I think you should change LANG to the locale you want and you have installed. As I said, it is a quick fix I used because language support broke with an update. 

Now, *locale* says:

```

LANG=pt_BR.utf8
LANGUAGE=pt_BR:en
LC_CTYPE="pt_BR.utf8"
LC_NUMERIC="pt_BR.utf8"
LC_TIME="pt_BR.utf8"
LC_COLLATE="pt_BR.utf8"
LC_MONETARY="pt_BR.utf8"
LC_MESSAGES=pt_BR.UTF-8
LC_PAPER="pt_BR.utf8"
LC_NAME="pt_BR.utf8"
LC_ADDRESS="pt_BR.utf8"
LC_TELEPHONE="pt_BR.utf8"
LC_MEASUREMENT="pt_BR.utf8"
LC_IDENTIFICATION="pt_BR.utf8"
LC_ALL=

```

and it all works for me.

(If I understood man pages correctly, LANG has priority over other locale variables. The session sets environment variables after a number of configuration places, including /etc/profile. So I added the locale variables I wanted to /etc/profile. I understand that it should be done by language packs, but something went broke when I updated so I had to modify /etc/profile directly.)


Hope it helps you.

---

### Post by Zatta on 2011-04-01
See this bug:
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/746694](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/746694)

---

### Post by Gonzalo_VC on 2011-04-01
I got this, when opening that file:

# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ -d /etc/profile.d ]; then
  for i in /etc/profile.d/*.sh; do
    if [ -r $i ]; then
      . $i
    fi
  done
  unset i
fi

if [ "$PS1" ]; then
  if [ "$BASH" ]; then
    PS1='\u@\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
	. /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

umask 022

:confused:  Where should I put those 3 lines? At the end of the file? Before the umask022 ?
Thanks!

---

### Post by Zatta on 2011-04-01
I didn't explain very well. I meant to put those 3 lines at the end of the file.

But I think that you should, before, take a look at the bug in the the link. It is a bug in gdm, that caused the problem with locales, for me. Today, an update to gdm corrected this bug and the problem went away.

---

### Post by Gonzalo_VC on 2011-04-02
> **Zatta said:**
> I didn't explain very well. I meant to put those 3 lines at the end of the file.

But I think that you should, before, take a look at the bug in the the link. It is a bug in gdm, that caused the problem with locales, for me. Today, an update to gdm corrected this bug and the problem went away.

Thanks.
I didn't change the file yesterday (was waiting for more details to do so), nor the apt-get -f install or anything else solved the problem (uninstaling, re-instaling the languages, re-starting the PC...). 
However, this morning, I got my old "locale" menu corrected again!!??  OK, I'll take it eventhough I don't know how it was done :D

---

### Post by InternationalDBA on 2013-02-09
I wanted to change the language used by cal and date so I did this:
[http://andrews-unix.blogspot.co.uk/2013/02/how-to-change-language-used-by-cal-and.html](http://andrews-unix.blogspot.co.uk/2013/02/how-to-change-language-used-by-cal-and.html)

---

### Post by wildmanne39 on 2013-02-09
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

