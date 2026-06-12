---
title: "Opening and using Rar file"
date: 2010-05-16
forum: General Help
---

### Post by HenrySkitsas05 on 2010-05-16
I've downloaded a game, thats a rar file, but when I try open it with archive manager it says Archive type not supported. What do I need to open / extract the files?

---

### Post by gmargo on 2010-05-16
Install the **unrar** package.

---

### Post by HenrySkitsas05 on 2010-05-16
I just did, and right click opened with "unrarfree" but nothing happened.

---

### Post by gmargo on 2010-05-16
Use "unrar l filename.rar" on the command line to list archive contents.  "unrar x ..." to extract.

---

### Post by HenrySkitsas05 on 2010-05-16
Sorry, I didn't understand. Could you tell me exactly what I need to do with the filename in steps. Sorry I'm new to Ubuntu, just came from Windows. The filename is "Heroes of Might and Magic III Complete.rar"

---

### Post by shantiq on 2010-05-16
[B][COLOR="Blue"]system/administration/synaptic package manager/enter rar


pick any of them maybe unrar click on apply click on reload


now try your file again  and it will be fine[/COLOR][/B]

---

### Post by samg34 on 2010-05-16
try installing another archive manager like 7-zip...

---

### Post by gmargo on 2010-05-16
> **HenrySkitsas05 said:**
> Sorry, I didn't understand. Could you tell me exactly what I need to do with the filename in steps. Sorry I'm new to Ubuntu, just came from Windows. The filename is "Heroes of Might and Magic III Complete.rar"

1. Open a terminal window.
2. Inside that terminal, navigate to the directory containing the file if it's not the home directory.
3. Type the unrar command.

For instance, if the file is in the /tmp directory:
```

$ cd /tmp
$ unrar l "Heroes of Might and Magic III Complete.rar"

```That command will give a listing of the contents.  What is in there?  Is it a Windows binary that you're planning to use within Wine?

---

