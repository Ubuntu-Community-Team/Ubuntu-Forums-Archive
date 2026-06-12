---
title: "Access to files"
date: 2006-04-25
forum: General Help
---

### Post by Sonic5688 on 2006-04-25
How do I allow a certain folder to let me copy files into it? When I try, it says "You do not have permission to write to this folder." Also, how do I set myself as the "owner"?

---

### Post by Sutekh on 2006-04-25
What folder are you trying to copy to?

Are you trying to copy with the command line or nautilus (the file browser)?

Use ```
sudo cp /<path of source files> /<path of target folder>
```
to copy using the terminal

Use```
gksudo nautilus
```
to open nautilus as root, which will allow you to graphically copy things.  Just be careful what you do.

---

### Post by rado_london on 2006-04-25
sudo chmod 777 /folder/you/want/to/change

777 allows the whole world to read write execute.

---

### Post by Sonic5688 on 2006-04-25
Im just trying to drag and drop some files from a CD into directory usr/local/games/doom3/base but it isnt letting me

---

### Post by rado_london on 2006-04-25
Because you dont have permission for root assuming /usr is root partition. in this case open terminal and type "sudo nautilus" eithout the quotes. then enter your usr password and do the draging.

Good luck

---

### Post by IYY on 2006-04-25
Use sudo like Sutekh suggested.

---

### Post by Sonic5688 on 2006-04-25
Thank you all for the help! This has solved my problem.

---

