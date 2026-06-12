---
title: "Shared Directory Permissions"
date: 2009-11-28
forum: General Help
---

### Post by gerowen on 2009-11-28
I have a desktop PC in my house which is kind of like the "family" computer for me and my wife for when we're home and don't need to pull out the laptops.  It's running Ubuntu 9.10.  We both like to play some of our old GBA and N64 games so I created a /home/shared directory where I plan on storing anything and everything that we would both need access to, such as a common pool of emulator ROMs.  The only problem I have is that if I put a ROM in there, she can't access it with the emulator until I do a chmod 777 on the /home/shared folder.  Is there a way to set a folder to persistently maintain the permissions you set on itself and all subfolders so if I do something it doesn't affect her ability to access the games?  After I set the permissions once it's all good on the files there, but when "I" add a new one I have to do that before it lets her access the game.  This would also be handy for fixing a similar issue on my webserver.

---

### Post by jbrown96 on 2009-11-28
The best way to do this is create a group and add both users to it, then make the shared directory owned by the shared gorup. 

1) create group. ```
sudo groupadd shared
``` you can change the name if you want.
2) add you and your wife's user. ```
sudo usermod -aG shared $USER
``` $USER will automatically change to the user that ran it. You will need to run it again but replace $USER with your wife's user name. 
3) Logout. you won't officially be part of the group until you login again. 
4) give the shared group control of the shared folder. ```
sudo chown -R shared:shared /home/shared
``` 
5) I'm not sure if the files actually need to be executable, but they probably don't. Fix the permissions with ```
sudo chmod -R 460 /home/shared
``` If you need execute privileges, then run ```
sudo chmod g+x /home/shared
```

This should completely fix your problem. What was happening was that you allowed everyone to rwx everything in /home/shared. However, when you create a new file there, it doesn't automatically inherit 777 privileges. However, new files automatically inherit the user:group of the folder in which it is placed. Since you and your wife are in the same group that owns that folder, then you will have permissions to access the files.

---

### Post by gerowen on 2009-11-28
Sweet, as soon as she's done playing Pokemon I'll do this, thanks!

---

