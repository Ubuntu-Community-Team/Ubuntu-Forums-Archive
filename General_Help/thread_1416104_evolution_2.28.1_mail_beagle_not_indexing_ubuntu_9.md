---
title: "evolution 2.28.1 mail beagle not indexing ubuntu 9.10"
date: 2010-02-25
forum: General Help
---

### Post by abecrab on 2010-02-25
I've just imported my thunderbird email into Evolution, to try Beagle.
(Thunderbird beagle does subjects only.)
Evolution mail and data-server are enable in search/preferences/data sources.

.beagle/Log contains 2010-02-25-21-00-46-Beagle, which has:

20100225 21:01:54.2808 04782 Beagle DEBUG: Starting Evolution mail backend
20100225 21:01:54.2810 04782 Beagle DEBUG: Starting mail crawl
20100225 21:01:54.3071 04782 Beagle DEBUG: Mail crawl finished
20100225 21:01:54.3073 04782 Beagle DEBUG: Evolution mail driver worker thread done in .03s

But I don't think that's found any email.
Just after that I see the dataserver:
20100225 21:01:54.3150 04782 Beagle DEBUG: Scanning EDS sources (Addressbook, Calendars, Memos, ...)
20100225 21:01:54.4632 04782 Beagle DEBUG: Skipping remote addressbook couchdb://127.0.0.1
20100225 21:01:54.5461 04782 Beagle DEBUG: Getting addressbook changes for file:///home/abe/.evolution/addressbook/local/system
20100225 21:01:54.5668 04782 Beagle DEBUG: Addressbook file:///home/abe/.evolution/addressbook/local/system: 0 added, 0 changed, 0 removed
20100225 21:01:54.5832 04782 Beagle DEBUG: Getting calendar changes for file:///home/abe/.evolution/calendar/local/system
20100225 21:01:54.6868 04782 Beagle DEBUG: Calendar file:///home/abe/.evolution/calendar/local/system: 0 added, 0 changed, 0 removed
20100225 21:01:54.8647 04782 Beagle DEBUG: Getting calendar changes for contacts:///
20100225 21:01:54.8654 04782 Beagle DEBUG: Calendar contacts:///: 0 added, 0 changed, 0 removed
20100225 21:01:54.8751 04782 Beagle DEBUG: Getting calendar changes for file:///home/abe/.evolution/tasks/local/system
20100225 21:01:54.9667 04782 Beagle DEBUG: Calendar file:///home/abe/.evolution/tasks/local/system: 0 added, 0 changed, 0 removed
20100225 21:01:54.9769 04782 Beagle DEBUG: Getting calendar changes for file:///home/abe/.evolution/memos/local/system
20100225 21:01:55.1010 04782 Beagle DEBUG: Calendar file:///home/abe/.evolution/memos/local/system: 0 added, 0 changed, 0 removed
20100225 21:01:55.1169 04782 Beagle DEBUG: Scanned EDS sources in .80s

and I can search the calendar - so that bit works.

The IndexHelper logfile has
20100225 21:08:58.5751 05152 IndexH DEBUG: Helper Size: VmRSS=19.2 MB, size=1.59, 14.8%
20100225 21:10:49.2024 05152 IndexH DEBUG: Optimizing EvolutionMailIndex
20100225 21:10:49.2079 05152 IndexH DEBUG: EvolutionMailIndex optimized in .00s
20100225 21:10:49.6808 05152 IndexH DEBUG: Helper Size: VmRSS=19.2 MB, size=1.59, 14.8%

which also suggests no mail found.

Looking in the mail index directory:
[EMAIL="abe@abe-laptop:%7E/.beagle"]abe@abe-laptop:~/.beagle[/EMAIL]/Indexes/EvolutionMailIndex$ ls -altr *
-rw-r--r-- 1 abe abe    5 2010-02-24 17:28 version
-rw-r--r-- 1 abe abe   23 2010-02-24 17:28 fingerprint

PrimaryIndex:
total 16
-rw-r--r-- 1 abe abe   20 2010-02-24 17:28 segments.gen
-rw-r--r-- 1 abe abe   20 2010-02-24 17:28 segments_1
drwxr-xr-x 2 abe abe 4096 2010-02-24 17:28 .
drwxr-xr-x 5 abe abe 4096 2010-02-24 17:28 ..

SecondaryIndex:
total 16
-rw-r--r-- 1 abe abe   20 2010-02-24 17:28 segments.gen
-rw-r--r-- 1 abe abe   20 2010-02-24 17:28 segments_1
drwxr-xr-x 2 abe abe 4096 2010-02-24 17:28 .
drwxr-xr-x 5 abe abe 4096 2010-02-24 17:28 ..

Locks:
total 8
drwxr-xr-x 5 abe abe 4096 2010-02-24 17:28 ..
drwxr-xr-x 2 abe abe 4096 2010-02-25 21:10 .


and the version is:
[EMAIL="abe@abe-laptop:%7E/.beagle"]abe@abe-laptop:~/.beagle[/EMAIL]/Indexes/EvolutionMailIndex$ cat version
19.5


Evloution email is stored in mbox type files imported from Thunderbird:

[EMAIL="abe@abe-laptop:%7E/.evolut"]abe@abe-laptop:~/.evolut[/EMAIL]ion/mail$ ls -l
total 28
drwxr-xr-x 2 abe abe 4096 2010-02-25 21:17 config
drwx------ 3 abe abe 4096 2010-02-21 17:30 imap
drwxr-xr-x 2 abe abe 4096 2010-02-25 21:52 local
drwx------ 4 abe abe 4096 2010-02-21 17:35 pop
-rw------- 1 abe abe   68 2010-02-24 21:59 searches.xml
drwx------ 2 abe abe 4096 2010-02-24 21:59 vfolder
drwxr-xr-x 2 abe abe 4096 2010-02-24 13:13 views

local contains all the files.

pop - I think that has sqlite stuff, but not sure.


Is there some config that beagle uses to find the emails, and it's missing them?  How do I configure the beagle mail searcher or should I check it somehow?

Any suggestions??

Thanks for any help -

Regards,

Abe

---

### Post by abecrab on 2010-02-27
I didn't have extended attributes on the filesystem, which is ext4.

user_xattr added.

I'm not sure what the extended attributes are used for, but I assume Beagle *adds* something, so I don't see how they'd have prevented indexing.

I renamed the mail index directory to provoke regeneration.

Still no change.

---

### Post by engellion on 2010-03-20
I have the same problem.  Beagle is not indexing emails.  No search results show for Evolution emails. These are emails received directly by Evolution.  Evolution Contacts and Calendar events are OK. Just Emails are not being searched.

Please help.

I have Ubuntu 9.10, Beagle 0.3.9, Evolution 2.28.1

Thanks.

PS: EvolutionDataServer is showing 995. But no search results for email are returned. It just says 0 on the results screen for Evolution.

---

