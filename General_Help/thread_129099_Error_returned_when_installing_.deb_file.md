---
title: "Error returned when installing .deb file"
date: 2006-02-12
forum: General Help
---

### Post by lakelovers on 2006-02-12
I need to install TurboPrint for my Canon i560 printer. I uploaded TurboPrint from a cd and created a deb file from the rpm. That deb file (or folder) is sitting in my /home/jerry/ folder. When I implement "sudo dpkg -i home/jerry/turboprint-1.92-2.i386.deb," I get this error:

" dpkg: error processing /home/jerry/turboprint-1.92-2.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:  /home/jerry/turboprint-1.92-2.i386.deb"

This suggests that I have to give a path to the Archive. I tried adding an archive to the path but I get the same error message.

What should I do?

---

### Post by atoponce on 2006-02-12
This may not be of much help, but first, what command did you use to create the deb file?  Also, what are the permissions of the deb file itself?  You could use alien to install the rpm, rather than making and installing a deb file.

---

### Post by lakelovers on 2006-02-13
I used the command: sudo dpkg -i (path)(file). Also, I just used the "alien" command and it gave me another "deb" file. What am I doing wrong or not doing?

Here's an update. I may have found the problem: the file has a lock on it and the "permisison" page in "properties" the owner has read and write permissions but not "execution" permission. I assume this is a necessary permission to install the file. If so, how do I get the file to permit my "execution?" All the selection boxes are grayed out.

---

### Post by Sutekh on 2006-02-13
[QUOTE=lakelovers]I used the command: sudo dpkg -i (path)(file). Also, I just used the "alien" command and it gave me another "deb" file. What am I doing wrong or not doing?

Here's an update. I may have found the problem: the file has a lock on it and the "permisison" page in "properties" the owner has read and write permissions but not "execution" permission. I assume this is a necessary permission to install the file. If so, how do I get the file to permit my "execution?" All the selection boxes are grayed out.[/QUOTE]

Issue this command on the file
```
chmod +x <file_name>.deb
```
This will add execute permissions to the file.  

If you created the .deb or copied the .deb using **sudo** then you will have to append **sudo** to the above command.
```
sudo chmod +x <file_name>.deb
```

---

### Post by lakelovers on 2006-02-14
Thanks. . . I got the "execution" permission open but I still cannot install the turboprint file. I continut to get this error message:  "cannot access archive: No such file or directory." The turboprint folder is on the desktop and that's where I set path. I tried opening the turboprint folder in the "archive manager" which shows "control.tar.gz;" data.tar.gz;" and "debian-binary." I have no idea where to go from here.

---

### Post by Sutekh on 2006-02-14
[QUOTE=lakelovers]That deb file (or folder) is sitting in my /home/jerry/ folder. [/QUOTE]

[QUOTE=lakelovers]
The turboprint folder is on the desktop and that's where I set path[/QUOTE]
Usually the desktop directory is /home/jerry/Desktop.  So could you confirm the location of the .deb.  Is it /home/jerry or /home/jerry/Desktop?

If you want to use the command line
```
ls -l ~/
```
This will list  - **ls -l** the files in /home/jerry/  - **~/**
and
```

ls -l ~/Desktop
```
This will list  - **ls -l** the files in /home/jerry/Desktop  - **~/Desktop**

---

### Post by lakelovers on 2006-02-14
Okay, I got it installed. Now all I have to figure out is how to get it setup and working with my printer. Thanks for all your help. If you or anybody has experience with Turboprint and Canon i560, I'd appreciate some tips on setup.

---

### Post by Sutekh on 2006-02-14
No need for 'root'

/home/jerry/Desktop is the correct path.

Have you tried these commands (exactly)?
```

cd /home/jerry/Desktop
sudo dpkg -i turboprint_1.92-2_i386.deb

```The reason I ask, is that if you tried to **dpkg** the package in /home/jerry it wouldnt work as *that* file doesn't have execute permissions



A bit more of an explanation:
Heres what you have in /home/jerry
[QUOTE=lakelovers]
Here's what I get with "ls -l ~/" plus a couple of other files:
-rw-r--r-- 1 root root 5357086 2006-02-13 13:04 turboprint_1.92-2_i386.deb[/QUOTE]
See the first part 
```
-rw-r--r--
```
These dashes represent the level or permissions for the file.  The first dash ignore for now.  

The next three dashes represent the permissions for the owner (in this case **root**).  Currently it has read (r), write(w) but not execute(x).  

The next three represent the permissions for the group owner (again **root**) and the last three for everyone else.

*** This file doesn't have execute permissions (as shown by the lack of an 'x')


Heres what you have in /home/jerry/Desktop
[QUOTE=lakelovers]And here's what I get with "ls -l ~/Desktop" plus a few more files:
-rwx------ 1 jerry jerry 5397187 2005-04-15 09:32 turboprint-1.92-1.i386.rpm
-rwxr-xr-x 1 root root 5357074 2006-02-13 13:17 turboprint_1.92-2_i386.deb[/QUOTE]
Again looking at the first part
```
-rwxr-xr-x
```
*** The .deb in /home/jerry/**Desktop** *does* have execute (x) permissions, so I'd like you to try dpkg from there.

---

### Post by lakelovers on 2006-02-14
Thanks for the explanation. It really helps. As I mentioned in the note, above, I do have it installed, thanks to your help, and now I'm trying to figure out how to get it setup to work worlk

---

