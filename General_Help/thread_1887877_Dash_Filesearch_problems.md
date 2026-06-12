---
title: "Dash Filesearch problems"
date: 2011-11-28
forum: General Help
---

### Post by everytimeref on 2011-11-28
Dash File search will only find files I have used on my computer since upgrading to 11.10. Equally I can't search a new network location.

e.g. If I search for *.jpg I only get about four recent files (and I know where they are because I opened them er... recently) There should be literally thousands of entries.

If Dash is not going to do this for me does anyone new a good search tool that will?

---

### Post by stinkeye on 2011-11-28
What about just searching for **.jpg** in nautilus.

---

### Post by everytimeref on 2011-11-28
I thought of that, when I search for *.jpg (even in my pictures folder!) It finds nothing.

---

### Post by stinkeye on 2011-11-28
Just use **.jpg**

---

### Post by everytimeref on 2011-11-28
> **stinkeye said:**
> Just use **.jpg**

I knew that:redface::redface::redface:

Thankyou.

I guess * does not work at a wildcard like in windows.

---

### Post by stinkeye on 2011-11-28
Works with the find command in terminal.
eg find all jpg's over 1000k.
```
sudo find / -name '*.jpg' -size +1000k
```

or
all png's on my Data drive
```
sudo find /media/Data -name '*.png'
```

---

### Post by 3rdalbum on 2011-11-28
What you describe is actually the way the searching backend (called Zeitgeist - not actually a search engine but an activity log) works.

There are still some problems with search in Unity, although of course it's a hundred times better than what desktop search used to be on Linux. I think the developers are looking at one of my bug reports about a situation where Zeitgeist won't log, and hopefully the situation should improve before too long.

---

### Post by everytimeref on 2011-11-30
Stinkeye Thank you for that that's really useful.

Zeitgeist seems to be great for a new installation but really problematic for upgrades... and what about if I plug in external media. Dash won't search that for me either? What is the Zeitgeist search actually for.

---

### Post by stinkeye on 2011-11-30
As I understand it's a logger not a file indexer.
This may explain it a bit better.
[**_[COLOR="DarkRed"]zeitgeist-project[/COLOR]_**]("http://zeitgeist-project.com/about/")
The logs aren't collected by an outside source but there may be some things you
 don't want to show up in the recent files list of the dash, if others use your computer. 
You can manage what it logs with activity-log-manager from the 
[URL="https://launchpad.net/~zeitgeist/+archive/ppa"][B][U][COLOR="darkred"]Zeitgeist ppa
[/COLOR][/U][/B][/URL]
You can disable the logging completely but I have found it useful
to find a file I have used and can't remember where it was located.

---

