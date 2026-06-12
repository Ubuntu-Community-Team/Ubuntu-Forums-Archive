---
title: "Annoying CD/DVD problem"
date: 2006-04-13
forum: General Help
---

### Post by Dr. Feelgood on 2006-04-13
For some reason when I insert a data DVD into my drive, it automatically mounts as usual, it lets me poke around the contents for about 30 seconds then the file manager window closes and it pretends there is no media in the drive.  It's very annoying.  If I tell the drive to eject and then close the drive again it goes through the same cycle everytime.  It didn't used to do this but I've installed an assload of programs recently.... an idea what could be causing this??  My first guess was the eject CD package that lets you eject the CD manually again by pushing the drive button (which doesn't even work by the way), but when I tried to uninstall the pakage with synaptic it said it wanted to uninstall ubuntu-minimal as well.  What gives?

---

### Post by dcstar on 2006-04-13
[QUOTE=Dr. Feelgood]For some reason when I insert a data DVD into my drive, it automatically mounts as usual, it lets me poke around the contents for about 30 seconds then the file manager window closes and it pretends there is no media in the drive.  It's very annoying.  If I tell the drive to eject and then close the drive again it goes through the same cycle everytime.  It didn't used to do this but I've installed an assload of programs recently.... an idea what could be causing this??  My first guess was the eject CD package that lets you eject the CD manually again by pushing the drive button (which doesn't even work by the way), but when I tried to uninstall the pakage with synaptic it said it wanted to uninstall ubuntu-minimal as well.  What gives?[/QUOTE]
Do:
```
dmesg
```
just before and just after the problem occurs and you may be able to spot a relevant message.

Don't worry about any "Ubuntu-" meta-package warnings, they are just the overall wrapper for many things you have installed under them, it won't hurt your system if they are gone.

---

### Post by Dr. Feelgood on 2006-04-13
Here is what dumped after it crapped out....

[4296278.873000] hdc: tray open
[4296278.873000] end_request: I/O error, dev hdc, sector 360

this message over and over and over again.  Then at the end I got this a few times...

[4296280.638000] VFS: busy inodes on changed media.

Any ideas?

---

### Post by an.echte.trilingue on 2006-05-24
What kind of dvds are you talking about?

If they are movies, movie companies go to great lengths to ensure that you can't poke around inside: the put in files that will make your drive go nuts.  Be sure to follow the restricted formats page on the wiki for movies.

If they are data DVDs, how did you encode them?

---

### Post by Dr. Feelgood on 2006-05-24
It's not a movie it's a data DVD.  Unfortunately I did not burn it so I don't know how it was encoded.  It does work on other computers though.

---

### Post by threethirty on 2006-05-25
here is a work around i used when i couldnt get ubuntu read a windows/mac hibred disk, go to a windows box on you network (sorry for the assumption) and share the disk drive, then use samba to connect to the disk drive and it should read just wonderfully

---

### Post by quincyjones on 2006-05-28
Maybe silly questions but, have you tried mounting (and ejecting) the DVD from terminal, it definately helps sometimes. Tried directly off a fresh reboot? I had a problem and it was with the eject button software, but only when I used the button.

---

### Post by DaveQB on 2006-06-03
[QUOTE=quincyjones]Maybe silly questions but, have you tried mounting (and ejecting) the DVD from terminal, it definately helps sometimes. Tried directly off a fresh reboot? I had a problem and it was with the eject button software, but only when I used the button.[/QUOTE]


I have this line:

```

VFS: busy inodes on changed media

```

in /var/log/messages **4x every 2 seconds**.  Needless to say my logs are filling fast.

The eject and then eject -t to close the tray seemed to stop this.  Why is this so ? What does one do in the future ? This only started happening after my upgrade to Dapper.

---

