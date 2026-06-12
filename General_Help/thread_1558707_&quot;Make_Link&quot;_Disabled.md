---
title: "&quot;Make Link&quot; Disabled"
date: 2010-08-22
forum: General Help
---

### Post by derkonig on 2010-08-22
The "Make Link" option is disabled in the context menu in Ubuntu 10.04. I want to make a hard link on the Desktop for my www folder.

I didn't have this problem in Linux Mint 8. I already tried the ln command. I also changed the owner and group that the folder belongs to, along with its permissions. Nothing helped.:???:

---

### Post by spjackson on 2010-08-22
You cannot create a hard link to a folder. I _think_ this applies in general to all linux flavours and all filesystem types. Why not simply create a symbolic link?
```
ln -s /path/to/www-folder ~/Desktop/
```assuming of course that you have write permission to you Desktop.

If you still have problems, perhaps you could indicate what errors you get when you try various commands.

---

### Post by derkonig on 2010-08-22
I got it to work. The ln -s command worked, but the folder was invisible. I had to view it through the terminal. After changing the permissions again, it appeared like a normal link.

Thanks for your help.

---

