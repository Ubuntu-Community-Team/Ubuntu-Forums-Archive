---
title: "ubuntu folders that is similar to windows c drive?"
date: 2011-05-10
forum: General Help
---

### Post by chuawenching on 2011-05-10
Hi everyone,

I am not sure what to google on this noob question.

In windows, i have c:\ drive and can create folders where i can place my files or install software to.

So in ubuntu, where should have my own files placed to? say software like tomcat and liferay or custom folder.

is it under /usr/ ???

any help?

---

### Post by dasan on 2011-05-10
First of all you can google about "linux folder structure"

All normal and even installation files can be kept at your home folder.
which will be /home/"your username"

if you want to install for all users it should be done with root privilege and it will go to system installation folders like /usr/bin or sbin etc

---

### Post by mcduck on 2011-05-10
Your own files go into your home home directory (*/home/yourusername/*).

What comes to programs, they aren't generally installed into any single location, but instead all files are put into different places based on the file's purpose (for example executable files go to /usr/bin and /usr/share/bin, documentation to /usr/share/doc, system-wide configuration files to /etc and so on). The package manager will handle all this automatically so you usually don't need to pay attention to where a certain program's files are located.

If you wish to install something from outside of the package management, then common locations would be in your home directory (if you just want to install it for your own user account) or /opt (if you want to install for all users). I recommend sticking with the package management way as long as possible, though, and for example both tomcat and liferea are available in the repositories so there really is no reason why you'd install them manually. :)

---

### Post by chuawenching on 2011-05-10
But I ask in liferay forum, i need to download the zip file from liferay (the one bundle with tomcat) and place into a folder itself. 

i saw tutorials having it under /usr/liferay

yeah maybe i need to understand linux folder structure better though .. ubuntu and linux are totally new to me :)

---

### Post by jerome1232 on 2011-05-10
Generally software like that which is manually installed should be placed under /usr/local or /opt.


Then you would create a symnlink to the actual executable in /usr/local/bin so that you can execute the program without writing out it's entire path (/usr/local/bin is in your $PATH variable)

---

