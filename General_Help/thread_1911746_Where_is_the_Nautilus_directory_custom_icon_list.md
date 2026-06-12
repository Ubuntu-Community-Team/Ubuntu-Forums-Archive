---
title: "Where is the Nautilus directory custom icon list?"
date: 2012-01-19
forum: General Help
---

### Post by sidewalkcynic on 2012-01-19
I had to remove my /home files to clear some problems.

I have a lot of folders with custom icons, but I cannot find the list in the files that I removed to put it back into my fresh /home.

Should be an easy question and solution - thanks.

---

### Post by Frogs Hair on 2012-01-19
Excuse me , I m a bit confused . > I had to remove my /home files to clear some problems.To where ? 

 > I cannot find the list in the files that I removed to put it back into my fresh /home.What do you mean by list ? Did you create a list or do you mean a group of files .

Custom Icon sets  are usually stored in  two  locations depending how they are installed . In the file system they are found in usr/share/icons and in /home the .icons hidden folder is used . Try the search function if you know the folder/s name or contents . If these are your own folders search the directory where you may have moved them . 

If you moved a .hidden folder to the desktop it will be not be visible unless you select desktop in Nautilus .  Also , you could try  variations of the following commands .

```
ls ~/.icons
ls /usr/share/icons
ls ~/.icons/name
ls /usr/share/icons/name

```

---

### Post by Frogs Hair on 2012-01-19
I am using using Nautilus  3.2.1 and the history tab that was was under go in older versions has been removed . I also can't seem find Nautilus history via the terminal either .

---

### Post by sidewalkcynic on 2012-01-19
Sorry, for the confusing terms.

I found that what i am looking for is in the /.local/share/gvfs meta

---

