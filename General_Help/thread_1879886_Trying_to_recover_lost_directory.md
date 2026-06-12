---
title: "Trying to recover lost directory"
date: 2011-11-12
forum: General Help
---

### Post by wyth on 2011-11-12
I recently tried out [cryptfolder-indicator]("http://www.webupd8.org/2011/06/cryptfolder-indicator-ubuntu.html") to mount an encrypted directory. I was trying to mount a directory that I had made with [cryptkeeper]("http://www.webupd8.org/2011/06/create-manage-encfs-folders-with.html").

I didn't get it to work, and in the cryptfolder-indicator preferences I chose to remove the directory I tried to import. That shouldn't have done anything except remove the encrypted directory from the application, nothing else.

However, after I closed cryptfolder-indicator, not only was my encrypted directory missing, but so was the entire directory in which the encrypted directory resided.

Nothing was in trash. But somehow I just lost nearly 200GB of data, the majority of which wasn't even in the encrypted directory.

Now I'm baffled. I'm no noob, and I've recovered data off crashed drives in the past, but this isn't a crashed drive. My home directory was encrypted on install, so booting to a live cd doesn't let me just poke around. I've tried photorec and extundelete; photorec hasn't found anything yet, and extundelete 
[LIST]
[*]Doesn't recognize the directory I'm trying to recover because the partition isn't mounted, but
[*]Can't recover from a partition once it is mounted.
[/LIST]

I've tried foremost and scalpel as well; I'm new to both and so far they haven't found anything either, but I'm trying to run those off a live usb and where I'm searching -- /dev/sda3 -- is encrypted unless I mount it.

So I'm really at a loss here. There wasn't a crash, my drive is perfectly healthy (it's 6 months old), and whatever happened seems to be related to my removing a directory from the cryptfolder-indicator application.

There must be a way to recover a directory and its files from a perfectly healthy drive, but I'm not sure what that is. Any ideas?

Thanks much.

---

### Post by wyth on 2011-11-12
bump

---

### Post by raja.genupula on 2011-11-13
> **wyth said:**
> I recently tried out [cryptfolder-indicator]("http://www.webupd8.org/2011/06/cryptfolder-indicator-ubuntu.html") to mount an encrypted directory. I was trying to mount a directory that I had made with [cryptkeeper]("http://www.webupd8.org/2011/06/create-manage-encfs-folders-with.html").

I didn't get it to work, and in the cryptfolder-indicator preferences I chose to remove the directory I tried to import. That shouldn't have done anything except remove the encrypted directory from the application, nothing else.

However, after I closed cryptfolder-indicator, not only was my encrypted directory missing, but so was the entire directory in which the encrypted directory resided.

Nothing was in trash. But somehow I just lost nearly 200GB of data, the majority of which wasn't even in the encrypted directory.

Now I'm baffled. I'm no noob, and I've recovered data off crashed drives in the past, but this isn't a crashed drive. My home directory was encrypted on install, so booting to a live cd doesn't let me just poke around. I've tried photorec and extundelete; photorec hasn't found anything yet, and extundelete 
[LIST]
[*]Doesn't recognize the directory I'm trying to recover because the partition isn't mounted, but
[*]Can't recover from a partition once it is mounted.
[/LIST]

I've tried foremost and scalpel as well; I'm new to both and so far they haven't found anything either, but I'm trying to run those off a live usb and where I'm searching -- /dev/sda3 -- is encrypted unless I mount it.

So I'm really at a loss here. There wasn't a crash, my drive is perfectly healthy (it's 6 months old), and whatever happened seems to be related to my removing a directory from the cryptfolder-indicator application.

There must be a way to recover a directory and its files from a perfectly healthy drive, but I'm not sure what that is. Any ideas?

Thanks much.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by Mark Phelps on 2011-11-13
From "a perfectly healthy drive" -- yes; from encrypted drives, folders, or files -- NO.

---

