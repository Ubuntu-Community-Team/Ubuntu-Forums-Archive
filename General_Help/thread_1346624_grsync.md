---
title: "grsync"
date: 2009-12-05
forum: General Help
---

### Post by cmcanulty on 2009-12-05
I have read the manuals for rsync but can't find anything describing the various options in grsync and there are many. Can someone please post directions for how to set up the correct options in grsync for a simple backup of the home or documents folder?

---

### Post by tom4everitt on 2009-12-05
rsync works much like cp. Since it is a folder you're copying you will want the -r (recursive) flag, and since you probably want to save time by not copying files that haven't been changed since the last backup, you probably want the -u (update) option.

Hence the command would look like this:

```

rsync -ur /home/myhome backupdir

```

A few notes:
-Appending a space after the folder, i.e /home/myhome/ instead of /home/myhome, will give a slightly different result. One will give you a ton of files in backupdir, the other a neat folder. I never manage to remember which is which though. 

-There is a -b option also, specifically designed for backups, but I'm not sure how that works.

---

### Post by tom4everitt on 2009-12-05
I actually got a bit interested in how to use rsync for backup, and found this excellent guide:

[http://www.mikerubel.org/computers/rsync_snapshots/#Rsync](http://www.mikerubel.org/computers/rsync_snapshots/#Rsync)

It describes some handy backup-techniques for rsync very well and thouroughly.

---

### Post by ssulaco on 2009-12-05
This is a good little tutorial Ive used
[http://mag.mypclinuxos.com/html/Issues/200708/page04.html](http://mag.mypclinuxos.com/html/Issues/200708/page04.html)

---

### Post by cmcanulty on 2009-12-05
Thanks

---

