---
title: "Search inside archives"
date: 2012-04-24
forum: General Help
---

### Post by jfreak53 on 2012-04-24
I'm looking for a program that will search inside zip and rar files for x filename and return that list.   I am used to using xplorer2 for windows, but when I install it in wine I get all sorts of problem's using it, so it's not working.

Ideally I would like to get a thumbnail of the image once found in the archive. I understand this might require to extract and that's fine.

Maybe a bash command to search for filenames inside archives then extract that file to current directory and rename to the archive filename with png extension or something of the sort's, so then I can just preview in nautilus.

Don't know though, maybe someone has a good solution.  Thanks.

---

### Post by newbie-user on 2012-04-24
The default file browser in Ubuntu will list the archive contents if you double-click on the archive. It doesn't give you thumbnail previews of the pictures, though. You can also search through the list with ctrl+f

---

### Post by jfreak53 on 2012-04-24
Yeah but I can't click on each of 100 files to search for this one picture, hence I need a grepping function.

---

### Post by jfreak53 on 2012-04-24
Well this seems to work:

```
find '/media/Extra/myzip/' -iname *.zip -print0 | xargs -0 -I{} unzip -l {} | grep "image.png" -H
```

But the problem is now that I found the image files now I have to find a way to pipe this with the filename back to unzip to unzip only that image file under the original archive name into X directory so I can thumbnail and see all images :(

Bummer

---

### Post by jfreak53 on 2012-04-24
Ok I just found this that also works great, probably better since it actually extracts the file in question:

```
find '/media/Extra/myzip/' -iname *.zip -print0 | xargs -0 -I{} unzip -oj {} */image.png -d /home/user/mine
```

That command above works excellent, because it actually extracts the image file to the directory specified.  Great, now the only problem is I don't want sub directories, I want all image files in the same directory named after it's original archive.  I'm stumped with that one :S

---

