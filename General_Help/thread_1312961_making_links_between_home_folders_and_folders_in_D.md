---
title: "making links between home folders and folders in D partition Windows"
date: 2009-11-03
forum: General Help
---

### Post by Cozze on 2009-11-03
I choose for a dual boot vista / Ubuntu and everything works fine. However I'd like to link the folders in my Ubuntu home directory to the folders on my Windows D:/ partition without the content being imported to ubuntu, the content needs to stay on the D:/ partition. I have access to the D:/ partition and it's folders when I am working in Ubuntu, I just don't manage to link both "Music" folders for example.

Tx, Cozze

---

### Post by Cozze on 2009-11-03
I choose for a dual boot vista / Ubuntu and everything works fine. However I'd like to link the folders in my Ubuntu home directory to the folders on my Windows D:/ partition without the content being imported to ubuntu, the content needs to stay on the D:/ partition. I have access to the D:/ partition and it's folders when I am working in Ubuntu, I just don't manage to link both "Music" folders for example.

Tx, Cozze

---

### Post by undecim on 2009-11-03
Go to a terminal and use the ln command with the --symbolic option.

For example, to make the folder /home/user/Music link to /media/Windows/Documents and Setting/Default User/Music/, you would run the following command in a terminal:```
ln --symbolic "/media/Windows/Documents and Settings/Default User/Music" /home/user/Music
```

Just remember to put them in the correct order. ```
ln --symbolic /folder/to/become/a/link /folder/where/the/real/files/are
```

And remember to use quotes around any folder that has spaces in the path name.

---

### Post by cariboo on 2009-11-03
Please don't double post, I have merged your two threads.

---

### Post by Cozze on 2009-11-04
Thanks everybody, gonna try it out. Sorry for the double posting as well.

Cozze

---

