---
title: "Why do my home folders appear on my dekstop?"
date: 2011-05-12
forum: General Help
---

### Post by aryzing on 2011-05-12
note: i was about to put this thread in the desktop environment forum since i believe it has to do with using unity, if an admin considers it so, please move the thread if necessary

The problem i have is that the folders i create in my home folder (/home/USRNAME/) now appear on my desktop (but not inside the desktop folder... since it no longer exists, u'll see). After a clean install of 11.04, there were a few default folders in my home folder (documents, music, videos, etc) however, i decided to rename them. After doing that, all of them (even the ones i didnt rename, like ubuntu one and templates appeared on my desktop (but not the desktop folder). I thought they were links, so i deleted the ones i saw on my desktop, and to my suprise, all the folders in my home folder have disappeared! Now everytime i create a new folder in my home folder it appears on my desktop, on top of my wallpaper, and if i delete either of them, both go away. Do you know how to change this behavior?

---

### Post by jerrrys on 2011-05-13
go to Accessories>terminal

in terminal enter **gconf-editor**

then under Apps; navigate to the screenshot and see if box is unchecked

[ATTACH]192033[/ATTACH]

---

### Post by aryzing on 2011-05-13
it is unchecked

---

### Post by matt_symes on 2011-05-13
Hi

You have deleted your Desktop folder in your home directory This is possibly the default behaviour if the Desktop folder is deleted. (Understand, this is a supposition).

Try recreating the Desktop folder in your home directory. It is case sensitive is it needs to be called

```
Desktop
```

Reboot PC.

Please post back if it works.

Kind regards

---

### Post by aryzing on 2011-05-13
should i do anything else? it seems to not work just yet since a folder I created after creating Desktop still appears on the deskotp.

---

### Post by jerrrys on 2011-05-13
try [B]gksudo gconf-editor

[/B]

---

### Post by aryzing on 2011-05-13
it is unchecked aswell

---

### Post by matt_symes on 2011-05-13
Hi

Can you post the output of 

```
cat ~/.config/user-dirs.dirs
```

Copy and paste this into a terminal and copy and paste the results back here.

Also do the same for this command

```
ls -l
```

That is a small L after ls.

Kind regards

---

### Post by Frogs Hair on 2011-05-13
It looks like your home was merged with your desktop because the home icon is missing from your list . Either it is a glitch or the home folder icon was dragged into the desktop from the list in nautilus by mistake.

In the screen shot you can see how the two are separate from each other . I'm not sure how get them apart.

---

### Post by aryzing on 2011-05-13
matt_symes the output of the command is ```
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/"
XDG_DOWNLOAD_DIR="$HOME/"
XDG_TEMPLATES_DIR="$HOME/"
XDG_PUBLICSHARE_DIR="$HOME/"
XDG_DOCUMENTS_DIR="$HOME/"
XDG_MUSIC_DIR="$HOME/"
XDG_PICTURES_DIR="$HOME/"
XDG_VIDEOS_DIR="$HOME/"

```

The output of ls -l is

```

total 2536
drwxr-xr-x 2 aryzing aryzing    4096 2011-05-13 18:40 Desktop
drwxr-xr-x 2 aryzing aryzing    4096 2011-05-13 02:05 dl
drwxr-xr-x 2 aryzing aryzing    4096 2011-05-13 12:20 docs
drwxr-xr-x 2 aryzing aryzing    4096 2011-05-13 18:41 folder created after creating Desktop
drwxr-xr-x 2 aryzing aryzing    4096 2011-05-13 19:25 hello
drwxr-xr-x 2 aryzing aryzing    4096 2011-05-13 02:06 movies
drwxr-xr-x 2 aryzing aryzing    4096 2011-05-13 02:05 music
-rw-r--r-- 1 aryzing aryzing 1014615 2011-05-13 12:29 out.ogv
-rw-r--r-- 1 aryzing aryzing  969380 2011-05-13 12:32 out.ogv.gz
drwxr-xr-x 2 aryzing aryzing    4096 2011-05-13 02:05 pics
-rw-r--r-- 1 aryzing aryzing  572655 2011-05-13 18:42 Screenshot.png
drwxr-xr-x 2 aryzing aryzing    4096 2011-05-13 02:05 templates

```

Frogs Hair I did not drag the home folder onto the desktop or anything similar: I believe it is a glitch or bug.

---

### Post by wojox on 2011-05-13
> **aryzing said:**
> I believe it is a glitch or bug.

It should look like this:

```
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```

---

### Post by matt_symes on 2011-05-13
Hi

> **Frogs Hair said:**
> It looks like your home was merged with your desktop because the home icon is missing from your list . Either it is a glitch or the home folder icon was dragged into the desktop from the list in nautilus by mistake.

I have to agree with this. I think deleting your desktop folder caused this behaviour, although i am unsure if it is a glitch. I think it might be the fall back behaviour if the folder is deleted.

If you just wanted to hide the folders and not delete then you can create a folder called .hidden in your home directory. Then add any folders or files you don't want displayed in that directory in nautilus to that file. You can create a .hidden file in any directory you want and use it to hide files in that directory. It saves having to add a dot in front of the file. Just refresh Nautilus after creating the file.

You will still be able to view then from the command line but they will be hidden in nautilus.

Kind regards

---

### Post by aryzing on 2011-05-13
What would be the effect of putting the names of the directories I have created instead of the ones that are there by default, such as:

```

XDG_DESKTOP_DIR="$HOME/desktop"
XDG_DOWNLOAD_DIR="$HOME/dl"
XDG_TEMPLATES_DIR="$HOME/templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"   this one i dont care cuz i dont have public
XDG_DOCUMENTS_DIR="$HOME/docs"
XDG_MUSIC_DIR="$HOME/music"
XDG_PICTURES_DIR="$HOME/pics"
XDG_VIDEOS_DIR="$HOME/movies"

```

---

### Post by matt_symes on 2011-05-13
Hi

> **aryzing said:**
> What would be the effect of putting the names of the directories I have created instead of the ones that are there by default, such as:

```

XDG_DESKTOP_DIR="$HOME/desktop"
XDG_DOWNLOAD_DIR="$HOME/dl"
XDG_TEMPLATES_DIR="$HOME/templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"   this one i dont care cuz i dont have public
XDG_DOCUMENTS_DIR="$HOME/docs"
XDG_MUSIC_DIR="$HOME/music"
XDG_PICTURES_DIR="$HOME/pics"
XDG_VIDEOS_DIR="$HOME/movies"

```

Then they will be your new directories. It's case sensitive. Either that or you could hide the directories as i specified in my last post.

Kind regards

---

### Post by wojox on 2011-05-13
I've answered this same question a few times. That always resolves it. Did you try to delete your Desktop Folder? Anyway put that in and log out and back in. See what happens. I think matt_symes has answered it a few times as well.

---

### Post by aryzing on 2011-05-13
> **matt_symes said:**
>  If you just wanted to hide the folders and not delete 
Kind regards

Sorry if i was not clear, but i dont want to hide anything, all i wanted was to rename the default folders to more conveniant names. Thanks for the info thought. Still, i am unsure how your proposal would help solve the issue.

---

### Post by matt_symes on 2011-05-13
Hi

I was unsure what you wanted to do so i was offering solutions depending on what you were trying to achieve. If you want to change the names to new folders do as wojox and i have specified.

The easiest way is to right click on the folder and select rename but as you have deleted the folders you need to follow the instructions to fix it.

Kind regards

---

### Post by aryzing on 2011-05-13
> **wojox said:**
> Did you try to delete your Desktop Folder? 

I renamed it, which I guess it the same. 

Ill try what you proposed and after restarting i'll comment on what has happened.

---

### Post by matt_symes on 2011-05-13
Hi

> **aryzing said:**
> I renamed it, which I guess it the same. 

Ill try what you proposed and after restarting i'll comment on what has happened.

If you renamed it it should have updated  ~/.config/user-dirs.dirs. Possibly there is a bug in 11.04 or the behaviour has changed. Editing  ~/.config/user-dirs.dirs should fix it though.

Kind regards

---

### Post by aryzing on 2011-05-13
While in order to change the file I used this code, and the following came back from the terminal, is this bad news?

```


aryzing@aryzing-1215B:~$ sudo gedit ~/.config/user-dirs.dirs 
[sudo] password for aryzing: 

(gedit:1985): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.XD29UV': No such file or directory

(gedit:1985): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:1985): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.OESWUV': No such file or directory

(gedit:1985): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory


```

---

### Post by wojox on 2011-05-13
No sudo just 

```
gedit ~/.config/user-dirs.dirs 
```

---

### Post by aryzing on 2011-05-13
> **matt_symes said:**
> 
If you renamed it it
Kind regards

sorry, technically i moved it with the command mv Desktop desktop

---

### Post by matt_symes on 2011-05-13
Hi

Press Alt + F2 and type 

```
gedit <file_and_path>
```

EDIT: You dont need gksudo here so i have edited my post. I think i just had a senior moment :)

