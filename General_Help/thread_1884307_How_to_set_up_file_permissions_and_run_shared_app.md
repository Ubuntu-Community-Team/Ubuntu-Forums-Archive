---
title: "How to set up file permissions and run shared app"
date: 2011-11-21
forum: General Help
---

### Post by Sidrabs on 2011-11-21
Hello,

I'd like to set up a simple game on my kids' PC, so that they can share the savegames etc. I've moved the game folder to /opt/gamename, assigned to the folder group "games", and changed the group rights to read+write. Both of the user accounts are included in the games user group. I've made sure that all the files in the folder also match the same group+rights.

However, my problem is that when one user has played the game and created the savegame, it is automatically owned by that user, and the other user who logs on later can only read the files created by the first user, and not overwrite.

How should I set up this thing so that the experience would be similar like when users would share the same user account? Should I create a dedicated user, re-own all the files by that user, and then run the game, impersonating that user? I'm not sure if it is possible, it's just my contemplation.

---

### Post by mcduck on 2011-11-21
If the game actually stores the saves in the install directory instead of in the user's home directory as usually, you could probably just add the setgid bit to the save directory's permissions. That would cause any new files created there to get their group from the directory instead of using the user's primary group as usually.

```
sudo chmod g+s /opt/gamename/saves
```

(this won't affect any already existing files or subdirectories, though, so you'll need to change their group manually.)

---

### Post by Sidrabs on 2011-11-21
Thanks for the reply,

I already had the savegames folder group set to "games", and the group permissions set to "read+write". However, the savegame folders created in there by other user accounts are owned by that user, and the group permissions are also only that user only.

There's another aspect I didn't tell in my OP, thought it is not relevant: I have created a symbolic link to the /opt/gamename in the users' home directories, because the game looks for ~/.gamename location to store its savegames. Perhaps that's the reason the savegame folders do not inherit the rights from /opt/gamename ? If so, how can I still fix this?

---

### Post by mcduck on 2011-11-21
> **Sidrabs said:**
> Thanks for the reply,

I already had the savegames folder group set to "games", and the group permissions set to "read+write". However, the savegame folders created in there by other user accounts are owned by that user, and the group permissions are also only that user only.

There's another aspect I didn't tell in my OP, thought it is not relevant: I have created a symbolic link to the /opt/gamename in the users' home directories, because the game looks for ~/.gamename location to store its savegames. Perhaps that's the reason the savegame folders do not inherit the rights from /opt/gamename ? If so, how can I still fix this?

I know you have already set the directory group, that's what you said in the first post. You *still* need the setgid bit in the permissions, that's what makes the new directories and files to inherit the save directory's group.

Normal permissions do not have any effect on created directory & file permissions, and ownership isn't inherited. 

So try setting that first, and if it's not working then we'll worry about the effect of linking from user's home directories might have. (although in that case changing the group & setting the setgid bit on the symlinks as well would probably work)

---

### Post by Sidrabs on 2011-11-21
Ok, did what you say,

Now the newly created folders in /opt/gamename/saves are still owned by the user who created them (as it should be), but the group is correctly set to "games" now. So, that's good. However, the group access is only "Access files", and the group permission to the files in the folder are "read only". If the folder and file access would be read+write, the problem would be fixed.

The /opt/gamename/saves group permissions are read+write, and I did, as you say, sudo chmod g+s /opt/gamename/saves

I checked, the permissions for the symlink folder are also games/create+delete.

---

