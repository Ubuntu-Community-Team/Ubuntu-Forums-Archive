---
title: "Home Folder Problems"
date: 2009-11-17
forum: General Help
---

### Post by stepstools on 2009-11-17
I did something to my settings, and now Ubuntu thinks the desktop is my home folder.  Does anyone know how to fix this.

---

### Post by bodhi.zazen on 2009-11-17
Did you delete the Desktop directory ?

When you say "I did something to my settings" what was it you were doing exactly ?

---

### Post by dcstar on 2009-11-17
> **stepstools said:**
> I did something to my settings, and now Ubuntu thinks the desktop is my home folder.  Does anyone know how to fix this.

Configuration Editor: /apps/nautilus/preferences/desktop_is_home_dir

---

### Post by stepstools on 2009-11-18
I think I must have deleted it.  And by apps do you mean applications?

---

### Post by stepstools on 2009-11-20
Whoops, scratch that last comment!  I definitely deleted the desktop folder, what to do now?

---

### Post by hwttdz on 2009-11-20
You can probably just create a ~/Desktop folder.  You may have to go to gconf-editor and uncheck /apps/nautilus/preferences/desktop_is_home_dir as dcstar suggested above.

---

### Post by stepstools on 2009-11-20
Ive already done the gconf thing, and where exactly do I put the folder?

---

### Post by bodhi.zazen on 2009-11-20
> **stepstools said:**
> Ive already done the gconf thing, and where exactly do I put the folder?

In your home directory

Open a terminal

Enter the commandd ```
mkdir ~/Desktop
```

---

### Post by michy99 on 2009-11-20
The Desktop folder goes into your home folder.

---

### Post by stepstools on 2009-11-21
So I ran that command, and now I just have a new folder called desktop on my desktop.

---

### Post by hwttdz on 2009-11-21
Note that it is in all likelihood caps sensitive and that you probably need to make the changes to gconf outlined previously.

---

### Post by hwttdz on 2009-11-21
You can also try editing the line in .config/user-dirs.dirs that reads
XDG_DESKTOP_DIR....
to 
XDG_DESKTOP_DIR="$HOME/Desktop"

---

### Post by renkinjutsu on 2009-11-21
it's case sensitive, so name it Desktop instead of desktop

mkdir ~/Desktop

---

### Post by stepstools on 2009-11-21
And where do I find that file?

---

### Post by hwttdz on 2009-11-21
If you were asking about .config/user-dirs.dirs, it's in ~ (being users home).  You should most certainly make the Desktop dir as opposed to the desktop dir first.  It's probably attempting to set your desktop to ~/Desktop which does not exist.

---

### Post by stepstools on 2009-11-21
Whoops, sorry for the miscommunication, the folder is Desktop (with caps).  Anyways, I'm still confused on the.config/user-dirs.dirs thing.

---

### Post by hwttdz on 2009-11-21
At a terminal "gedit ~/.config/user-dirs.dirs" then change the line that reads "XDG_DESKTOP_DIR.....whatever" to "XDG_DESKTOP_DIR="$HOME/Desktop"" save and exit, you should log out-log in before you make this edit.  As it won't change your desktop during a session.  Then after making the edit, log out, log in again.

---

### Post by stepstools on 2009-11-21
Now there is nothing but my external drives on the desktop.

---

### Post by hwttdz on 2009-11-21
And that's not the proper behavior why?  (if you want to not show drives on desktop uncheck "/apps/nautilus/desktop/volumes_visible" in gconf-editor)

---

### Post by stepstools on 2009-11-21
The problem is that all my launchers are in the Home Folder now, and when I try to move them back to the desktop, it says something like, "Cant move file into already containing folder"

---

### Post by hwttdz on 2009-11-21
If you create something on the desktop by right clicking->new file, does it show up in ~/Desktop.  Are the launcher files, I think there're .ink or .desktop in the ~ or the ~/Desktop (or both) folder?  What about moving them through an intermediate folder.  i.e. mkdir temp, mv launcherfiles* temp, cd temp, mv * ~/Desktop

---

### Post by stepstools on 2009-11-22
I just moved them from home to the desktop folder and now everything is back to normal. At least for now...

---

