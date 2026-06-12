---
title: "Permissions question."
date: 2006-02-03
forum: General Help
---

### Post by jeff-- on 2006-02-03
Hey guys, I had a question about some of my file permissions.  For all my music I just copied them over from my windows hard drive, but now in ubuntu they all have lock over the icon, and I can't move the folders or anything because I don't have enough permissions.  The only thing I can do is listen to the music.  Any idead what I can do to give me sufficient permissions on these folders?

Thanks in advance for help :)

---

### Post by Sutekh on 2006-02-03
Yup, for you to copy these files from Windows you'd need do so with sudo.  Sowhen they are copied they are 'owned' by **root**.

You can change the ownership of these files by using the chown command
```
sudo chown -R <username>:<groupname> /<path of your files>
```
just substitute the <username> and <groupname> with your username, and specify the path of the mp3s.

Then to change the permissions, you can use the chmod command or right-click the files and click the boxes under the  'Permissions' tab.
Anyway, chmod
```

sudo chmod -R 777 /<path to your files>
```
This will give full permissions to your files.

---

