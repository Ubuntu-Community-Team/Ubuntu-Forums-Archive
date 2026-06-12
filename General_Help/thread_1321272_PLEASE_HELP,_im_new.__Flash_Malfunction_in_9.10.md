---
title: "PLEASE HELP, im new.  Flash Malfunction in 9.10"
date: 2009-11-09
forum: General Help
---

### Post by c.daruvala on 2009-11-09
Today is my first day of use with ubuntu.  I downloaded and installed ubuntu 9.10, and have it installed side by side with Windows Vista.  I know little to nothing about ubuntu.

PROBLEM:
It seems adobe flashplayer has taken over my computer.  Apparently it is "no longer supported, or in the package archive"  I am TOTALLY CONFUSED.  I have tried to install adobe flashplayer again, and it does not work, saying "Could not open 'install_flash_player_10_linux.deb'   the package might be corrupted or you are not allowed to open the file.  Check the permissions of the file"  I have checked the permissions of the file, but i am just utterly ignorant in regards to ubuntu.  

SAVE ME.  It is not letting me install new programs from the software center, or update.  

PLEASE help........

---

### Post by williejones on 2009-11-09
How did you install flash player?  Try to uninstall and reinstall it.

---

### Post by MelDJ on 2009-11-09
type this in terminal and see if it works: sudo apt-get install -f

---

### Post by c.daruvala on 2009-11-09
```
cristian@Luraan:~$ sudu apt-get install -f
No command 'sudu' found, did you mean:
 Command 'tudu' from package 'tudu' (universe)
 Command 'sudo' from package 'sudo' (main)
 Command 'sudo' from package 'sudo-ldap' (universe)
sudu: command not found

```

Thats what happened when i did the sudo command thing.

I installed flash from the website.  It is not letting me un-install it, unless i am doing it wrong?

---

### Post by MelDJ on 2009-11-09
if you observe, you typed SUDU. you should type SUDO instead ;)

---

### Post by c.daruvala on 2009-11-09
I tried to open synaptic package manager, and this is what happened:

E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

---

### Post by williejones on 2009-11-09
You typed sudu instead of sudo

edit oops late replying

---

### Post by c.daruvala on 2009-11-09
> **MelDJ said:**
> type this in terminal and see if it works: sudo apt-get install -f

hahaha mistype, my bad :)

Its asking me for [sudo] password for (my name)

but it is not letting me type my password :O

---

### Post by MelDJ on 2009-11-09
what output did sudo apt-get install -f give?

---

### Post by c.daruvala on 2009-11-09
okay, i typed it correctly, this is what happened:

```
cristian@Luraan:~$ sudo apt-get install -f
[sudo] password for cristian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.

```

---

### Post by MelDJ on 2009-11-09
> **c.daruvala said:**
> hahaha mistype, my bad :)

Its asking me for [sudo] password for (my name)

but it is not letting me type my password :O

thats normal. in terminal when you type, the password is invisible. just type it and press enter.

try typing sudo apt-get remove adoble-flashplugin

---

### Post by c.daruvala on 2009-11-09
okay, i typed it correctly, this is what happened:

```
cristian@Luraan:~$ sudo apt-get install -f
[sudo] password for cristian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.

```

---

### Post by MelDJ on 2009-11-09
try: sudo apt-get remove adoble-flashplugin

---

### Post by c.daruvala on 2009-11-09
This happened:
```
cristian@Luraan:~$ sudo apt-get remove adoble-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
cristian@Luraan:~$ 

```

Thank you for helping me through this problem btw!  hopefully we can fix it!  :)

---

### Post by Zanterian on 2009-11-09
Do you know if you are using 32-bit or 64?
From what I've seen, 64-bit has a lot of trouble with flash plater 10 as flash player 10 is built for 32-bit only.
Therefore it could be that you cannot install it simply because you are using an unsupported architecture. 

What are your intentions with using flash?
Is it to watch videos on youtube?
or play flash games on sites such as addictinggames.com or the like?

If you want to try to watch videos, I am pretty sure there is a firefox plugin that covers SWF (youtube videos) support.

To install the plugin in question i think you can do something like 

```

sudo apt-get install swfdec-mozilla

```After that is complete, you should have support for youtube videos and other flash sites. Although it is not quite as smooth as flash 10, it is the best I can think of.

- Zanty

---

### Post by MelDJ on 2009-11-09
try this link: [http://www.linuxquestions.org/questions/debian-26/cant-open-synaptic-after-trying-install-flash-deb-of-ubuntu-739384/](http://www.linuxquestions.org/questions/debian-26/cant-open-synaptic-after-trying-install-flash-deb-of-ubuntu-739384/)

its for debian but the commands are the same for ubuntu. hope it helps.

---

### Post by dserver on 2009-11-09
You could try installing the flashplugin-nonfree. I'm not sure if it'll help.

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by MelDJ on 2009-11-09
to zanterian and dserver

read the OP's first post, he cant install anything now ;)

---

### Post by c.daruvala on 2009-11-09
Thanks for the help guys.

In the end i had to:

```
dpkg --purge --force-all adobe-flashplugin
```

That fixed everything!!!

Oh the relief hahaha.  :)

---

