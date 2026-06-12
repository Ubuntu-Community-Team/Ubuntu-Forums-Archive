---
title: "unpack multiple files for;do;done"
date: 2010-01-19
forum: General Help
---

### Post by aristo c. on 2010-01-19
Hi all,

I'm trying to unpack some 2000 rar and zip files via terminal with just one operation using for;do;done, but I'm not getting the results I want.

I need to unrar or unzip a number files into a different folder, and there into a folder with the same name of the rar or zip file.

Help would be much appreciated.
aristo

---

### Post by synapsys on 2010-01-19
What does your command look like?

Have you tried something like this?

```
for x in *.zip; do unzip $x; done
```

If I'm way off, it's because I don't understand exactly what you're trying to do.

---

### Post by aristo c. on 2010-01-19
So far my command looks like this:

```
for var in *.rar;do unrar xf "$var" /media/HDD/folder;done
```

Of course this works without any problem for packages which have compressed a directory, but I need the ones that have only compressed files at "/" inside to be extracted to a new folder with the same filename as the rar file, otherwise all the packages with files at "/" will extract to the same location given by /media/HDD/folder, and mix together making it very difficult to sort them out.

---

### Post by synapsys on 2010-01-19
Ah ok, I get it now. Would this work for you?

```
for var in *.rar;do unrar xf "$var" /media/HDD/folder/**$var**/;done
```

---

### Post by aristo c. on 2010-01-19
Perfect! Thanks a lot.
For some stupid reason I was obsessed about including mkdir in that command.

---

