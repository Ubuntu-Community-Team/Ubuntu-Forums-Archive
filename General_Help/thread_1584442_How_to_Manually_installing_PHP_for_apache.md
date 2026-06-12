---
title: "How to Manually installing PHP for apache?"
date: 2010-09-29
forum: General Help
---

### Post by MMAMail on 2010-09-29
Does anyone have a link on how to install php manually for apache?

I don't want to use the package manager.

thanks

---

### Post by WorMzy on 2010-09-29
> I don't want to use the package manager.

Why?

If you don't want to use packages, you're basically left with compiling and installing from source.

[Here's the source code]("http://www.php.net/get/php-5.3.3.tar.bz2/from/a/mirror"), and [here's the manual]("http://php.net/manual/en/install.php").


If you decide that you'd rather install it the easy way, just run

```
sudo apt-get install php5 libapache2-mod-php5
```

---

### Post by MMAMail on 2010-09-29
> **WorMzy said:**
> Why?

because it puts the files in too many places which is difficult for me to remember. Although if one can learn these places it will be more effective. But I have a gold-fish memory I forget the places and have to look everything up everyday :(

---

### Post by WorMzy on 2010-09-29
You don't need to remember where it puts the files, *it* remembers.

```
dpkg-query -L php5
```

You shouldn't need to know where all the files are anyway. You just need to know that daemons and config files go in /etc, and executables go in /bin or /usr/bin.

---

### Post by MMAMail on 2010-09-29
> **WorMzy said:**
> You don't need to remember where it puts the files, *it* remembers.

```
dpkg-query -L php5
```

You shouldn't need to know where all the files are anyway. You just need to know that daemons and config files go in /etc, and executables go in /bin or /usr/bin.

Generally what's a better approach? 

using the package manager 
or
manually doing everything

---

### Post by WorMzy on 2010-09-29
Using the package manager:
- Precompiled, so potential performance loss
- Precompiled, so no option to edit source code
+ Quick and easy installation of software
+ Automatically installs dependencies
+ Self-updating database of all installed software
+ Automatic updates
+ Easy to remove unwanted packages

Installing from source:
- Slower installation, due to compilation times.
- Need to manually install dependencies too
- No list of installed software
- Can only remove software easily if you still have the source.
- Updates have to be manually compiled and installed once you find out about them
+ Possible performance gain from compiled applications
+ Ability to modify the source code before installation

I can't tell you what's best for you, but I'd recommend only installing precompiled packages, unless software you need isn't available in the repos.

---

