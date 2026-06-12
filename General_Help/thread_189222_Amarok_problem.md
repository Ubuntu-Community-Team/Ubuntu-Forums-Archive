---
title: "Amarok problem"
date: 2006-06-04
forum: General Help
---

### Post by drobvice on 2006-06-04
I installed amarok 1.4 and: 1)There was no icon installed to the applications menu like it has in the past and is not available in alacarte to add (could do it manually though).  2)When importing my library, it stops at 86% every time.  I think I had this problem before but solved it by deleting the amarokrc file and reimporting but that isn't happening.  3)I just tried to run amarok from terminal and it sits there with no message.  What's going on?

---

### Post by royg1234 on 2006-06-22
I'm getting the same problem, except at 32%.  And it freezes the computer.

---

### Post by blackjack6.21.91 on 2006-06-22
Try reinstall in terminal.  Does it fail?  If so, what does the terminal return.
> sudo apt-get update
sudo apt-get install -f
sudo apt-get remove amarok
sudo apt-get install amarok

By the way I'm not running Ubuntu right now so I'm not so sure amarok's package name is in fact "amarok".  Double check that one for me, guys.

Fish and chips,
blackjack

---

### Post by Dryer Lint on 2006-06-22
You probably have some defective file in your collection.

Try scanning it folder by folder (by moving them into the collection one by one) to isolate the file amaroK chokes on.

---

### Post by asimon on 2006-06-22
If the collection scanning stalls the last scanned file should be found in ~/.kde/share/apps/amarok/collection_scan.log .

Removing the last mentioned file in this log may let the scanning finish, maybe not...

Even if it's a defective file I think amarok should not hang while scanning the collection. Thus I say it's a bug.

Under KDE amarok has an icon in the menu. Maybe an issue with the new human icon theme?

---

