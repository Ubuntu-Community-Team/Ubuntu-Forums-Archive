---
title: "&quot;Search for Files&quot; doesn't find known files"
date: 2012-06-17
forum: General Help
---

### Post by fester225 on 2012-06-17
Precise (12.04)

I just ran Search for Files to find known files, it didn't find them.

The files in question are on my main drive, and the searches were done on "File System". I added "Show hidden and backup files", but that didn't help.

Considering my first searches took no longer than the time it took to press the Enter button, I'm guessing "Search for Files" is only checking the root directory.

What should I do to get "Search for Files" to search the whole drive?

---

### Post by adroitster on 2012-06-18
Are you talking about the search option in Nautilus ? 

After you search for any file using 'search for files' it will present you with search results (if it didn't find anything then the window will be blank). Here you can change the location it's searching in and select your specific partition for it. You can click the '+' button and add the file type you are looking for.

---

### Post by marinerojoven on 2012-07-16
> **adroitster said:**
> Are you talking about the search option in Nautilus ? 

After you search for any file using 'search for files' it will present you with search results (if it didn't find anything then the window will be blank). Here you can change the location it's searching in and select your specific partition for it. You can click the '+' button and add the file type you are looking for.

But search for known files (that is I know where they are and can see them)  still yields a blank page.  Searching for known file to try to solve this problem.:popcorn:

---

### Post by marinerojoven on 2012-07-16
Found problem...doesn't like wild cards such as *pdf

---

### Post by philinux on 2012-07-16
> **marinerojoven said:**
> Found problem...doesn't like wild cards such as *pdf

Yes it seems to put it's own wildcard in.

---

### Post by andrew.46 on 2012-07-17
You could do worse than spend a little time getting to know my old friend *find*:

[https://help.ubuntu.com/community/find](https://help.ubuntu.com/community/find)

---

