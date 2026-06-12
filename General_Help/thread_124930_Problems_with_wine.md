---
title: "Problems with wine"
date: 2006-02-02
forum: General Help
---

### Post by BitTorrentBuddha on 2006-02-02
After installing and uninstalling wine a few times, I still can't get wine to work properly, everytime I install it I get a list of errors all similar to 

Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/username', starting in the Windows directory.

when I try to do anything, and when using the winecfg gui it locks up when you do anything...

---

### Post by chronusdark on 2006-02-02
do you have a /.wine directory in your home folder and if you do check your permissions on it

---

### Post by BitTorrentBuddha on 2006-02-02
no I do not :(

---

### Post by dcstar on 2006-02-02
[QUOTE=BitTorrentBuddha]no I do not :([/QUOTE]
It is a hidden directory, so you have to enable viewing of hidden stuff in Nautilus.

If you do actually have a .wine directory in your home drive, rename it and start winecfg again.

---

### Post by BitTorrentBuddha on 2006-02-02
rename it anything?

---

### Post by Sutekh on 2006-02-02
[QUOTE=BitTorrentBuddha]rename it anything?[/QUOTE]
How about

```
mv ~/.wine ~/.wine_bak
```

This will 'rename' (actually move) the .wine folder to .wine_bak.  The '~/' means your home folder - /home/<usrname>

Then go the winecfg again.

---

### Post by BitTorrentBuddha on 2006-02-02
ahh, ok i see what was going on, thanks for the help ;)

---

