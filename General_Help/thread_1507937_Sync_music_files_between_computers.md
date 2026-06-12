---
title: "Sync music files between computers"
date: 2010-06-12
forum: General Help
---

### Post by SpinningAround on 2010-06-12
I have a music archive on several computers, from time to time do I add, remove or change the archive on one computer. To keep this changes will I have to copy the new version of the music archive to all the other computers.

Question is if there is a easier way to do this, is there a program that can sync the music files. Let say that I update the info in one music file, then will the sync program notice the newer version and replace the old file with the new files on all the other computers.

I guess I would need a dedicated server for this where all changes are stored with some kind of version number of the music archive. Since not having a server would make everything (I guess) much more complicated. All computers would have to communicate with each other to check for a new version instead of only communicate with one computer (the server).

---

### Post by SlidingHorn on 2010-06-12
You could set up a media server which hosts all the files and gain access from your other machines...here's a few places to get you started (they may be a bit outdated, but it's a good starting point):

[http://www.geek.com/articles/chips/feature-linux-media-server-using-ubuntu-810-2009065/](http://www.geek.com/articles/chips/feature-linux-media-server-using-ubuntu-810-2009065/)

[http://ubuntuforums.org/showthread.php?t=459691](http://ubuntuforums.org/showthread.php?t=459691)

This one's more about physically building one: [http://www.popularmechanics.com/technology/how-to/build-pc/4247239](http://www.popularmechanics.com/technology/how-to/build-pc/4247239)

---

### Post by howefield on 2010-06-13
> **SpinningAround said:**
> Question is if there is a easier way to do this, is there a program that can sync the music files. Let say that I update the info in one music file, then will the sync program notice the newer version and replace the old file with the new files on all the other computers.

Dropbox has a neat lan feature.

[http://www.dropbox.com/help/137](http://www.dropbox.com/help/137)

Free accounts come with 2 gigabyte of space, you can push that up by referring other users.

If you need more space than that, another option might be to purchase a NAS drive which would connect to a router accessible to all computers on your network.

---

### Post by SpinningAround on 2010-06-13
Thanks for the answers but it isn't really what I'm looking for. All computers aren't always connected to the same network making the use of a media server not really possible. The total size of the music archive is above two gigabyte, that make it problematic using Internet based storage. Guess some programming is required, to make it a little easier is there a program like ftp that you can send a command to replace a certain file?

---

### Post by howefield on 2010-06-14
Setup a cron job with rsync ?

---

