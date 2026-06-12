---
title: "How do you search for files ?"
date: 2011-07-02
forum: General Help
---

### Post by birkopf on 2011-07-02
Just a quick question. I usually search for files by build in Search function or Midnight Commander. Currently I have a problem. Looks like that:


I want to find all files with extension .cmc

One file is on my desktop and it's called File.cmc

I search in whole File System with option *.cmc 

Nothing is being found :(

What could be causing it ?

---

### Post by TeoBigusGeekus on 2011-07-02
```
find / -iname "*.cmc" 2>/dev/null
```
```
man find
```
for more info

---

### Post by jim_deadlock on 2011-07-02
```
sudo updatedb
sudo locate .cmc
```

updatedb makes a list of all the files in your entire filesystem, it takes a couple of minutes, then locate searches that list, it's very quick and very thorough and will find any part of the file's path.

---

### Post by birkopf on 2011-07-02
> **jim_deadlock said:**
> ```
sudo updatedb
sudo locate .cmc
```

updatedb makes a list of all the files in your entire filesystem, it takes a couple of minutes, then locate searches that list, it's very quick and very thorough and will find any part of the file's path.

Thanks. That worked ;)

- But how to explain that normal system search is not finding a file which is on my Desktop as well as Midnight Commander which never failed me before... ? :(

In fact I had this problem on one Maverick... After install it works like a charm and after time it stops.

---

### Post by WorMzy on 2011-07-02
btw, you don't need to use sudo with locate, just updatedb.

Can't explain your problem with MC, I don't use it. ;)

---

### Post by beew on 2011-07-02
> **birkopf said:**
> Thanks. That worked ;)

- But how to explain that normal system search is not finding a file which is on my Desktop as well as Midnight Commander which never failed me before... ? :(

In fact I had this problem on one Maverick... After install it works like a charm and after time it stops.

This is crazy but to use  "search for files" you need to go to gconf-editor, open apps > gnome-search-tool and disable (uncheck) quick search.

Don't ask me why. I have been doing this since 10.04 and once "quick search" is disable it can find anything.

---

### Post by birkopf on 2011-07-04
> **beew said:**
> This is crazy but to use  "search for files" you need to go to gconf-editor, open apps > gnome-search-tool and disable (uncheck) quick search.

Don't ask me why. I have been doing this since 10.04 and once "quick search" is disable it can find anything.

It is exactly what I was thinking about! Just was too strange to name it and you did it. Great! 

I couldn't believe when I saw my config there! Path to look for was pointing wrong, a lot of folders excluded by default, and other issues. 

Just want to mention before closing the topic that in my case its
*disable_quick_search* that needs to checked (ticked)

---

