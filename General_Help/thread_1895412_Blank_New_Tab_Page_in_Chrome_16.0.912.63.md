---
title: "Blank New Tab Page in Chrome 16.0.912.63"
date: 2011-12-14
forum: General Help
---

### Post by Joseph Schwenker on 2011-12-14
I'm on Ubuntu 11.04 32-bit with Google Chrome 16.0.912.63, and I launch Google Chrome with a special command to use Chrome's old new tab page so I don't have to click an extra time to open a recently closed tab.
```
/opt/google/chrome/google-chrome --new-tab-page %U
```

When I opened Chrome today, the new tab page was blank, and had a scroll bar on the side that could be scrolled slightly up and down. When I remove --new-tab-page from Chrome's launch command, I get the new new tab page. When ran in the terminal, Chrome outputs:

```
joseph@joseph:/opt/google/chrome$ ./google-chrome --new-tab-page

(google-chrome:5160): IBUS-WARNING **: Connect to unix:abstract=/tmp/dbus-oK7kSzxRen,guid=680334b76346d0d38c98efde00000016 failed: Failed to connect to socket /tmp/dbus-oK7kSzxRen: Connection refused.
[5160:5160:1570796051:ERROR:CONSOLE(5372)] "Uncaught TypeError: Cannot read property 'offsetHeight' of null", source: chrome://newtab/ (5372)
[5160:5160:1570796167:ERROR:CONSOLE(5372)] "Uncaught TypeError: Cannot read property 'offsetHeight' of null", source: chrome://newtab/ (5372)
[5160:5160:1570796208:ERROR:CONSOLE(6331)] "Uncaught TypeError: Cannot call method 'updateSettingsLink' of undefined", source: chrome://newtab/ (6331)
[5160:5160:1570796235:ERROR:CONSOLE(4984)] "Uncaught TypeError: Cannot call method 'getString' of undefined", source: chrome://newtab/ (4984)
[5160:5160:1570797542:ERROR:CONSOLE(7179)] "Uncaught TypeError: Cannot call method 'getString' of undefined", source: chrome://newtab/ (7179)
[5160:5160:1585476216:ERROR:CONSOLE(6331)] "Uncaught TypeError: Cannot call method 'updateSettingsLink' of undefined", source: chrome://newtab/ (6331)

```

Can anyone else reproduce this problem?

---

### Post by Joseph Schwenker on 2011-12-16
The problem does not exist in Chromium, though that could be due to the fact that the version of Chromium I have installed - 15.0.874.121 (Developer Build 109964 Linux) - is significantly older than the version of Chrome I have installed.

I've reported the problem to Google through the Help>Report an Issue... menu, and [I've started a thread]("http://www.google.com/support/forum/p/Chrome/thread?tid=7a405a9cd258b575&hl=en") on the official Google Chrome help forum.

---

### Post by Joseph Schwenker on 2011-12-18
Apparently, the flag --new-tab-page has been removed, hence the blank page. I'll leave this thread unsolved, however, as I would still like the old new tab page back with recently closed tabs and windows at the bottom of the page.

---

### Post by vasa1 on 2011-12-18
> **Joseph Schwenker said:**
> ..., and [I've started a thread]("http://www.google.com/support/forum/p/Chrome/thread?tid=7a405a9cd258b575&hl=en") on the official Google Chrome help forum.
Just curious ... but was it you who marked the respondent's answer unhelpful? Sometimes, the answer may not be what we want to hear but it is the correct answer. In which case, **IMHO**, it is not fair to mark the answer as unhelpful as whoever has done.

---

### Post by Joseph Schwenker on 2011-12-18
> **vasa1 said:**
> Just curious ... but was it you who marked the respondent's answer unhelpful? Sometimes, the answer may not be what we want to hear but it is the correct answer. In which case, **IMHO**, it is not fair to mark the answer as unhelpful as whoever has done.

I don't think I did. Then again, I don't always remember which buttons I press. I just clicked "Yes" to give the guy more credit for responding with a good answer.

---

