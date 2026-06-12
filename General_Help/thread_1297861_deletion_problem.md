---
title: "deletion problem"
date: 2009-10-22
forum: General Help
---

### Post by piyush.neo on 2009-10-22
i am using **ubuntu 9.04.**.when i am deleting a file by using delete button..then its deleting file but the size of the folder remain same(and insufficient disk space problem exist)....while i am deleting by** right click->send to trash**..then only its showing its reducing the size of the folder....](*,)


Can anybody suggest the solution..and where those file are, which are deleted by pressing "delete button"?????

---

### Post by RichardLinx on 2009-10-22
This is a pretty simple suggestion but it doesn't sound like you actually deleted the file after moving it to "trash". Unless you delete the file from "trash" then space will still be occupied. You can delete a file from the garbage bin (located in the bottom left corner of the screen if you have a standard Ubuntu GNOME install) by right clicking the icon and selecting "Empty Garbage bin"

Though in this case it sounds more like a really strange bug. 

You could also try:
```
sudo apt-get autoremove
```
```
sudo apt-get autoclean
```

---

### Post by zer0x on 2009-10-22
Hi,

I assume its just moving the files to the Trash folder.

You can completely remove the files by right-clicking on your 'Deleted Items' and selecting 'Empty Deleted Items'.

The files are stored here:

```
~/.local/share/Trash
```

HTH

zer0x

---

### Post by piyush.neo on 2009-10-22
thanks...actully what happening was...when i deleted files from pen drive...a folder named RECYCLER was automatically created in pen drive with all that files....when i deleted that folder permenentaly, the files are removed.....

THANKS!!!!

---

