---
title: "Error transferring file"
date: 2011-08-04
forum: General Help
---

### Post by linuxuser12345 on 2011-08-04
I get an error message every time I want to save a background to my usr...share...backgrounds folder. ```
Error opening file '/usr/share/backgrounds/aurora2.1.jpg': Permission denied
```
Is there any way I can get permission to transfer the file to this folder? I would like to have some of my own pictures in this folder so I can use them for login screen backgrounds.

---

### Post by fdrake on 2011-08-04
> **linuxuser12345 said:**
> I get an error message every time I want to save a background to my usr...share...backgrounds folder. ```
Error opening file '/usr/share/backgrounds/aurora2.1.jpg': Permission denied
```
Is there any way I can get permission to transfer the file to this folder? I would like to have some of my own pictures in this folder so I can use them for login screen backgrounds.

```
sudo chmod -R 775 /usr/share/backgrounds
```
if you want to share it everybody using the pc use 777

---

### Post by linuxuser12345 on 2011-08-04
I still get the error message. :( 
Can anyone help me?

---

### Post by The Cog on 2011-08-04
[SIZE="10"][COLOR="DarkRed"]No![/COLOR][/SIZE]
> **fdrake said:**
> ```
sudo chmod -r 775 /usr/share/backgrounds
```

This won't work, and it's a very bad idea to mess with system folder permissions anyway. Don't get into the habit of doing that.

Save the image file somewhere within your own home directory and then copy it to /usr/share/backgrounds. You will need to use sudo to copy the file (to gain the needed permissions), either with the command line like this:
```
sudo cp whatever.jpg /usr/share/backgrounds
```
or by launching a root file manager like this:
```
gksu nautilus
```
Be very careful with that file manager - you have permission to thrash the entire system with it.

P.S.
Use these two commands to undo the damage that "sudo chmod -R 775 /usr/share/backgrounds" does:
```
sudo chmod 755 /usr/share/backgrounds
sudo chmod 644 /usr/share/backgrounds/*
```

---

### Post by fdrake on 2011-08-04
@The Cog
opss.. i apologize for the bad advice.  I read a little bit more about the use of /usr and you are right about the write permissions..
my bad !!!:(:

---

### Post by The Cog on 2011-08-04
No Probs, live and learn.

Just a little more explanation:

"sudo chmod -R 775 /usr/share/backgrounds" doesn't give normal users write permissions to the directory (only to user root and members of group root), so they still cannot copy files there. Also, it makes all the image files in that directory executable which is not needed and perhaps undesirable.

---

### Post by linuxuser12345 on 2011-08-04
Actually, I did what fdrake said, only with "777" instead of "775", and I got everything to work fine immediately. It took minimal time and I was able to save my image directly to the backgrounds folder.

---

### Post by linuxuser12345 on 2011-08-04
The Cog, what is the asterisk for in " sudo chmod 644 /usr/share/backgrounds/* " ?
Is that where I enter the filename?

---

### Post by plucky on 2011-08-05
> **linuxuser12345 said:**
> The Cog, what is the asterisk for in " sudo chmod 644 /usr/share/backgrounds/* " ?
Is that where I enter the filename?

The * is the wildcard character which means all folders in that directory will get the chmod 644 applied to them.

---

### Post by The Cog on 2011-08-05
No, the * gets expanded to all the files in that folder. Try > ls /usr/share/backgrounds/* or > echo /usr/share/backgrounds/* for instance.

Interestingly, it is the command interpreter that expands * to a full list of filenames, not the program that's being launched. So for instance, the command "echo *" gets converted to the command echo followed by a long list of file names, and only then does echo get launched with that long list of arguments. Putting the * in quotes prevents that expansion by the shell, so "echo *" and "echo '*'" produce very different results.

You can do things like **ls *.jpg** and the *.jpg will get expanded to the names of all the files that end in .jpg.

---

### Post by Morbius1 on 2011-08-05
Don't mean to nitpick and I admit that in this instance it doesn't matter because the target directory has no subdirectories but .........
> sudo chmod 644 /usr/share/backgrounds/*That will make sure every file within that folder is not executable - that's what you want it to do. But it will also make every sub-folder not executable and that means you won't be able to open it to see what's inside. Folders always have to have an odd octal setting for them to be accessible.

---

### Post by The Cog on 2011-08-05
You're absolutely right. Changing the files but not any subfolders is somewhat trickier. Probably involves "find /usr/share/backgrounds -type f" in some way.

I did check before posting.

---

### Post by Morbius1 on 2011-08-05
You mean this:
```
find /path -type f -print0 | xargs -0 sudo chmod 644
```And if you think I did that from memory without looking at my notes ..... :)

---

### Post by The Cog on 2011-08-05
I think you probably did.

There is also
```
sudo find /path -type f -exec chmod 644 '{}' \;
```
which is equally cryptic

---

