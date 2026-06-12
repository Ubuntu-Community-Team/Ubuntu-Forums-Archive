---
title: "Keep files, remove parent folder"
date: 2011-05-07
forum: General Help
---

### Post by mtthwjsph on 2011-05-07
Im pretty new to linux and Ive hit a wall. I have a folder 'forum'. I need all files and subfolders but I dont want them in forum. I have tried it with the gui, but it wont let me paste them. How do I move all the folder data without moving the folder itself via terminal? Any help would be GREATLY appreciated

---

### Post by josephku on 2011-05-07
Why don't you "rename" the folder to the new parent folder and create a new folder with the old name?

---

### Post by WorMzy on 2011-05-07
```
mv /path/to/folder/* /destination/folder/
```

If your folder has hidden files and folders (e.g. files beginning with a ".", like .settings), then enable dotglob option first.

In bash, you do this by running
```
shopt -s dotglob
```
In zsh:
```
setopt dotglob
```

Not sure about any other shells.

---

### Post by mtthwjsph on 2011-05-07
Its all sitting in the folder i need it in... if that makes any sense. to help me learn linux better, i decided to make a home web server as a little project. installed apache, mysql, etc. i grabbed a open source website to put on it. the instructions say to put it in var/www/"domain"/ and then run index.php in firefox. i placed the folder forum there, but it doesnt run in firefox. only thing different from the code they say to put in the url bar is the fact that i left all of the files in the forum folder. but adding forum to it doesnt make it work. after 5 hrs or so reading faqs and installation guides and just kinda staring at the screen, the only thing i can figure is get rid of the folder forum. my files are /var/www/"domain"/forum/install/index.php. the guide says it should be /var/www/"domain"/install/index.php. i could be barking up the wrong tree in all honesty. but i have reread all the installation files for apache2, mysql, phpmyadmin, and bee hive forum. this is the only thing that is different, and the only thing not working

---

### Post by WorMzy on 2011-05-07
What address are you opening in Firefox? You need to go to [http://localhost]("http://localhost") to access your webserver, and not [file:///var/www]("file:///var/www").

If you're going to the second URL, you won't be "served" pages by apache, and so firefox will just ask you what you want to do with the file (much like nautilus does when it's faced with a file type it doesn't know what to do with).

Also, are you sure you've installed both the php5 and libapache2-mod-php5 packages?

---

