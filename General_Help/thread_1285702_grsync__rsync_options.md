---
title: "grsync / rsync options"
date: 2009-10-08
forum: General Help
---

### Post by Jim_in_Germany on 2009-10-08
Hi,

I want to use grsync to synchronize two folders.

1. Folder "Music" which is on an external HD, mounted under "/media/Music"
2. Folder "Media" which is also on a (different) external HD, mounted under "/media/Back up/Media/"

I want to syncronize the folders from left to right.
That is, I want to check which files have changed in folder 1. (new files, renames and deletes) and copy these actions to folder 2.
So, for example if there is a new file somewhere in folder 1. it should be copied to folder 2. If a file in folder 1. has been renamed it should also be renamed in folder 2. If a file has been deleted in folder 1. it should be deleted in folder 2.
I also want to copy all files, sub-folders and anything else from folder 1. to folder 2.

I do not want to copy anything from folder 2. to folder 1. ie. if a file has been deleted in folder 2. I want grsync to realize this and to copy the file back from folder 1. to folder 2. I do not want grsync to delete this file in folder 1.

So, I opened grsync and had it do a simulation. It told me that it would effectively be running rsync with the following options:

rsync -r -n -t -v --progress /media/Music/ /media/Back up/Media/

I'm being paranoid here as everything looks good, but could somebody confirm that the above command will do what I described above.

It would be disastrous if it went wrong!

Thanks in advance.

---

### Post by akakingess on 2009-10-08
I am not too familiar with the two programs as of yet, but maybe you should backup folder 1 (temporarily, of course) and just run it, changing a few things, etc. as you had described that you wanted to be done, and if for some reason if fails any of your tests, you have the backup to pull back in and start over with. Just a suggestion, as I haven't had a chance yet to delve too much into rsync and grsync, although I recommend it to others as I have seen it suggested so often on this forum as the best way to go. I know this isn't what you wanted to hear, but it is at least one way to test it without needing to wait for a response from here (in case you were anxious to see if it would work).

---

### Post by Jim_in_Germany on 2009-10-08
Hi,
Thanks for that.
I'm not too sure about temporarily backing up my music folder as it is over 80GB in size.
I already tried making a superficial folder structure and playing around with it to see if it did what I wanted and everything seemed to work well.
Normally I am quite impulsive when it comes to messing about with stuff on the computer, but in this case it would be a disaster if anything went wrong.
Therefore I would still like to hear back from someone who feels comfy using rsync and can confirm that what it wants to do and what I want it to do are one and the same :)
Cheers

---

### Post by akakingess on 2009-10-08
I understand completely, didn't know how much music or spare space you had so just thought I would just throw that suggestion out there. Anyway, hope someone more knowledgeable with rsync chimes in and helps you out, good luck to ya.

---

### Post by StuartN on 2009-10-08
> **Jim_in_Germany said:**
> So, for example if there is a new file somewhere in folder 1. it should be copied to folder 2. If a file in folder 1. has been renamed it should also be renamed in folder 2. If a file has been deleted in folder 1. it should be deleted in folder 2.

You might want to use -ptgo (preserve permissions, times, group and owner) instead of just -t (times).

If you want files that have been deleted on the source to also be deleted on the destination, then add --delete.

rsync is dumb in the sense that there is no source for the previous name of a file / directory. If you rename a file on the source drive, then it will be treated as if the old name was deleted and the new name was created. If you rename a huge folder, then you can also rename it on the destination to save a huge deletion and recreation.

Grsync seems to have reported the space in "Back up" without a backslash, while rsync on the command line would require \space.

Your command would become:

```
rsync -n -rptgov --progress --delete /media/Music/ /media/Back\ up/Media/
```

and remove the -n when you are ready for the actual syncing.

---

### Post by Jim_in_Germany on 2009-10-08
Wonderful.
Thanks very much indeed for that.
I have added the -ptgo options that you suggested and will now run the synchronization.
Thank you very much for your help.

---

