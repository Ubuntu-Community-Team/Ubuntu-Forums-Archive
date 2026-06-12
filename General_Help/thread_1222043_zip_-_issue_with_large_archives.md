---
title: "zip - issue with large archives"
date: 2009-07-24
forum: General Help
---

### Post by Muscovy on 2009-07-24
For some reason when zipping my home folder to an external drive, somewhere between 2 and 3 GB in, I get the following error:
zip I/O error: File too large
zip error: Output file write failure (write error on zip file)

---

### Post by Cheesemill on 2009-07-24
What format is your external drive?
Some filesystems have a limit on the size of a single file.

---

### Post by Muscovy on 2009-07-24
I think it's NTFS.
  And I think I've got an installer DVD or two already on there, so I don't think that's the issue. (Refering to the fact they're ~4 GB).

---

### Post by credobyte on 2009-07-24
> The original Zip file format limited the number of member files in a Zip file to 65,535, and the maximum size of both the Zip file itself and any member file to 4 gigabytes.

This should pretty much answer to your question ..

---

### Post by Muscovy on 2009-07-24
Oh, alright. :( Pity.
  In that case, is there a way to use the cp command and exclude hidden files? I was looking for a fast copy-ish method, but I used zip because it did have a -x command.

---

