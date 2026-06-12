---
title: "Search by content of a file"
date: 2010-07-01
forum: General Help
---

### Post by techforay on 2010-07-01
According to the ubuntu pocket guide for 10.4 you should be able to search by content of a file per the pasted info below

Desktop search
Ubuntu offers a powerful desktop search tool in the form of Tracker.
Unlike standard file searching tools, Tracker is able to catalog the
contents of files such as PDFs or office documents, as well as their
filenames. This means you are able to search not only by filename, but
by key phrases that the document might contain.
To activate Tracker, click System &#61537; Preferences &#61537; Search and Indexing.
Put a check in the Enable Indexing and Enable Watching boxes. If
you’re using a notebook computer, you might also check Disable All
Indexing When on Battery. Click OK once done, and click the RESTART
button when prompted.

I can not find "search and indexing" in any list.

---

### Post by duanedesign on 2010-07-01
From a Terminal you can search the contents of files in a folder with the following command.


```
grep -i -R -l word folder/*
```


This would look for 'word' in all files in the 'folder' directory.

**UPDATE:** Here is some info on Tracker:

To install Tracker
```
sudo apt-get install tracker-search-tool
```

From the Tracker Preferences application, you can configure what you want to index

**References**
[https://help.ubuntu.com/community/MetaTracker](https://help.ubuntu.com/community/MetaTracker)
[http://projects.gnome.org/tracker/documentation.html](http://projects.gnome.org/tracker/documentation.html)

---

### Post by techforay on 2010-07-01
I am new to linux and I must be doing something wrong. I created a word doc with my name Diviney in the content.  I saved it to the desktop.  I typed a comand "grep -i -R -l Diviney Desktop/* and it did somthing and came back to prompt.

---

