---
title: "Best backup solution for me?"
date: 2011-04-27
forum: General Help
---

### Post by shaggy999 on 2011-04-27
So I've been looking at setting up a backup system and I've been doing a lot of research, but really can't find anything that seems to work for me. Hopefully someone can point me in the right direction.

So far I've looked at:

rsync
rdiff-backup
unison
git/mercurial/subversion
various git-derived backup programs

My setup & requirements:

At the moment I have a desktop PC, a netbook, and a server. At least 2 more systems will be added within a year. On each of these systems I only have a few sparse files that I would like backed up. My main computer has things like:

.bashrc/.screenrc settings and such
/etc/mpd.conf
dwarf fortress saves + other games
bookmarks
random useful scripts mostly in ~/bin
a few documents

My netbook has:

.bashrc/.screerc settings
zsnes saves
bookmarks
a few documents
a truecrypt partition with about 100 MB of important documents

My server has:
rtorrent settings/files
http/samba files/settings
random scripts/configuration files

Things I need:
* rotated backups with daily/weekly/monthly snapshots
* version control for managing discrepancies between files on multiple systems (such as my bookmarks)
* must be fully functional from the command line so it can be scripted and automated
* ability to "run backups" when disconnected from the network (for example, I may change some scripts and such while out and about and want to at least get the changes checked into a repository of sorts
* version control must handle binary files (sometimes I go back to an earlier save in dwarf fortress)
* must be able to recover deleted files (meaning, if I delete a file and then sync, the backups should have a copy of the file somewhere in case I decide that I really needed the file)

Trying to figure out how to version-control/snapshot data inside my truecrypt volume in an automated fashion while remaining cryptographically secure is a tricky setup and may not be possible, so I will refer to the security forums for that matter. For right now I'm resigned to rsync'ing the file and having no snapshots/version control of the data contained within.

There doesn't seem to be any one program that can do all of this. It seems I would definitely need something like git for managing scripts and such, but I really only want some specific files backed up/version controlled and I'm not sure how to accomplish this. Can I just create a ~/backup directory and symlink all the files I want backed up into it and then version control that?

What should I use? All of the requirements above are really important to me. If a backup solution fails in any of those ways it's not really worth using. The only thing that "seems" to do everything is git, but I keep hearing how git is not designed for backing up files (such as it doesn't maintain permissions, which isn't an issue for me as I would be resetting the permissions myself or from a script anyways) and it doesn't handle individual files. None of the git-derived backup programs seem to be reliable enough at the moment (meaning what I get out is not necessarily what I put in, and that's just a complete fail, or the projects are dead... the one with the most promise is bup). Unison seems to support dealing with different versions of files on two different systems... but ONLY on two different systems, I will have 5 total within a year. rdiff-backup seems nice, but similiar to unison it won't run when I'm off network and it's not clear to me but it seems that when you delete a file it completely deletes it from the backup as well?

EDIT: Solutions involving "online storage"/cloud etc. are not an option for me.

---

### Post by Lars Noodén on 2011-04-27
You could look at fancier options like bacula or radmind.

I use rsync myself.

---

