---
title: "apt-cache --names-only search seamonkey"
date: 2012-07-03
forum: General Help
---

### Post by adit on 2012-07-03
What exactly --names-only option do?
I don't understand the output.  Below is the command and its output in my Ubuntu 12.04.
The command outputs 4 results.  *None of the results have the word 'seamonkey'.*  Please try the same command in your ubuntu 12.04 and tell me whether it produces same output.
```
:~$ apt-cache --names-only search seamonkey
enigmail - GPG support for Thunderbird and Debian Icedove
xul-ext-calendar-timezones - Calendar Extension for Thunderbird - Timezone data
xul-ext-gdata-provider - Calendar Extension for Thunderbird - Google Calendar support
xul-ext-lightning - Calendar Extension for Thunderbird
```

---

### Post by vasa1 on 2012-07-03
> **adit said:**
> What exactly --names-only option do? ...
Hi, what information are you wanting to get?

BTW, I see what you see.

---

### Post by codemaniac on 2012-07-03
> **adit said:**
> What exactly --names-only option do?
I don't understand the output.  Below is the command and its output in my Ubuntu 12.04.
The command outputs 4 results.  *None of the results have the word 'seamonkey'.*  Please try the same command in your ubuntu 12.04 and tell me whether it produces same output.
```
:~$ apt-cache --names-only search seamonkey
enigmail - GPG support for Thunderbird and Debian Icedove
xul-ext-calendar-timezones - Calendar Extension for Thunderbird - Timezone data
xul-ext-gdata-provider - Calendar Extension for Thunderbird - Google Calendar support
xul-ext-lightning - Calendar Extension for Thunderbird
```

from man apt-cache

> search performs a full text search on all available package lists for the POSIX regex pattern given, see regex(7). It searches the package
           names and the descriptions for an occurrence of the regular expression and prints out the package name and the short description, including
           virtual package names. If --full is given then output identical to show is produced for each matched package, and [B]if --names-only is given
           then the long description is not searched, only the package name is[/B]

---

### Post by vasa1 on 2012-07-03
But why isn't seamonkey present in the results? I have Seamonkey installed, FWIW.

Others that seem logical:
```
~$ apt-cache --names-only search opera
opera - Fast and secure web browser and Internet suite

```
```
~$ apt-cache --names-only search empathy
empathy - GNOME multi-protocol chat and call client
empathy-common - GNOME multi-protocol chat and call client (common files)
empathy-dbg - GNOME multi-protocol chat and call client (debug symbols)
nautilus-sendto-empathy - GNOME multi-protocol chat and call client (nautilus-sendto plugin)

```
```
~$ apt-cache --names-only search chromium
chromium-browser - Chromium browser
chromium-browser-dbg - chromium-browser debug symbols
chromium-browser-l10n - chromium-browser language packages
chromium-bsu - fast paced, arcade-style, scrolling space shooter
chromium-bsu-data - data pack for the Chromium B.S.U. game
chromium-codecs-ffmpeg - Free ffmpeg codecs for the Chromium Browser
chromium-codecs-ffmpeg-dbg - chromium-codecs-ffmpeg debug symbols
chromium-codecs-ffmpeg-extra - Extra ffmpeg codecs for the Chromium Browser
chromium-codecs-ffmpeg-extra-dbg - chromium-codecs-ffmpeg-extra debug symbols

```

---

### Post by adit on 2012-07-03
> what information are you wanting to get?
I don't want to get any information.  I think this command behaves abnormally.
From the apt-cache man page:
> if --names-only is given then the long description is not searched, only the package name is
I have given --names-only option.  It should search *only* the package names.  If it searches only package names, each of the above 4 results returned by the above command should contain the word 'seamonkey'.  But none of the results have the word 'seamonkey'.  How can it happen?

---

### Post by codemaniac on 2012-07-03
Seems like seamonky is not available in the Universe .
You can get it from the below link .

[http://www.seamonkey-project.org/releases/](http://www.seamonkey-project.org/releases/)

---

### Post by vasa1 on 2012-07-03
> **codemaniac said:**
> Seems like seamonky is not available in the Universe .
You can get it from the below link .

[http://www.seamonkey-project.org/releases/](http://www.seamonkey-project.org/releases/)
That's not the point. The question is a fair one. On what basis are the other non-Seamonkey results being offered?

---

### Post by codemaniac on 2012-07-03
> **adit said:**
> 
I have given --names-only option.  It should search *only* the package names.  If it searches only package names, each of the above 4 results returned by the above command should contain the word 'seamonkey'.  But none of the results have the word 'seamonkey'.  How can it happen?

**apt-cache search** searches the package list for a regex pattern .
In my case the search results are returned only if the regex qualifies .

Please have a look .
> codemaniac@codemaniac:~$ sudo apt-cache --names-only search gmail
checkgmail - alternative Gmail Notifier for Linux via Atom feeds
enigmail - GPG support for Thunderbird and Debian Icedove
gmail-notify - A Gmail Notifier
gnome-gmail - support for Gmail as the preferred email application in GNOME
gnome-gmail-notifier - A Gmail Inbox Notifier for the GNOME Desktop
kcheckgmail - A Gmail notifier-like notifier for KDE
kgmailnotifier - Gmail notifier applet for KDE

In the above result set only the packages that are having gmail in the short desc are returned .
I am not sure if any hidden short descriptions are also getting searched in your case .

---

### Post by adit on 2012-07-03
At last I found out the answer myself.
Seamonkey is not available in the universe.
So I searched the following file (universe repository file) in my ubuntu system
/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_universe_binary-amd64_Packages
It does not have the package seamonkey listed.  But there are 4  packages
1) enigmail
2) xul-ext-calendar-timezones
3) xul-ext-gdata-provider
4) xul-ext-lightning
which provide the 'virtual package' seamonkey.  That is why apt-get listed like this..  Whenever we search for a 'virtual package' it happens like this.
**The results of the above command are correct**

---

### Post by vasa1 on 2012-07-03
> **adit said:**
> At last I found out the answer myself...
**The results of the above command are correct**
Good job :D

---

