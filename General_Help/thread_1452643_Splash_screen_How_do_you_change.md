---
title: "Splash screen? How do you change?"
date: 2010-04-12
forum: General Help
---

### Post by schwabdale on 2010-04-12
Hello, 
Can someone tell me how to change the initial boot up screen on 9.10? I'm looking for some cool looking boot screens.

---

### Post by wojox on 2010-04-12
Try GDM2 [http://www.ubuntugeek.com/gdm2-setup-a-login-interface-management-utility-for-the-new-gdm.html](http://www.ubuntugeek.com/gdm2-setup-a-login-interface-management-utility-for-the-new-gdm.html)

---

### Post by codemaniac on 2010-04-12
Background colors and images are configured in a script located in **/etc/grub.d/** if you look in there you will find a file called **05_debian_theme** which is the default color scheme for GRUB 2. Now to create your own color scheme you have a few options, you can copy and edit the default 05_debian_theme or create your own script. 
All the files in /etc/grub.d/ are run in order, so if you have 2 theme files, 05_debian_theme and 06_mytheme, the latter (06_mytheme) will be run last, which will be the background you see. 


 
**Copy/Edit Default Colors**

 Copy the default color theme
```

$ sudo cp /etc/grub.d/05_debian_theme /etc/grub.d/05_debian_theme.BACKUP
$ sudo nano /etc/grub.d/05_debian_theme
```

Now you can edit the file to your hearts content.  
**Create a new theme file**

 Create the new theme file
```
$ sudo nano /etc/grub.d/06_mytheme
```

Now you can put whatever you want in here 

 --From the grub2 wiki ..

---

### Post by schwabdale on 2010-04-12
Thanks for all the help everyone!

---

