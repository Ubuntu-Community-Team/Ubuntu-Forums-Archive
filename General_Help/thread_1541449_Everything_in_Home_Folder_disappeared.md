---
title: "Everything in Home Folder disappeared?"
date: 2010-07-29
forum: General Help
---

### Post by kuraykillua on 2010-07-29
I installed Ubuntu yesterday, ran into quite a few problems but I  managed to fix all of the bigger ones, and so far I LOVE Ubuntu. Way  better than Mac or Windows IMO.
However there's also a few smaller problems I'd like to take care of,  and I decided to start a separate thread for each one.
So I don't know what happened, but everything in my home folder disappeared. So, I recreated the folders with the respective names. However, they just don't function the same. The icons look different, they don't register the same way ex: Cairo-dock's shortcuts... the links don't work, they don't show up under Places, and they show up on my desktop. I can't delete them from desktop either because they will simply disappear from the folder as well, which isn't like the real folders.
So my question is how do I get those folders back and get them to look and function the same? Thanks!

---

### Post by viralmeme on 2010-07-29
> **kuraykillua said:**
> So my question is how do I get those folders back and get them to look and function the same? Thanks!
Create a new user and start from scratch again ...

---

### Post by Stefanie on 2010-07-29
I think you might have accidentally enabled the setting "use home as Desktop folder". It makes everything on your home folder show up on the desktop, and if you delete it from the desktop it's deleted from the home folder as well.  Hit alt-f2, enter "gconf-editor" without the quotation marks. Then navigate to apps>nautilus>preferences and untick the line "desktop_is_home_dir". If this option is not ticked, the problem is elsewhere.

About your disappeared folders, I think you might have accidentally deleted them while cleaning up the desktop. Did you look in the trash folder? Maybe you can restore them. Otherwise, you need to recreate the folders, right click > preferences and set their correct icon. To add them to the places menu, I believe there is a "bookmarks" option in the file manager where you can configure which folders show up in the menu.

---

### Post by Stefanie on 2010-07-29
creating a new user is always possible, but that way you won't understand what really happened and you might accidentally do it again.

---

### Post by kuraykillua on 2010-07-29
So, under the Desktop is home option, it's already unchecked. It's not in the Trash either. 
So when I create a new folder, such as pictures, I can change the icon to a folder with a camera... and it still shows up on my desktop.
I seem to be able to add links to Applications, and systems but not places...
I'm tempted to just create a new user but I really want to know what's causing this and what to do if I accidentally delete another folder in the future...

---

### Post by Stefanie on 2010-07-29
are you sure you're working in the home folder and not the desktop folder? give us some screenshots so we can figure it out. did you mess with any settings?

---

### Post by kuraykillua on 2010-07-29
Screenshot attached. The folder is a direct double click of Kuray's Home  on the desktop.
No I didn't mess with any folder settings yet... I have been trying to fix the panels disappearing though, and required to run a few rm -rf commands, but I'm pretty confident that I typed it in correctly. It could be that, of course, but that's the same as deleting the folders right? I'm pretty sure there is a way to get them back...

---

### Post by Stefanie on 2010-07-29
the rm -rf commands might have done the harm. i've been using ubuntu for years and it's not normal to have to run that kind of commands if you want to stop your panels from disappearing. 

anyway, try to drag the "pictures" folder to the left pane, right under the trash icon. normally the folder should show up under the places menu that way. 

about the desktop, i can clearly see on your screenshot that your home folder is set to function as the desktop folder. please run this command:
```
cp ~/.config/user-dirs.dirs ~/logfile.txt
```
this command copies the user-dirs.dirs file from the .config folder to the file "logfile.txt", in your home folder. attach this file to your post so i can look and see if we can solve the problem by editing that file.

---

### Post by kuraykillua on 2010-07-29
I've dragged the folder to the divider under trash, and it just works like a regular shortcut. Can't delete the original because then the shortcut wouldn't work.
So, I did the terminal command, and this is what I got:

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




------------------
Looks like this might work...

---

### Post by cbstryker on 2010-07-29
Here's a thought. When you installed Ubuntu, did it create a separate partition for your home folder? If so, then you may just have a problem with that particular partition not being mounted to /home.

