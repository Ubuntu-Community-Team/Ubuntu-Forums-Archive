---
title: "Firefox Error Console"
date: 2010-05-12
forum: General Help
---

### Post by Prognatus on 2010-05-12
Hi all,

After installing Lucid Lynx on a clean partition, as I usually do with all new releases, I had the idea of backing up my Firefox settings and stuff from the old installation with the Firefox plugin FEBE, to restore it into my new Firefox.

It didn't go so well.

I should've settled for just restoring the extentions, not settings and preferences too.  Below is a copy of the Error Console, right after startup of Firefox.  It seems something originally present (is it the Ubuntu One plugin?) was lost when I restored the FEBE files:

[img]http://photos.softace.com/d/1424-1/Screenshot-Firefox_Error_Console.png[/img]


Any help is greatly appreciated!

---

### Post by Prognatus on 2010-05-13
I think I've found out why this happen.  All files exists, but file permissions aren't retained (by FEBE).  The permissions on file level for the source (old backup) files aren't the same as the destination (new restore) files.

For instance regarding the first message in the list above, the .cvsignore file originally looked like this:

.cvsignore -r-x------ (0500)

...but after FEBE restore, it looks like this:

.cvsignore -rw-r--r-- (0644)

So, to make the story short: I'm restoring all the original file permissions to the new Firefox plugins, with the old files as a guide.  I'll report back with the result.

---

### Post by Prognatus on 2010-05-13
Yep, that did the trick.  Problem solved!

However, I get the message about "...potentially vulnerable to CVE-2009-3555" for virtually every open tab(!)  But I'll open a new thread for that problem.

EDIT: No need for that new thread, since the problem is a general design flaw of SSL/TSL:

[https://wiki.mozilla.org/Security:Renegotiation](https://wiki.mozilla.org/Security:Renegotiation)

---