Kind regards

---

### Post by matt_symes on 2011-05-13
Hi

> **aryzing said:**
> sorry, technically i moved it with the command mv Desktop desktop

Yes. That may explain it.

Kind regards

---

### Post by aryzing on 2011-05-13
After modifying the file, the same thing is still happening, but now the folder icon have an additional icon ontop of them. take a look at the screen shot.

---

### Post by matt_symes on 2011-05-13
Hi

Hold on. I will boot into natty and have a look from there.

Kind regards

---

### Post by wojox on 2011-05-13
Delete the files on your desktop or move them into your home. In your screen shot your in your Desktop directory in your home folder creating these folders so naturally their going to show up.

---

### Post by matt_symes on 2011-05-13
Hi

> **wojox said:**
> Delete the files on your desktop or move them into your home. In your screen shot your in your Desktop directory in your home folder creating these folders so naturally their going to show up.

Follow wojox's advice. I have just booted into 11.04 and i can confirm that the solution we have posted does work in 11.04 and allows you to change your desktop directory. 

Kind regards

---

### Post by jerrrys on 2011-05-13
create a new user and see if it will work

---

### Post by matt_symes on 2011-05-13
Hi

> **jerrrys said:**
> create a new user and see if it will work

That would also fix it.

Kind regards

---

### Post by matt_symes on 2011-05-13
Hi

I have got to pick up some speakers. Good luck with the fix.

Kind regard

---

### Post by aryzing on 2011-05-13
sorry i took so long to reply, it was dinner time here in spain. Anyways, i know why my last attempt failed even though I changed the paths in the .config/user-dirs.dirs: because I assigned the desktop to the Desktop directory (with capital D) before creating the Desktop directory, so in not finding the folder, it chose my home directory as my desktop directory. 

Wow, I am amazed at your support, and am truly grateful for it. I have learned a lot today. I hope to be able to help anyone who encountrs this problem in the future. Good night from spain.

---

### Post by wojox on 2011-05-13
> **aryzing said:**
> I hope to be able to help anyone who encountrs this problem in the future.

You will. I deleted my Desktop folder once and had the same problem. That's why I knew where to look. :P

---

