---
title: "How to move files between user accounts?"
date: 2009-12-23
forum: General Help
---

### Post by JoeyF on 2009-12-23
Ok, look at:
[http://ubuntuforums.org/showthread.php?t=1362112&page=2](http://ubuntuforums.org/showthread.php?t=1362112&page=2)

I moved my music from one account to the other. And now i have a music folder inside my music folder.

Lets say i buy some songs on account 2 and want to copy it to account one. How could i do that without copying all of my music? lets say just the two new songs.

And also, It won't let me delete files that i copied from 1 to 2. Both accounts have the same rights and it still won't let me even if i am on account 1.

Any ideas?

Thanks.

---

### Post by JoelOl75 on 2009-12-23
You can study up on user accounts, but if there's 2 accounts on the same computer that I don't mind each having access to the others files (I mean ALL files shared between the 2 users) I just add the second user to the 1st's groups and the 1st user to the seconds group.

Like lets say there's two users, paul and frank.

Add the group "frank" to pauls account and add the group "paul" to franks group.

Then all files between them can be shared.  If you don't want to share everything DON'T do this!

Then just use permissions to allow "other" access to the music folder

---

### Post by JoeyF on 2009-12-23
> **JoelOl75 said:**
> You can study up on user accounts, but if there's 2 accounts on the same computer that I don't mind each having access to the others files (I mean ALL files shared between the 2 users) I just add the second user to the 1st's groups and the 1st user to the seconds group.

Like lets say there's two users, paul and frank.

Add the group "frank" to pauls account and add the group "paul" to franks group.

Then all files between them can be shared.  If you don't want to share everything DON'T do this!

Then just use permissions to allow "other" access to the music folder

How do i do the last part?

Thanks.

---

### Post by JoelOl75 on 2009-12-23
Sorry, should have been more clear, you don't have to do the last part if you add the users to each others groups.  This is only if you don't want to share everything between the two users.

Right click on the music directory in nautilus, select properties, then click the permissions tab.  In the "Others" section change Access files to create and delete files.

There's security implications in doing this as anyone on the computer (even the guest) may change and delete files.

Another way I didn't mention is to create a new group, let's call this new group mshare for media share. Add the users you want to access these folders to the new mshare group. Then you can recursively change the group on the folders you want to share to mshare.  Now only users that belong to this mshare group can change and delete files.

Sorry for throwing out 3 different ways to do this, it just depends on what you want to do.  

The first method has the security implication that paul can change and delete anything that frank has and vice-versa.  The second allows any account on the system to change and delete files in these folders, even the guest account or say someone finds an exploit in apache (If your running a webserver) and roams your system with the permissions of "nobody', even they can change and delete these files!

The third is the most fine-grained and secure way IMO.  There's probably many more ways to do this.

The second (Just alowing others to create and delete files) is the easiest though.

---

### Post by prshah on 2009-12-23
> **JoeyF said:**
> 
Lets say i buy some songs on account 2 and want to copy it to account one. How could i do that without copying all of my music? 

An easier way would be to simply "link" your music folder to the other user's folder.

Eg, ```
sudo ln -s /home/joey/Music /home/autumn/Music/Joey\'s\ Music
``` This will create a folder in autumn's Music folder which will be called "Joey's Music" and will contain all of Joey's music.

If there is any particular file that you do not want autumn to have access to, remove permissions for "others" to "read" the file; Eg```
chmod o-r /home/joey/Music/somefile
```

By default, "others" have "r"ead and e"x"ecute permissions; in this case, autumn can playback Joey's Music, but cannot change/delete anything.

From your linked post, you have copied the entire Joey's directory to autumn's music directory (aka folder). To copy only files and subdirectories (subfolders), you need to modify the command slightly; use```
sudo cp -r /home/joey/Music[color=red]/*[/color] /home/autumn/Music/
```

---

