---
title: "Danish characters not shown when mounting FAT32 USB drive"
date: 2011-05-23
forum: General Help
---

### Post by trevva on 2011-05-23
Hi,

I have an external USB HDD that has predominately been used in the Windows world - its formatted as FAT32. I can mount the disk fine using mount e.g.

```
sudo mount /dev/sdc1 /mnt/
```

However, the problem is that some of the files on the disk contain what you might call "special characters" ie in this case the Danish letters æ, ø and å - when I go to the directory in question, instead of a file being displayed as Risø_meeting.doc, it is displayed as Ris?_meeting.doc.

I'm assuming that this has something to do with the character sets that I am using when I mount it. How should I mount this properly?

Running Ubuntu 10.04 LTS as a fileserver.

Thanks for the help.

Mark

---

