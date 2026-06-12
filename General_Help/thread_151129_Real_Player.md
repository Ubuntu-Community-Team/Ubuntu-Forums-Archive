---
title: "Real Player"
date: 2006-03-27
forum: General Help
---

### Post by gladd8tor on 2006-03-27
Hi ... I am a newbie to this type of system ( linux ) I am trying to install Real Player from the " Add Applications " area and when I do I get this error below 

The file /root/rp8_linux20_libc6_i386_cs2_rpm does not exist, or it is corrupt. You may have downloaded the wrong file, or put it in the wrong location. Please try again.

If the file you downloaded has a different name, the filename may have changed since this installer was last updated. You can still try to use the installer; just rename the file you downloaded to /root/rp8_linux20_libc6_i386_cs2_rpm . Note that if you do this, there is no guarantee the installer will work.

I'm curious as to whether the file is corrupted or its being place in the wrong area ? Thanks

---

### Post by Ubuntuud on 2006-03-27
You shouldn't install that one, it is an old version and does not work. Look on the wiki  page with the title "restrictedformats", there you can download the file for realplayer 10, and it works...

---

### Post by bluevoodoo1 on 2006-03-27
[https://wiki.ubuntu.com/RealplayerInstallationMethods](https://wiki.ubuntu.com/RealplayerInstallationMethods)

---

### Post by gladd8tor on 2006-03-27
[QUOTE=Ubuntuud]You shouldn't install that one, it is an old version and does not work. Look on the wiki  page with the title "restrictedformats", there you can download the file for realplayer 10, and it works...[/QUOTE]

Oh ok , thanks , Will do , One more question because its old from the add app area , Is it because that needs to be updated ? Like right now its version 5.10 and within june its going to be updated 6 point something  , Is this correct ? I am just trying to get a idea how the programs get updated ? thanks

---

### Post by taurus on 2006-03-27
Just change all the lines that have breezy to dapper and run (from a terminal)
```

sudo apt-get update
sudo apt-get dist-upgrade

```

---

### Post by gladd8tor on 2006-03-27
Hi ... I just done what Ubuntuud suggested and it was easy , Its my first installment beside this OS , Though I am now curious as to what you mean Taurus ? I thought that version isn't out yet ? Or is it ? Thanks

---

### Post by Ubuntuud on 2006-03-27
[QUOTE=gladd8tor]Oh ok , thanks , Will do , One more question because its old from the add app area , Is it because that needs to be updated ? Like right now its version 5.10 and within june its going to be updated 6 point something  , Is this correct ? I am just trying to get a idea how the programs get updated ? thanks[/QUOTE]

Right now it wont be smart to update since dapper (6.04 (the 6 stands for 2006, the 04 for the month)) isn't near to be released. The apps in the "add applications" are still quite up to date, but some (like realplayer) aren't... You could always check the website of a program to see if there are any newer versions...

---

