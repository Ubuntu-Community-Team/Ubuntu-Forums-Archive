---
title: "Finding &quot;near-duplicate&quot; files"
date: 2012-06-12
forum: General Help
---

### Post by monkeytype on 2012-06-12
Apologies in advance, because this is probably easy! ... and likely to be explained already elsewhere...  It's really a general UNIX question rather than Ubuntu-specific.

Sometimes I find myself in the following, or an analogous, situation: I have a historic backup of a directory structure, rooted in path1, which is say
~/oldbackups/201106/
and I want to search through and delete (well, let's say list - then I'll pipe to rm) all files that are "near-duplicates" (see below) of files in path2, the directory that I originally backed up, which is say
~/backup/

For the test of whether a file is a near-duplicate, I want something very cheap and quick, but I'd like a few options available - depending e.g. on how close I am to just deleting the historic backup without checking anything.

So for a first cut, I might list and delete all files under path1 that have exactly the same name AND size as some file under path2 - though not necessarily the same position relative to the two trees' roots.  A next cut might be files with exactly the same name and relative position, but the file under path1 has smaller size AND earlier mod date than that under path2.  (Next I might do the same again but without the relative position condition, and then without the mod date condition either, by now probably doing manual checks as well before I delete - etc. etc.)

Many thanks for your help, all answers appreciated.

---

### Post by Terry of Astoria on 2012-07-22
That is a good idea. I would use that program. I want to weed out near-dupes from my video collection and music library. I haven't found one yet that is user-friendly (me being "user") :-)

---

