---
title: "Games?"
date: 2010-12-19
forum: General Help
---

### Post by joelkat on 2010-12-19
I got 1 or 2 but they are run files?

---

### Post by karthick87 on 2010-12-19
To install a run file,type the following in terminal
```
chmod +x filename.run
``````
./filename.run
```

---

### Post by DarkAmbient on 2010-12-19
> **joelkat said:**
> I got 1 or 2 but they are run files?


here you go. [http://ubuntuforums.org/showthread.php?t=239797](http://ubuntuforums.org/showthread.php?t=239797)

---

### Post by joelkat on 2010-12-19
the file name is tremulous-1.1.0-installer.x86 what would i do

---

### Post by joelkat on 2010-12-19
Bump

---

### Post by joelkat on 2010-12-19
please help I want to play...

---

### Post by Verbeck on 2010-12-19
where is the file placed?

assuming it is in your Downloads folder, do the following from a terminal
```

cd ~/Downloads
[FONT=monospace]chmod +x [/FONT]tremulous-1.1.0-installer.x86.run
./tremulous-1.1.0-installer.x86.run

```

edit: 
alternatively, right click the file>properties>permissions>check 'allow executing file as a program'
then right click>open

---

### Post by joelkat on 2010-12-19
it says Please enter the installation path [/usr/local/games/tremulous/]

---

### Post by Joeb454 on 2010-12-19
If that's the exact output (with /usr/local/* path in square brackets), that usually means the default value, and will be assumed unless you enter something else.

---

### Post by joelkat on 2010-12-19
what do I press?

---

### Post by I'mGeorge on 2010-12-19
> **joelkat said:**
> what do I press?

Press ENTER and your game will be installed in /usr/local/games/tremulous/ . If you want to choose another location just choose another path. It's just like in windows.

By the way tremulous should already be in your repositories and you should be able to install it with

```

apt-get install tremulous

```

---

### Post by joelkat on 2010-12-19
it says no write permission

---

### Post by DarkAmbient on 2010-12-19
As imgeorge says, the game should be in the repositories. Either use that command he wrote, or open software center and search for that game.

---

### Post by joelkat on 2010-12-19
?????????

---

### Post by joelkat on 2010-12-19
> **DarkAmbient said:**
> As imgeorge says, the game should be in the repositories. Either use that command he wrote, or open software center and search for that game.

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)

---

### Post by DarkAmbient on 2010-12-19
> **joelkat said:**
> E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)

It means you have another process/application open, which you can for exMple install in. It locks all the other apps acces to install then.. Try to close everything else first. Terminals too. Then try install with either software center or System->administration->synaptic.

Sry for misspell. On my iphone now.

---

### Post by DarkAmbient on 2010-12-19
You can install it and some other games (or read howto) here.

[http://www.ubuntugamer.com/2010/11/five-awesome-native-ubuntu-first-person-shooters-you-may-not-know-about/](http://www.ubuntugamer.com/2010/11/five-awesome-native-ubuntu-first-person-shooters-you-may-not-know-about/)

Good luck now. If you fix it mark this thread as solved (under thread tools i think)

---

### Post by I'mGeorge on 2010-12-19
> **joelkat said:**
> it says no write permission

now either you change the path to a directory where root privileges aren't required like your home dir, for example /home/username/tremulous or you launch the bin file in this manner 

```
sudo sh tremulous.bin
``` and you will be asked for your password.

---

### Post by unplugged23 on 2010-12-19
How about you just pop open ubuntu's software manager type in 'tremulous' and install it from there?

---

### Post by Verbeck on 2010-12-21
select a location inside your home folder as the installation directory
/home/usrname/tremulous

or run the file as root
sudo ./tremulous-1.1.0-installer.x86.run

or install from the software center/synaptic

edit: didn't see that all of it were already suggested..

---

