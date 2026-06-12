---
title: "Can't create folder because already used in this folder -&gt; can't find it"
date: 2009-07-12
forum: General Help
---

### Post by Aen107 on 2009-07-12
hello community,

In order to start the watermark screenlet on startup, I have to create a directory called "autostart" in /home/xx/.config.
If I try so, it says: "The name "autostart" is already used in this folder. Please use a different name."

Even if I click on "Show hidden files", I am not able to find such an directory.

I am confused.

Ubuntu suggests to create the directory for me when I start the screenlets:
"There is no existing autostart directory for your user account yet. Do you want me to automatically create it for you?"

Unfortunately, this also fails:

"Automatic creation failed. Please manually create the directory:
/home/xx/.config/autostart/"


All hints and tips are welcome!

Bye,
Aen

---

### Post by oldos2er on 2009-07-12
Can you post the output from this command:
```
ls -la ~
```

---

### Post by Aen107 on 2009-07-13
> **oldos2er said:**
> Can you post the output from this command:
```
ls -la ~
```

here you go

```
igor@ubuntuTV:~$ ls -la ~
total 336
drwxr-xr-x 41 igor igor  4096 2009-07-13 18:58 .
drwxr-xr-x  3 root root  4096 2009-06-21 19:44 ..
drwx------  3 igor igor  4096 2009-06-21 19:51 .adobe
-rw-r--r--  1 igor igor   188 2009-07-12 20:04 .asoundrc
-rw-r--r--  1 igor igor   355 2009-07-12 20:04 .asoundrc.asoundconf
drwxr-xr-x 13 igor igor  4096 2009-07-13 20:04 .azureus
-rwx------  1 igor igor  3132 2009-07-12 20:33 .bash_history
-rwxr--r--  1 igor igor   220 2009-06-21 19:44 .bash_logout
-rwxr--r--  1 igor igor  2940 2009-06-21 19:44 .bashrc
drwxr-xr-x  3 igor igor  4096 2009-06-21 17:48 .cache
drwx------  3 igor igor  4096 2009-06-21 18:13 .compiz
drwxr-xr-x  8 igor igor  4096 2009-07-12 16:34 .config
drwxr-xr-x  2 igor igor  4096 2009-07-12 20:34 Desktop
-rw-------  1 igor igor    28 2009-07-13 18:35 .dmrc
drwxr-xr-x  2 igor igor  4096 2009-06-21 17:48 Documents
-rwx------  1 igor igor    16 2009-06-21 17:48 .esd_auth
lrwxrwxrwx  1 igor igor    26 2009-06-21 19:44 Examples -> /usr/share/example-content
drwxr-xr-x  2 igor igor  4096 2009-06-23 18:56 .fontconfig
drwx------  5 igor igor  4096 2009-07-13 18:35 .gconf
drwx------  2 igor igor  4096 2009-07-13 20:03 .gconfd
-rwxr-----  1 igor igor     0 2009-07-12 20:19 .gksu.lock
drwx------ 13 igor igor  4096 2009-07-12 22:56 .gnome2
drwx------  2 igor igor  4096 2009-06-21 17:48 .gnome2_private
drwx------  2 igor igor  4096 2009-07-13 18:35 .gnupg
drwxr-xr-x  2 igor igor  4096 2009-07-12 18:55 .gstreamer-0.10
-rw-r--r--  1 igor igor   104 2009-07-13 18:35 .gtk-bookmarks
dr-x------  2 igor igor     0 2009-07-13 18:35 .gvfs
-rwx------  1 igor igor   489 2009-07-13 18:35 .ICEauthority
drwxr-xr-x  2 igor igor  4096 2009-06-21 18:03 .icons
drwxr-xr-x  3 igor igor  4096 2009-06-21 17:48 .local
drwx------  3 igor igor  4096 2009-06-21 19:51 .macromedia
drwx------  3 igor igor  4096 2009-06-21 17:48 .metacity
drwx------  5 igor igor  4096 2009-06-22 18:46 .mozilla
drwxr-xr-x  2 igor igor  4096 2009-07-10 22:47 .mplayer
drwxr-xr-x  2 igor igor  4096 2009-06-21 17:48 Music
drwxr-xr-x  3 igor igor  4096 2009-07-12 22:56 .nautilus
drwx------  3 igor igor  4096 2009-07-12 20:11 .openoffice.org2
drwxr-xr-x  2 igor igor  4096 2009-07-11 14:46 Pictures
-rwxr--r--  1 igor igor   586 2009-06-21 19:44 .profile
drwxr-xr-x  2 igor igor  4096 2009-06-21 17:48 Public
drwxr-xr-x  2 igor igor  4096 2009-07-12 20:08 .pulse
drwxr-xr-x  4 igor igor  4096 2009-07-12 19:55 pulse-backup
-rwx------  1 igor igor   256 2009-06-21 17:48 .pulse-cookie
-rw-r--r--  1 igor igor 84334 2009-07-13 18:58 .recently-used.xbel
drwx------  2 igor igor  4096 2009-06-27 16:28 .scim
drwxr-xr-x  2 igor igor  4096 2009-06-27 14:49 .screenlets
drwx------  2 igor igor  4096 2009-06-21 17:48 .ssh
-rwxr--r--  1 igor igor     0 2009-06-21 17:49 .sudo_as_admin_successful
drwxr-xr-x  2 igor igor  4096 2009-06-21 17:48 Templates
drwxr-xr-x  2 igor igor  4096 2009-06-21 18:03 .themes
drwx------  4 igor igor  4096 2009-06-21 18:04 .thumbnails
drwxr-xr-x  5 igor igor  4096 2009-07-02 19:31 .transmission
drwxr-xr-x  2 igor igor  4096 2009-06-21 17:49 .update-manager-core
drwx------  2 igor igor  4096 2009-06-21 19:47 .update-notifier
drwxr-xr-x  2 igor igor  4096 2009-06-21 17:48 Videos
drwxr-xr-x  3 igor igor  4096 2009-06-23 18:59 .vlc
-rw-------  1 igor igor   119 2009-07-13 18:35 .Xauthority
-rw-r--r--  1 igor igor 40156 2009-07-13 20:02 .xsession-errors

```

