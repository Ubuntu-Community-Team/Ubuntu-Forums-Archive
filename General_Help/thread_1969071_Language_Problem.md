---
title: "Language Problem"
date: 2012-04-29
forum: General Help
---

### Post by merlinus on 2012-04-29
All of a sudden, for no apparent reason, I am logged in with a different language!  It looks like Japanese.

How can I change this back to English?  It is impossible to figure out, as all the menus and such are in this different language.

I tried changing to US English in System Settings/Gnome Language Selector, but could not change anything.

---

### Post by merlinus on 2012-04-29
I added LANGUAGE="en_GB:en_US:en_GB:en"
LANG=en_US.UTF-8

to /etc/environment

and logged out and back in, but nothing changed.

I also dragged Englsih (US) to the top of the listings in gnome-language-selector, but to no avail.

---

### Post by roncville on 2012-04-29
Exact same problem here, using xubuntu 12.04 in my case.  The first 5 or so boots after the new installation were fine.  But the 6th time it came up in a Japanese-looking language, and has stayed there.

---

### Post by jockyburns on 2012-04-29
I have the same problem,,,, but only when I have to phone VirginMedia call centres. :lolflag::lolflag::lolflag:

---

### Post by merlinus on 2012-04-29
> **roncville said:**
> Exact same problem here, using xubuntu 12.04 in my case.  The first 5 or so boots after the new installation were fine.  But the 6th time it came up in a Japanese-looking language, and has stayed there.

So, have you decided to live with the situation, or ???

If no one can offer a solution, I will try re-installing, but without formatting the / partition.

---

### Post by roncville on 2012-04-29
> So, have you decided to live with the situation, or ???

I'll wait it out for awhile.  There's a bug somewhere, so someone will come up with a workaround, and eventually a fix.  I'll do some more searching of my own, too.  Meanwhile, I'll revert to 11.10 which is still installed on the same machine.  I'm not too interested in reinstalling 12.04, without understanding the odds of it happening again.

---

### Post by Wastl on 2012-04-30
I have the same problem after upgrading from 11.10 (with swiss german locale).
after some logins into the newly installed ubuntu 12.04 the system language switched to english. there is no effect when i set it back to german in the "language support" dialog in the system settings (the user language is also set to german). i also tried to remove and install german language support, but that did not work either.
looking at the output of `locale` shows that every variable is set to a german or swiss german locale, also for the root account (if this is crucial).
has anyone solved this issue yet or found a workaround?

---

### Post by merlinus on 2012-04-30
A workaround is to go to System Settings/User Accounts, and select the language you are wanting from the dropdown box next to Language.  Then restart.

Clearly this is a bug, and it is rather distressing that not one single moderator has responded to either of the posts regarding this issue!!!

You will probably have it easier, though, since the language for me changed to Chinese, and I had to try several times to pick the right one!

---

### Post by Wastl on 2012-04-30
> **merlinus said:**
> A workaround is to go to System Settings/User Accounts, and select the language you are wanting from the dropdown box next to Language.  Then restart.


thank you for your quick response. unfortunately your workaround does not work for me.
any other suggestions? environment variables in /etc/environment and /etc/default/locale are set to german.

---

### Post by merlinus on 2012-04-30
Just to be sure, did you click Unlock before making the change, and edit the language for the particular user?  Editing the environment variables was useless, but this method worked.

---

### Post by tobiasquinn on 2012-04-30
I've had the same problem, it seems the language is being changed to zh_CN which means it is not really possible to fix using the GUI as the labels are all in chinese. The /etc/environment has LANG=zh_CN type lines in it, my other machine only has a PATH= line.

Removing the LANG lines from /etc/environment AND changing the line(s) in /etc/default/locale to be en_GB, not zh_CN seems to fix the problem.

In summary the files/lines to look for are in:

/etc/environment AND /etc/default/locale

---

### Post by uylug on 2012-04-30
Also, it might be a good idea to check that you have complete language support:

Update Sources:
```
sudo apt-get update
```

Install **English** Pack:
```
sudo apt-get install language-pack-en*
```

Or Install Spanish pack
```
sudo apt-get install language-pack-es*
```

And so on...

---

### Post by Wastl on 2012-05-02
> **merlinus said:**
> Just to be sure, did you click Unlock before making the change, and edit the language for the particular user?

yes I did. however, the settings do not have any effect. i also looked at the files /etc/environment AND /etc/default/locale again as indicated by tobiasquinn, but do not see any english language setting there.

In /etc/environment I have:
```

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANGUAGE="de_DE:en"
LANG="de_DE.UTF-8"

```

In /etc/default/locale I have:
```

LANG="de_DE.UTF-8"
LANGUAGE="de_DE:en"
LC_MESSAGES=POSIX
LC_NUMERIC="de_CH.UTF-8"
LC_TIME="de_CH.UTF-8"
LC_MONETARY="de_CH.UTF-8"
LC_PAPER="de_CH.UTF-8"
LC_NAME="de_CH.UTF-8"
LC_ADDRESS="de_CH.UTF-8"
LC_TELEPHONE="de_CH.UTF-8"
LC_MEASUREMENT="de_CH.UTF-8"
LC_IDENTIFICATION="de_CH.UTF-8"

```

and here is the content of ~/.pam_environment
```

LANG=de_DE.UTF-8
LANGUAGE=de_DE:en_GB:en
LC_NUMERIC=de_CH.UTF-8
LC_TIME=de_CH.UTF-8
LC_MONETARY=de_CH.UTF-8
LC_PAPER=de_CH.UTF-8
LC_NAME=de_CH.UTF-8
LC_ADDRESS=de_CH.UTF-8
LC_TELEPHONE=de_CH.UTF-8
LC_MEASUREMENT=de_CH.UTF-8
LC_IDENTIFICATION=de_CH.UTF-8

```

(the german language packs are installed)


BTW, the language setting for "Regional Formats", e.g. the formatting of the date in the upper desktop panel, works fine.

I think I have to re-install 12.04 or go back to 11.10... :(

---

