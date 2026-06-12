---
title: "Need help with remastersys distro backup"
date: 2010-11-29
forum: General Help
---

### Post by ivarn on 2010-11-29
Hey. I want to make a distro backup but with my own customized menus (apps, places and system). 
SO, what file from my home folder do I overwrite with what file?
Thanks in advance :)

---

### Post by JOHNNYG713 on 2010-11-29
Make your tweaks, back up your browser bookmarks, clean your system I recommend Ubuntu tweak and bleachbit (NOT AS ADMINISTRATOR!!) sudo nautilus ( in terminal ) open your home folder,click "veiw" click "show hidden files" copy and past your unhidden home folder to a CLEAN ect/skell folder, while folders are still grayed out right click any gray folder, click properties, click permissions and set "group" and "others" to " Access Files " This is important ! close all open windows and terminal, open remastersys and have at it!!! Good luck !:p

---

### Post by ivarn on 2010-11-29
Thanks but that is not what I asked.
I would have done all that cleanup work if I was going to do a private backup.
But I want to make a distro backup.
So again. I want to keep the customized start menus in my distro backup.
So what file do I overwrite with what file and where?

---

### Post by ezsit on 2010-11-29
Most of the settings are contained in the hidden folders
.gconf
.gconfd
.gnome

and maybe a few others, you will have to look through Gnome documentation for the rest. Copy these folders to /etc/skel directory like so from your /home folder:

sudo cp -r .gconf /etc/skel/
sudo cp -r .gconfd /etc/skel/
sudo cp -r .gnome /etc/skel/

As I said, you will probably find another couple of folders from your /home directory useful, but the ones I listed should get you started. By the way, the other poster gave you good advice too. I don't copy my entire /home folder because it is not needed, but doing so would definitely preserve the settings you mentioned.

---

### Post by ivarn on 2010-11-29
Thanks a billion :)
So I guess all the gnome settings (menus and panels) are all in the .gnome2 folder, right?
So if I just copy that folder to /etc/skel they will be a part of the OS when I install the backed up dvd?
So, do I need to chmod and group all the files and folders in order to take effect for all the users?

---

### Post by ezsit on 2010-11-29
If you copy the .gnome2 folder with the sudo or as root you should not need to change the ownership of the files, they will be copied as root and owned by root.

Here is another reference if you really want to tweak the files manually:
[http://www.yolinux.com/TUTORIALS/GNOME.html#GCONF](http://www.yolinux.com/TUTORIALS/GNOME.html#GCONF)

I got this from Remastersys's website under the INFO link.

---

### Post by ivarn on 2010-11-29
Thanks a lot!
Does anyone know the specific files for the panel settings, start menu settings and desktop background settings? Since these are the only customized things I want on the distro.
Also, there's no such directory as .gnome. I have .gnome2 though.
The menu icons and sub menus are located in /home/ivarn/.local/applications and desktop directories.
But what about the settings? You know, in which sub menu the apps and games are.?
Also, what and where's the config file for what background I use? I know the background links are in the file called backgrounds.xml under .gnome2.
But all the icons and stuff is unnecessary to backup cuz they will be installed with the program anyway and relocated from their icon folders (i.e /usr/share/icons). 
So what I need to backup is the settings for everything.
Not literally everything but you know. Panels, menus, background.
I wish I could google for this but as you can tell, I don't know the pc words for everything so I don't really know what to look up.

---

### Post by ivarn on 2010-12-20
So how do I set group permissions to everything in the etc/skel from terminal?
Using the drop down list in properties>permissions is the worst nightmare. It has like 100 entries.
Also, should the skel folder remain root or doesn't it matter?

EDIT: So in order to set everything in /etc/skel as group I need to run this command:
sudo chmod -R 755 /etc/skel ?
I believe 755 is group. Not sure. these things are very advanced to me.

---

### Post by ivarn on 2010-12-23
Bump

Hey can somebody please help me here?
I really want this thing to work, and now when all the folders has root permission I don't know if remastersys will send them from /etc/skel to the username folder during the installation, so what do I do here?
I need to change the skel folder to group permission, right?
So, how?

---

### Post by ivarn on 2010-12-24
Oh wait, you mean the section Root and Others must be access files and not read and write?
But they must all be root, right?
I think I got it now. sorry for my misunderstanding.

---

