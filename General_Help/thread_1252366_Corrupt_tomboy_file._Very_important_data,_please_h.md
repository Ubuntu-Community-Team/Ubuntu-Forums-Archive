---
title: "Corrupt tomboy file. Very important data, please help"
date: 2009-08-28
forum: General Help
---

### Post by IrishAdam on 2009-08-28
Hi folks,

I really need your help. I have lost a very very important tomboy note with a lot of contacts and info for my business.

I know I should have backed it up somehow....

The note that I lost still exists in /.tomboy but it now has 0 bytes. There is no copy of the file in /.tomboy/Backup and the note does not show up in tomboy.

I suspect my only chance is some type of data recovery program to find the text on the hard drive.

The note files are XML file format with .note extension.

Can anyone help me get the data back?

Adam

---

### Post by iver2435 on 2009-08-28
Maybe try the "octal dump" command to view the "raw" file.  If there is anything in the file at all, it will show up:

```
od lost.note > recovered.note
```

good luck!

---

### Post by IrishAdam on 2009-08-28
Thanks iver2435.

Unfortunately, recovered.note only contained 8 bytes which was "0000000".

Can anyone suggest a file recovery program that might help me?

---

### Post by IrishAdam on 2009-08-29
bump

---

### Post by warreno on 2009-08-29
> **IrishAdam said:**
> Thanks iver2435.

Unfortunately, recovered.note only contained 8 bytes which was "0000000".

Can anyone suggest a file recovery program that might help me?

I don't know if [this]("http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html") might help or not, but it might be worth a shot. Typically if a file is dereferenced in a NIX OS, it's gone forever, but what the heck.

---

### Post by Rhubarb on 2009-08-29
You could try using a file recovery tool like testdisk / photorec.

Please do a search on how to use these tools, they've very powerful.
I'm in a bit of a hurry so I can't elaborate too much for you :(

---

