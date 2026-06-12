---
title: "Cant move files into folder - permisisons?"
date: 2009-08-22
forum: General Help
---

### Post by mulluysavage on 2009-08-22
I'm trying to drag some files into my usr folder, but can't is this because I need root permission somehow? How do I do that?

---

### Post by wojox on 2009-08-22
Open a terminal:
```
gksudo nautilus
```

---

### Post by chessnerd on 2009-08-22
Well, there is the mv command. 

Example:
```
sudo mv /home/bob/myfile.txt /usr
```

That moves the file "myfile.txt" into the /usr folder.

EDIT: Post above might be better for multiple files

---

### Post by mulluysavage on 2009-08-22
okay, did gksudo nautilus.. then tried to drag and drop - no dice... is there another step?

---

### Post by mulluysavage on 2009-08-22
> **chessnerd said:**
> Well, there is the mv command. 

Example:
```
sudo mv /home/bob/myfile.txt /usr
```

That moves the file "myfile.txt" into the /usr folder.

EDIT: Post above might be better for multiple files

Will this move or copy? I'd like to copy oh and I do have a million files that I want to move

---

### Post by chessnerd on 2009-08-22
> **mulluysavage said:**
> Will this move or copy? I'd like to copy oh and I do have a million files that I want to move

Move, but once it is in /usr you shouldn't need root access to copy it back.

EDIT: Also, command should work for folders.

---

### Post by Buuntu on 2009-08-22
Yes, this is done to protect you.  Your /usr however shouldn't contain anything too crucial (mostly applications). 
To get root permitions you can precede any command in the terminal with ```
sudo
``` For example - ```
sudo mv /$HOME/music /usr/music
``` You will then be prompted for your root password and you should be good :D.

---

### Post by mulluysavage on 2009-08-22
> **Buuntu said:**
> Yes, this is done to protect you.  Your /usr however shouldn't contain anything too crucial (mostly applications). 
To get root permitions you can precede any command in the terminal with ```
sudo
``` For example - ```
sudo mv /$HOME/music /usr/music
``` You will then be prompted for your root password and you should be good :D.

cool so how do I do many many files - the gksudo nautilus didn't work or I was doing something wrong - the screen just flickered and I couldn't drag/drop

---

### Post by chessnerd on 2009-08-22
> **mulluysavage said:**
> cool so how do I do many many files - the gksudo nautilus didn't work or I was doing something wrong - the screen just flickered and I couldn't drag/drop

Put all the files into one folder and the do the mv command for that folder. Example:
```
sudo mv /home/bob/folder /usr
```
That will move the folder "folder" into /usr

---

### Post by Buuntu on 2009-08-22
Lots of posts while I was writing this, so I was a little late :razz:
To copy, you can use
     ```
sudo cp /home/bob/myfile /usr/
``` 

To move many files, you can just copy them all one by one, or if they are all in one directory you can copy that whole directory over with
     ```
sudo cp -r /home/bob/mydirectory /usr/ 
```
(-r means recursively, which is used to copy the contents of directories)

You can also copy all files with similar file extensions or names using an *. * means anything can go there. FE- sudo cp *.jpg would copy all files with a jpg extension, sudo cp F*.* would copy all files beginning with a capital F, and so on...

---

### Post by michy99 on 2009-08-22
Can I ask why you are moving these particular files into /usr? This is a system folder and really shouldn't be used for personal files.

---

### Post by Buuntu on 2009-08-22
> Put all the files into one folder and the do the mv command for that folder. Example:
 	Code:
 	sudo mv /home/bob/folder /usr 
That will move the folder "folder" into /usr
This will work, if you only want the folder by itself :P.  An -r is needed after mv to copy all the files/direcotires inside the folder.

---

### Post by michy99 on 2009-08-22
> **Buuntu said:**
> This will work, if you only want the folder by itself :P.  An -r is needed after mv to copy all the files/direcotires inside the folder.

Um.. no. It will move the directory and everything in it. Where do you think the contents would be left, otherwise?

---

### Post by wojox on 2009-08-22
```
gksudo nautilus
```

Probably to much for a GUI app. Million plus files? Better of with mv command. I tried it to double check, but it was just one file and it worked.

---

### Post by Buuntu on 2009-08-22
> **michy99 said:**
> Um.. no. It will move the directory and everything in it. Where do you think the contents would be left, otherwise?
Oh, sorry... I was thinking of cp :P.

---

### Post by mulluysavage on 2009-08-22
> **chessnerd said:**
> Put all the files into one folder and the do the mv command for that folder. Example:
```
sudo mv /home/bob/folder /usr
```
That will move the folder "folder" into /usr

okay... got 'inter-device move failed, unable to remove target; it is a directory'

---

### Post by mulluysavage on 2009-08-22
> **michy99 said:**
> Can I ask why you are moving these particular files into /usr? This is a system folder and really shouldn't be used for personal files.

trying to get my MAME roms into the roms folder, which is there.

---

### Post by Buuntu on 2009-08-22
Yes, you have to use -r at the end of mv.  Read my post above.
Also I think you have to add a / at the end of /usr (/usr/ not /usr), because if not you are trying to tell it to replace /usr with your folder (I think...).

---

### Post by mulluysavage on 2009-08-22
> **michy99 said:**
> Um.. no. It will move the directory and everything in it. Where do you think the contents would be left, otherwise?

since there seems to be an inter-device problem, I moved my files into a folder on my desktop. where is my desktop folder?

---

### Post by wojox on 2009-08-22
In your user directory. Open a terminal:

```
ls
```

---

### Post by chessnerd on 2009-08-22
> **mulluysavage said:**
> since there seems to be an inter-device problem, I moved my files into a folder on my desktop. where is my desktop folder?

Usually /home/[your name]/Desktop.

---

### Post by 3rdalbum on 2009-08-23
I'm interested as to why "gksudo nautilus" didn't work - are you sure you typed it correctly? It opens up a file browser as root, so any operations that require root access can be done within this window.

Also, I'm not a MAME user but I'm surprised that you need to put your roms into a system-wide location. Have a look at the MAME documentation - I would have thought there would be a per-user location like /home/username/.roms or /home/username/.mame - both of those locations don't require root access.

---

