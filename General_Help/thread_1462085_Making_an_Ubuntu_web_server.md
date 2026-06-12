---
title: "Making an Ubuntu web server"
date: 2010-04-25
forum: General Help
---

### Post by fterh on 2010-04-25
I have Ubuntu desktop installed, and I want to play around, try building a web server, etc.

Should I reinstall Ubuntu (server) or manually install Apache, etc.? I'm an advanced PC user, but very new to Linux, although I learn quite fast.

---

### Post by SnickerSnack on 2010-04-25
Just install apache.  Ubuntu server lacks a gui and many other programs that a desktop user often needs, so (assuming this is your main computer) by installing the server edition, you'll end up taking one step forward and ~100 steps back.

You should also install php and maybe even mysql.

---

### Post by rjcroy on 2010-04-25
Yes, just install Apache and any other packages like databases and programming languages / Apache mods that you need. They will all be in the Repository. Ubuntu, and Linux generally, is not like Windows where you buy a flavor on the OS and only get certain features. All the server software and features are available for the desktop version.

---

### Post by wmatthews on 2010-04-25
Whenever I decide to install LAMP I just run.

sudo tasksel install lamp-server

---

### Post by fterh on 2010-04-25
> **rjcroy said:**
> Yes, just install Apache and any other packages like databases and programming languages / Apache mods that you need. They will all be in the Repository. Ubuntu, and Linux generally, is not like Windows where you buy a flavor on the OS and only get certain features. All the server software and features are available for the desktop version.

By repository you mean Ubuntu software center? I wanted to try some hands-on by downloading Apache source and building it, but I got lost at step 2 (configuring). :P

---

### Post by Paper Tiger on 2010-04-25
Yep, the software centre, I've just done exactly the same thing.

I installed apache, mysql and php

Apache will set it's root directory in /var/www, which without using sudo and a command prompt you won't have permission to copy your project files into.  So, I changed my apache root directory to /home/papertiger/www - if you want to do the same then the files to be modified are /etc/apache2/sites-available/default and default-ssl

Of course if someone has a better way of changing the default web root then please post after me because I'd like to know too, (I'm also a newbie but figuring things out by myself for the most part)

---

### Post by fterh on 2010-04-25
I ran the configure script with the following options:

```
./configure --no-create --quiet
```

However at the end of the output it states:

```
Construct makefiles and header files...

creating config_vars.mk
```

And files **were created**. Any idea why?

Edit: Another question. I installed LAMP (successfully) but made a blunder by ```
sudo chown -R root
``` the directory (and its files). Naturally I couldn't chmod the index.html. I tried ```
sudo chmod 755 index.html
``` but it doesn't work either. How come? By sudo chmod I'm chmod-ing it as root, no?

---

### Post by fterh on 2010-04-25
> **fterh said:**
> I ran the configure script with the following options:

```
./configure --no-create --quiet
```

However at the end of the output it states:

```
Construct makefiles and header files...

creating config_vars.mk
```

And files **were created**. Any idea why?

Edit: Another question. I installed LAMP (successfully) but made a blunder by ```
sudo chown -R root
``` the directory (and its files). Naturally I couldn't chmod the index.html. I tried ```
sudo chmod 755 index.html
``` but it doesn't work either. How come? By sudo chmod I'm chmod-ing it as root, no?
Bump!

---

### Post by Gunman1982 on 2010-04-25
> **fterh said:**
> I ran the configure script with the following options:

```
./configure --no-create --quiet
```

However at the end of the output it states:

```
Construct makefiles and header files...

creating config_vars.mk
```

And files **were created**. Any idea why?

Edit: Another question. I installed LAMP (successfully) but made a blunder by ```
sudo chown -R root
``` the directory (and its files). Naturally I couldn't chmod the index.html. I tried ```
sudo chmod 755 index.html
``` but it doesn't work either. How come? By sudo chmod I'm chmod-ing it as root, no?

Most software you compile from source has 3 steps:

./configure (Checks if you have the needed libs installed, disables/enables supported stuff)

make (builds the executables dependant on what was configured in teh 1. step)

make install (moves the executables to the system, most of the time you run it with sudo since you can't write to systemfolders otherwise)

Since you already installed lamp from the repository those 3 steps shouldn't be necessary.
So: Where did you do this chown and why? You don't need to change the permissions of the index.html file since its not executed by the system (doesn't need execution flag) but is interpreted by the apache webserver. 
Where did you save the index.html, what happens when you access [http://localhost/index.html](http://localhost/index.html) and what is in the logs?

---

### Post by fterh on 2010-04-26
> **Gunman1982 said:**
> Most software you compile from source has 3 steps:

./configure (Checks if you have the needed libs installed, disables/enables supported stuff)

make (builds the executables dependant on what was configured in teh 1. step)

make install (moves the executables to the system, most of the time you run it with sudo since you can't write to systemfolders otherwise)

Since you already installed lamp from the repository those 3 steps shouldn't be necessary.
So: Where did you do this chown and why? You don't need to change the permissions of the index.html file since its not executed by the system (doesn't need execution flag) but is interpreted by the apache webserver. 
Where did you save the index.html, what happens when you access [http://localhost/index.html](http://localhost/index.html) and what is in the logs?
My question was, is ```
./configure --quiet
``` supposed to create any files? Because it created a file (forgot the name) and I wasn't expecting it to.

Heh, I know I can take a shortcut by installing LAMP directly, but I thought I'd play around with terminal and install the components manually :D

Did the chown in terminal after installation, made a mistake and changed owner to root. It's working now after I "sudo chown fabian", but I'm just wondering why won't "sudo chmod 755 index.html" work since by having a "sudo" in front I'm running the command as root user. :confused:

---

