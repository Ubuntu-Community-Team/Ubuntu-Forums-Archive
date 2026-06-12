---
title: "Search command"
date: 2009-12-28
forum: General Help
---

### Post by RedSingularity on 2009-12-28
Hey guys,

I am looking for a good terminal command to search for both FILES and DIRECTORIES by a name.  Any ideas?

---

### Post by shendric on 2009-12-28
The "find" command should work for you.  The -d option will limit the search to directories, I believe.

---

### Post by lukeiamyourfather on 2009-12-28
The command "locate" will search a local database of all files and directories. Use "updatedb" to add new files and directories before searching. If you're not familiar with it, use "man locate" to get the full details. Cheers!

---

### Post by RedSingularity on 2009-12-28
Yeah i just tested it out (find) and it works the way i want it.  Thanks.  Now how can i search for hidden folders and files?

---

### Post by shendric on 2009-12-28
> **RedSingularity said:**
> Yeah i just tested it out (find) and it works the way i want it.  Thanks.  Now how can i search for hidden folders and files?

To find the hidden files from the CWD:

find ./ -name '.*'

That should find work.

---

### Post by RedSingularity on 2009-12-28
Ahh very good.  That works and 

find -name .example

works as well.  Thanks:)

---

### Post by Zoot7 on 2009-12-28
**locate **I find is the best one, only thing you have to do is run **sudo updatedb** to update the indexes every now and again.
A nice little frontend to both locate and find is Catfish which is in the repos.

---

### Post by shendric on 2009-12-28
> **Zoot7 said:**
> **locate **I find is the best one, only thing you have to do is run **sudo updatedb** to update the indexes every now and again.
A nice little frontend to both locate and find is Catfish which is in the repos.

My understanding is that locate is faster, but requires periodic updates, but that find takes longer but searches all current files and directories.  I like them both, but it's kind of annoying when I can't find something with locate, because the DB hasn't been updated.

I'll have to take a look at Catfish, sounds interesting!

---

### Post by RedSingularity on 2009-12-28
> **shendric said:**
> 

I'll have to take a look at Catfish, sounds interesting!


Me too!

---

### Post by Zoot7 on 2009-12-28
> **shendric said:**
> My understanding is that locate is faster, but requires periodic updates, but that find takes longer but searches all current files and directories.
Yup, that's about the long and short of it.

---

### Post by falconindy on 2009-12-28
FYI: locate's DB is updated nightly by a cron job. Of course, if your computer isn't on at midnight, this will never happen (and you might consider changing when **all** the daily cron jobs run).

---

### Post by dcstar on 2009-12-28
> **falconindy said:**
> FYI: locate's DB is updated nightly by a cron job. Of course, if your computer isn't on at midnight, this will never happen (and you might consider changing when **all** the daily cron jobs run).

Which is exactly why the **anacron** package is installed by default and things like this are run by it whenever you boot up.

---

