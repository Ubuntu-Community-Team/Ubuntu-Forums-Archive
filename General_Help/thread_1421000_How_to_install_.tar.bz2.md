---
title: "How to install .tar.bz2"
date: 2010-03-03
forum: General Help
---

### Post by shadowfax1 on 2010-03-03
I know there's a number of post on here about installing these types of packages but I think I'm losing something here...Downloaded the package unzipped it and transferred to my 'home' directory.
Can someone in layman's terms explain the terminal commands from here..

Thanking you in advance

---

### Post by frt975 on 2010-03-03
Could you link to the file you downloaded?

---

### Post by Enigmapond on 2010-03-03
Can you tell us what you are trying to install??? This would help.

---

### Post by shadowfax1 on 2010-03-03
Vuze_installer.tar.bz2...its actually for a friend who's newer to this than I am.
He doesn't care for 'deluge'

---

### Post by aysiu on 2010-03-03
Go to Applications > Ubuntu Software Center (Ubuntu 9.10) or Applications > Add/Remove (Ubuntu 9.04 or 8.04) and install Vuze through there.

Forget the .tar.bz2 file.

More details here:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Enigmapond on 2010-03-03
To make it easier and accept updates, that is available through the repos.

---

### Post by huangweiqiu on 2010-03-03
Tar.gz is compressed file like zip file. It can't be installed

---

### Post by shadowfax1 on 2010-03-04
The repos don't have the updated one...if you install the repos version it
prompts you to install the update...

---

### Post by aysiu on 2010-03-04
Ignore the prompt? Always best to stick with the repos.

If you insist on using the .tar.bz2 manual download, this is how you would do it. Paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
wget -c http://hwcdn01.vuze.com/files/Vuze_Installer.tar.bz2
tar -xvjf Vuze_Installer.tar.bz2
cd vuze
./azureus &
```

---

### Post by shadowfax1 on 2010-03-04
Tried that but nothing happened except a bunch of scripting then it reported 'errors'
Is there a tutorial or list of commands with an explanation somewhere..

---

### Post by chris_l_13 on 2010-03-04
If you post the 'ls' of the directory where the files were extracted I might be able to help.  There's probably a makefile or a install.sh in there.

---

### Post by aysiu on 2010-03-04
> **shadowfax1 said:**
> Tried that but nothing happened except a bunch of scripting then it reported 'errors'
Is there a tutorial or list of commands with an explanation somewhere.. Here's an explanation: ```
wget -c http://hwcdn01.vuze.com/files/Vuze_Installer.tar.bz2
``` Download the .tar.bz2 file to the current directory.
```
tar -xvjf Vuze_Installer.tar.bz2
``` Extract the archived folder ```
cd vuze
``` Change directories to the one that just got extracted. ```
./azureus &
``` Execute the *azureus* script.

I tried the commands myself. I know they work. The last command will give you a lot of weird output first, but eventually it will launch Vuze.

---

