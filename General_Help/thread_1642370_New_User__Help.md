---
title: "New User / Help"
date: 2010-12-10
forum: General Help
---

### Post by Rgonzales8296 on 2010-12-10
I am a new user to Ubuntu 10.04, so I know very little.

My problems is that while repairing someones PC I back-up files to a my Ubuntu desktop through my network connection, and now it says that they are locked? It will not let me delete them.
Conceptionaly, I know that I need to log on as root, and then delete them, but I do not know how to do that!

Thanks in advance for any assistance that you may be able to offer!

---

### Post by user1001 on 2010-12-10
Open terminal and type 
```
sudo nautilus the/path/to/where/your/files/are
```
then you'll be able to delete your files..
Note: The password for root is your usual password

---

### Post by nothingspecial on 2010-12-10
gksudo for gui apps

---

### Post by Rgonzales8296 on 2010-12-10
It worked! Thanks a lot. 

Would you happen to know of a web location where commands like nautilus and others would be listed and explained?

Thanks for your help!

---

### Post by ajgreeny on 2010-12-10
It is a long job learning all the command line possibilities, but here are three sites with lots of info.
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)
[http://www.onlamp.com/linux/cmd/](http://www.onlamp.com/linux/cmd/)

You should also remember that info about any command can be found in terminal with ```
man <command>
```though some of the output can be a bit cryptic.

---

### Post by ender4 on 2010-12-10
also, the commands "apropos" and "man -k" allow you to search the manuals for programs that match a set of keywords, although often you will get a very long list, and you may want to filter it to section 1 for user commands or section 8 for administration commands, you can do this by passing the "-s" option followed by the number of the section (i.e. 1 or 8) to the apropos or man command.

---

### Post by Habitual on 2010-12-10
> **ender4 said:**
> also, the commands "apropos" and "man -k" allow you to search the manuals for programs that match a set of keywords, although often you will get a very long list, and you may want to filter it to section 1 for user commands or section 8 for administration commands, you can do this by passing the "-s" option followed by the number of the section (i.e. 1 or 8) to the apropos or man command.

everyone forgets about info <command>
Now why is that? :)

Browser-based help could be really useful (printing out commands etc)
[http://ss64.com/bash/](http://ss64.com/bash/)

---

### Post by Rgonzales8296 on 2010-12-10
Thanks for the info! I have a lot to learn, but that Helped. 

After using the command that you gave me it dawned on me that  sudo invoke the root function, while nautilus  is the application to run with the root privilidges.

I guess now I need to learn any other main applications names like "nautilus", that can be used to make system changes that may be needed for other projects.

Thanks for the help, I kinda feel that a light switch has been turned on!

---

### Post by RJ12 on 2010-12-10
One program name that you won't see in the menus is
```
gnome-control-center
``` Which is basically all of the System > Preferences / Administration Menu in on Window (like the Windows Control Panel)

That command doesn't use "sudo" though. So don't type gnome-control-center with sudo, you will be changing root's preferences :)

---

### Post by ender4 on 2010-12-12
Habitual is right. Info is extremely useful. It often has more complete and sometimes more user friendly documentation.

---

