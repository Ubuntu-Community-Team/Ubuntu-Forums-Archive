---
title: "Spotify help"
date: 2012-05-06
forum: General Help
---

### Post by dpuk44 on 2012-05-06
Hi all this is my first post here as I have just install Linux Ubuntu for the first time.
 
I have just download Spotify.exe right clicked it and selected run with wine. I got two files appear on my desktop. 1 x Spotify logo file and 1 x Spotify.lnk. I really want to keep my desktop clean and want to know can i delete these files?
 
Also i removed libreoffice writter shortcut icon by mistake from the left side menu. Is there a way to get this shortcut back. Eg, find the exe file, right click and create shortcut. Where are my program files stored?
 
Thanks

---

### Post by scarleo on 2012-05-06
Yes you can delete them, or even better install the native Linux Spotify client: [http://www.spotify.com/se/download/previews/](http://www.spotify.com/se/download/previews/)

LibreOffice is not .exe, but you can add them back in several ways. Open dash (top icon on launcher menu), search for it and then drag it to the launcher. Or just start the program and right click on the launcher icon for LibreOffice and select Lock to launcher.

---

### Post by dpuk44 on 2012-05-06
Scarleo thats fantastic, much appreciate and the quick reply. I am enjoying the speed and flexibility of Ubuntu, just gotta get used to it I think.
 
Can I ask, you know in Windows you have the C:/Program Files where all the programs are install, well where is that in Ubuntu by default. Iv search but had no luck finding it.

---

### Post by scarleo on 2012-05-06
That depends :)

You need to read up a bit on the linux file system to get a complete answer, actually you can install programs to pretty much anywhere. [http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html)

The short answer is that your programs can be found in folders called bin and where they are depends on what function they have on your system, /usr/bin, /usr/local/bin /usr/local/sbin, /sbin/ are some of the paths and depends on who shall be able to run them.

---

### Post by dpuk44 on 2012-05-06
thats great, thanks again :)

---

### Post by djb6 on 2012-05-06
I'm going to piggyback off this thread.  I am trying to install the linux version of spotify.  I do run a dual boot because my work requires me to have windows, but I really like using Ubuntu on my netbook.  I am checking that link out and I don't really understand what I am supposed to do with the first two steps.  That is something that I have never really understood in linux, editing repositories.  Any help with this would be appreciated.  Thanks!

---

### Post by dpuk44 on 2012-05-06
hey djb6, i too am working on this and have found this that I am following. hope this helps

[http://www.youtube.com/watch?v=4vAta6BFMvw](http://www.youtube.com/watch?v=4vAta6BFMvw)

---

### Post by djb6 on 2012-05-06
I don't have time right now.  I will take a look at that a bit later.  I can't display video yet since I haven't installed all the plugins yet :).  Thanks dpuk44.

---

### Post by dpuk44 on 2012-05-06
no worries just so you know iv just followed it and it works fine (use gedit as editor). welcome

---

### Post by scarleo on 2012-05-06
You guys should explore the wiki and help pages of Ubuntu, there's a lot of information in there:

Editing repositories:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Editing repositories from command line:
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

So basically either through Software Sources with a gui or just do:
```
gksu gedit /etc/apt/sources.list
``` and add the lines for Spotify repos. 
Then:
```
sudo apt-get update # To refresh your newly added repos
```
```
sudo apt-get install spotify # To install Spotify
```

---

### Post by father_ted on 2012-05-06
I used the instructions on the spotify site to load the native linux version. been on it since its release - problem free for me. very happy.

[http://www.spotify.com/uk/download/previews/](http://www.spotify.com/uk/download/previews/)

---

### Post by djb6 on 2012-05-06
I appreciate the help on this.  I am new to using Ubuntu and it is something that I do want to look into more.  I have a new netbook and windows just seems so bloated on it that it can't do much.  I right now am running Ubuntu installed through the wubi installer just so I can get a feel for it.  Problem is, for work, I need to be able to run windows on it as well.  I am now installing Spotify.  I just couldn't figure out how to edit the repositories.  Thanks again!

---

