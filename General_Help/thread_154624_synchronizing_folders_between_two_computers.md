---
title: "synchronizing folders between two computers"
date: 2006-04-03
forum: General Help
---

### Post by sgleo87 on 2006-04-03
Ok, this is the situation: (I alpologize ahead of time for my high demands :mrgreen: )

I have a laptop and a desktop (both with ubuntu). I use the laptop at school to take notes and the desktop at home to take notes from the reading assignments in the same files that I use during class. So I need these files updated on both computers and it should be a two way sync because I don't want to risk accidently overriding any files if for example I changed different files on both computers between syncs.

In windows I have a program called syncback and I connect my laptop to my home network after I get home from school to sync with my desktop and then sync again before I go to bed so I have the updated notes on my laptop for school.

I already read some stuff on the forums about this and it seems unison is what I need (or is there a better app?). It is important that the app asks me during the sync if I want to delete a file or copy it to the other computer if there is a file on one computer and not the other and I also need to be able to set up a filter so it ignores certain files.

Now my question is what is the easiest and most convenient way to set this up? (I am lazy so it would be awesome if the sync would automatically in the background without me doing anything). I am still a linux noob so detailed answers and instructions would be appreciated ;)

---

### Post by marks_linux on 2006-04-03
I would check out rsync. Its command line, but can be scheduled to run when you want. It deals with file changes etc etc, copying only modified files.

you can tell it to exclude fiels/file patterns etc.

I use lines such as the following to back up all my home area (except things ending in things like .tar whci are specidied in the exlude.txt file) to another machine whos name is linuxserver:

rsync -e ssh --timeout=180 --exclude-from=/home/markw/cron/exclude.txt -Cavub /home/ LinuxServer:/hd2/mirror/home/

---

### Post by sgleo87 on 2006-04-03
[QUOTE=marks_linux]I would check out rsync. Its command line, but can be scheduled to run when you want. It deals with file changes etc etc, copying only modified files.

you can tell it to exclude fiels/file patterns etc.

I use lines such as the following to back up all my home area (except things ending in things like .tar whci are specidied in the exlude.txt file) to another machine whos name is linuxserver:

rsync -e ssh --timeout=180 --exclude-from=/home/markw/cron/exclude.txt -Cavub /home/ LinuxServer:/hd2/mirror/home/[/QUOTE]

but isn't rsync a one way sync??? I do change different files on both computers so i do need an app like unison that does a two way sync.

---

