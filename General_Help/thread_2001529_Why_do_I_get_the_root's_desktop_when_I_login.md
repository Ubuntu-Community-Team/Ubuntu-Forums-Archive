---
title: "Why do I get the root's desktop when I login ?"
date: 2012-06-11
forum: General Help
---

### Post by Avrit on 2012-06-11
Hi everyone,

Since upgrading to version 12.04 I have problems logging in to the system.
After working around some of these problems (like the 'Places' menu not working, yet consuming a lot of resources and thus slowing down the computer dramatically until killed), I got to a state where I can work, but it's still annoying:
When I login using my own user name (under Gnome - my video card doesn't support the new fancy GUI) I see the root's desktop (/root/Desktop) instead of my own.

I mentioned before the 'Places' problem because it might have something to do with this problem. My workaround was to add a launcher for nautilus to the panel, but in order to see all places I run it with root permissions (gksudo nautilus /home), and since it bothers me to always have to enter my password, I gave myself the permission to run nautilus as root with no password (in /etc/sudoers).

I'd be thankful if anyone can make sense of all of it and advise.

---

### Post by zombifier25 on 2012-06-11
Looks like you did it yourself. In GNOME Nautilus manages the desktop, and since you run Nautilus as root, it has to give root's desktop.

---

### Post by Avrit on 2012-06-11
Thanks [zombifier25]("http://ubuntuforums.org/member.php?u=1251447"),

I guess you're right, so this leads back to the question of the 'Places' menu that doesn't work. Why doesn't it work ?
I'll gladly provide any additional information required, I just don't know where to start figuring it up :confused:

---

### Post by mcduck on 2012-06-11
You could start by chekcing the ownership and permissions of all the directories in your home, and also the Try ~/.config/user-dirs.dirs and it's contents.

And of course keep in mind that if you run Nautilus as root, the places and home directory you see would be root's places and home, not your normal users. (And of course any files you create or copy using root nautilus will be owned by root as well, which is a great way to cause more problems if you deal with any config files that should belong to your normal user...)

---

### Post by Avrit on 2012-06-11
Thanks [mcduck]("http://ubuntuforums.org/member.php?u=17309"),

I made sure all the files in my home directory are under my name, then I removed the nautilus line from /etc/sudoers.

when I choose "Home Folder" from the "Places" menu I see on the tasks panel a new 'tab' saying: "Opening xxx" (xxx being my user name), and after a few seconds it goes away. no other effect, besides the CPU usage jumps from 0%-10% to 65%-95%. this 
state remains until I manually end the nautilus process.

This is why I had to put the nautilus launcher on the panel in the first place, only for that I had to use gksudo, so it comes out that I'm running it as root.

Any ideas ?

---

### Post by mcduck on 2012-06-11
What are the contents of the user-dirs.dirs file I mentioned?

And also, what files you have in your home directory? If possible, try moving any files directly under your home to some other location. If there's a corrupted file or something, Nautilus might hang while trying to display it or generate a thumbnail for it.

---

### Post by Avrit on 2012-06-12
Thanks again mcduck,

The contents of the user-dirs.dirs file is:
[COLOR=Navy]XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
[/COLOR]
About the contents of the home directory, I'm uncomfortable moving them to another location since there are quite a few ini files there, and I don't know what effect it might cause. Is there a way to check the correctness (or at least validity) of the files on spot (something like windows' chkdsk for files) ?

---

