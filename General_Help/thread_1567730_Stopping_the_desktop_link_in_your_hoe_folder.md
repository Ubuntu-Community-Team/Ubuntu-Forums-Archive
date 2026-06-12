---
title: "Stopping the desktop link in your hoe folder"
date: 2010-09-04
forum: General Help
---

### Post by kolo-01 on 2010-09-04
hi,
i think this is either easy or impossible, i want to get rid of the desktop link that reappears constantly in the home folder. it can be deleted but reappears instantly, im not really sure why this is necessary and i would like to stop it reappearing. help appreciated

---

### Post by Ms_Angel_D on 2010-09-04
You might want to check out [Ubuntu Tweak]("http://ubuntu-tweak.com/"), it allows you to tweak certain settings on the desktop as well as having a nice repository of some software you can download and install if you wish. It's one of the first programs I install on a fresh Ubuntu/Kubuntu Setup.

---

### Post by kolo-01 on 2010-09-04
> **Ms_Angel_D said:**
> You might want to check out [Ubuntu Tweak]("http://ubuntu-tweak.com/"), it allows you to tweak certain settings on the desktop as well as having a nice repository of some software you can download and install if you wish. It's one of the first programs I install on a fresh Ubuntu/Kubuntu Setup.

i have installed that but not sure where to go to sort out my problem. i also tried hiding it but it just reappears again after you do that. do you know how to use the tool to solve the problem?

---

### Post by Ms_Angel_D on 2010-09-04
Have a look at [this article on howtoforge]("http://www.howtoforge.com/tweaking-hidden-ubuntu-settings-with-ubuntu-tweak") their are screenshots included it should give you an idea of how it works.

---

### Post by kerry_s on 2010-09-04
you need that folder, the desktop folder is the desktop.

if you don't want nautilus to manage the desktop you can turn that off in gconf-editor.

---

### Post by kolo-01 on 2010-09-04
> **kerry_s said:**
> you need that folder, the desktop folder is the desktop.

if you don't want nautilus to manage the desktop you can turn that off in gconf-editor.

thanks for that, im still in windows way of thinking

---

### Post by WorMzy on 2010-09-04
Nautilus will automatically recreate that directory, as will XDG iirc.

You can tell nautilus not to control your Desktop, and fiddle around with your XDG settings (~/.config/user-dirs.dir), but why go through the trouble? Make the folder hidden by creating a new file in your ~ directory. Call the file ".hidden" and put```
Desktop
```in it. You can add other folders that you don't want to see in this file, one folder name per line. After you've finished adding folder names, save the file and refresh the nautilus window.

You could also change the permissions of the folder with chmod. Remove write permissions from the folder with

```
chmod -w ~/Desktop
```

This will stop you being able to save files into the directory, so you won't be tempted to use it.

---

