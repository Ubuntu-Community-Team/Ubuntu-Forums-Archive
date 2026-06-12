---
title: "&quot;Infinite&quot; folder depth (recursive)! I want to remove!"
date: 2010-11-16
forum: General Help
---

### Post by gothxx on 2010-11-16
Got a strange problem...
Somehow i got a folder with the same foldername inside and i cant remove it because nothing happens (says "preparing" but no progressbar is active). Now i have it in my garbage but cant remove it...

It's like this for "infinity", or at least very very very long
```

Folder
|--Folder
   |--Folder
      |--Folder

```

is there any way to remove the root folder so i just get rid of the reference? As it is now I believe the system tries to follow the references to the last recursion level and remove when going back so to say.

//thx

---

### Post by Barriehie on 2010-11-17
Try removing the garbage can.  Your trash folder is /home/user_name/.local/share/Trash and has two subfolders, named files and info.  You should be able to remove the /Trash folder and then recreate the files and info folders therein.

---

### Post by yuki-nagato on 2010-11-17
> **gothxx said:**
> Got a strange problem...
Somehow i got a folder with the same foldername inside and i cant remove it because nothing happens (says "preparing" but no progressbar is active). Now i have it in my garbage but cant remove it...

It's like this for "infinity", or at least very very very long
```

Folder
|--Folder
   |--Folder
      |--Folder

```is there any way to remove the root folder so i just get rid of the reference? As it is now I believe the system tries to follow the references to the last recursion level and remove when going back so to say.

//thx

That's fascinating that you've managed to somehow create such a beast but in any case 
rm -r /recursive_folder_name is your friend here.  you may, as the second poster suggested, cd to the trash directory and use rm -r to delete the recursive directory.

---

### Post by sisco311 on 2010-11-17
> **gothxx said:**
> Got a strange problem...
Somehow i got a folder with the same foldername inside and i cant remove it because nothing happens (says "preparing" but no progressbar is active). Now i have it in my garbage but cant remove it...

It's like this for "infinity", or at least very very very long
```

Folder
|--Folder
   |--Folder
      |--Folder

```

is there any way to remove the root folder so i just get rid of the reference? As it is now I believe the system tries to follow the references to the last recursion level and remove when going back so to say.

//thx

Try deleting it from the terminal:
```
cd ~/.local/share/Trash/files/
rm -rv Folder
```

If the output is:
```
rm cannot remove `Folder/Folder/Folder<...>/Folder/Folder': No such file or directory
```
Then the path is too long. In that case, try renaming the directories first:
```
cd ~/.local/share/Trash/files/
while [ -e Folder ]; do mv Folder a; cd a; done
```

After 5-10 minutes you can probably skip the command (Ctrl-c).

Then remove the dir:
```
cd ~/.local/share/Trash/files/
rm -rv ./a

```

---

