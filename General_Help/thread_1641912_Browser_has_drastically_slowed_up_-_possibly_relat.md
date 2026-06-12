---
title: "Browser has drastically slowed up - possibly related to large number of files on file"
date: 2010-12-09
forum: General Help
---

### Post by neuromorphic on 2010-12-09
*Thread title should be '..large number of files on *disk*'.  Whoops!

Hi, this is my first UbuntuForums post!

***** Problem: Browser has drastically slowed up. *****
I've experienced a fairly sudden slow-up in my browser performance.  I've had something just like this a year or so ago as well.  I just suffered under it at that time, as I didn't know where to begin to try to address the problem.  Eventually I got a newer, larger internal HD, together with a fresh installation of Ubuntu.  The problem basically went away then, though it seems to have returned.

***** Likely Cause: Filesystem. *****
I'm fairly sure the underlying causes have to do with the state of the filesystem.  This was the most likely correlation before, and also seems to be the clear correlation this time.  To people with a better (ie any) understanding of filesystems the cause may seem obvious, once I describe what I've been doing.  But alas I'm pretty clueless about the basic principles of how filesystems work, and how filesystem performance varies in real situations.  (I'm guessing it's probably behaving in a quite comprehensible way that reflects these basic principles, though perhaps that's wishful thinking.)  I'm also ignorant of the principles of browser behavior (or of Firefox's particular architecture), and perhaps that also contributes to the explanation for the slowness.

Here's the thing: I'm kind of addicted to logging.  >:D  I've got various kinds of record-keeping activities running all the time.  Some of them eventually generate a huge number of files.

***** Culprit 1: PyKeyLogger *****
I have PyKeyLogger - it logs keystrokes, and takes a screenshot every 20s.  The screenshots all get stored in a folder, which I haven't peeked at in a long time, and is by now horrifyingly large.  That is, it certainly contains a large *number* of files.  The keystrokes get added to the end of a log file.

***** Culprit 2: Slogger *****
I also run the Firefox addon Slogger.  It stores a copy of every webpage visited.  But in fact this will store many more files than just one for every page visit, given that saving a complete webpage stores many smaller ancillary files as well (including images).  Slogger organizes these files by putting all that day's files (and subfolders) into a directory for that day (eg '2010-12-09'), and by now there are at least a year's worth of those, all sitting in the same directory.

***** Possible Culprit 3: Calibre ebook collection. *****
Another factor, which could be even more important for all I know, is that I have significantly filled up the internal HD in a big burst recently.  It is a 640GB disk (ordinary, no SSD sadly), of which the Ubuntu partition has about 480GB.  Up until recently it had over 200GB free, but I imported a few large ebook collections from external HDs (I discovered the wonderful Calibre!), plus a bunch of video for good measure, and it now has just over 100GB free (77% disk usage for the Ubuntu partition).

***** Principles of filesystem/ext4 behavior, causes, solutions? *****
I would very much appreciate if anyone could explain to me what the critical variables are, and what they affect - in principle and in practice.  For example, a year ago, it eventually reached the stage where simple file copying operations were so slow that copying even fairly small folders was just about impossible.  Thus it seemed that problems on one part of the filesystem could affect one's ability to do things elsewhere on the filesystem.

I can imagine it could be the case that somehow having a very large number of files in even a single directory (and regardless of whether the files are all very small) is enough to create the problem, particularly if that directory is being regularly accessed by a program, like PyKeyLogger (a Python script) or Slogger (a FF addon), or even by lower level system utilities called by those programs.

I am unclear about whether any kind of manual (user-initiated) filesystem maintenance utilities should/can be run on the filesystem in general in order to 'clean it up' somehow, or if I'm simply reaching limits of some sort.  Alternatively, perhaps changes to the directory/file tree structure itself are necessary.  Another possibility is that the problem was solved before because the whole filesystem was copied over to the new internal HD, allowing it to (re)organize itself in a sensible way, removing the accumulated inefficiencies.  If so, perhaps there is a way to do this more deliberately using filesystem maintenance utilities rather than messing around with extra disks?

I'm curious whether Linux (particularly ext4) power users actually do run all sorts of optimization and maintenance programs on their filesystems, or if there are fundamental reasons why they more-or-less don't.  It's not something I hear people talk about often, but then again I don't hear the conversations of people who're really into kernels and so on.

***** A few other things I should mention *****
I run the disk encryption available as in install option in recent Ubuntus.  And, for the record, I'm running Maverick on a MacBook Pro.

Also, I've been having a bit of trouble over the last few months with a filesystem issue that has affected others.  ([http://ubuntuforums.org/showthread.php?t=1200023](http://ubuntuforums.org/showthread.php?t=1200023))  Despite regular system updates it continues to recur from time to time, and is fixed each time by logging in from LiveCD or recovery mode shell and running fsck, during which it fixes a bunch of 'inodes that were part of orphaned inode lists', 'block counts' and 'inode counts'.

***** In conclusion *****
I'm curious about the underlying factors that cause this, and how to avoid these issues arising in the future.  But of course my immediate concern is how to get my performance back.  (..to 2010 levels, that is.  I don't want to end up in slow-Internet acclimatization training camp, alongside all the people preparing themselves mentally and physically for time travel back to the 1990s.  I'm not made of tough enough stuff.  Leave it to Jean-Claude Van Damme.  ;D)

---

