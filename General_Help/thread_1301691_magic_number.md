---
title: "magic number"
date: 2009-10-26
forum: General Help
---

### Post by weishigoname on 2009-10-26
I am using ubuntu ,and sometimes ,there were some problems that the outputs mention "magic number".I searched it ,but did not understand what it means,how it works,Is there someone can explain that?

---

### Post by Giblet5 on 2009-10-26
> **weishigoname said:**
> I am using ubuntu ,and sometimes ,there were some problems that the outputs mention "magic number".I searched it ,but did not understand what it means,how it works,Is there someone can explain that?


"Magic numbers", or simply "magic" are values (binary or text strings) that are placed at the beginning of a data file that identify the data type and/or the software used to create or manipulate it.

The file /etc/magic can provide definitions of magic strings for use by the /usr/bin/file program. It usually ships empty because the command has most file "standards" built-in.

---

### Post by alphaniner on 2009-10-26
Magic number errors can also be related to filesystem problems.  It would help to have more information regarding what you are trying to do when you see the errors.

---

### Post by weishigoname on 2009-10-28
thanks for your reply,I got a look at that files you mentioned ,but I did not understand the words ,the numbers ,evern everything in that files .how can I get to known what they mean?

---

### Post by amauk on 2009-10-28
Windows uses file extensions to identify the type of files.
Open a file with a .jpg extension, windows interprets that as a JPEG image, and launches the appropriate application to view the file

*nix systems use a different way,
they use magic numbers
every data format has a unique identifier in the header of the file
when you open a file on a *nix system, the magic number is read and the file type determined, and the appropriate application launched

---

### Post by wojox on 2009-10-28
```
cat /usr/share/file/magic | less
```

```
man magic
```

---

### Post by weishigoname on 2009-11-01
thanks!! get some  idea about it

---

### Post by P4man on 2009-11-01
> **amauk said:**
> Windows uses file extensions to identify the type of files.
Open a file with a .jpg extension, windows interprets that as a JPEG image, and launches the appropriate application to view the file

*nix systems use a different way,
they use magic numbers
every data format has a unique identifier in the header of the file
when you open a file on a *nix system, the magic number is read and the file type determined, and the appropriate application launched

Do you know how nautilus uses this in combination with extensions ? If you rename any file (say a video) and you add .txt as extension, nautilus ignores the file header and treats it like a text file, just like windows. Use .torrent and it thinks its a torrent file etc. This kind of annoys me. it seems like nautilus looks at the extension first, and if it doesnt know it or there is none, only then checks the file header.

---

### Post by amauk on 2009-11-01
> **P4man said:**
> Do you know how nautilus uses this in combination with extensions ? If you rename any file (say a video) and you add .txt as extension, nautilus ignores the file header and treats it like a text file, just like windows. Use .torrent and it thinks its a torrent file etc. This kind of annoys me. it seems like nautilus looks at the extension first, and if it doesnt know it or there is none, only then checks the file header.According to this, it used to use magic
[http://ubuntuforums.org/showthread.php?t=607895](http://ubuntuforums.org/showthread.php?t=607895)

Seems it's been changed at some point

---

