---
title: "Grsync Excusions?"
date: 2010-09-13
forum: General Help
---

### Post by 2CV67 on 2010-09-13
I am still struggling with implementing my exclusions, from this thread:
[http://ubuntuforums.org/showthread.php?t=1570758](http://ubuntuforums.org/showthread.php?t=1570758)

Backups via Grsync are OK, but I want to exclude a bunch of hopefully-useless stuff, like thumbnails, trash, cache etc.

It looks easy here:
[http://www.pclinuxos.com/forum/index.php?topic=72371.0](http://www.pclinuxos.com/forum/index.php?topic=72371.0) (last post)
[http://www.wilderssecurity.com/showthread.php?t=246629](http://www.wilderssecurity.com/showthread.php?t=246629)

So I had a first attempt, to exclude the ".thumbnails" folder.
I created a text file "exclusions" in "/home/me/.grsync".
In that file, I wrote "-.thumbnails/".
In Grsync Advanced Options, I wrote "--exclude-from=/home/me/.grsync/exclusions".
Simulation results showed no red errors but no good results.
Execution showed the .thumbnails folder still present.

I tried manually deleting the .thumbnails folder from the backup & rerunning Grsync, but it puts all the thumbnails back.

I changed the "exclusions" file to say just "-.thumbnails" (I really am not familiar with CLI syntax) but that does not work either.

Thanks for any explanations/suggestions!

---

### Post by ajgreeny on 2010-09-13
Delete the - and trailing / (and the " " if you have them in the file, though I suspect they just show in your post here, not in the file) from the folder name in your exclusions file and it should work OK.  It is certainly working for me with no problems at all.

The one other difference I can see is that my txt file is called **exclude.txt**, ie it has the .txt suffix in the name, though I would not expect that to make any difference.

Here's my exclude.txt file as an example:-
> .thumbnails
Videos

---

### Post by 2CV67 on 2010-09-13
Thanks for your suggestions!

The "" are not in the file, just in the post.
I removed the leading - & trailing / so my exclusions file now contains just > .thumbnails
Still no good...

I added > .txt to the exclusions file name & to the Grsync Options line.
Still no good...

I tried a trailing / in case it was needed as .thumbnails is a directory (I am floundering here).
Still no good.

I suppose I have made a tiny stupid error somewhere (a - or a /), but how to find where?

---

### Post by ajgreeny on 2010-09-13
OK, now try renaming the file as mine is **exclude.txt**; perhaps the name is important.

Also make sure you have the letter case in the names of the folders excluded, and the file name correct, as linux is case sensitive.

If that does not work, I am totally baffled.  I've just done a simulation of my backup to double check and all works as it should.

---

### Post by 2CV67 on 2010-09-13
Thanks for your continuing interest.
Your warnings about case & any other detail are very welcome, though I don't think case or spelling are my problems this time...

I renamed the file to exclude.txt as you suggested, but still no action.

In case there is something else obviously wrong, I include some screenshots.

What else could help diagnosis?

[IMG]http://i838.photobucket.com/albums/zz309/2CV67/Grsync.png[/IMG]
[IMG]http://i838.photobucket.com/albums/zz309/2CV67/exclude.png[/IMG]
[IMG]http://i838.photobucket.com/albums/zz309/2CV67/contents.png[/IMG]
[IMG]http://i838.photobucket.com/albums/zz309/2CV67/thumbnails.png[/IMG]

Thanks!

---

### Post by DeMus on 2010-09-13
Instead of using a file try this:
In Grsync type ```
--exclude .thumbnails
```
and see what it does then. This works fine for me.

---

### Post by 2CV67 on 2010-09-13
Thanks again for all these suggestions!

In the meantime, I found a pretty comprehensive man page for rsync: [http://samba.anu.edu.au/ftp/rsync/rsync.html](http://samba.anu.edu.au/ftp/rsync/rsync.html)
 - comprehensive, but not simple enough for me...

I tried DeMus' suggestion & it did not SEEM to work.

Then, from the man page, I tried adding a / after .thumbnails & that didn't seem to work either.

At that point & with those settings, I decided to manually remove the .thumbnails folder from my backup & try Grsync again.
I had already done this once or twice previously, with no success.

Aha!
This time, the thumbnails were NOT copied over to my backup. :)
I have slowly back-tracked through all the previous steps & they all "work" (don't copy over .thumbnails) until I re-introduce the "-" in front of .thumbnails in my exclusions file.

But none of these solutions actually REMOVE thumbnails once they are in the backup, even with "Delete on destination" checked.
They just ignore the folder.

Is that how it is supposed to be?
You can't introduce exceptions & expect them to be removed from an existing backup?

Summary of (good) Additional Options which do not copy thumbnails to backup:
"--exclude .thumbnails"
"--exclude .thumbnails/"
"--exclude-from=/home/me/.grsync/exclude.txt" where "exclude.txt" contains ".thumbnails"
"--exclude-from=/home/me/.grsync/exclude" where "exclude" contains ".thumbnails"
"--exclude-from=/home/me/.grsync/exclusions" where "exclusions" contains ".thumbnails"

(Bad) Additional Option which does copy .thumbnails to backup:
"--exclude-from=/home/me/.grsync/exclusions" where "exclusions" contains "-.thumbnails"

So I suppose I can now add other unwanteds to my exclusions file (without "-") but then I need to wipe the whole backup before running Grsync?

Thanks again for your patience & suggestions!

---

### Post by QLee on 2010-09-13
[QUOTE=2CV67]...
But none of these solutions actually REMOVE thumbnails once they are in the backup, even with "Delete on destination" checked.
They just ignore the folder.

Is that how it is supposed to be?
You can't introduce exceptions & expect them to be removed from an existing backup?
...[/QUOTE]

Correct, it functions as it is supposed to.

Think for a moment, when you "exclude" something from rsync, that means it is not copied from source to destination. So, if you have the target folder or file on the source, it will not be copied to destination (unless you make a mistake in configuration on first run). However, even after you have corrected the exclusion configuration all the "exclusion" does is not copy the folder or file, doesn't care if the file is already on the destination, doesn't even look for it. There is no way for the system to know to do any more than you instruct it to do. Now in the present case, if you had checked delete on destination, then deleted the .thumbnails folder on the source, then run the rsync, the folder would have been gone from both your main system (source) and your backup (destination). I can think of a scenario where the behaviour that we are talking about might be useful if one is using this rsync as a backup.

---

