---
title: "single folder with symbolic links to multiple folders"
date: 2010-08-04
forum: General Help
---

### Post by fcuk112 on 2010-08-04
hi - posting this here but it is a general linux question i guess.

i am using ps3mediaserver to expose my photos collection which is distributed across multiple sub-folders.  unfortunately the ps3 can only show a slideshow for a single folder at a time, hence i was wondering if there was a quick way to create a single folder containing symbolic links to all my pictures.  does there exist an app that can help with that?

thanks.

---

### Post by chopinhauer on 2010-08-04
```
cd /destination/folder && find /origin/folder -name '*.jpg' -exec ln -s {} . ;
```

I doubt there is an application just for that, but it's extremely easy to do the job by combining multiple commands (**cd**, **find** and **ln** in this example).

---

### Post by Zorgoth on 2010-08-04
Assuming that no two objects in any of the folders share a name (in which case of course there is no way to do what you want, except by renaming files based on the folder they came from, which is possible easily by modifying the code below), you could use the command ln as in this script:

Note: FOLDERS must be a list of paths separated by spaces and ENDING in /.  These paths should not include spaces (you may be able to include spaces by escaping with \, but spaces in path names is just not a good idea)

To set FOLDERS, simply type

FOLDERS='path1 path2 path3 ...'

```

for folder in ${FOLDERS}
do
    LINKS=`ls -A $folder`
    for link in ${LINKS}
    do
        ln $folder/$link /path/to/target_dir/$link
    done
done

```

To understand each component, read the appropriate bits of:
man bash
man mount
ls --help
man ln

And do I rule?  Yes, I do.

EDIT:  If you want, for example, only jpg files, you could change

`ls -A $folder`
to
```

`ls -A $folder | grep '.*.jpg'`

```

---