---

### Post by The Cog on 2009-07-13
for me, the command **ls -l ~/.config** shows that ~/.config/autostart already exists:
> steve@Dingly:~$ ls -l ~/.config
total 52
drwx------ 2 steve steve   40 2009-07-02 11:47 autostart
drwx------ 4 steve steve 4096 2009-07-13 14:12 chromium
drwx------ 3 steve steve    8 2009-06-21 16:25 compiz
... I would regard this as the real proof as to whether the directory exists or not.

---

### Post by Aen107 on 2009-07-14
> **The Cog said:**
> for me, the command **ls -l ~/.config** shows that ~/.config/autostart already exists:
I would regard this as the real proof as to whether the directory exists or not.

Thanks, I'll try that out tonight after work!

---

### Post by Aen107 on 2009-07-14
> **The Cog said:**
> for me, the command **ls -l ~/.config** shows that ~/.config/autostart already exists:
I would regard this as the real proof as to whether the directory exists or not.

ok, it gives me

```
igor@ubuntuTV:~$ ls -l ~/.config
total 36
-rwxr--r-- 1 igor igor  215 2009-06-27 14:48 autostart
drwx------ 3 igor igor 4096 2009-06-21 18:00 compiz
drwx------ 2 igor igor 4096 2009-07-12 22:43 gtk-2.0
drwxr-xr-x 5 igor igor 4096 2009-06-27 16:33 Screenlets
drwx------ 2 igor igor 4096 2009-07-14 19:24 totem
drwx------ 2 igor igor 4096 2009-06-21 17:48 tracker
drwxr-xr-x 2 igor igor 4096 2009-07-12 16:34 untitled folder
-rwx------ 1 igor igor  630 2009-06-21 17:48 user-dirs.dirs
-rwxr--r-- 1 igor igor    5 2009-06-21 17:48 user-dirs.locale

```

So the directory is there.
The problem is that 1) I can't see it
2) The Screenlet "watermark" cant see or use it neither.

What to do? 

Thanks!

---

### Post by The Cog on 2009-07-15
You mean you can't "see" it in nautilus? Try the menu View->Show Hidden Files. 

I don't know why the screenlet might not be able to see it though.

---

