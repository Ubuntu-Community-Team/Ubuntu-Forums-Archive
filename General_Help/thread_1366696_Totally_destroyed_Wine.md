---
title: "Totally destroyed Wine"
date: 2009-12-28
forum: General Help
---

### Post by Cider2000 on 2009-12-28
Hi, i've got a bit of a problem with Wine.

Recently, i moved to Ubuntu Linux knowing that it was possible to install certain windows programs through a program called Wine. 
I was particular interested in Microsoft Office and chose to check the compatibility. On the Wine web-page it looked good, so i gave it a try. 

Following an on-line guide all went well, until the program just crashed. But that's not all. I tried to start the installer again, but it didn't work, because some installation files still were there from the first installation. So i started to delete suspective files but it still didn't work. Regrettably i ended up deleting the entire wine folder thinking, that i could just reinstall it... I was wrong. :(

When i tried to reinstall wine i just got an error message saying, that some packages were missing or the Wine package itself is defect.

But i know nothing is wrong with the packages as i have installed the program in that way before. :confused:

Nothing works, not even the "winecfg" command to restore the C: drive.

If anyone could PLEASE tell me how i can install wine from the ground up with everything. I don't even care about Office anymore. I i can just get wine back.

I just want to know how to make everything work just like when you've just installed the program.

I'm using Ubuntu 9.10
Thanks in advance. :)

---

### Post by RedSingularity on 2009-12-28
When you say deleted are you talking about the "hidden" wine folder?

---

### Post by Cider2000 on 2009-12-28
Not only that folder but every folder that had anything to do with wine  ](*,)

---

### Post by Mr Nemo on 2009-12-28
Did you try sudo purge wine?

---

### Post by hyperdude111 on 2009-12-28
To remove wine open "terminal" via applications - accessories

Then Type:
```
sudo apt-get autoremove wine
```

Then Install wine via a .deb file (similar to .exe)
Download and install either this file for 32bit [http://www.lamaresh.net/apt/dists/lenny/main/binary-i386/wine_1.1.33~winehq1-1_i386.deb](http://www.lamaresh.net/apt/dists/lenny/main/binary-i386/wine_1.1.33~winehq1-1_i386.deb)
or this file for 64 bit [http://www.lamaresh.net/apt/dists/lenny/main/binary-amd64/wine_1.1.33~winehq1-1_amd64.deb](http://www.lamaresh.net/apt/dists/lenny/main/binary-amd64/wine_1.1.33~winehq1-1_amd64.deb)

---

### Post by Cider2000 on 2009-12-28
Nope, doesn't work... I have also tryed to completely remove Wine from synaptic package manager and that didn't work either.

---

### Post by Cider2000 on 2009-12-28
The first part worked perfectly, but when i tried to install the deb package, the handler stated that the package could not be installed because Wine 1.2 was already installed.

But i'm pretty sure that i've checked both the software program and synaptic for Wine programs and programs related to it. :confused:

---

### Post by RedSingularity on 2009-12-28
Have you searched the system for wine related folders to make sure?

sudo find / -name wine*

---

### Post by hyperdude111 on 2009-12-28
Type into terminal 
```
winecfg
```

does anything come up?

---

### Post by Cider2000 on 2009-12-28
To the post from RedSingularity: The shell just gives me some information on how to use the command. Here's what it says: find: paths must precede expression: winetricks.1
Usage: find [-H] [-L] [-P] [-Olevel] [-D help|tree|search|stat|rates|opt|exec] [path...] [expression]

To the most recent post: As i mentioned in my original post on the top, i've already tried the "winecfg" command. It says that it is missing some files (which i have probably deleted).

---

### Post by foxmulder881 on 2009-12-28
So just reinstall WINE from scratch.

---

### Post by hyperdude111 on 2009-12-28
Try 

```
gksu nautilus
```

Press "Ctrl +f" Search in title bar "wine" delete the files you think are associated with the app.

---

### Post by Cider2000 on 2009-12-28
That's what i've tried to do all along. I can't. It just comes up with an error message.

I want to know how to COMPLETELY delete and reinstall Wine.

---

### Post by foxmulder881 on 2009-12-28
Tried using Synaptic? Complete Remove and then Reinstall.

---

### Post by RedSingularity on 2009-12-28
You sure you entered it correct?  

Here try this one

sudo updatedb && locate wine

---

### Post by Cider2000 on 2009-12-28
When i tried to use the shell command i got the following error:

[FONT=Lucida Console](nautilus:5377): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:5377): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:5377): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:5377): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: "net usershare" returnerede fejl 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:5377): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time[/FONT]

I have no idea what this means.

And for the other post: As i've mentioned before i have checked synaptic for remaining pakages.

---

### Post by Cider2000 on 2009-12-28
This command just gives me a huge list of wine files, maybe i haven't deleted them all :confused:

Anyway what should this command do?

---

### Post by RedSingularity on 2009-12-28
> **Cider2000 said:**
> When i tried to use the shell command i got the following error:

[FONT=Lucida Console](nautilus:5377): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:5377): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:5377): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:5377): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: "net usershare" returnerede fejl 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:5377): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time[/FONT]

I have no idea what this means.

And for the other post: As i've mentioned before i have checked synaptic for remaining pakages.


Well thats no good.....how about just

locate wine

Does that work?

---

### Post by Cider2000 on 2009-12-28
This command also just gives me a list of directories and files. I have no idea what to do with them.

---

### Post by RedSingularity on 2009-12-28
If that command is giving a list of directories then there are wine folders you didnt delete.

---

### Post by Cider2000 on 2009-12-29
I also noticed that. Anyway i would still like to make a completely fresh install of wine, so that everything will be as if i've never touched it.

All programs should be deleted, all system files, mostly dll's, should also be restored. Isn't there a simple way to do this, or will i have to do a fresh Ubuntu install?

---

### Post by RedSingularity on 2009-12-29
After you have done **sudo apt-get autoremove wine** then you can use those search commands to find any residual files and delete them manually.

---

### Post by Cider2000 on 2009-12-30
I thought it to be too daunting to delete all the hundreds of wine files, so i chose to make a fresh Ubuntu install.

Of course wine is now working again. Thanks for the help!

---

