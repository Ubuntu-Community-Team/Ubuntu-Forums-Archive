---
title: "Rsync for windows pc"
date: 2010-03-10
forum: General Help
---

### Post by gottijr on 2010-03-10
-linux newbie-

  trying to buil a home server on ubuntu 9.10 (xubuntu installed)

  Trying to understand how i can backup some location (rsync i guess) to my ubuntu linux server.

  pls advice, maybe some easy to read tutorials that you guys know.

  thanks

---

### Post by Dayofswords on 2010-03-10
if your backing up windows, it has it own way 

need to know if its xp, vista or 7

---

### Post by gottijr on 2010-03-10
I'm using vista in the home network

  i need to keep a backup (sync) to the server with updates for changes. I remember i've read about it before just don't remember where.

---

### Post by Dayofswords on 2010-03-10
windows has feature called restore points, where it takes a snapshot of the current configurations and saves them for a time that you may need to revert back

read this
[http://www.howtogeek.com/howto/windows-vista/using-windows-vista-system-restore/](http://www.howtogeek.com/howto/windows-vista/using-windows-vista-system-restore/)

when it says to restore the recommend point or choose a different one, chose the link underneath

---

### Post by gottijr on 2010-03-10
I know about the restore point in windows

  I'm more looking to protect myself for hard failure or something similar

  I've heard of this sync option

  i wouldn't sync my windows hard drive but maybe a specific folder with documents (let's presume)

---

### Post by Dayofswords on 2010-03-10
EDITED, to respond to last post better
sync center is most likey what you heard, that is for syncing data to devices like media players

if you want to back up the whole computer
from my windows vista college book:
Backup entire computer(makes a virtual hard drive image of it)

[LIST=1]
[*]start the computer and logon
[*]close all applications that start up automatically
[*]click **start**, point to **all programs**, click **accessories**, click **system tools**, and click Backup status and Configuration
[*]click, complete Pc Backup on the right(choose backup files if you want specify files, where you make it automatically backup certain files and folders)
[/LIST]
the book goes a different direction that the last step, so your on your own from there

---

### Post by gottijr on 2010-03-10
again

  i know all this working in windows is no problem for me

  linux is the problem!

  i'm trying to sync (for the intention of the backup)

  sync in real time

  folder A - from Windows vista pc

to

   folder B - ubuntu server 9.10

  thanks

---

### Post by Dayofswords on 2010-03-10
in my last post in part 4."click, complete Pc Backup on the right(choose backup files if you want specify files, where you make it automatically backup certain files and folders)"

you can have it automatically back up certain files to a network share at certain times(daily at XX:XX, weekly on XXXday at XX:XX)


if you have samba set up this should be easy

but there isnt a real time option in windows(back uped when it happens), you would need third-party for that

---

### Post by gottijr on 2010-03-10
good point with samba

  than what would be a good third party software for real time backup from folder A (under vista) to network samba share?

  thanks

---

### Post by Dayofswords on 2010-03-10
i know of none myself
and google isnt helping either for backing up in real time to a network folder

---

### Post by gottijr on 2010-03-10
i'm google-ing myself

  but nothing special

  i've seen delta copy (downloads.com) but with just 3000 downloads doesn't look like a reliable software.

p.s. actually is not really what i need

---

### Post by gottijr on 2010-03-10
I found SyncBack

  good software but not sure if can backup just the difference in file and it might backup the entire file.

  i'm still looking for other suggestions.

  thank you.

---

### Post by alfplayer on 2010-03-10
If you want to manage the backups from windows you could use Cobian Backup to connect to a samba shared folder on your linux box. The updates or synchronizations are not instantaneous like Dropbox but they can be scheduled.

---

### Post by alfplayer on 2010-03-10
> **gottijr said:**
> I found SyncBack

  good software but not sure if can backup just the difference in file and it might backup the entire file.

  i'm still looking for other suggestions.

  thank you.

I don't think it can backup partial files. I don't know any backup software that can do this because file contents should be scaned and compared and this might be unnecessary and use too much resources.

---

