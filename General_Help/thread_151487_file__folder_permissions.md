---
title: "file / folder permissions"
date: 2006-03-28
forum: General Help
---

### Post by m.musashi on 2006-03-28
If there is one thing I still don't get (and actually there are still many) it's file permissions - or more specifically, changing them.

I read some wiki pages on chmod and chown but I still don't get it. I find it frustrating when I want to move a file from my /home to somewhere else. Invariably, the new location is owned by root and I do not have permission to write there. I know there are good reasons for this but if I want to copy a new desktop background to the /usr/share/wallpapers folder (humor me) I can't unless I do it from a terminal with sudo.

Now, I know I can use chmod 777, for example, to make a file rwx by everyone but that only seems to work if I own it to begin with. What happens when I want to do that with a file owned by root? Do I have to enable root login or use sudo? And what do I do when I want to change the permissions of a FOLDER and not a file?

If anyone can explain this without a bunch of mumbo jumbo that would be great. I also read several wiki pages on file permissions and didn't find them overly helpful.

Thanks.

EDIT: one more thing, is there a way to open/run nautilus as root so that you can move files around? I know it's probably not recommended but does that mean you can't...never?

---

### Post by Blunts on 2006-03-28
As I am lazy, I prefer to enable root acces and root login. I switch to it by logging out and logging in as root. This can be done by : 

 How to set/change/enable root user password


```
sudo passwd root
```


How to disable root user account


```
sudo passwd -l root
```


How to allow root user to login into GNOME

    * Read #How to set/change/enable root user password
    * System -> Administration -> Login Screen Setup
    * Login Screen Setup 

Security Tab -> Options -> Allow root to login with GDM (Checked)


How to switch to root user in Console mode
 
```
sudo -s -H
```
```
Password: <specify user password>
```

Then there are no permission problems. Its not the right/secure way but if you want it simple, its the good way.

---

### Post by IYY on 2006-03-28
> 
Now, I know I can use chmod 777, for example, to make a file rwx by everyone but that only seems to work if I own it to begin with. What happens when I want to do that with a file owned by root? Do I have to enable root login or use sudo? And what do I do when I want to change the permissions of a FOLDER and not a file?

Obviously, if the file is owned by root, you have to be root in order to change its permissions. Would be quite silly otherwise. So... Use sudo. If you want to change the permissions of a folder, you can treat it like a file but then you're not doing anything to the subdirectories and files in it. The best idea is to use the -R (recursive) argument. For example, chmod -R 777 /some/folder will change the permissions not only on the folder, but on anything in it. 

Chown is used to change the owner of the file.

> EDIT: one more thing, is there a way to open/run nautilus as root so that you can move files around? I know it's probably not recommended but does that mean you can't...never?

Sure. **sudo nautilus --no-desktop**.

---

### Post by m.musashi on 2006-03-28
Cool. Thanks for the ideas. I'll play around with these and see if I can't get it to do what I want.

---

### Post by jazzgossen on 2006-03-28
I don't really understand why so many people use octal arguments to chmod ("chmod 777" etc). I find that it's much easier to use the alphabetical flags.

Like:
"chmod u+w file" to add write rights for the user (owner) of a file
"chmod a+rw-x file" to add read/write rights, but remove execution rights, for all

and so on. That feels much easier to remember than those number flags.

---

### Post by trent dillman on 2006-03-28
You shouldn't use chmod too loosely. You can seriously mess up your system, or worse yet allow unauthorized access to integral parts of the OS.

---

### Post by m.musashi on 2006-03-28
[QUOTE=jazzgossen]I don't really understand why so many people use octal arguments to chmod ("chmod 777" etc). I find that it's much easier to use the alphabetical flags.

Like:
"chmod u+w file" to add write rights for the user (owner) of a file
"chmod a+rw-x file" to add read/write rights, but remove execution rights, for all

and so on. That feels much easier to remember than those number flags.[/QUOTE]
chmod 777 makes sense to me because that is one I know. If you asked me to something wierd like x by owner rw by group and r by user or something like that I wouldn't have a clue in either system. What is the equivalent of 777 in alpha?

Actaully, I'm not into chmoding a bunch of stuff. There are just times when I want to put a file in a folder that is not /home - specifically theme tweaks. If you want to change the usplash you might want to move the new file to the same location as the old and unless you use sudo you can't (or log in as root). Or if you want to add all your backgrounds to the same folder as the defaults (an issue in KDE not gnome) you can't. I get the benefits of this but sometimes I'd just like to be able to drag and drop a file and not hassle with permissions. Maybe windows spoiled me (I always run as admin - and yes I know that is considered unwise but I've never had a problem yet)

---

### Post by towsonu2003 on 2006-03-28
[QUOTE=Blunts]As I am lazy, I prefer to enable root acces and root login. I switch to it by logging out and logging in as root. This can be done by : 

 How to set/change/enable root user password


```
sudo passwd root
```


How to disable root user account


```
sudo passwd -l root
```


How to allow root user to login into GNOME

    * Read #How to set/change/enable root user password
    * System -> Administration -> Login Screen Setup
    * Login Screen Setup 

Security Tab -> Options -> Allow root to login with GDM (Checked)
[/QUOTE]
I felt like this should be linked around here... not to offend anyone, but read this bf enabling the root account: 
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

