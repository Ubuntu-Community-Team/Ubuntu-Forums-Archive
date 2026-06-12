---
title: "Problems using a samba share for IE favorites"
date: 2006-02-15
forum: General Help
---

### Post by jcl on 2006-02-15
Howdy,

I realize this is probably more of a windows question than ubunu, but I respect the pool of knowlege here more than any microsoft site...

I have a samba share that I'm wanting all of my XP clients to use for their IE favorites instead of the local drive. I've mapped a drive on the XP box to automatically reconnect without a password and that seems to work ok... the files appear when I click on the drive letter. I've modified the registry entry to point IE to Z:\bookmarks\username... the problem is on reboot and first login IE doesn't see the bookmarks until I physically click on the drive mapping in explorer... then it sees them ok... even if I log out and log back in it still sees them ok... only on reboot does this happen...

So on XP when you have a mapping automatically reconnect, does it not really reconnect until you manually use it?

Thanks

---

### Post by dcstar on 2006-02-15
[QUOTE=jcl]Howdy,

I realize this is probably more of a windows question than ubunu, but I respect the pool of knowlege here more than any microsoft site...
......
So on XP when you have a mapping automatically reconnect, does it not really reconnect until you manually use it?

Thanks[/QUOTE]
Who really knows??    :( 

A work-around may be to have a startup cmd file in the Windows boxes that runs the "map" command and forces an access to the share.

---

### Post by jcl on 2006-02-20
I did what you suggested... set up a .bat file to run on startup to map the drive then stat it... that works...

Why do things have to be so kludgey in windows?

Thanks

---

