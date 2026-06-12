---
title: "clementine media player gives error"
date: 2012-01-06
forum: General Help
---

### Post by lolpolt on 2012-01-06
When I try to start clementine I just get an error window that says:

   "LibraryBackend: database disk image is malformed Unable to fetch row"



I'm not good with computers and I have no idea what to do.. I hope someone can help me with this problem..


(I'm using ubuntu 11.10 (64-bit))

---

### Post by fizikz on 2013-04-22
I am getting this same error if I try to search the library through the search bar. Also, after doing a full library rescan, the following error shows up: 

"LibraryBackend: songs.mtime may not be NULL Unable to fetch row"

I'm not sure what caused it, but these errors showed up just recently. I've never had this problem before. It looks like it has to do with the library database, but beyond that I have no clue. Any ideas?

---

### Post by SeijiSensei on 2013-04-22
Have you tried forcing Clementine to rebuild its database?  I don't have a copy in front of me right now, but you can do it from Settings.

---

### Post by fizikz on 2013-04-22
I tried doing a full library rescan, and that is how I get the error mentioned in the OP. Is there another way to rebuild or fix the database?

---

### Post by SeijiSensei on 2013-04-22
Not that I know of. You could try renaming the current database file and building it from scratch, I suppose.

---

### Post by fizikz on 2013-04-22
I could give that a try. Where is the database located?

---

### Post by SifGrey on 2013-04-22
[COLOR=#000000][FONT=arial]"On [/FONT][/COLOR]**Linux**[COLOR=#000000][FONT=arial]: [/FONT][/COLOR]~/.config/Clementine/clementine.db" 
Source: [https://code.google.com/p/clementine-player/wiki/FAQ](https://code.google.com/p/clementine-player/wiki/FAQ)

---

### Post by fizikz on 2013-04-22
Thanks. I renamed the database file and tried restarting Clementine, but it fails with the following output (in a terminal):

```
17:23:09.724 DEBUG NetworkProxyFactory:30           Detected system proxy URLs: ("", "", "", "") 
17:23:09.725 DEBUG CoverProviders:34                Registered cover provider "Amazon" 
17:23:12.303 INFO  Database:578                     Updating "songs" for %allsongstables 
17:23:12.303 INFO  Database:578                     Updating "magnatune_songs" for %allsongstables 
17:23:12.304 INFO  Database:578                     Updating "jamendo.songs" for %allsongstables 
17:23:12.304 ERROR Database:625                     db error:  QSqlError(1, "Unable to execute statement", "duplicate column name: skipcount") 
17:23:12.304 ERROR Database:626                     faulty query:  "ALTER TABLE jamendo.songs ADD COLUMN skipcount INTEGER NOT NULL DEFAULT 0" 
17:23:12.304 ERROR Database:627                     bound values:  QMap() 
17:23:12.304 ERROR unknown                          Unable to update music library database 
Aborted (core dumped)

```

Any ideas?

---

### Post by SifGrey on 2013-04-22
Might it be possible that you've edited the file extensions when renaming the files?

---

### Post by SifGrey on 2013-04-22
I've noticed there's another thread with a similar and probably the same issue:
[http://ubuntuforums.org/showthread.php?t=2092249](http://ubuntuforums.org/showthread.php?t=2092249)

Keep updating the thread when you've made any progress.

---

### Post by fizikz on 2013-04-22
That thread gave me the clues I needed. I think I've fixed my problem.

I noticed that I got the errors in my previous post and the Clementine crash after renaming the clementine.db (to something like clementine.db.bak) but not the jamendo.db. So, I renamed both, and I did not get those errors anymore when starting Clementine. Then, I had to reselect the directory where the library is found, and did a full library scan. No errors this time, and everything works fine. 

Smooth sailing once more! Thanks for the help.

---

### Post by SifGrey on 2013-04-23
I'm glad the problem is solved. Please edit this thread to 'Solved' once you're satisfied with it.

---

### Post by Elfy on 2013-04-23
> **SifGrey said:**
> I'm glad the problem is solved. Please edit this thread to 'Solved' once you're satisfied with it.

It's only the OP and staff can mark threads solved - not someone who's added things afterwards.

---

### Post by SifGrey on 2013-04-23
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads) 
I have my own thread in which I can do the exact same thing as is described on this page so how does it work then?

Add to that:
[http://ubuntuforums.org/showthread.php?t=2137855](http://ubuntuforums.org/showthread.php?t=2137855) I've marked this thread as 'SOLVED'. Does that only appear as solved to me?

---

### Post by Elfy on 2013-04-23
> **SifGrey said:**
> [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads) 
I have my own thread in which I can do the exact same thing as is described on this page so how does it work then?

Add to that:
[http://ubuntuforums.org/showthread.php?t=2137855](http://ubuntuforums.org/showthread.php?t=2137855) I've marked this thread as 'SOLVED'. Does that only appear as solved to me?

That is your thread - this thread is not fizikz's.

---

### Post by SifGrey on 2013-04-23
I see now. I thought it was.

---

### Post by SifGrey on 2013-04-23
Have you tried deleting the Clementine database and doing a library scan yet, lolpolt?
It might have become corrupt after the application closed abruptly.
The databse can be found at ~/.config/Clementine/clementine.db.

---

### Post by Elfy on 2013-04-23
Closed.

If the OP comes back after 15 months thye'd be best with a new thread.

---

