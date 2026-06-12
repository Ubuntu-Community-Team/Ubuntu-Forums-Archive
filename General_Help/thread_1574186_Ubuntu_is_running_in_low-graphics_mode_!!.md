---
title: "Ubuntu is running in low-graphics mode !!"
date: 2010-09-13
forum: General Help
---

### Post by RatedM on 2010-09-13
[B]hi guys, i think most of you people have heard about this problem !

but i know where i did wrong, i deleted GDM ( Gnome Display Manager ) with the ubuntu desktop system by mistake.[/B] [B]

and then it restarted into low graphics mode with no option but to use that mode and no way to fix it !![/B] [B]

the other options i get don't do anything.[/B] [B]

i continue in low graphics mode with a terminal like screen only .. [/B] [B]:)

please help i just want the files in the home folder and then i will format i DON'T CARE !! [/B] [B]

i attached a screen shot of what i deleted, please take a look for more inf[/B] o.

---

### Post by robsoles on 2010-09-14
Can you access a terminal? Does pressing [CTRL]+[ALT]+[F1] get you a terminal session? If you can get a terminal then you could reinstall GDM.```
sudo apt-get install gdm
```

Is your home directory encrypted?

---

### Post by RatedM on 2010-09-14
> **robsoles said:**
> Can you access a terminal? Does pressing [CTRL]+[ALT]+[F1] get you a terminal session? If you can get a terminal then you could reinstall GDM.```
sudo apt-get install gdm
```

Is your home directory encrypted?


hi my friend, I think I am in the terminal its a black screen with my username and a $ waiting for commands, I tried the sudo thing to download gdm and it finds the package but at the end i get 'could not resolve ubuntu.qatar.cmu.edu'
'failed to fetch [http://ubuntu.qatar.cmu.edu](http://ubuntu.qatar.cmu.edu)'

and no my home folder is not encrypted

---

### Post by robsoles on 2010-09-14
You can (fairly) safely install 'around' your /home directory by manually specifying that the drives are configured as previously configured - installer may whinge about the existing system files but when I resorted to this on someone's PC a while back using 10.04 installer it deleted system stuff before installing anyway.

Don't rush into it. Would you like to try disabling that 'http://ubuntu.gatar.cmu.edu' repository and try to install gdm again?

---

### Post by RatedM on 2010-09-14
> **robsoles said:**
> You can (fairly) safely install 'around' your /home directory by manually specifying that the drives are configured as previously configured - installer may whinge about the existing system files but when I resorted to this on someone's PC a while back using 10.04 installer it deleted system stuff before installing anyway.

Don't rush into it. Would you like to try disabling that 'http://ubuntu.gatar.cmu.edu' repository and try to install gdm again?

yes please show me how to disable the repository and keep in mind that I only have the black screen ( I think terminal ) 
I can't see the desktop or any other file.

---

### Post by realzippy on 2010-09-14
[http://ubuntu.qatar.cmu.edu/](http://ubuntu.qatar.cmu.edu/) is down,indeed.Open sources list:

 ```
sudo nano /etc/apt/sources.list
``` and put a "#" in front of that line to disable.Adding a new source depends on your ubuntu version,so which ubuntu do you run?Can you reach the U.S. main servers from the place you are?

---

### Post by realzippy on 2010-09-14
[I]please help i just want the files in the home folder and then i will format i DON'T CARE !!
[/I]


...if you boot your Ubuntu LiveCD you can mount your filesystem and "burn down" your home stuff.

---

### Post by RatedM on 2010-09-14
> **realzippy said:**
> [http://ubuntu.qatar.cmu.edu/](http://ubuntu.qatar.cmu.edu/) is down,indeed.Open sources list:

 ```
sudo nano /etc/apt/sources.list
``` and put a "#" in front of that line to disable.Adding a new source depends on your ubuntu version,so which ubuntu do you run?Can you reach the U.S. main servers from the place you are?

I don't know how to edit this nano file thing !! 

I'm running the last version 10.4 
I think it was on the U.S. server but I changed it to my country server

how can I burn the files with the live cd ?

---

### Post by realzippy on 2010-09-14
In

Places/computer
the filesystem should occur.
Burn with brasero...

If you are online with linux,you can train "nano" easily with any file (that is not important)..

---

