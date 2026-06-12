---
title: "task: pdf management help"
date: 2009-10-06
forum: General Help
---

### Post by miesnerd on 2009-10-06
I am trying to get one huge bibliography organized.
To do this, I need to get my pdfs into Referencer.
That's a simple drag and drop....once you getall the pdfs found.
I am hoping to find a program, shell script, or something to search all media attached to my computer (ie not just /home) and copy every pdf to one location (probalby /home/pdf_backup/). How can this be done?

Thanks in advance,

Miesnerd

---

### Post by kaibob on 2009-10-06
The following command recursively searches for all PDF files and prints the file names to the screen. I am suggesting this as a first step so that you will know what is going to be copied. I ran a test, and the command did find PDF files on attached USB hard drives and flash drives.

```
find / -iname '*.pdf' -type f 2>/dev/null
```

If everything looks OK, use the following commmand to actually copy the PDF files. You have to change /target/directory.

```
find / -iname '*.pdf' -type f -exec cp '{}' /target/directory ';'
```

Both of the above commands will take some time. Also, the second command will issue many error messages--ignore these.

---

