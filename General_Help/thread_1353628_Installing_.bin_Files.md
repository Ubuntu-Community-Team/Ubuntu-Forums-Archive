---
title: "Installing .bin Files"
date: 2009-12-13
forum: General Help
---

### Post by ..::| Dave89 |::.. on 2009-12-13
I downloaded Adobe Reader 9.2 from Adobe's website, it's in .bin format.  How do I install this?

---

### Post by RedSingularity on 2009-12-13
In a terminal get to the directory of the file......fo example,
if you put the .bin on the desktop do this in terminal,,,,,,

cd /home/you/Desktop

then once you do that run the .bin by doing this...........

sh ./name-of-bin.bin

---

### Post by MelDJ on 2009-12-13
type sh into terminal then drag the file into the terminal

---

### Post by RedSingularity on 2009-12-13
> **MelDJ said:**
> type sh into terminal then drag the file into the terminal

Thats a little faster than my way.  I should have thought of that :)

---

### Post by ..::| Dave89 |::.. on 2009-12-13
This is what I got: 
dave89@dave89-laptop:~$ cd /home/dave89/Desktop
dave89@dave89-laptop:~/Desktop$ sh ./AdbeRdr9.2-1_i486linux_enu.bin
./AdbeRdr9.2-1_i486linux_enu.bin: 1: Syntax error: "(" unexpected
dave89@dave89-laptop:~/Desktop$ 


I was able to install Google Earth the same way.  I think the Adobe Reader file is corrupted.

---

### Post by MelDJ on 2009-12-13
since you already used cd into the folder, you can just type sh *filename*

---

### Post by 3rdalbum on 2009-12-13
Firstly, Adobe Acrobat Reader is available in the Partner repository. Go to System > Administration > Software Sources, the Third Party tab, check both the "partner" entries, close the program and reload the sources list, and then do a search in Synaptic Package Manager for "Adobe" and install it.

Always use the repositories to install software, wherever possible. It's easier and allows for security patches and the like to be sent to you.

Secondly, if the .bin file is not a shell script, then telling 'sh' to run it will do nothing meaningful. Thirdly, this file is an installer, which means that it needs root permission - you need to run it with sudo. Fourthly, you need to use "sudo chmod a+x filename.bin" to make it executable before you can run it.

---

### Post by ..::| Dave89 |::.. on 2009-12-13
I downloaded Reader through Synaptic.  1 more question... if I install an application from a .bin or .deb package, how do I uninstall it?

---

### Post by Sin@Sin-Sacrifice on 2009-12-13
From a bin search for files of that program...```
Killmandline:$ sudo locate foobillard
[sudo] password for sin: 
/home/sin/.foobillardrc
/home/sin/.foobillardrc~
/root/.foobillardrc
/usr/games/foobillard
/usr/share/app-install/desktop/foobillard.desktop
/usr/share/app-install/icons/foobillard.png
/usr/share/applications/foobillard.desktop
/usr/share/doc/foobillard
/usr/share/doc/foobillard/README.Debian
/usr/share/doc/foobillard/README.gz
/usr/share/doc/foobillard/TODO
/usr/share/doc/foobillard/changelog.Debian.gz
/usr/share/doc/foobillard/changelog.gz
/usr/share/doc/foobillard/copyright
/usr/share/games/foobillard
/usr/share/games/foobillard/ball_ball.raw
/usr/share/games/foobillard/blende.png
/usr/share/games/foobillard/bumpref.png
/usr/share/games/foobillard/cloth.png
/usr/share/games/foobillard/cue_shadow.png
/usr/share/games/foobillard/foobillard.gif
/usr/share/games/foobillard/foobillard.png
/usr/share/games/foobillard/full_symbol.png
/usr/share/games/foobillard/fullhalf_symbol.png
/usr/share/games/foobillard/half_symbol.png
/usr/share/games/foobillard/lightflare.png
/usr/share/games/foobillard/negx.png
/usr/share/games/foobillard/negy.png
/usr/share/games/foobillard/negz.png
/usr/share/games/foobillard/place_cue_ball.png
/usr/share/games/foobillard/posx.png
/usr/share/games/foobillard/posy.png
/usr/share/games/foobillard/posz.png
/usr/share/games/foobillard/queue.png
/usr/share/games/foobillard/queue_shadow.png
/usr/share/games/foobillard/shadow2.png
/usr/share/games/foobillard/shadow3.png
/usr/share/games/foobillard/shadow_alpha.png
/usr/share/games/foobillard/sphere_map_128x128.png
/usr/share/games/foobillard/sphere_map_128x128_light.png
/usr/share/games/foobillard/sphere_map_64x64.png
/usr/share/games/foobillard/table-frame.png
/usr/share/games/foobillard/tabletex_fB_128x128.png
/usr/share/games/foobillard/tabletex_fB_256x256.png
/usr/share/icons/foobillard.png
/usr/share/man/man6/foobillard.6.gz
/usr/share/menu/foobillard
/var/lib/dpkg/info/foobillard.list
/var/lib/dpkg/info/foobillard.md5sums
/var/lib/dpkg/info/foobillard.postinst
/var/lib/dpkg/info/foobillard.postrm
``` 

```
sudo rm folders_and_files_created_by_program_installation_listed_from_previous_command
```

From a deb just ```
sudo apt-get remove --purge package_name
```

---

### Post by OAtleta on 2010-01-02
Tks a lot [3rdalbum]("http://ubuntuforums.org/member.php?u=61044") . you help me so much woth the tip about software sources and search for adobe.

---

