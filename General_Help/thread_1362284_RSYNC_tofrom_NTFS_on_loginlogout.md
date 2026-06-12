---
title: "RSYNC to/from NTFS on login/logout?"
date: 2009-12-22
forum: General Help
---

### Post by Toadinator on 2009-12-22
My mother has a laptop and I have just finished installing Ubuntu 9.10 64bit on a separate partition (not Wubi). However, she frequently uses Google Picasa for her photo management and she might use Windows one day and Ubuntu the next. I rsync-ed her photos over from her Vista account to her new Ubuntu account for this, and running rsync on its own works perfectly.

What I want to do is have rsync automatically copy new files from Vista's NTFS partition on login and on logout have it copy things back (with rsync, of course, like I've been using before). I've tried putting rsync commands in .bashrc and .bash_logout like some people suggest, but they aren't working for some reason! If I run the commands I set after I log in, they work perfectly.

Here's how I've set my commands:
```
rsync -a [win directory] [ubuntu directory] #this is for restoring any changes from Windows (goes in .bashrc)

rsync -a [ubuntu directory] [win directory] #this is for syncing changes with windows (goes in .bash_logout)
```

Any help would be appreciated! None of the above types of commands work when they're in those files, but they work fine when I use them after login.

---

### Post by lavinog on 2009-12-23
I think bashrc and bash_logout only run when a terminal is opened.

make a script and add it to the startup applications.
I am not sure what to do about the logout though.
You could have the script run after she closes her photo management program.
(make a wrapper script that will load the program, then run the rsync script.)

---

### Post by Toadinator on 2009-12-23
> **lavinog said:**
> I think bashrc and bash_logout only run when a terminal is opened.

make a script and add it to the startup applications.
I am not sure what to do about the logout though.
You could have the script run after she closes her photo management program.
(make a wrapper script that will load the program, then run the rsync script.)

great idea; I'll try that!

anyone knowing of a good way to sync on logout would be great.

---

### Post by lavinog on 2009-12-23
There might be a way to write the script to stay idle until it receives a signal to terminate, but I think if the sync takes too long, you run the risk of it being terminated prematurely.

---

### Post by dcstar on 2009-12-23
> **Toadinator said:**
> 
.......
What I want to do is have rsync automatically copy new files from Vista's NTFS partition on login and on logout have it copy things back (with rsync, of course, like I've been using before). I've tried putting rsync commands in .bashrc and .bash_logout like some people suggest, but they aren't working for some reason! If I run the commands I set after I log in, they work perfectly.

Here's how I've set my commands:
```
rsync -a [win directory] [ubuntu directory] #this is for restoring any changes from Windows (goes in .bashrc)

rsync -a [ubuntu directory] [win directory] #this is for syncing changes with windows (goes in .bash_logout)
```

Any help would be appreciated! None of the above types of commands work when they're in those files, but they work fine when I use them after login.
For login put a script in System-Preferences-Startup Applications, for logout:
[http://ubuntuforums.org/archive/index.php/t-628616.html](http://ubuntuforums.org/archive/index.php/t-628616.html)

---

### Post by Toadinator on 2009-12-23
> **dcstar said:**
> For login put a script in System-Preferences-Startup Applications, for logout:
[http://ubuntuforums.org/archive/index.php/t-628616.html](http://ubuntuforums.org/archive/index.php/t-628616.html)

Wow, thanks! I'll be sure to try this out (I can't believe I didn't think of it before... I used to do that kind of thing all the time)!

---

### Post by StuartN on 2009-12-23
> **Toadinator said:**
> I rsync-ed her photos over from her Vista account to her new Ubuntu account for this, and running rsync on its own works perfectly.

@reboot is a nice shorthand time in your crontab (man 5 crontab).

I like the automatic backup, but would it not be possible to achieve the mirroring effect by mounting the windows partition in fstab, and linking the Windows pictures folder into the Ubuntu home folder?

---

### Post by lavinog on 2009-12-23
> **StuartN said:**
> @reboot is a nice shorthand time in your crontab (man 5 crontab).

I like the automatic backup, but would it not be possible to achieve the mirroring effect by mounting the windows partition in fstab, and linking the Windows pictures folder into the Ubuntu home folder?

That could be the easiest and would require the least amount of diskspace.  It would however, be vulnerable to a single point failure such as ntfs corruption.

---

