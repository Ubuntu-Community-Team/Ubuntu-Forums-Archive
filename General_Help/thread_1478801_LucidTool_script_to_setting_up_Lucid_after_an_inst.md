---
title: "LucidTool: script to setting up Lucid after an install"
date: 2010-05-10
forum: General Help
---

### Post by SAKO2008 on 2010-05-10
Hi, I made a script I want to share with you. I'm not a programmer, I do this as a hobby! I have tested LucidTool on my computer and it seems work properly. I hope it is useful to you!

I have an official page on launchpad:
[https://launchpad.net/lucidtool](https://launchpad.net/lucidtool)

I'm italian but I translated it into English and I wrote about it on my blog here:
[http://freetimesblog.altervista.org/blog/?page_id=1786](http://freetimesblog.altervista.org/blog/?page_id=1786)

              **[CENTER] What is LucidTool?[/CENTER]**

LucidTool help you in configuration and installation of important libraries and codecs needed immediately after the first installation of Lucid. LucidTool will also help you later to keep clean and updated your favorite distribution.

Features:

1. Installs all multimedia codecs with one click.

2. Keeps the system clean.

3. Keeps the system updated.

4. Adds and updates automatically GPG keys.

5. Restores the original Lucid sources.list.

6. Restores the sources.list you had before using LucidTool.

7. Installs the latest versions of some useful programs.

8. Modifies some system configurations but allows you to restore the default settings.

9. Uses the Ubuntu Notification System.

LucidTool check if:

- the script is ran as root.
- there is an active internet connection, to make sure you can install the required packages, etc...

Requirements:

- Operating System: Ubuntu Lucid 10.04.

- The following dependencies can be installed automatically when you first run LucidTool_install:
    Zenity
    Libnotify-bin

You can download it from Launchpad. 

**How to Use:**

1) _Install_

Extract the archive you have downloaded in your home. Then:
```
cd LucidTool
sudo ./LucidTool_install
```


2) _Run_

After the install:
```
sudo ./LucidTool
```


3) _Uninstall_

If you want to uninstall LucidTool:
```
cd LucidTool
sudo ./LucidTool_uninstall
```

Please tell me about any bugs and if you want to add any features.

---

### Post by dino99 on 2010-05-10
keep goes on, nice job for a non coder :P

will try it

---

### Post by SAKO2008 on 2010-05-11
Thank you!
Let me know what you think, after you've tried!

---

