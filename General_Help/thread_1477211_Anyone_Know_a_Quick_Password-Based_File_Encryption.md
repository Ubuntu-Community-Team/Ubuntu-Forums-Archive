---
title: "Anyone Know a Quick Password-Based File Encryption Tool?"
date: 2010-05-08
forum: General Help
---

### Post by Penguin Guy on 2010-05-08
EDIT: I would like something that's in a repo or PPA. I do **not** want True Crypt.


I have a password file that I keep on an external USB. Whenever I need to add a password to the file, process goes as follows:
[LIST=1]
[*]Plug in USB
[*]Give ownership of the archive to me [FONT="Courier New"]sudo chown josh 'Inconspicuous-Looking File.zip'[/FONT] [SIZE="1"]*[/SIZE]
[*]Enter user password
[*]Extract here in nautilus
[*]Enter archive password
[*]Shred archive [FONT="Courier New"]shred -fuz 'Inconspicuous-Looking File.zip'[/FONT]
[*]Open file in GEdit
[*]Add a password
[*]Close file
[*]Shred GEdit's backup file [FONT="Courier New"]shred -fuz 'Inconspicuous-Looking File~'[/FONT]
[*]Re-create archive
[*]Enter archive password
[*]Change archive permissions [FONT="Courier New"]chmod 700 'Inconspicuous-Looking File.zip'[/FONT]
[*]Give ownership of the archive to root [FONT="Courier New"]chown root 'Inconspicuous-Looking File.zip'[/FONT]
[*]Unplug USB
[/LIST]
:(

I want to shorten that to something more like this:
[LIST=1]
[*]Plug in USB
[*]Open file in GEdit
[*]Enter archive password
[*]Add a password
[*]Unplug USB
[/LIST]
:)

Anybody know a tool that can do this? Since the file is on an external USB, the focus is on speed rather than security.

Thanks.

[SIZE="1"]* I called the file 'Inconspicuous-Looking File.zip' so that it would be blatantly obvious to humans (me) that it contained confidential information, while being less obvious to robots.[/SIZE]

----------

I'm now using an [EncFS]("apt:encfs") folder, with some aliases to simplify the process. The process is now:
[LIST=1]
[*]Unlock EncFS `[FONT="Courier New"]unlock[/FONT]`
[*]Enter password
[*]Open file in GEdit
[*]Add a password
[*]Lock EncFS `[FONT="Courier New"]lock[/FONT]`
[/LIST]

---

### Post by Southwind on 2010-05-08
You might take a look at truecrypt at [http://www.truecrypt.org](http://www.truecrypt.org).  There is a version for linux as well as window.  same file or drive can be opened by either system. 
Larry

---

### Post by Penguin Guy on 2010-05-08
> **Southwind said:**
> You might take a look at truecrypt at [http://www.truecrypt.org](http://www.truecrypt.org).  There is a version for linux as well as window.  same file or drive can be opened by either system. 
Larry
I want something that's in a repository or a PPA, and I especially don't want True Crypt.

---

