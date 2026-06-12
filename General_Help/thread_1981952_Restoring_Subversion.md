---
title: "Restoring Subversion"
date: 2012-05-17
forum: General Help
---

### Post by Kentucky88 on 2012-05-17
Something bad happened and I had to reinstall Ubuntu.  I had backed up my home directory including the subversion (SVN) repository.  However, I had commited changes into Subversion a few times since my last backup and now my development box is out of sync with the SVN server.  I could delete the project from SVN and re-commit, but then I would lose all update history.  What is the proper way to force all updates from my dev box onto my SVN server?

---

### Post by 1clue on 2012-05-17
You had a svn repo (server side) in your home directory?

Actually I think this can all boil down to one or two things:
[LIST=1]
[*]Is the uncommitted source at a version which  does not exist yet in the backup?
[*]How much data is lost, and is it server-side or client-side?
[/LIST]

One solution is to **svn up -r HEAD**  (you may need a **--force** in there somewhere) and take your working directory to whatever the new HEAD is in the repo, for whatever branch you're on.  Your uncommitted changes will follow along, but the committed stuff may get funky.

This is basically the same if you have multiple committers, you modify source at the same time as somebody else, you commit last and need to update before being able to commit.

The difference if your backup is older than your working directory is that you're undoing changes which were committed in the trashed server code.

---

### Post by 1clue on 2012-05-17
Another option is this:

[LIST=1]
[*]Check out a new copy of the HEAD of whatever branch you're on.
[*]cd to your existing, modified directory.
[*]**rm -rf `find . -name .svn -print`** -- this makes your existing code no longer an SVN checkout!
[*]**cp -prd * /path/to/new/directory** -- without a trailing /
[*]Commit in the new directory.
[/LIST]

What that does is gets a valid working directory, and then takes ALL the differences between the backup's version and your working copy, and commits them as one commit.

---

