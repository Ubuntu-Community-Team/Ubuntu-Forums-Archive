---
title: "search"
date: 2006-03-22
forum: General Help
---

### Post by gos1 on 2006-03-22
hi can anyone tell me how to search for a file both with terminal and gnome. I am clicking on search files and type the file I know existing but it returns with "0".

---

### Post by Ramses de Norre on 2006-03-22
```
sudo updatedb
locate [file name]
```
This works very very well for me (no way you can equalize it with the win explorer search!)

I've never used nautilus to search before, and I don't find the function, strange..

---

### Post by akiro.yamamoto on 2006-03-22
[quote=gos1]hi can anyone tell me how to search for a file both with terminal and gnome. I am clicking on search files and type the file I know existing but it returns with "0".[/quote]

By default
 Places >> Search For Files 
Only looks in your Home Folder.
To search for your file in the entire system change the search path. ( / )
If the file may be on another mounted drive.. specify that drive.
If after all that still NO JOY!! ahhh you may have deleted the file... hope it's in the
trash if not, it's gone.... soorrryyyy...

---

### Post by gos1 on 2006-03-22
thank you works fine but do I have to updatedb all the time. and another question I cannot find the command to make a directory (md) in ubuntu do you know the command

---

### Post by can_climber on 2006-03-22
I belive the command is mkdir, and depending on the directory (outside the home), you may have to sudo mkdir. thats for making a directory.

---

