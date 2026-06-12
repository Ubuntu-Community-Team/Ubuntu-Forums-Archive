---
title: "Deleting Folders from the Home folder?"
date: 2011-07-07
forum: General Help
---

### Post by samuel.cole on 2011-07-07
I accidentally created a folder in my /home directory and its ticking me off because i cant delete it and im anal about my organization on the computer and having this extra empty folder is driving me nuts

---

### Post by foxmulder881 on 2011-07-07
In a terminal:

```
sudo rm -fr /home/username/foobar
*password*
```

replacing username with your own and foobar as your stubborn directory.

---

### Post by Surendil on 2011-07-07
```
 sudo nautilus /home/username/
*password*
```

---

### Post by samuel.cole on 2011-07-08
No not that home folder, whoops i meant the /home folder as in the one before username as in -----> /home/username

---

### Post by e79 on 2011-07-08
The commands provided by **Surendil** and **foxmulder881 **still applies with a little modification:
 
```
sudo rm -rf /home/undesired-folder
```
 
[COLOR=red]WARNING :[/COLOR] Do not replace 'undesired-folder' with your actual username but rather with the folder name you wish to remove !!!
 
Good Luck

---

### Post by CatKiller on 2011-07-08
> **Surendil said:**
> ```
 sudo nautilus /home/username/
*password*
```

Don't use *sudo* with graphical applications. Use *gksudo* instead.

With file management like this, graphical is definitely the way to go. Much less likely to make mistakes than at the command line.

---

