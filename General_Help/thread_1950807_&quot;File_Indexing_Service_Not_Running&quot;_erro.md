---
title: "&quot;File Indexing Service Not Running&quot; error"
date: 2012-04-01
forum: General Help
---

### Post by bcasanov on 2012-04-01
Hello,

I have Kubuntu Oneiric and have the Kubuntu ppa installed so that I can get KDE 4.8.  I have a problem with the file indexing service Nepomuk in that when I hover over the Desktop Search File Indexing panel icon it says "File indexing service not running."  When I right-click on it and choose "Configure File Indexing" I get the Desktop Search configuration window and under Nepomuk Desktop File Indexer, I have it enabled, but there is the same message "File indexing service not running" in bold underneath.  What can I do to really enable file indexing?

Thank you.

---

### Post by 2F4U on 2012-04-01
Did you verify in System Settings (Personal Settings or Configure Desktop) -> Desktop Search that &#8220;Enable Nepomuk Semantic Desktop&#8221; and &#8220;Enable Strigi Desktop File Indexer&#8221; are checked?

---

### Post by bcasanov on 2012-04-01
Yes, &#8220;Enable Nepomuk Semantic Desktop&#8221; is checked and &#8220;Enable Nepomuk Desktop File Indexer&#8221; is checked.  There is no &#8220;Enable Strigi Desktop File Indexer&#8221; option.

---

### Post by bcasanov on 2012-04-02
Bump.

---

### Post by Perey on 2012-05-06
I had the same problem (KDE 4.8 on Precise, rather than from a PPA). The nearest thing I could find to an answer was that the Nepomuk database might be corrupt and it should be deleted.

If you go to System Settings > Desktop Search and click "Details..." under Nepomuk Semantic Desktop, does it say "Indexed Files: Calculating..." and never actually give you a number? That's what happened for me, and that strongly suggests a bad database is the problem. Here's how I fixed it.

[LIST=1]
[*]Stop the Nepomuk service. In System Settings > Desktop Search, uncheck "Enable Nepomuk Semantic Desktop".
[*]The database is located under ~/.kde/share/apps/nepomuk/, so you'll want to move that directory somewhere else (or delete it outright). From a command line, run:```
mv ~/.kde/share/apps/nepomuk /tmp/nepomuk_problems
```
[*]Restart the Nepomuk service (same as step 1, except check the box, instead of unchecking it).
[/LIST]

Hopefully you'll see the indexer start up shortly thereafter. If it works, you can delete the old database:```
rm -rf /tmp/nepomuk_problems
```
If not, you can put the old database back with:```
mv /tmp/nepomuk_problems ~/.kde/share/apps/nepomuk
```

(About Strigi: Like you, I noticed that the indexer is now called "Nepomuk File Indexer", not "Strigi File Indexer", in the settings dialog. And I found that the package strigi-daemon wasn't even installed. I wonder, have they just rebranded Strigi and rolled it into Nepomuk, or has it actually been replaced?)

---

### Post by Perey on 2012-05-13
So the problem just reoccurred for me. At least I can confirm my previous steps worked successfully to fix it again. :)

I don't remember seeing this before, but this time around the problem was heralded by the following notification popping up:> Nepomuk Semantic Desktop needs the Virtuoso RDF server to store its data. Installing the Virtuoso Soprano plugin is mandatory for using Nepomuk.

Now, I double checked that Virtuoso (package virtuoso-minimal) was definitely installed. It appears to have simply died when hitting some database error, leaving Nepomuk thinking that Virtuoso wasn't available. The question remains, **why is Virtuoso dying?** What's going wrong with the database? Where can I find some log files?

The only log file I can locate is ~/.kde/share/apps/nepomuk/repository/main/data/virtuosobackend/soprano-virtuoso.log, which has several entries all but identical to this over the past few days:
>                 Sat May 12 2012
15:58:42 Malformed data received from IP [0.0.0.0] : Bad incoming tag 166. Disconnecting the client
15:58:42 Invalid log entry in replay. Delete transaction log /home/redacted/.kde/share/apps/nepomuk/repository/main/data/virtuosobackend/soprano-virtuoso.trx or truncate at point of error. Valid data may exist after this record. A log record begins with bytes 193 188 5 188 0. Error at offset 8193
15:58:42 Searching for the next valid header signature starting at 8194
15:58:42 No valid looking header found.
That's not particularly helpful.

If anyone knows something, please do tell. Otherwise I'll see if I can find some answers out on the web, and I'll share anything I do discover.

**EDIT:** It may be sufficient to delete the file soprano-virtuoso.trx that was mentioned in the log entry. See [https://bugs.kde.org/show_bug.cgi?id=284747](https://bugs.kde.org/show_bug.cgi?id=284747)

---

### Post by Perey on 2012-05-29
Okay, so it happened again. This time, it was heralded by the "An application has crashed" notification, which told me that "KNetAttach" had crashed. In the details it clarified that /usr/bin/nepomukserver had crashed.

Deleting just soprano-virtuoso.trx **did not work**. However, removing the folder ~/.kde/share/apps/nepomuk/repository/main/data/virtuosobackend/ (rather than the entirety of ~/.kde/share/apps/nepomuk/) **did** work. I think. The file indexer is running, but "Indexed files" is stuck at "Calculating..." as previously reported.

*sigh*

---

### Post by Perey on 2012-06-03
And again -- but this time, deleting just soprano-virtuoso.trx **did work**. Once I re-enabled Nepomuk, it reappeared and very quickly grew from a few hundred bytes to 16 or so megabytes. All's well so far and it's still got the old database.

I also peeked at the end of the old .trx file, and through the binary noise I thought I could make out the name of the file it had last tried to index. I've removed that directory from those to be indexed (not an important one anyway), and am waiting to see if that avoids future crashes. If it does, I'll have to see if I can conclusively prove what file caused the indexer to crash, and report it... somewhere...

---

### Post by aSystemOverload on 2012-11-10
> **Perey said:**
> And again -- but this time, deleting just soprano-virtuoso.trx **did work**. Once I re-enabled Nepomuk, it reappeared and very quickly grew from a few hundred bytes to 16 or so megabytes. All's well so far and it's still got the old database.
.

Hi, just to add.  I'm running Linux Mint 12, and I stopped being able to search for most of my files with QuickSand.

I stopped the service [akonadictl stop].
Deleted [ ~/.kde/share/apps/nepomuk/repository/main/data/virtuosobackend/soprano-virtuoso.trx ]
Deleted [ ~/.kde/share/apps/nepomuk/repository/main/data/soprano-virtuoso.trx ]
Started the service [akonadictl start] and after few seconds the .trx file in /data re-appeared and increased to 2MB+, I tried QuickSand and I could see my files once more...

Thanks.!

---

