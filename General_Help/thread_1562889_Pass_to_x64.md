---
title: "Pass to x64"
date: 2010-08-28
forum: General Help
---

### Post by EPurpl3 on 2010-08-28
Hi, i have some issues with my linux and no one knows how to fix it ([http://ubuntuforums.org/showthread.php?t=1562422](http://ubuntuforums.org/showthread.php?t=1562422)) and i want to move to x64, i was wondering if i backup all my setting will those work on a x64 system? If it works that what backup tool is the best?

---

### Post by amauk on 2010-08-28
Looking at your original thread,
you may want to try enabling the reduced resources thing in Gnome

Applications > Accessories > Terminal
Type: gconf-editor

Apps > Metacity > General
Tick "reduced_resources"

---

### Post by jakupl on 2010-08-28
> **EPurpl3 said:**
> Hi, i have some issues with my linux and no one knows how to fix it ([http://ubuntuforums.org/showthread.php?t=1562422](http://ubuntuforums.org/showthread.php?t=1562422)) and i want to move to x64, i was wondering if i backup all my setting will those work on a x64 system? If it works that what backup tool is the best?

I would first give it some time. Maybe the one person that knows the best about this kind of stuff hasn't seen your thread yet. It has only been up for 17 hours. And it's not sure that changing to 64 bit will help.

But to answer your question. Yes. if you back up your /home directory, [it should work fine under 64 bit.]("http://ubuntuforums.org/showthread.php?t=1101348")

---

### Post by EPurpl3 on 2010-08-28
Thanks for the answers.


> **amauk said:**
> Looking at your original thread,
you may want to try enabling the reduced resources thing in Gnome

Applications > Accessories > Terminal
Type: gconf-editor

Apps > Metacity > General
Tick "reduced_resources"

Does this makes linux to look worst? The computer is good enough to handle the standard linux configuration + some compiz effects. The configuration is: 

Core2Duo 2.2Ghz
Ati Mobility Radeon HD2600
4GB ram (sees only 3 on x86)
2xHDD 160Gb (i have no idea how many Rpm)



> **jakupl said:**
> I would first give it some time. Maybe the one person that knows the best about this kind of stuff hasn't seen your thread yet. It has only been up for 17 hours. And it's not sure that changing to 64 bit will help.

But to answer your question. Yes. if you back up your /home directory, [it should work fine under 64 bit.]("http://ubuntuforums.org/showthread.php?t=1101348")

I wanted for some time to install x64 on linux and windows. So i wont change the OS only to repair the problem.

---

### Post by jakupl on 2010-08-28
> **EPurpl3 said:**
> 
I wanted for some time to install x64 on linux and windows. So i wont change the OS only to repair the problem.

Well then you should just go for it.

---

### Post by jakupl on 2010-08-28
In your case, I would back up to an external hard disk using tar.
go to terminal and do something like:
```
tar -pczvf /path/to/backup/destination.tar.gz /home/username
```

and to recover:

```
tar -xzvf /path/to/backup/destination.tar.gz
```

I haven't tried it, but it should do the trick. I don't think you would need super user privileges.

---

### Post by EPurpl3 on 2010-08-28
Thank you, i think that will help, it will also save the themes and the preferences?

---

### Post by jakupl on 2010-08-28
> **EPurpl3 said:**
> Thank you, i think that will help, it will also save the themes and the preferences?

Yes.

---

### Post by EPurpl3 on 2010-08-28
I have found the problem. 

I have installed linux x64, updated, installed the drives for my ATI grafica card, restoret backup files, restarted and, guess what, the same problem apperared. I have created a new admin account, deleted the old one and nothing has changed but the only thing that was still there was the ATI driver. I have uninstalled it and everything works perfect now (at least for the softwares that dont require OpenGL).

---

