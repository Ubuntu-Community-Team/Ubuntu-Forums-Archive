---
title: "Opera &amp; Flash"
date: 2009-08-08
forum: General Help
---

### Post by Kd40 on 2009-08-08
hey, i had firefox and it was good, but it was also slow. i looked a little and found opera so i downloaded it. *love it* but it cant seem to run flash, i cant seem to get it to install either. how can i do it?

---

### Post by Arup on 2009-08-08
What version of Ubuntu? How did you install flash?

---

### Post by Kd40 on 2009-08-08
opera version 9.6

I tried installing vier numerouse codes in the terminal that i picked up from forum posts. (non worked) also i reinstalled flash by using synaptic, and restarted opera...flash still didnt work.

---

### Post by Arup on 2009-08-08
> **Kd40 said:**
> opera version 9.6

I tried installing vier numerouse codes in the terminal that i picked up from forum posts. (non worked) also i reinstalled flash by using synaptic, and restarted opera...flash still didnt work.

Are you on x32 or x64 Ubuntu. In case of former, download the deb file from Adobe site or install via synaptic. Also check to see if /usr/lib/mozilla/plugin as libflashplayer.so in it.

---

### Post by Kd40 on 2009-08-08
1# im x32

2# how, where do i find the deb file?

3# i dont know what the command is to find '/usr/lib/mozilla/plugin' but i did check .mozilla/plugins and it was in that directory.

---

### Post by Arup on 2009-08-08
Nope Opera looks in /usr/lib/mozilla/plugins for libflashplayer.so

You can go to Adobe site and look for deb file for Flash 10. Make sure you remove the older flash.

---

### Post by Kd40 on 2009-08-08
ok i found the directory, i have 5 flash files in there they are...flashplugin-alternative.so, libtotem-cone-plugin.so, libtotem-gmp-plugin.so, libtotem-mully-plugin.so, libtotem-narrowspace-plugin.so. none of them is libflashplayer.so


also how do you find the 'deb' file? when you say that do you just meen install flash from the adobe site?

---

### Post by Kd40 on 2009-08-09
ok just found it, downloaded it and then tryed to install it, came up with this message ```
A later version is available in a software channel

You are strongly advised to install the version from the software channel, since it is usually better supported.
```

---

### Post by Arup on 2009-08-09
> **Kd40 said:**
> ok just found it, downloaded it and then tryed to install it, came up with this message ```
A later version is available in a software channel

You are strongly advised to install the version from the software channel, since it is usually better supported.
```

Have you enabled medibuntu repos?

---

### Post by Kd40 on 2009-08-09
no i dont think so, how would i do?

---

