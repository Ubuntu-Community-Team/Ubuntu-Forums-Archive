---
title: "Can't make Folder/File/Edit existing one in var/www/"
date: 2009-10-07
forum: General Help
---

### Post by ankurTheKing on 2009-10-07
Hello friends
This is my first post here.
Yesterday only, I have installed Ubuntu 8.10 on my PC. Its fantastic, its design and visual effects are great as I am having nVidia.

I have installed Apache, PHP5, MySQL, Phpmyadmin.
Now it has become web server.:P
But problem is that I cannot make folder or file or edit existing one in following folder.

**FileSystem** > **var** > **www**

When I do right click, Creat folder and create Doc are disabled.
When I tried to edit existing file **index.html** (Where it is written as It Works) and saved, it said something about permissions.
How can I log in as root ? Else what I have to do ?:confused:
Thanks:)

---

### Post by mr.suchy on 2009-10-07
to change user:

```
su root
```and then write password or 
```
sudo mkdir /var/www/homepage
``` and then write password. Firstly change premision to this folder:
```
chown your_login:your_login /var
```

---

### Post by ankurTheKing on 2009-10-07
What to write in 
chown your_login:your_login /var
Whats your_login:your_login ?
My current username is ankur

---

### Post by 3rdalbum on 2009-10-07
> **mr.suchy said:**
> to change user:

```
su root
```and then write password or 
```
sudo mkdir /var/www/homepage
``` and then write password. Firstly change premision to this folder:
```
chown your_login:your_login /var
```

I'm sorry, but this is TERRIBLE advice. Firstly, "su" doesn't work on Ubuntu. Secondly, your solution is to change the ownership of /var? That's likely to cause BIG problems.

Ankur, don't follow that.

As you've gathered, you need to be root to modify files and folders outside your home directory. The easiest way for a new user to "become root" is to open a file browser window as root, which can be done like this:

```
gksudo nautilus
```

Anything you do in this window will be done as root, and any program you run from this window will be run as root. Be careful!

A tip for you: There's a package called "nautilus-gksu" in the software repositories. If you install it, when you next log in, you can right-click on any file or folder and you'll have the option to "Open as Administrator". This saves you a trip to the terminal when you want to do some file management as root.

Finally, if you just want to run a single terminal command as root, prefix it with "sudo".

---

