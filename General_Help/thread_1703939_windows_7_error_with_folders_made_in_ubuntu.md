---
title: "windows 7 error with folders made in ubuntu"
date: 2011-03-09
forum: General Help
---

### Post by ranvier on 2011-03-09
Hey I'm running Lucid 64 bit and its great. The only problem is I am still dependent on my windows 7 partition. I need it for school and virtualization isn't really an option. When I make a folder in Ubuntu and then move it onto my windows partition from Ubuntu and then reboot and try to open files in that folder in windows. I get this error that says "the directory name is invalid". Moving individual files into windows this way from Ubuntu doesn't seem to cause a problem, neither does moving folders that were originally created in windows. Any ideas?

---

### Post by new_tolinux on 2011-03-09
What names did you use?
I know that folders with "special" characters (like á, ë or ò) give problems, but "normal" characters (a-z, A-Z, 0-9) don't as far as I know.

---

### Post by ranvier on 2011-03-09
Yeah thats just it they all have normal sounding names like big project, no unusual characters. I think its some form of windows issue if I put the folder on a flash drive and then open it up in windows it will work fine. Just not if I place it in the windows file system from Ubuntu.

---

### Post by new_tolinux on 2011-03-09
Are you exceeding the maximum amount of 256 characters (/path/to/very/large/subfolder/name/with/files.txt) ?

---

### Post by ranvier on 2011-03-10
Shouldn't be, the folder i have been testing this on is simply called big project and I'm placing it on the desktop in windows from Ubuntu. The weird thing is it shows up in windows and when trying to open files in it, I get the aforementioned directory error. Although I'm able to move files out of the folder and they will open up just fine. The folder also shows its taking up zero hard disk space in windows.

---

### Post by new_tolinux on 2011-03-10
Strange....
I guess that's more or less a clue that something goes wrong when ubuntu writes folders to the directory-index on your Windows 7-partition. But that's more something that came to mind than an educated guess.
This _could_ mean that your problem will disappear after running scandisk (in Windows). Since running Scandisk won't harm you anyway, that's (at the moment) the best advice I can give you.

---

### Post by mastablasta on 2011-03-10
how is Ubuntu installed? Is it a Wubi install?
 
ok another option is to go into linix console/terminal whatever and then try to see what name the folder has there by typing in dir when in your desktop folder.
 
could it be possible that linux somehow locked the folder with it's user permission? i.e. the folder is not shared with other users.

---

### Post by ranvier on 2011-03-10
Its not wubi, its a dual boot. I hadn't thought to try a scan disk. I'll  try it over the weekend sometime. About the permissions, I thought about  that but the permissions look to be the same across folders. Whats weird is that folders originally made in windows will transfer perfect, just not the other way around. I think your on to something with the permissions though it makes the most sense.

---

### Post by new_tolinux on 2011-03-10
> **ranvier said:**
> I think your on to something with the permissions though it makes the most sense.
It doesn't.

Linux accesses NTFS as Administrator (the default built-in Administrator-account in Windows).

---

### Post by ranvier on 2011-03-10
Alright I seemed to have narrowed it down some more, It only appears to be happening if I place the folder in the desktop directory in windows. If I place the folder in my documents or some other directory i get no errors. Now I'm even more confused lol. Its no big deal I don't really store much on the desktop anyway, I am curious as to what the issue is though with the desktop directory.

---

