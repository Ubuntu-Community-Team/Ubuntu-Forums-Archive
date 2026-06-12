---
title: "file compare on different PC's?"
date: 2010-05-16
forum: General Help
---

### Post by chitowner2 on 2010-05-16
Hi folks;

Just looking for some general advice here, and maybe the discussion will be helpful for others.

I have multiple PC's on a LAN, sharing the same router and all running either karmic or lucid with kde desktop. I want to clean up a couple directories, copying unique files from one PC to another and also deleting duplicates from the first. My goal is to empty the directory on the first PC without losing anything and without laboriously poring over directory trees manually.

The latter is especially important because the directory trees have evolved independently for some time.

I have heard of things like rsync and fslint but have not used them much directly, tho i have used rsync over ssh occasionally to batch-move files. 

So does this seem like a project than can be run in a straight-forward manner? Ideally it would be run in a single job, with a second go just to confirm it worked recursively.

Thanks,
CT
:)

---

### Post by aparigraha on 2010-05-16
as you said, **rsync** is the way!

just a word of [COLOR="Red"]caution[/COLOR]... when using the [COLOR="Red"]--delete[/COLOR] option (which deletes files on machine A that are deleted on machine B) try it first with a test directory so you don't accidentally delete anything.

a simple rsync parameter to build on would be something like this:

```
rsync -avvz --progress --stats --perms --delete /path/to/your/source/dir login@your.remote.location.com:/your/destination/dir
```

-avvz  and --progress will give you informaton if something is not right.
and note that there is a difference if you are using **/** or not, at the end of your paths. (eg. **/home/** or just **/home**)

man rsync for more advanced options

---

### Post by chitowner2 on 2010-05-16
It wouldn't be too much trouble to do the compare & copy, then delete later as opposed to compare & move I guess. But ya, a test run to be sure of how the command runs is always a good idea.

Thanks for the feedback aparigraha.

CT

---

### Post by chitowner2 on 2010-05-16
LOL
I should have anticipated this: a major part of the data I'm dealing with is mp3 files ripped from my CD's, but some CD's have tracks that are on more than one album, so now i gotta figure out how to deal with that.

Maybe there's a way for rysnc to replace the redundant tracks with some kind of link to the "first" occurrence of it? But how would that work with Amarok and mySQL?

:guitar:

---

### Post by tgalati4 on 2010-05-16
I would flip the problem.  Use rsync to syncronize the directories so that all pc's have the exact same file set.  Then you have at least one backup and you can delete the directories on the machines that really don't need it.

Weeding out duplicate tracks can be laborious.  I find it is best handled by importing the directory into a new music player (rhythmbox, listen, songbird, banshee, etc).  Then sorting your list of artists and albums and the duplicates will quickly stand out.  Then you can either delete them through the music player or just delete them by hand in the file manager.

---

### Post by chitowner2 on 2010-05-22
> **tgalati4 said:**
> I would flip the problem.  Use rsync to syncronize the directories so that all pc's have the exact same file set.  Then you have at least one backup and you can delete the directories on the machines that really don't need it.

Weeding out duplicate tracks can be laborious.  I find it is best handled by importing the directory into a new music player (rhythmbox, listen, songbird, banshee, etc).  Then sorting your list of artists and albums and the duplicates will quickly stand out.  Then you can either delete them through the music player or just delete them by hand in the file manager.


I use amarok via mySQL. Is there a way to expedite the find&delete process with SQL?

---

