---
title: "Trouble extracting rar"
date: 2011-06-16
forum: General Help
---

### Post by DrKnobblez on 2011-06-16
Trying to unpack this rar. Inside is a raw CD image.

I've tried using archive manager. So here is me trying through terminal:

knobblez@knobblez-HP-Pavilion-dv7-Notebook-PC:~$ cd Desktop
knobblez@knobblez-HP-Pavilion-dv7-Notebook-PC:~/Desktop$ ./unrar PE.rar
bash: ./unrar: No such file or directory
knobblez@knobblez-HP-Pavilion-dv7-Notebook-PC:~/Desktop$ ./unrar '/home/knobblez/Desktop/PE.rar'   
                                                                                   **^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^I dragged the file to terminal ^^^^^^^^^^^^^^^^^^^^**
bash: ./unrar: No such file or directory
knobblez@knobblez-HP-Pavilion-dv7-Notebook-PC:~/Desktop$ 

The forum I was following said use the command

./unrar e rarfile

I have tried with the 'e' added. Same problem.

---

### Post by mister_playboy on 2011-06-16
Use unrar rather than ./unrar.

---

### Post by idoitprone on 2011-06-16
is unrar is in ur working directory?

If not and it is in your $PATH

use 
```
unrar e "/home/knobblez/Desktop/PE.rar"
```

---

### Post by DrKnobblez on 2011-06-17
knobblez@knobblez-HP-Pavilion-dv7-Notebook-PC:~/Downloads/PE$ sudo unrar PE.rar
[sudo] password for knobblez: 

unrar 0.0.1  Copyright (C) 2004  Ben Asselstine, Jeroen Dekkers


Extracting from /home/knobblez/Downloads/PE/PE.rar

Extracting  PE.iso                                                    Failed    
1 Failed


:/

---

### Post by jerome1232 on 2011-06-17
I smell a corrupt archive, do you have enough free space to extract this file?

Archive manager will work fine for rar's if unrar is installed, was this a torrent or regular download, if a regular download did the download site have checksums for the files available?

---

### Post by pqwoerituytrueiwoq on 2011-06-17
i would use the GUI myself
if this rar has multiple parts you will need all of them to open it
```
sudo apt-get install rar
```

---

### Post by DrKnobblez on 2011-06-17
It is XP Performance Edition. I downloaded it as a Torrent. I use a private torrent website and there was plenty of supporting feedback. :/ Is there an automated check I can use?




**EDIT

[pqwoerituytrueiwoq]("http://ubuntuforums.org/member.php?u=865458")

thank you :D

The GUI worked

---

