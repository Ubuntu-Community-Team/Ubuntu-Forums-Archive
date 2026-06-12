---
title: "converting jpg to png."
date: 2011-03-22
forum: General Help
---

### Post by warrior_juggalo on 2011-03-22
I'm trying to put a background on a DVD through DeVeDe, Image i want to use is jpg and it only accepts png, I do prefer to work from terminal so i can learn and become more comfortable with it, But a GUI would be good too.

Thanks in advance.

---

### Post by VCoolio on 2011-03-22
install imagemagick, then
```
convert file.jpg file.png
```
Easy as pie. Create a nautilus script or thunar custom action or whatever for the command to be executed on files and you have a gui too.

---

### Post by WorMzy on 2011-03-22
```
convert input.jpg output.png
```

---

### Post by warrior_juggalo on 2011-03-23
> **VCoolio said:**
> install imagemagick, then
```
convert file.jpg file.png
```
Easy as pie. Create a nautilus script or thunar custom action or whatever for the command to be executed on files and you have a gui too.

Thank you, Worked perfect.

How do i make the script, Is there a tutorial around to learn that sort of thing?

---

### Post by pqwoerituytrueiwoq on 2011-03-23
[http://www.imagemagick.org/script/index.php](http://www.imagemagick.org/script/index.php)
or 
man convert
sudo apt-get install nautilus-scripts-manager

---

### Post by VCoolio on 2011-03-24
Chech [here](https://help.ubuntu.com/community/NautilusScriptsHowto?highlight=%28%28NautilusScriptsHowto%29%29) for a howto on nautilus scripts. Example on image converting [here](http://ubuntuforums.org/archive/index.php/t-609454.html). Don't forget to make the scripts executable (chmod +x file) or they won't work.

---

