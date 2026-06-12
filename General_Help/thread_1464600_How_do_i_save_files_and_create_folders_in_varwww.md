---
title: "How do i save files and create folders in var/www"
date: 2010-04-28
forum: General Help
---

### Post by neoreloaded00 on 2010-04-28
Hello everyone this is my first post.  

I am a web programmer and recently installed ubuntu to to use as a web development OS.  I have run into a few problems that have got me stuck. 

I have installed lamp successfully.  How do i go about creating a new website project in the var/www folder.  I open jedit and try to save a folder or file inside var/www using jedt and it refuses to let me create or save anythink in the var/www directory.

I have used the terminal to create a new folder and file inside the var/www directory and when i open the file with jedit or gedit and write some code into it it wont save the code either.

I am used to just creating a new directory and saving files into it with ease using windows so this is puzzling me a little.  I also installed lamp server through the terminal and the phpmyadmin folder installed somewhere different from the var/www file.

If someone could please explain what i am doing wrong it would be real cool.

Cheers. :-)

---

### Post by tgm4883 on 2010-04-28
Sounds like permissions issues. You will need write access (or you will need to be in a group that has write access) to /var/www

phpmyadmin should be accessible by going to

[http://IPADDRESS/phpmyadmin](http://IPADDRESS/phpmyadmin)

---

### Post by dino99 on 2010-04-28
you are here into the general forum to address basic knowledge to new comers, not devs, you might post into dev forum.

---

### Post by Sin@Sin-Sacrifice on 2010-04-28
If you're going to develop directly from www then you'll have to run any editors and so forth with gksudo (as root). You can press alt+F2 and type ```
gksudo bluefish
``` changing bluefish to whatever editor or program you wish to use.

Edit: Do NOT run your browser as root.

---

### Post by sisco311 on 2010-04-28
Hi and welcome to the forums!

Check out:

[uhelp]community/ApacheMySQLPHP#Virtual%20Hosts[/uhelp]
and
[uhelp]community/FilePermissions[/uhelp]

If you have any future questions, please feel free to ask.

---

### Post by neoreloaded00 on 2010-04-28
> **tgm4883 said:**
> Sounds like permissions issues. You will need write access (or you will need to be in a group that has write access) to /var/www

phpmyadmin should be accessible by going to

[http://IPADDRESS/phpmyadmin](http://IPADDRESS/phpmyadmin)

How do i gain write access or be in a group?  Cheers this forum is very helpfull and real quick with feedback :)

---

### Post by scouser73 on 2010-04-28
**1** - Go to **Applications** > **Accessories** & select **Terminal**, copy & paste this command: > **gksudo nautilus** that will open Terminal as root

**2** - Navigate to the folder or file or drive you wish to gain permissions on, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your folder or file or drive.

---

