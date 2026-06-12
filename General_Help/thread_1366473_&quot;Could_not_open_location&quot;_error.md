---
title: "&quot;Could not open location&quot; error"
date: 2009-12-28
forum: General Help
---

### Post by bovender on 2009-12-28
Hi all,

for the last couple of days I have been unable to open folders from the "Places" menu in Ubuntu 9.10. I get the following error message:

```

Could not open location: 'file:///home/XXXXX'
No application is registered as handling this file

```

How can I reset the default handler for the FILE protocol?

Thanks.

---

### Post by bovender on 2009-12-28
I solved it myself -- here's how to do it in case someone else has the same problem:

Open a terminal window, enter "nautilus" to start the file browser.

Right-click on a folder icon, choose "open with other application...", and then "File Browser".

I don't know why, but it works -- I can now use the "Places" menu again!

---

### Post by Synicade on 2011-03-29
Thanks a ton! I had the exact problem, and it fixed it for me to!

---

### Post by pascie on 2011-08-08
I'm having the same problem and I read the proposed trick on all forums, but it doesn't seem to work for me. 

I noticed that the problem goes away when I create a new user, so does anyone have an idea which file in my home folder I might need to edit/delete.

thanks in advance!

---

### Post by mc4man on 2011-08-08
Open a terminal and go 
```
nautilus ~/.local/share/applications
```
inside should be a file, mimeapps.list
You could make an edit(s) inside or simply just delete it, it will be rebuilt thru use of the context and default menus

If deciding to edit look for this line
inode/directory=

If you want to post that file AND what release of ubuntu you're using feel free, can square you up.

---

