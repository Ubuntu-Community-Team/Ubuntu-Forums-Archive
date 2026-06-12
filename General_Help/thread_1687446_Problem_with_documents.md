---
title: "Problem with documents"
date: 2011-02-13
forum: General Help
---

### Post by TimmyK. on 2011-02-13
Now I have a real problem. Every time I try to open and folder (Documents, Pictures, Music, Desktop etc.) it opens it with VLC media player, and I can't look at or use any files except ones VLC can play (mp3, avi, etc.). Is there any cure for this?

---

### Post by Vaphell on 2011-02-13
yes.
right click on any folder, open with..., select file browser, make sure 'remember this app for this type' checkbox is ticked, ok, done. Most likely you opened some media directory once with VLC with the checkbox enabled and that set VLC as a default app for folders. It's a frequently occuring issue with 10.10, default setting of that checkbox is not the most fortunate.

---

### Post by WorMzy on 2011-02-13
Open up a terminal (Applications -> Accessories -> Terminal) and run the following:

```
sed -r -i '/^inode\/directory/d' ~/.local/share/applications/mimeapps.list
```

Alternatively, if you'd rather not run a command that you don't understand, open the terminal, run
```
gedit ~/.local/share/applications/mimeapps.list
```
to open the file in gedit (text editor) and delete the line beginning with "inode/directory".

---

### Post by TimmyK. on 2011-02-13
Thanks guys; problem solved. :D

---

