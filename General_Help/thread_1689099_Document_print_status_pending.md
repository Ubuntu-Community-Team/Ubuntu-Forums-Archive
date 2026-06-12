---
title: "Document print status pending"
date: 2011-02-16
forum: General Help
---

### Post by krige on 2011-02-16
I have a problem with a network printer: every document I try to print it goes in the printing queue and there its status stays "pending" forever. Where could be the problem or where can I find clues to solve it?

---

### Post by quixote on 2011-02-17
Sound like you may need to get into the innards of cups and restart that printer.  To get at cups ("common unix printing system"), open your browser and in the address bar type ```
http://localhost:631
```You'll see a tab for "Printers".  Go there, find the bad printer in the list, and see if it isn't reported as stopped or something like that.  If so, all you need to do is hit the "restart" or "start" (don't remember) next to that printer's name.  

If cups shows no problems, then I'm not sure what to suggest from a computer perspective.  What I'd do then is go over to the printer and turn it off and then back on again.

If it's used by someone who also uses Windows, it'll sometimes set flags that cups interprets as saying the printer is paused or in use.

Postscript: If it is a simple matter of restarting, be sure to go to the "Jobs" tab first and dump all the duplicate jobs that are now pending, or you'll get all your re-tries printing out, one after the other....

---

