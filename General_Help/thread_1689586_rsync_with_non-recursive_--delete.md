---
title: "rsync with non-recursive --delete"
date: 2011-02-17
forum: General Help
---

### Post by c4traz on 2011-02-17
Hello,

I'm struggling to make rsync delete files which don't exist on source but not to delete any sub-folders which don't exist on source.

```

rsync -dutv --delete /dirA/_backup/ /dirB/_backup --dry-run
building file list ... done
./
deleting Folder/
deleting File.txt

```So it should delete 'File.txt' but not delete 'Folder/'
I want to avoid specifying 'Folder/' in an exclude option, it should rather not delete sub-folders in general.

Any advise would be appreciated :)

c4traz

---

### Post by YesWeCan on 2011-02-17
One way is to combine the find command with rsync

perhaps
find /dirA/_backup -type f | rsync --files-from=- -dutv --delete --dry-run /dirA/_backup /dirB/_backup

or perhaps
find /dirA/_backup -type d | rsync --exclude-from=- -dutv --delete --dry-run /dirA/_backup /dirB/_backup

If you want to sync directories that do exist in the source I suppose you could run rsync twice, the first time with no exclusions and no deletions, then run with find to delete just the files that no longer exist in the source.

---

### Post by c4traz on 2011-02-20
Hey YesWeCan,

thank you very much :)
I hoped there would be a rsync-only way but anyway works good :)

---

