---
title: "Link one folder to another?"
date: 2012-01-26
forum: General Help
---

### Post by carlosbgois on 2012-01-26
I have a music folder which is not /home/user/Music, and I wish this linked to that, which is in another partition of my HD. Is it safe doing it? If I do it, will my music files show under the music tab in unity?

Thanks

---

### Post by sudodus on 2012-01-26
You can link folders using symbolic links. This can be done using the terminal command with the -s option ```
ln -s 'your-music-folder' 
``` which creates a link to 'your-music-folder' in the current directory. The link can be moved or renamed.

It can also be done using the file browser Nautilus. You right-click on your music folder and select 'Create link'. Afterwards you can move that link to where you want it (in your /home/user folder or in your /home/user/Music folder.

---

