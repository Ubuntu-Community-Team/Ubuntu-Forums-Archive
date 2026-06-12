---
title: "apt-get find?"
date: 2009-08-26
forum: General Help
---

### Post by apmcd47 on 2009-08-26
I'm normally a Kubuntu user and use *adept* for my package installation. One of the reasons for using this is the ability to find a package simply by typing all or part of the name into a search box. Unfortunately with KDE 4 *adept* is a dead duck - no longer so easy to use, and development has terminated, to boot. So as I normally use the command line for most things I think it's about time I got to grips with *apt-get* ... except there doesn't seem to be a way of saying "list all packages"; "list all installed packages"; "list all packages where the name or description match this".

Is there an option to *apt-get* to get this functionality? Or a sister-application to get this info? Alternatively where is the information kept so I could just list the information manually? E.g. "grep -i package /path/to/list"

Yes, I've read the fine manual page, and I've read the /usr/share/doc/ documentation and I'm still non-the-wiser.

Andrew

---

### Post by tjwoosta on 2009-08-26
In debian I always search with aptitude and install/remove with apt-get

---

### Post by amauk on 2009-08-26
apt-cache search foo

---

### Post by kerry_s on 2009-08-26
"**apt-cache search** " is to search

"**dpkg -l | grep** " is used to check if its installed


set yourself some alias's of the commands.
here's mine:

```
[B]alias !='sudo'
alias u='sudo upgrade-system'
alias i='sudo apt-get install --no-install-recommends'
alias r='sudo apt-get remove --purge'
alias s='apt-cache search'
alias ?='dpkg -l | grep'
alias ch='clear;rm -f ~/.bash_history;history -c'[/B]
```

ps: "upgrade-system" is a package: **sudo apt-get install upgrade-system**

---

### Post by spiderbatdad on 2009-08-26
also ```
dpkg --get-selections
``` or write to a file in your home:
```
dpkg --get-selections > package-list
```

---

### Post by apmcd47 on 2009-08-26
Thanks - this is the sort of thing I was looking for. Apt-cache looks like the app to find all packages, installed or not. But I couldn't find a way to list the full description of a non-installed application. It's late - I'll sleep on it.

Andrew

---

### Post by kerry_s on 2009-08-26
[http://www.debian.org/doc/manuals/apt-howto/](http://www.debian.org/doc/manuals/apt-howto/)

---

### Post by jerome1232 on 2009-08-26
just fyi no need to use sudo with apt-cache search, it can be done as a regular user.

---

### Post by credobyte on 2009-08-26
```
sudo aptitude search <string>

```

Unless you are too lazy to check the symbol before each packages name/description ( i - installed ), this is pretty much all you need :)

---

### Post by kerry_s on 2009-08-26
> **jerome1232 said:**
> just fyi no need to use sudo with apt-cache search, it can be done as a regular user.

my bag, corrected. you just get so use to sudo. :lolflag:

---

### Post by tjwoosta on 2009-08-27
Same with aptitude search, you don't need sudo to search.

---

### Post by oldos2er on 2009-08-27
> **apmcd47 said:**
> Thanks - this is the sort of thing I was looking for. Apt-cache looks like the app to find all packages, installed or not. But I couldn't find a way to list the full description of a non-installed application. It's late - I'll sleep on it.

Andrew

**apt-cache show foo**

---

### Post by apmcd47 on 2009-08-27
> **oldos2er said:**
> **apt-cache show foo**

Didn't work for a non-installed package for me last night (*aptitude show* did).

Just checked again now for a different package and it displayed the information. Odd.

I shall have to have a play, take notes, read the docs I can find and possibly write my own wrappers.

Thanks, all.

Andrew

---

### Post by oldos2er on 2009-08-27
I never seem to be able to remember if apt-cache show works on installed packages only. Anyway, you might also want to look into the **dpkg-query **command.

---

### Post by credobyte on 2009-08-27
> **oldos2er said:**
> I never seem to be able to remember if apt-cache show works on installed packages only. Anyway, you might also want to look into the **dpkg-query **command.

Logically, apt-cache should extract data from packages, located at /var/cache/apt/archives, which means, they shouldn't be installed ( you can download packages & don't install them, etc. ) .. Tough, I'm not 100% sure if it's true.

---

### Post by jerome1232 on 2009-08-27
apt-cache search searches everything in that cache, both installed and not installed.

apt-cache show will indicate whether the package is installed or not.

---

