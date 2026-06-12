---
title: "can not start firefox-3.5"
date: 2009-08-11
forum: General Help
---

### Post by yescookie on 2009-08-11
After I update the Firefox to 3.5,When I start it,I'm gotten a error "The application has been updated but your version of SQLite is too old and the application cannot run."

I'm sure I have the SQLite3.

So....What can I do to save my Firefox~~~~~~~~~~~~~~~~

---

### Post by dcstar on 2009-08-12
> **yescookie said:**
> After I update the Firefox to 3.5,When I start it,I'm gotten a error "The application has been updated but your version of SQLite is too old and the application cannot run."

I'm sure I have the SQLite3.

So....What can I do to save my Firefox~~~~~~~~~~~~~~~~

SQLite is the database that Firefox uses, delete the firefox-3.5 profile and let it create a fresh one.

---

### Post by fluffman86 on 2009-08-12
actually, you probably won't need to kill the whole profile.  Instead, go to Places > Home Folder, press ctrl+H to show your hidden files, and navigate to /home/<username>/.mozilla/firefox

From here, you can delete anything ending in .sqlite without harming the rest of your profile.  If this doesn't work, *then* you may have to kill the profile per dcstar's suggestion.

---

### Post by dcstar on 2009-08-12
> **fluffman86 said:**
> actually, you probably won't need to kill the whole profile.  Instead, go to Places > Home Folder, press ctrl+H to show your hidden files, and navigate to /home/<username>/.mozilla/firefox

From here, you can delete anything ending in .sqlite without harming the rest of your profile.  If this doesn't work, *then* you may have to kill the profile per dcstar's suggestion.

If 3.5 does not have an existing profile it will attempt to import an existing 3.x profile, so you can basically delete any new 3.5 profile because it will always build another.

If you ever want a totally fresh 3.5 profile, you have to rename your existing firefox profile so it has nothing to use for a conversion (because sometimes existing 3.0 settings will stuff up 3.5 and stop things working correctly).

After 3.5 has created a totally fresh profile, you renames you old firefox profile back again so your 3.0 will work as it did previously.

---

### Post by lovinglinux on 2009-08-12
I agree with most suggestions posted above, since Firefox profiles get corrupted easily and deleting the profile or specific files related to some common problems usually fix it. Nevertheless, it seems to me that the problem is not a profile corruption, but a dependency issue. As the error report says: "The application has been updated but your version of SQLite is too old and the application cannot run."

Are you sure you have the newest SQLite version? Please notice that when you open Synaptic Package Manager and search for sqlite, you will see a package named sqlite3, which is not the package used by Firefox. This is a command-line SQLite tool, for querying the database from terminal. The SQLite package that Firefox (and a lot of other programs) uses is **libsqlite3-0**, which current version is **3.6.10-1ubuntu0.2**.

So check if you have the correct package and try to update your system. BTW, what release of Ubuntu are you using?

---

### Post by yescookie on 2009-08-13
Thanks all of above suggestions,I can start firefox-3.5 now~

---

### Post by Mr.R on 2009-08-29
> **yescookie said:**
> Thanks all of above suggestions,I can start firefox-3.5 now~
I encountered the same problem, how do you solve it&#65311;
   Thanks!

---

