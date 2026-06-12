---
title: "Changing file permissions in a game"
date: 2012-08-07
forum: General Help
---

### Post by MistaT on 2012-08-07
Hello, I am new to Ubuntu and love it but am still shaky on doing any commands in terminal.  Here is the thing: I have installed Armagetron Advanced and love the game, there are a great many mods to the game such as adding "moviepacks" which will give you different arenas.  

As detailed here with installation instructions: [http://wiki.armagetronad.org/index.php/Customizing_the_game#Installing_a_Moviepack](http://wiki.armagetronad.org/index.php/Customizing_the_game#Installing_a_Moviepack)

When I try and place the folder with in the game folder which is located at: usr/share/games/armagetronad I am getting a permissions denied because root is the owner of the file. 

In my research I found this link:  

[https://help.ubuntu.com/community/FilePermissions#chmod_with_sudo](https://help.ubuntu.com/community/FilePermissions#chmod_with_sudo)

which gives details about how to change the file permissions.  I just don't quite understand them, lol.

The commands to add read,write, execute to everyone are listed as:

user@host:/home/user$ chmod ugo+rwx file4 

user@host:/home/user$ ls -l file4 -rwxrwxrwx  1 user user 0 Nov 19 20:13 file4 

user@host:/home/user$

So to apply those commands to the armagetron file would it be this?

user@host:/usr/share/games/armagetronad$ chmod ugo+rwx file4 

user@host:/usr/share/games/armagetronad$ ls -l file4 -rwxrwxrwx  1 user user 0 Nov 19 20:13 file4 

user@host:/usr/share/games/armagetronad$

---

### Post by MistaT on 2012-08-07
never mind, the issue has been solved by the guys on the armagetron forums.8)

---

