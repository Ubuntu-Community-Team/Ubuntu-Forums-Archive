---
title: "Broken Repository? Or not?"
date: 2009-08-26
forum: General Help
---

### Post by zkriesse on 2009-08-26
Hey everybody not sure if this is the right forum section. Trying to install PHP5/Apache2 for development(which I got installed)the problem is when I tried a certain way to do it I had to install repositories. Which didn't work. I do have PHP5/Apache2 installed by a different method naturally not requiring the repositories! When I run Sudo apt-get update I get this error. sudo apt-get update
Err [http://us.archive](http://us.archive) jaunty Release.gpg
  Could not resolve 'us.archive'
Err [http://us.archive](http://us.archive) jaunty/main Translation-en_US
  Could not resolve 'us.archive'
Err [http://us.archive](http://us.archive) jaunty/restricted Translation-en_US
  Could not resolve 'us.archive'
Err [http://us.archive](http://us.archive) jaunty/universe Translation-en_US
  Could not resolve 'us.archive'
Err [http://us.archive](http://us.archive) jaunty/multiverse Translation-en_US
  Could not resolve 'us.archive'
Err [http://us.archive](http://us.archive) jaunty-updates Release.gpg
  Could not resolve 'us.archive'
Err [http://us.archive](http://us.archive) jaunty-updates/main Translation-en_US
  Could not resolve 'us.archive'
Err [http://us.archive](http://us.archive) jaunty-updates/restricted Translation-en_US
  Could not resolve 'us.archive'
Err [http://us.archive](http://us.archive) jaunty-updates/universe Translation-en_US
  Could not resolve 'us.archive'
Err [http://us.archive](http://us.archive) jaunty-updates/multiverse Translation-en_US
  Could not resolve 'us.archive'
Err [http://us.archive](http://us.archive) jaunty-security Release.gpg
  Could not resolve 'us.archive'
Err [http://us.archive](http://us.archive) jaunty-security/main Translation-en_US
  Could not resolve 'us.archive'
Err [http://us.archive](http://us.archive) jaunty-security/restricted Translation-en_US
  Could not resolve 'us.archive'
Err [http://us.archive](http://us.archive) jaunty-security/universe Translation-en_US
  Could not resolve 'us.archive'
Err [http://us.archive](http://us.archive) jaunty-security/multiverse Translation-en_US
  Could not resolve 'us.archive'
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release.gpg               
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release               
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages
Reading package lists... Done
W: Failed to fetch [http://us.archive/ubuntu/com/ubuntu/dists/jaunty/Release.gpg](http://us.archive/ubuntu/com/ubuntu/dists/jaunty/Release.gpg)  Could not resolve 'us.archive'

W: Failed to fetch [http://us.archive/ubuntu/com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2](http://us.archive/ubuntu/com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive'

W: Failed to fetch [http://us.archive/ubuntu/com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2](http://us.archive/ubuntu/com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive'

W: Failed to fetch [http://us.archive/ubuntu/com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2](http://us.archive/ubuntu/com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive'

W: Failed to fetch [http://us.archive/ubuntu/com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2](http://us.archive/ubuntu/com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive'

W: Failed to fetch [http://us.archive/ubuntu/com/ubuntu/dists/jaunty-updates/Release.gpg](http://us.archive/ubuntu/com/ubuntu/dists/jaunty-updates/Release.gpg)  Could not resolve 'us.archive'

W: Failed to fetch [http://us.archive/ubuntu/com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_US.bz2](http://us.archive/ubuntu/com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive'

W: Failed to fetch [http://us.archive/ubuntu/com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive/ubuntu/com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive'

W: Failed to fetch [http://us.archive/ubuntu/com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2](http://us.archive/ubuntu/com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive'

W: Failed to fetch [http://us.archive/ubuntu/com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive/ubuntu/com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive'

W: Failed to fetch [http://us.archive/ubuntu/com/ubuntu/dists/jaunty-security/Release.gpg](http://us.archive/ubuntu/com/ubuntu/dists/jaunty-security/Release.gpg)  Could not resolve 'us.archive'

W: Failed to fetch [http://us.archive/ubuntu/com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2](http://us.archive/ubuntu/com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive'

W: Failed to fetch [http://us.archive/ubuntu/com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2](http://us.archive/ubuntu/com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive'

W: Failed to fetch [http://us.archive/ubuntu/com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2](http://us.archive/ubuntu/com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive'

W: Failed to fetch [http://us.archive/ubuntu/com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2](http://us.archive/ubuntu/com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

HELP PLEASE! How do get rid of those repositories? I ask how because they don't show up in my synaptic manager.

---

### Post by lovinglinux on 2009-08-26
Have you tried a different server?

---

### Post by aesis05401 on 2009-08-26
Your repos are stored in a plain text file that you can modify with any text editor. 

From a terminal, for instance, you could type:
```

sudo nano /etc/apt/sources.list

```

This would open the 'sources.list' text file that is located in the /etc/apt/ directory of your system.  You could use gedit or any other text editor as well.

Once you have the file open correct the addresses of the repos that are throwing the us.archive error.  Here is an example of a correct address for 'us.archive' for jaunty main: 
```

deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted

```

Make sure your punctuation matches.  If you have a space or a slash in the wrong place you will receive an error.  

To delete lines you no longer want use ctrl+k in nano, or whatever other method you want in other text editors.  Then save and exit (in nano: ctrl+o, enter, ctrl+x).

Does this help?

---

### Post by zkriesse on 2009-08-26
Yes! Thanks Guys.

---

### Post by P4man on 2009-08-26
looks like your sources.lst is screwed.
Have a look at it here:
```
gksudo gedit /etc/apt/sources.lst
```

Post it here if you're not sure.

edit: damn, Im slow. LOL

---

### Post by zkriesse on 2009-08-26
Uh....gedit won't let me save!

---

### Post by P4man on 2009-08-26
> **P4man said:**
> looks like your sources.lst is screwed.
Have a look at it here:
```
**gksudo** gedit /etc/apt/sources.lst
```



.

---

### Post by zkriesse on 2009-08-26
That brings up a blank file.

---

### Post by P4man on 2009-08-26
oops sorry

```
gksudo gedit /etc/apt/sources.**list**
```

---

### Post by lovinglinux on 2009-08-26
> **Zachk18 said:**
> That brings up a blank file.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by zkriesse on 2009-08-26
[FONT=Verdana]I took out the last two which looked like this. *deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe main restricted universe*[I]
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe[/I][/FONT] [I][FONT=Verdana]
[/FONT]all i did was replace dapper with jaunty. in the file it had these two lines(modified like i just described)i removed them. and i still have the error.
[/I]

---

### Post by aesis05401 on 2009-08-26
> **Zachk18 said:**
> [FONT=Verdana]I took out the last two which looked like this. *deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe main restricted universe*[I]
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe[/I][/FONT] [I][FONT=Verdana]
[/FONT]all i did was replace dapper with jaunty. in the file it had these two lines(modified like i just described)i removed them. and i still have the error.
[/I]

Please post the contents of sources.list.

---

### Post by zkriesse on 2009-08-26
Ok....reloaded my system...it's ok. I needed to anyway so it is all good. Thanks for the info guys.

---