### Post by Aen107 on 2009-07-15
> **The Cog said:**
> You mean you can't "see" it in nautilus? Try the menu View->Show Hidden Files. 

I don't know why the screenlet might not be able to see it though.

I have already tried "view-show hidden files" in nautilus: Can't see it.

The screenlet can't create the directory automatically (probably because it's already there?) and asks me to do it manually.

 Strange stuff.:-k

---

### Post by JohnFH on 2009-07-15
> **Aen107 said:**
> ok, it gives me

```
igor@ubuntuTV:~$ ls -l ~/.config
total 36
-rwxr--r-- 1 igor igor  215 2009-06-27 14:48 autostart
drwx------ 3 igor igor 4096 2009-06-21 18:00 compiz
drwx------ 2 igor igor 4096 2009-07-12 22:43 gtk-2.0
drwxr-xr-x 5 igor igor 4096 2009-06-27 16:33 Screenlets
drwx------ 2 igor igor 4096 2009-07-14 19:24 totem
drwx------ 2 igor igor 4096 2009-06-21 17:48 tracker
drwxr-xr-x 2 igor igor 4096 2009-07-12 16:34 untitled folder
-rwx------ 1 igor igor  630 2009-06-21 17:48 user-dirs.dirs
-rwxr--r-- 1 igor igor    5 2009-06-21 17:48 user-dirs.locale

```

So the directory is there.
The problem is that 1) I can't see it
2) The Screenlet "watermark" cant see or use it neither.

What to do? 

Thanks!

You have autostart, but it's not a directory, it's a file.  You can't have a directory and a file with the same name.

---

### Post by The Cog on 2009-07-15
> **JohnFH said:**
> You have autostart, but it's not a directory, it's a file.  You can't have a directory and a file with the same name.
Gah! I should have spotted that. Doesnt't explain why it doesn't show up in nautilus though.
 
Before deleting the file, try and find out what's in it:
**cat ~/.config/autostart**

---

### Post by Aen107 on 2009-07-15
> **The Cog said:**
> Gah! I should have spotted that. Doesnt't explain why it doesn't show up in nautilus though.
 
Before deleting the file, try and find out what's in it:
**cat ~/.config/autostart**

```
igor@ubuntuTV:~$ cat ~/.config/autostart
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Screenlets Daemon
Exec=/usr/share/screenlets-manager/screenlets-daemon.py
X-GNOME-Autostart-enabled=true
Name[de_DE]=Screenlets Daemon
Name[et_EE]=Screenlets'i deemon
igor@ubuntuTV:~$ 

```


I always thought that directory and file were the same thing.

The output seems to be the thing that should be in the autostart: autostart the screenlet!

Should I delete it anyway?

---

### Post by CatKiller on 2009-07-15
> **Aen107 said:**
> Should I delete it anyway?

Yes. That directory should be able to contain many .desktop files.

---

### Post by Aen107 on 2009-07-16
> **CatKiller said:**
> Yes. That directory should be able to contain many .desktop files.

Thanks guys.
The solution was to type

```
igor@ubuntuTV:~/.config$ sudo rm -rf autostart

```

Then screenlet was suddenly able to create the directory autostart!

---

### Post by CatKiller on 2009-07-16
Actually, you shouldn't have needed the sudo to remove something from your own Home folder. Sudo is like dynamite; you don't use it unless you **really** have to...

---

### Post by Aen107 on 2009-07-17
> **CatKiller said:**
> Actually, you shouldn't have needed the sudo to remove something from your own Home folder. Sudo is like dynamite; you don't use it unless you **really** have to...

Ok, wasn't thinking about the fact that sudo is not needed in home folder. I am still learning and will try reduce the use of sudo :)

---

### Post by mcduck on 2009-07-17
> **CatKiller said:**
> Actually, you shouldn't have needed the sudo to remove something from your own Home folder. Sudo is like dynamite; you don't use it unless you **really** have to...

And "-rf" options for rm are unnecessary use of force as well.. :D

(-r means recursive, and is used for removing directories with their contents and subdirectories. Not needed for single files. And -f is for force, which shouldn't be used unless you are unable to remove something without that option. It ignores missing files and lack of write permissions for the files etc, and overrides any confirmation prompts.)

---