### Post by asmoore82 on 2010-03-10
looking for Grsync for Windows?

Grsync homepage: [http://www.opbyte.it/grsync/](http://www.opbyte.it/grsync/)
Grsync for Win32 download page: [http://sourceforge.net/projects/grsync-win/files/](http://sourceforge.net/projects/grsync-win/files/)
^^ported by :D Me!

Grsync can handle remote sync folders, you just have to type the path in ~
in other words, it is unable to "Browse" to them for you...

see attached screenshot.

---

### Post by eriqjaffe on 2010-03-10
This could also be done with Robocopy.  It has a /MON switch that will trigger a sync every X number of change, which is pretty close to real-time duplication.  Really, Robocopy is one of the best things MS ever did.

```
robocopy /?
```

...in a command prompt will give you all sorts of information.

---

### Post by gottijr on 2010-03-11
> **asmoore82 said:**
> looking for Grsync for Windows?

Grsync homepage: [http://www.opbyte.it/grsync/](http://www.opbyte.it/grsync/)
Grsync for Win32 download page: [http://sourceforge.net/projects/grsync-win/files/](http://sourceforge.net/projects/grsync-win/files/)
^^ported by :D Me!

Grsync can handle remote sync folders, you just have to type the path in ~
in other words, it is unable to "Browse" to them for you...


  how would i be able to choose a folder from my windows pc (from linux)?

  sorry, i'm a newbie to linux just installed ubuntu a week ago.

  thanks

---

### Post by alfplayer on 2010-03-11
> **gottijr said:**
> how would i be able to choose a folder from my windows pc (from linux)?

  sorry, i'm a newbie to linux just installed ubuntu a week ago.

  thanks

If you want to do it the other way around (from windows), I've just seen this thread: [http://opbyte.freeforums.org/grsync-from-windows-to-linux-t122.html]("http://opbyte.freeforums.org/grsync-from-windows-to-linux-t122.html"). Hope it helps.

---

### Post by asmoore82 on 2010-03-11
> **gottijr said:**
> how would i be able to choose a folder from my windows pc (from linux)?

  sorry, i'm a newbie to linux just installed ubuntu a week ago.

  thanks

you'd just have to have the openssh-server package installed on linux and that's it,
grsync for windows will default to using that access method when it's given a remote folder
line of the format *<user>***@***<hostname>***:***<folder>*

---

### Post by gottijr on 2010-03-11
thanks for the grsync advice sounds interesting if i can fix a few things like:

  ```

  rsync: recv_generator: failed to stat "/home/gottijr/blogs/MyTheme.zip": Permission denied (13)
rsync: recv_generator: failed to stat "/home/gottijr/blogs/Synchronization_Log.txt": Permission denied (13)
rsync: recv_generator: mkdir "/home/gottijr/blogs/09-Website" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/home/gottijr/blogs/MyTheme" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/home/gottijr/blogs/mythemes" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at /home/lapo/packaging/rsync-3.0.4-1/src/rsync-3.0.4/main.c(1040) [sender=3.0.4]
  
```

  than if can input the password somehow so it doesn't require my password all the time

  and if i could schedule it so i don't have to run it myself.

  thank you

---

### Post by alfplayer on 2010-03-11
That looks like a file permission error.

Unlike grsync, Cobian Backup does support scheduling, and you don't have to enter username or password if you allow guest access on your samba share on linux.

---

### Post by gottijr on 2010-03-11
> **alfplayer said:**
> That looks like a file permission error.

Unlike grsync, Cobian Backup does support scheduling, and you don't have to enter username or password if you allow guest access on your samba share on linux.

  yes i figured the cobian backup out

  this is no problem to run

  would anyone advice to make grsync work with those options mentioned before?

  thanks

---

### Post by alfplayer on 2010-03-11
I haven't tested it myself, but you could add the rsync option "--password-file *filename*" on "Advanced options" and save a session on the grsync interface, and schedule to run using windows's task scheduler:

grsync -e "name of session"

Also, if you can't get grsync to work with ssh, you can try setting up an rsync daemon on your linux box, but it might be a bit more difficult to do.

---

