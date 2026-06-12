---
title: "file and folder permissions"
date: 2012-01-24
forum: General Help
---

### Post by conradin on 2012-01-24
Hi all, 
I have some files and folders on a computer I want to share with other all other users and groups. I tried 
```
chmod -R a+r /root/SharedStuffFolder 
```
but users cannot enter or read the folder. how do I set read permissions for all users and groups into the contents of a directory?

---

### Post by wolfen69 on 2012-01-24
Can I ask why you are sharing a folder in root? Why not just create a folder in your /home and share there?

---

### Post by Old_Grey_Wolf on 2012-01-24
Using the terminal, try to navigate to the folder you are trying to share in order to determine the path. I don't think Ubuntu will let you navigate to the /root directory; that is, unless you enabled the root user and you are logged in as the root user. If you can't get to the /root directory and I think you can't; then, move the shared folder into another directory. Then type in the pwd command to get the path. Put the path in the following ```
sudo chmod -R a+r <path>
```

Edit: like wolfen69 said, why are you trying to share something in root?

---

### Post by conradin on 2012-01-24
/root was an example, The folder is in my user home directory. I created a test user, and the permissions listed in from the command ll are all question marks. The permissions are getting all screwed up in this folder.

---

### Post by Old_Grey_Wolf on 2012-01-24
Rather than the "ll" command try "ls -al". I don't know if Ubuntu supports the "ll" command.

---

### Post by conradin on 2012-01-24
ll is supported: its in my list of aliases.

```
$ chmod  ug=r,o=r Fu/
$ ls -al Fu/
ls: cannot access Fu/C_Programing: Permission denied
ls: cannot access Fu/.: Permission denied
ls: cannot access Fu/..: Permission denied
ls: cannot access Fu/xc: Permission denied
total 0
d????????? ? ? ? ?                ? .
d????????? ? ? ? ?                ? ..
d????????? ? ? ? ?                ? C_Programing
-????????? ? ? ? ?                ? xc

```

---

### Post by redmk2 on 2012-01-24
> **conradin said:**
> ll is supported: its in my list of aliases.

```
$ chmod  ug=r,o=r Fu/
$ ls -al Fu/
ls: cannot access Fu/C_Programing: Permission denied
ls: cannot access Fu/.: Permission denied
ls: cannot access Fu/..: Permission denied
ls: cannot access Fu/xc: Permission denied
total 0
d????????? ? ? ? ?                ? .
d????????? ? ? ? ?                ? ..
d????????? ? ? ? ?                ? C_Programing
-????????? ? ? ? ?                ? xc

```
To see inside a directory you need to set it to executable.  It would look like this in octal notation```
chmod 775 Fu
```

My guess is this would be like this symbolically```
chmod ug=rwx,o=rx Fu
```

This sets the execute bit on the folder for all.  In other words, to traverse a directory the execute bit needs to be set.

---

### Post by conradin on 2012-01-25
I appreciate the help, but Im still confused. 
What Im looking for is a command to set the permissions to directories to
drwxr-xr-x 
and the permissions to files as:
-rw-r--r--

There is 1 main folder i want to share with several sub-folders, and files inter mixed with other directories. 

When I use the chmod -R option, either the files are set to executable, or the folders become unreadable. I need to recursively set the permissions on directories, and set the permissions on files to something else. I though this would be much easier, but Im so confused now.

---

### Post by conradin on 2012-01-25
Ok, so I have something that works, but code elegance I think it is not. If anyone can improve this method, I would LOVE to see it. 
First, I change all the sub-dirs of Fu to permission 755
```

find Fu/ -type d -exec chmod 755 {} \;

```
Then I change the files to permission 644 so no one is running scripts.
```

find Fu/ -type f -exec chmod 644 {} \;

```

---

### Post by redmk2 on 2012-01-25
> **conradin said:**
> Ok, so I have something that works, but code elegance I think it is not. If anyone can improve this method, I would LOVE to see it. 
First, I change all the sub-dirs of Fu to permission 755
```

find Fu/ -type d -exec chmod 755 {} \;

```
Then I change the files to permission 644 so no one is running scripts.
```

find Fu/ -type f -exec chmod 644 {} \;

```

A quick look at the pertinent man pages revels this> The  letters  rwxXst select file mode bits for the affected users: read
       (r), write (w), execute (or search for directories) (x), [B][COLOR="Red"]execute/search
       only  if  the file is a directory or already has execute permission for
       some user (X)[/COLOR][/B]

So that means this will do what you want recursively 
```
chmod -R u=rwX,go=rX Fu
```

---

### Post by gsgleason on 2012-01-25
/root is not executable by others normally.  In order to use a directory, that directory and all directories in the path must be executable.

---

### Post by conradin on 2012-01-26
> **redmk2 said:**
> A quick look at the pertinent man pages revels this

So that means this will do what you want recursively 
```
chmod -R u=rwX,go=rX Fu
```

redmk2 Has it! Thank you, that works much better than my former method!

---

