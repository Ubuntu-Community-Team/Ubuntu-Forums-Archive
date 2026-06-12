---
title: "Amule does not start."
date: 2006-03-05
forum: General Help
---

### Post by Akli on 2006-03-05
It was working normally untill I changed the directory where the files were downloaded, I restarted Amule but I got an error message:

FATAL ERROR: Bad permissions on TEMP directory

I uninstalld it, and Installed it afterwards but I got the same error message.

How do I do to remove amule completely, with no trace of the previous install?

---

### Post by ow50 on 2006-03-05
The configuration file is ~/.aMule/amule.conf. In there, under section "eMule", you should have lines
```
IncomingDir=...
TempDir=...
```
Both directories must exist and you must have read and write permissions in them.

---

### Post by Akli on 2006-03-05
I can't find the amule.conf file, here is a screenshot of the search:

[[IMG]http://img337.imageshack.us/img337/1967/screenshot5om.th.png[/IMG]](http://img337.imageshack.us/my.php?image=screenshot5om.png)

---

### Post by ow50 on 2006-03-05
[QUOTE=Akli]I can't find the amule.conf file, here is a screenshot of the search[/QUOTE]
If you really want to use the search, you'll need to have it display hidden files. It's under "Select more options" in your screenshot. Also, you can limit that search to your home folder.

Or, you can just use the file browser (Nautilus). In Nautilus, use Ctrl+H to toggle showing hidden files.

---

### Post by Akli on 2006-03-05
How can I get rid of amule? I mean a total uninstall as if I have never installed it, it keeps the ancient configuration and I don't want that.

---

### Post by Akli on 2006-03-05
ow50, 

here is what I get when showing hidden files:

[[IMG]http://img334.imageshack.us/img334/1083/screenshot0ab.th.png[/IMG]](http://img334.imageshack.us/my.php?image=screenshot0ab.png)

I found nothing in the Home directory.

---

### Post by ow50 on 2006-03-05
All aMule settings are saved in the ~/.aMule directory. Removing that directory in addition to removing the amule package(s) with apt-get (with --purge option) or Synaptic (mark for complete removal) constitutes full uninstall.

Based on your search screenshot, you don't seem to have the ~/.aMule directory. If that is true, my next guess would be that you have somehow ruined your home folder permissions. On a fresh install aMule will try to create the temp and incomplete directories under ~/.aMule. Try running the following commands at the terminal. The output should help us know what might be wrong.
```
cd
mkdir .aMule
ls -la .aMule
```
"cd" changes to your home folder (~). "mkdir" creates the .aMule directory and "ls -la .aMule" lists all files in that directory and their permissions.

---

### Post by Akli on 2006-03-05
that's weird:

[[IMG]http://img149.imageshack.us/img149/4517/screenshot16eq.th.png[/IMG]](http://img149.imageshack.us/my.php?image=screenshot16eq.png)

---

### Post by Akli on 2006-03-05
When I use the command "ls", I don't see the .amule folder, but when I try to create the forlder I can't because it exists.

---

### Post by Akli on 2006-03-05
ow50, 

Thank you very much!! I deleted the ./aMule folder and everything got working as before! 

And as before, the ./aMule folder is still hidden, is that normal? I can access it with the "cd  .aMule" but can't see it through the "ls" command.

I have enabled "the show hidden files" in Nautilus and I can see the .aMule folder.

---

### Post by ow50 on 2006-03-05
[QUOTE=Akli]When I use the command "ls", I don't see the .amule folder, but when I try to create the forlder I can't because it exists.[/QUOTE]
"ls" doesn't list hidden files. Try "ls -a".

[QUOTE=Akli]And as before, the ./aMule folder is still hidden, is that normal?[/QUOTE]
Yes. All files and folders, whose names start with "." are hidden in UNIX. All application configuration files and folders directly under your home folder are hidden, it is customary.

---

### Post by Akli on 2006-03-05
I have just read that it's normal, the .amule is by default hidden, that's stupid.

How do we change the properties of a folder? (I don't want it to be hidden), thanks again.

---

### Post by Akli on 2006-03-05
Ok, so I can't change the properties of the folder, anyway, thank you for help ow50, my problem is solved.

---

