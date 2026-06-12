---
title: "Changing the usplash on ubuntu 10."
date: 2010-06-04
forum: General Help
---

### Post by cavemanweb on 2010-06-04
Hello, i want to change the boot splash logo/animation like i have changed in 9.10, I download the src of the theme and then make it, then open up startupmanager but i dont have the option to change the usplash theme in the startup manager so I have cheked the usplash package if he is installed and says:
 
sudo apt-get install usplash
 
Error depends of initramfs-tools but he is installed.
 
Can anyone have changed the splash screen when ubuntu starts?.
 
Thanks.

---

### Post by wojox on 2010-06-04
It doesn't use usplash it uses Plymouth. [FoundationsTeam/LucidBootExperience]("https://wiki.ubuntu.com/FoundationsTeam/LucidBootExperience")

---

### Post by dino99 on 2010-06-04
usplash is not used with lucid, and may conflict with plymouth, search about "plymouth" into synaptic to choose a theme

---

### Post by cavemanweb on 2010-06-04
thanks you all, but there is any guide to create my own plymouth theme?.

---

### Post by wojox on 2010-06-04
Try this [Plymouth theming guide]("http://brej.org/blog/?p=158")

---

