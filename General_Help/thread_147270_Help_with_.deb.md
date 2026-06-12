---
title: "Help with .deb"
date: 2006-03-19
forum: General Help
---

### Post by matthewinuk on 2006-03-19
I'm having real problems installing a .deb file.
i tried sudo dpkg --install totem_1.3.0-1_i386.deb when i had navigated to the home folder but it said file not recognised.

How do i navigate around the file system in terminal? I made a folder which I added to the home folder called "downloads" but when i typed cd /downloads it didnt recognise it

Is there any way to see what folders are in the one you;re at similar to MS DOS where you type 'dir/w/p'?

thanks:confused: :confused:

---

### Post by Bradl3yJ on 2006-03-19
cd /downloads would enter a download folder on the root of the drive


If you want to enter the downloads folder that is in the folder you are currently in, you need to type:

```
cd downloads
```

ls is the equivilent of dir, the following will show a detailed directory listing

> ls -l

On the first part of each line you will see something like "drwxr-xr-x"

If the first letter is d that means it is a directory

to navigate to the home directory you can type one of these two things:

> cd ~
cd /home/[username]

if you use the second, you need to replace [username] with the account name

---

### Post by Jucato on 2006-03-19
1.You have to use dpkg in the directory were the .deb file is stored.
2. When you type "cd /downloads" what that means is you want to change to the "downloads" directory which is under the "/" (root) directory. So obviously, it will return an error because that does not exist.
3. You can know where you are by looking at the path after your username/hostname. Something like:
```
username@hostname:*path*
```
Anything that has a "~" means it's in the user's home directory.  For example:
```
username@hostname:~/downloads
``` means that you are in the /home/username/downloads directory. 

Remember that terminal commands can either be relative to where you currently, or absolute from the "/" (root) directory (which is what you were doing in #2).

To find out which directory you are in, type
```
pwd
```
in the terminal.

---

### Post by pranith on 2006-03-19
hi,
    The command u are looking for is [COLOR="Red"]ls[/COLOR]
U can try out [COLOR="Red"]dir[/COLOR] also
the command u have to type to go to downloads directory is [COLOR="Red"]cd ~/downloads [/COLOR] or simply [COLOR="Red"]cd downloads[/COLOR] if u r in home itself
/downloads means downloads direcory in "/" directory....
thats y it is giving error...
hope that helps

---

