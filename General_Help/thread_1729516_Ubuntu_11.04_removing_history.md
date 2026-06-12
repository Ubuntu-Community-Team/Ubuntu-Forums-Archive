---
title: "Ubuntu 11.04 removing history"
date: 2011-04-15
forum: General Help
---

### Post by jabo5360 on 2011-04-15
[SIZE=2]**Ubuntu 11.04 Removing History**[/SIZE]

Iv'e seen some similar posts but not this specific on.  In the new 11.04 on the apps doc panel on the left hand side there is a button called **[COLOR=Blue]"Files & Folders[/COLOR]**", when clicked on it brings up 

[LIST=1]
[*]recent
[*]downloads
[*]favorites
[/LIST]
Is there a way to clear the history, maybe disable it altogether or at the very least limit the amount of history it retains?  I am very sure other people will want an answer to that as well
>  Thanks

---

### Post by r-senior on 2011-04-15
The history comes from Zeitgeist, so clearing and controlling history is down to controlling that.

For example:

[http://www.webupd8.org/2010/12/how-to-clear-zeitgeist-history-quick.html](http://www.webupd8.org/2010/12/how-to-clear-zeitgeist-history-quick.html)

I've never tried that, by the way, and I'm not sure how Unity would respond to disabling Zeitgeist. I have used the activity journal:

[http://askubuntu.com/questions/31918/deleting-last-few-hours-of-zeitgeist-history-like-in-firefox](http://askubuntu.com/questions/31918/deleting-last-few-hours-of-zeitgeist-history-like-in-firefox)

Package for the activity journal is gnome-activity-journal.

---

### Post by jabo5360 on 2011-04-15
r-senior
That sorta was the right idea the file did contain some recent activity data but deleting did nothing.  Unfortunately the activity journal does not appear to work with unity yet anyway.  Hopefully I will get an answer to my quandary, I am sure that I am not the only one who will need this addressed

---

### Post by r-senior on 2011-04-15
> **jabo5360 said:**
> Unfortunately the activity journal does not appear to work with unity yet anyway.
Did it just crash? It did when I tried it on 11.04 (when I say I've used it, that was on 10.10 I think). There are no bug reports for it though.

I think that is the way to do it, unless someone knows otherwise?

---

### Post by jabo5360 on 2011-04-15
After doing the updates today and restarting the computer "Activity Journal" worked.
Though I can only seem to remove one item at a time.  So I removed just the sensitive items like client profiles, ip addresses login information etc. though these are in hidden folder they still show up in that list after being used.  Will take way to long to delete all 600+ items.  Hopefully there will be an easier solution forthcoming.  But I am sure you are right the Zeitgeist is the answer I think I just have to find the right log files and / or journal

---

### Post by PratterFak on 2011-04-29
I did the following which stopped new entries from being added:

rm ~/.local/share/recently-used.xbel 
touch ~/.local/share/recently-used.xbel 
sudo chattr +i ~/.local/share/recently-used.xbel

Then I did the following that cleared all the entries that were in there:

rm ~/.local/share/zeitgeist/activity.sqlite 
zeitgeist-daemon --replace


Now there is no longer even a Recent area when I click files and folders. Hope this helps :)

---

### Post by trikster_x on 2011-06-09
Thanks for the solution PratterFak.  In case anyone was curious, that also takes care of the history for Totem movie player.

Here is a script version for those who don't want to completely disable the history function:

```

#! /bin/bash

DELPATH=/home/USERNAME/.local/share

rm $DELPATH/recently-used.xbel
touch $DELPATH/recently-used.xbel
rm $DELPATH/zeitgeist/activity.sqlite
zeitgeist-daemon --replace

```

This just leaves out the part that changes the recently-used file to immutable.  Now clearing your history is just a double-click away :D

---

