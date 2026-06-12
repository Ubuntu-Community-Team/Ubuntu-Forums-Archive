---
title: "Gnome 3 Search - how to update cache?"
date: 2011-11-17
forum: General Help
---

### Post by jabz on 2011-11-17
Hi, 
I'm using GNOME 3 on my Ubuntu 11.04. I need help, tuning the desktop search tool. 

I realized, that all files I've ever opened are findable through the GNOME 3 search utility. So far that is not bad.

What's bothering me is, that even deleted files and files from external (unavailable) sources (e.g. an external harddrive or usb stick) show up in the results. This means, the search results show files I cannot access. 

I stressed Google for some food 30 minutes to find a solution to update the cache or at least tune the indexing mechanism. 

Unfortunately, I'm not even sure what I am looking for. Gnome-search-tool? Tracker is not even installed on my system.
What is the underlaying technology of desktop search? I'm stuck.

Can anyone help?

Thanks.

---

### Post by Bonster on 2011-11-18
if you're using gnome-search-tool, u can update the database it using

> sudo updatedb

---

### Post by jabz on 2011-11-18
For me it is still unclear, which technology is used for gnome 3 search. I believe it's not gnome-search-tool.

However, at least I was able to clear the recent items (which cleared unavailable files from search results). I simply replaced the recently-used.xbel file with a recently-used.xbel directory.

However, I can still search and find deleted files. So the cache problem still exists. Main source of the problem seem sto be, that nobody knows how gnome 3 desktop search really works. 
There is also a discussion going on on identi.ca: [https://identi.ca/conversation/85345950#notice-85429752](https://identi.ca/conversation/85345950#notice-85429752)

---

### Post by Bonster on 2011-11-19
if u have 11.04 is probably **zeitgeist**, it a logger not really a search tool

---

