---
title: "Package Manager error?"
date: 2010-10-02
forum: General Help
---

### Post by Sakurafang17 on 2010-10-02
Hello, I'm brand new to the Ubuntu community. I know a few of the basics with Ubuntu, but this error completely went over my head.

[SIZE=1]This red button with a white dash across it appeared next to my wireless connection and when I hover my mouse over it it says this:
An error occured, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was: 'Error: Opening the cache (E:Malformed line 58 in source list /ect/apt/sources.list (dist parse), E:The list of sources could not be read.)' This usually means that your installed packages have unmet dependencies

So, I right click and click 'start package manager' and this pop up appears:
An Error Occured
The following details are provided:
E: Malformed line 58 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

What is the repository dialog?

Also, when I try to open a song with Rythmbox, it says that I need to search for a suitable plug in, but it just opens and immediately closes to Package Manager. Are these two related?

Some more information is that I attempted to download Java the other day and gave up half way before this error appeared. Could that have to do with this?

It isn't an incredibly big deal, but I'd just like to know what is going on, because I am utterly lost. 
[/SIZE]

---

### Post by Soul-Sing on 2010-10-02
: [http://ubuntuforums.org/archive/index.php/t-1084691.html](http://ubuntuforums.org/archive/index.php/t-1084691.html)

(you have to edit your sources.list)

---

### Post by snowpine on 2010-10-02
/etc/apt/sources.list is a file that holds your list of "software sources." You (or someone else with administrative access to your computer) "broke" this file by adding a malformed line 58. To edit the file:

```
gksu gedit /etc/apt/sources.list
```

Scroll down to line 58 and fix it. If you aren't sure what you did wrong, copy & paste it here and I'll take a look for you. :)

---

### Post by Sakurafang17 on 2010-10-02
Ok, I see what I did! (there was a space missing)
Thank you so much! I feel kind of silly now :)

---

### Post by Soul-Sing on 2010-10-02
please don't feel silly. Enjoy linux!

---

