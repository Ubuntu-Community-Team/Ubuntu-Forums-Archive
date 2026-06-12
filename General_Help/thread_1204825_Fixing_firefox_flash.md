---
title: "Fixing firefox flash"
date: 2009-07-05
forum: General Help
---

### Post by Nevart on 2009-07-05
I'm sure that title needed a few more "F" words in it.

Anyway, what I want to do is get the flash out of firefox and put a new one in, but it doesn't let me remove the plugin like a normal add-on, it only lets me disable it.  

Instructions at Mozilla only give the method to uninstall from Win.

Can anyone assist?

---

### Post by ivanvajar on 2009-07-05
Not that it's my bussiness, but do you need to do that? Experience sais that you are pushin' your luck when doing things like that.

---

### Post by gamblor01 on 2009-07-05
If you really want to remove it then you need to remove the libflashplayer.so file.  Unfortunately it may be in one of several places so you have to search for it.  Often times it is stored in one directory and then symbolically linked elsewhere.  The following command should find it on your system (and using -mount forces it to NOT look on other partitions that might be mounted on your machine...which saves you time):

```

sudo find / -mount -name 'libflashplayer.so'

```
Once you find it you should probably back up the existing file(s) instead of removing it/them entirely.  Afterwards, I would recommend you go here:

[http://www.adobe.com/go/EN_US-H-GET-FLASH](http://www.adobe.com/go/EN_US-H-GET-FLASH)

download the .deb file for Ubuntu 8.04+ and then run:

```

sudo dpkg -i install_flash_player_10_linux.deb

```
That will get you the latest flash from Adobe, which is probably going to be compatible with more sites than any other flash implementation, and it supports some of the latest formats.

---

### Post by Nevart on 2009-07-05
@ivanvajar: Yes I do need to because the currently installed version is only partially functional.  Risky, but I am sick of all the problems.  Can't even open some sites for fear it will crash the browser.

@gamblor01: Thanks, I will try and will report on what happens (maybe not right away, you understand...)  ;)

---

### Post by lovinglinux on 2009-07-05
> **Nevart said:**
> I'm sure that title needed a few more "F" words in it.

:lol: I agree.

> **Nevart said:**
> Anyway, what I want to do is get the flash out of firefox and put a new one in, but it doesn't let me remove the plugin like a normal add-on, it only lets me disable it.

This is normal behavior. You need to uninstall it from Synaptic. Here is the command to solve your problems:
```

sudo apt-get remove adobe-flashplugin flashplugin-installer flashplugin-nonfree flashplugin-nonfree-extrasound libflashsupport swfdec-mozilla mozilla-plugin-gnash
```

Then install the one you need. I recommend:

```
sudo apt-get install flashplugin-nonfree
```

> [color=#CC0000]**How to run commands in a Terminal: **[/color]Open "Applications >> Accessories >> Terminal", then type or paste the code (CTRL+SHIFT+V) and hit *Enter*. You might be prompted to enter your password. You cannot see it while you type, but it is there. Then just hit *Enter* again to run the command. Please do not run commands without knowing what they do. If you do not understand what a command does, ask for explanations.

Also visit [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567) for optimization tips and how to fix most common Firefox issues.

> **ivanvajar said:**
> Not that it's my bussiness, but do you need to do that? Experience sais that you are pushin' your luck when doing things like that.

There nothing risky about removing flash, if you use the proper commands or through Synaptic. I lost the count of how many times I did it. Just install again and you ready to go.

---