You would still be able to log in, but everything in your home folder would be empty (edit: actually I'd imagine that it would be reset, to be honest, I'm not 100% sure what exactly would be Ubuntu's result, as in, would it create a few default items or nothing at all?). This what it sounds like to me.

Of course if you do not have a /home partition then my post is irrelevant and you should just ignore it.

---

### Post by kuraykillua on 2010-07-29
No, when I installed Ubuntu I just chose to create separate partition for Ubuntu, didn't have an option for separate home folder. Either way, it's on my built in Hard drive, it's not like it could be disconnected.

---

### Post by cbstryker on 2010-07-29
> **kuraykillua said:**
> No, when I installed Ubuntu I just chose to create separate partition for Ubuntu, didn't have an option for separate home folder. Either way, it's on my built in Hard drive, it's not like it could be disconnected.

Did you use "Guided" or "Manual" partitioning during install?

---

### Post by kuraykillua on 2010-07-29
I don't quite remember... probably manual.
Either way what can I do to change the user directories? They all seem to be set on the home folder...

---

### Post by cbstryker on 2010-07-29
> **kuraykillua said:**
> Either way what can I do to change the user directories? They all seem to be set on the home folder...

Can you please explain in more detail? Are you trying to set them up so that they aren't in the /home folder? If so why would you want to do that?

---

### Post by kuraykillua on 2010-07-29
If you look at the screenshot provided earlier, the default folders that are in the home folder are not there. By some unknown means they have disappeared, or deleted. So, in order to recreate the folders, I cannot simply create new folder, and name it the same. The icons are different, and they show up on my desktop, which I do not want them too. They don't show up in Places on the panel, and they don't show up on my cairo-dock shortcuts either.
When I ran the code to list the user directories, they have all been SET TO the home folder. I want to to be set to folders I've created inside the home folder.

---

### Post by cbstryker on 2010-07-29
> **kuraykillua said:**
> If you look at the screenshot provided earlier, the default folders that are in the home folder are not there. By some unknown means they have disappeared, or deleted. So, in order to recreate the folders, I cannot simply create new folder, and name it the same. The icons are different, and they show up on my desktop, which I do not want them too. They don't show up in Places on the panel, and they don't show up on my cairo-dock shortcuts either.
When I ran the code to list the user directories, they have all been SET TO the home folder. I want to to be set to folders I've created inside the home folder.

Ok, if I'm understanding your problem I may have a solution.

First, create a new user:
```
sudo adduser temp
```

Second, copy all the new directories to your /home/kuraykillua directory.

As for seeing your files on your desktop, type this in:
```
sudo gedit /etc/passwd
```

Find your username and make sure it looks something like this at the end:
```
/home/kuraykillua:/bin/bash
```
And not like this:
```
/home/kuraykillua/Desktop:/bin/bash
```

The last one may be a long shot, but worth a try. No idea how it would have been altered in the first place if that is the problem.

As for the user "temp", just type this to get rid of it:
```
sudo userdel -r temp
```

The "-r" is important to clean up the associated /home directories.

Hope all that works.

Edit!: Actually, looking at your screen shot again, it may very well be that you're seeing everything on the desktop is because there is no "/home/kuraykillua/Desktop" folder, so it's just falling back to "/home/kuraykillua". So simply recreating the Desktop folder and the rest of the /home folders as I outlined above should solve that, restarting Gnome may be necessary.

---

### Post by kuraykillua on 2010-07-29
My Ubuntu ended up with another problem... black screen after login. I kinda just decided to reinstall.
I have tried coping identical folders from another ubuntu, but that didn't really do anything. They just appear on my desktop like regular files. I did eventually change the desktop dir to another folder I specified, but I couldn't figure out how to do the same with the rest.

---

### Post by cbstryker on 2010-07-29
> **kuraykillua said:**
> My Ubuntu ended up with another problem... black screen after login. I kinda just decided to reinstall.
I have tried coping identical folders from another ubuntu, but that didn't really do anything. They just appear on my desktop like regular files. I did eventually change the desktop dir to another folder I specified, but I couldn't figure out how to do the same with the rest.

Ya, a reinstall will ultimately give you the best results. Best of luck.

---

### Post by Stefanie on 2010-07-30
Hm, too bad you ended up reinstalling. The file you posted was the key to the solution:

```

XDG_DESKTOP_DIR="$HOME/"
XDG_DOWNLOAD_DIR="$HOME/"
XDG_TEMPLATES_DIR="$HOME/"
XDG_PUBLICSHARE_DIR="$HOME/"
XDG_DOCUMENTS_DIR="$HOME/"
XDG_MUSIC_DIR="$HOME/"
XDG_PICTURES_DIR="$HOME/"
XDG_VIDEOS_DIR="$HOME/"

```

Instead that part of the file should look like this:

```

XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"

```

If you'd just changed this file back to these settings your desktop problem would have been solved. 

cbstryker, your instructions messed things up very badly... You don't need those commands to create a new user anyway.

---

