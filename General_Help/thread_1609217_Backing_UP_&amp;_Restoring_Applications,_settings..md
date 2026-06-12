---
title: "Backing UP &amp; Restoring Applications, settings..my options?"
date: 2010-10-30
forum: General Help
---

### Post by ram130 on 2010-10-30
hello,

I love Ubuntu and spent hours if not days getting it to work how I want it to. I am trying my best to keep using it but one thing I hate is resetting up everything on a new install. I am currently planning to install Ubuntu on a lot more systems where I work but my only issue right now is a solid back up method.

 I would like to know what are my options for backing up my current installed applications along with their settings and system settings. Then some how with one click have them restored automatically upon  a new installation as if nothing had happen. You know just like how the Android OS backs up users apps and settings to their Google Account. 


Also if you can answer. I've herd others say to back up your home directory. My question is will it restore everything, apps, settings when I copy it back over to a new install? 

Thanks in advance!!

---

### Post by cowdogmoocat on 2010-10-30
you could use ubuntu one to back up your files, and you can always write a list of programs you added on a piece of paper, and then restoring them is as easy as searching for them in software center or synaptics.

---

### Post by Verbeck on 2010-10-30
you make make a distributable copy of the existing installation along with all the applications using remastersys

[http://www.geekconnection.org/remastersys/repository/karmic/remastersys_2.0.17-1_all.deb](http://www.geekconnection.org/remastersys/repository/karmic/remastersys_2.0.17-1_all.deb)

none of the applications are installed in the home directory, only the settings are. there should be a couple of folders starting with a  (.) period

---

### Post by ram130 on 2010-10-30
Thanks for the reply guys! I'm looking for a program that can back up all the applications installed as they are and then restore them to a new system. If possible let me select which  to not install or so fort. Are there no other options? This is what is preventing some of my friends from switching currently and me from installing from more systems. I would have thought this kind of thing was sorted already since it's native in Android.

I also herd about OneConf but not sure how it works. Please help.

---

### Post by ram130 on 2010-11-14
Guys if I back up my home folder and restore it on a new installed system will all my applications be restored??

Guess I'm asking for a impossible thing.

---

### Post by oldfred on 2010-11-14
/home will have all your user settings for your software, but that does not reinstall the apps.

To reinstall apps:
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

I export list of apps and have created a small script to edit fstab, mount partitions, reorganize as I want it and use the list to reinstall all my apps. I started small with just a few commands that I had run in the command line and then listed history to have the commands. Then started adding them to a bash file to rerun them.

---

### Post by ram130 on 2010-11-24
> **oldfred said:**
> /home will have all your user settings for your software, but that does not reinstall the apps.

To reinstall apps:
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

I export list of apps and have created a small script to edit fstab, mount partitions, reorganize as I want it and use the list to reinstall all my apps. I started small with just a few commands that I had run in the command line and then listed history to have the commands. Then started adding them to a bash file to rerun them.

Well thank you for all the information. This is really helpful! I guess I will just have to work with this method for now until Ubuntu gets more advanced/friendly in the area.:)

---

### Post by kanishkdudeja on 2010-11-24
aptoncd will be a good choice

---

### Post by nl4m on 2010-11-24
I do not know if this will help. But you can type is command to find out the exact path of any program.

```
type bash
```

You can change "bash" with the name of the program, like "firefox". For the most part the applications/programs are stored in "/usr/bin". Of course programs need other files to work so backing up the main file may not do you much good, in most cases. Just test it out before you make the big move.

---

### Post by ram130 on 2010-11-24
> **kanishkdudeja said:**
> aptoncd will be a good choice

I like the idea. I'm gonna try and see if it works out ok. I'll let you know.

---

### Post by ram130 on 2011-05-11
Sucks I got to use a cd though..:( ..

---