### Post by afroman10496 on 2009-08-09
[COLOR=Black][FONT=Arial][COLOR=#ff0000][FONT=monospace][COLOR=Black]```
sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list -O /etc/apt/sources.list.d/medibuntu.list
``````
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - &&
```
```
sudo apt-get update
```[/COLOR]
[/FONT][/COLOR][/FONT][/COLOR][FONT=Arial][COLOR=#ff0000][FONT=monospace][/FONT][/COLOR][/FONT]

---

### Post by Kd40 on 2009-08-09
ok done all that you wanted. just checked again for ```
/usr/lib/mozilla/plugins for libflashplayer.so
``` still no sign of it.

---

### Post by Arup on 2009-08-09
> **Kd40 said:**
> no i dont think so, how would i do?

[http://help.ubuntu.com/community/Medibuntu](http://help.ubuntu.com/community/Medibuntu)

---

### Post by nikhilbhardwaj on 2009-08-09
i'm facing a similar issue
even if i put the libflashplugin.so in /usr/share/opera/plugins
it doesn't pick it up

and also it doesn't install the java plugin

---

### Post by Arup on 2009-08-09
> **nikhilbhardwaj said:**
> i'm facing a similar issue
even if i put the libflashplugin.so in /usr/share/opera/plugins
it doesn't pick it up

and also it doesn't install the java plugin

It has to be in /usr/lib/mozilla/plugins and for Java to work, it has to be the latest Java 14, Opera 10 beta works better with Java than version 9.64. In case of 9.64, you have to point it to the Java installation folder.

---

### Post by darco on 2009-08-09
Try checking in Opera the Tools/Preferences/Advanced tab then Contents.Look for the Plugin Options and confirm that Flash plugin is detected. You may have to re-point to the correct folder...
Same for Java...

darco

---

### Post by Kd40 on 2009-08-09
just a quick little thing, would it work if i dragged the file from the expanded downloaded flash package into '/usr/share/opera/plugins'? i located the file libflashplugin.so in the expanded package i downloaded.

---

### Post by Kd40 on 2009-08-09
ok i installed medibuntu repos, and i installed the flash deb file, all i found was the same old 5 files flash file in the directory from last time. also i tried dragging it into the directory and it said access denied :/

---

### Post by martinbaselier on 2009-08-09
flashplugin-alternative.so is a just a link. 

```

ls /usr/lib/mozilla/plugins/flashplugin-alternative.so -al
lrwxrwxrwx 1 root root 37 2009-04-12 14:22 /usr/lib/mozilla/plugins/flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin

ls /etc/alternatives/mozilla-flashplugin -al
lrwxrwxrwx 1 root root 48 2009-08-03 13:31 /etc/alternatives/mozilla-flashplugin -> /usr/lib/flashplugin-installer/libflashplayer.so
ls /usr/lib/flashplugin-installer/libflashplayer.so -al

ls /usr/lib/flashplugin-installer/libflashplayer.so -al
-rw-r--r-- 1 root root 10278616 2009-08-09 14:04 /usr/lib/flashplugin-installer/libflashplayer.so

```
The package to install is adobe-flashplugin

**sudo apt-get install adobe-flashplugin**

These links are useful too:

optimize firefox:
[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

comprehensive multimedia guide for ubuntu
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by Kd40 on 2009-08-09
k i did the terminal install code for flash, went to the location and couldnt find anything, except the same old 5 links. i did the second code and got this```
kd40@tango-laptop:~$ ls /usr/lib/mozilla/plugins/flashplugin-alternative.so -al
lrwxrwxrwx 1 root root 37 2009-08-09 05:37 /usr/lib/mozilla/plugins/flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
kd40@tango-laptop:~$ lrwxrwxrwx 1 root root 37 2009-04-12 14:22 /usr/lib/mozilla/plugins/flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
bash: /etc/alternatives/mozilla-flashplugin: Permission denied
kd40@tango-laptop:~$ 
kd40@tango-laptop:~$ ls /etc/alternatives/mozilla-flashplugin -al
lrwxrwxrwx 1 root root 48 2009-08-09 16:49 /etc/alternatives/mozilla-flashplugin -> /usr/lib/flashplugin-installer/libflashplayer.so
kd40@tango-laptop:~$ lrwxrwxrwx 1 root root 48 2009-08-03 13:31 /etc/alternatives/mozilla-flashplugin -> /usr/lib/flashplugin-installer/libflashplayer.so
bash: /usr/lib/flashplugin-installer/libflashplayer.so: Permission denied
kd40@tango-laptop:~$ ls /usr/lib/flashplugin-installer/libflashplayer.so -al
-rw-r--r-- 1 root root 10278616 2009-08-09 05:37 /usr/lib/flashplugin-installer/libflashplayer.so
kd40@tango-laptop:~$ 
kd40@tango-laptop:~$ ls /usr/lib/flashplugin-installer/libflashplayer.so -al
-rw-r--r-- 1 root root 10278616 2009-08-09 05:37 /usr/lib/flashplugin-installer/libflashplayer.so
kd40@tango-laptop:~$ -rw-r--r-- 1 root root 10278616 2009-08-09 14:04 /usr/lib/flashplugin-installer/libflashplayer.so

```

i dont really understand it so someone else may?

---

### Post by afroman10496 on 2009-08-09
> **Kd40 said:**
> k i did the terminal install code for flash, went to the location and couldnt find anything, except the same old 5 links. i did the second code and got this```
kd40@tango-laptop:~$ ls /usr/lib/mozilla/plugins/flashplugin-alternative.so -al
lrwxrwxrwx 1 root root 37 2009-08-09 05:37 /usr/lib/mozilla/plugins/flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
kd40@tango-laptop:~$ lrwxrwxrwx 1 root root 37 2009-04-12 14:22 /usr/lib/mozilla/plugins/flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
bash: /etc/alternatives/mozilla-flashplugin: Permission denied
kd40@tango-laptop:~$ 
kd40@tango-laptop:~$ ls /etc/alternatives/mozilla-flashplugin -al
lrwxrwxrwx 1 root root 48 2009-08-09 16:49 /etc/alternatives/mozilla-flashplugin -> /usr/lib/flashplugin-installer/libflashplayer.so
kd40@tango-laptop:~$ lrwxrwxrwx 1 root root 48 2009-08-03 13:31 /etc/alternatives/mozilla-flashplugin -> /usr/lib/flashplugin-installer/libflashplayer.so
bash: /usr/lib/flashplugin-installer/libflashplayer.so: Permission denied
kd40@tango-laptop:~$ ls /usr/lib/flashplugin-installer/libflashplayer.so -al
-rw-r--r-- 1 root root 10278616 2009-08-09 05:37 /usr/lib/flashplugin-installer/libflashplayer.so
kd40@tango-laptop:~$ 
kd40@tango-laptop:~$ ls /usr/lib/flashplugin-installer/libflashplayer.so -al
-rw-r--r-- 1 root root 10278616 2009-08-09 05:37 /usr/lib/flashplugin-installer/libflashplayer.so
kd40@tango-laptop:~$ -rw-r--r-- 1 root root 10278616 2009-08-09 14:04 /usr/lib/flashplugin-installer/libflashplayer.so

```i dont really understand it so someone else may?
It says "Permission Denied," so use ```
sudo
``` before executing the commands.

---

### Post by Kd40 on 2009-08-09
so like ```
sudo ls /usr/lib/mozilla/plugins/flashplugin-alternative.so -al
sudo lrwxrwxrwx 1 root root 37 2009-04-12 14:22 /usr/lib/mozilla/plugins/flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin

sudo ls /etc/alternatives/mozilla-flashplugin -al
sudo lrwxrwxrwx 1 root root 48 2009-08-03 13:31 /etc/alternatives/mozilla-flashplugin -> /usr/lib/flashplugin-installer/libflashplayer.so
sudo ls /usr/lib/flashplugin-installer/libflashplayer.so -al

sudo ls /usr/lib/flashplugin-installer/libflashplayer.so -al
sudo -rw-r--r-- 1 root root 10278616 2009-08-09 14:04 /usr/lib/flashplugin-installer/libflashplayer.so
``` ?

---

### Post by Kd40 on 2009-08-09
ok just put up a vague vid on youtube of what im on about.
[http://www.youtube.com/watch?v=IPRA6HmLllI](http://www.youtube.com/watch?v=IPRA6HmLllI)

---

### Post by benerivo on 2009-08-09
Have you tried downloading flash from the adobe website? It is available [here]("http://get.adobe.com/flashplayer/"). Choose the .tar.gz download option. Extract the downloaded file and put the libflashplayer.so in a folder called```
/home/Kd40/plugins
```Then in Opera, go to Tools > Prefs > Advanced > Content > Plugin Options. Change the paths where it looks for plugins, so that it just looks in the new one you've made.

---

### Post by Kd40 on 2009-08-09
just did, seems there is'nt a folder, kept coming up with an error ```
/home/Kd40/plugins
```
error
```
Could not find "/home/Kd40/plugins".
Please check the spelling and try again.
```

---

### Post by benerivo on 2009-08-09
Where did that error message come from? Was this from Opera? Have you definitely made a folder called plugins inside of your home?

EDIT - Sorry Kd40, i didn't specify that when i said /home/Kd40/plugins, i meant that you should replace Kd40 with whatever your ubuntu username is.

---

### Post by afroman10496 on 2009-08-09
> **Kd40 said:**
> so like ```
sudo ls /usr/lib/mozilla/plugins/flashplugin-alternative.so -al
sudo lrwxrwxrwx 1 root root 37 2009-04-12 14:22 /usr/lib/mozilla/plugins/flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin

sudo ls /etc/alternatives/mozilla-flashplugin -al
sudo lrwxrwxrwx 1 root root 48 2009-08-03 13:31 /etc/alternatives/mozilla-flashplugin -> /usr/lib/flashplugin-installer/libflashplayer.so
sudo ls /usr/lib/flashplugin-installer/libflashplayer.so -al

sudo ls /usr/lib/flashplugin-installer/libflashplayer.so -al
sudo -rw-r--r-- 1 root root 10278616 2009-08-09 14:04 /usr/lib/flashplugin-installer/libflashplayer.so
``` ?
yup. try it now.

---

### Post by JasenGroves on 2009-08-09
What version of Opera are you using? I had the same problem. I was directed to use the non-static version.

[http://ftp.opera.com/pub/opera/linux/1000b2/beta2/en/i386/](http://ftp.opera.com/pub/opera/linux/1000b2/beta2/en/i386/)

the version I'm using is opera_10.00.4492.gcc4.qt3_i386.deb. It works fine right out of the box.

---

### Post by martinbaselier on 2009-08-09
In my example above only the lines with ls are commands. The other ones are the output of ls. You have the correct flasplayer installed, though in the correct location. Jasen's tip looks helpful.

---

### Post by stinkeye on 2009-08-10
> **JasenGroves said:**
> What version of Opera are you using? I had the same problem. I was directed to use the non-static version.

[http://ftp.opera.com/pub/opera/linux/1000b2/beta2/en/i386/](http://ftp.opera.com/pub/opera/linux/1000b2/beta2/en/i386/)

the version I'm using is opera_10.00.4492.gcc4.qt3_i386.deb. It works fine right out of the box.
I use the beta version as well with flash working okay.Still a bit buggy on some sites though.
P.S. If you like dark themes try this skin:
[[COLOR="Red"]Opera IBIS[/COLOR]]("http://my.opera.com/community/customize/skins/info/?id=8655")
I change the red highlights to indigo in tools-appearance-skin.

---

