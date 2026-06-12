---
title: "Ubuntu (Partitionable) Directories Explained?"
date: 2011-03-20
forum: General Help
---

### Post by snoopy-2009 on 2011-03-20
I have seen this posted in a couple different areas, some with good explanations, and others without.. such as [http://ubuntuforums.org/showthread.php?t=1335819](http://ubuntuforums.org/showthread.php?t=1335819) 

but what im hoping i can accomplish here, is a better explanation of EACH of the directories available as Mount Points in the Ubuntu Installer. Such as, / /boot /home /tmp /usr /var /srv /opt and /usr/local

i have a pretty good idea of what a few are for, such as /boot /home and /tmp

im hoping someone could be kind enough to do more of an explanation (even short) of each, in a simple definition list.

what sprung this in my mind, is i have a 500gb hdd in which im dedicating to ubuntu. i am creating a seperate home partition, for the obvious benefits (not losing data in reinstall, and sharing to my other hdd, etc). what im more curious about is, how large can the / dir grow to be, with packages being installed etc.. ?

and how well does it actually work if you mount /[whichever directory is for installed software packages].. if u reinstall ubuntu, are those packages already installed from the get go?

---

### Post by ChipOManiac on 2011-03-20
the / directory is the root partition itself... how much you want it to store is dependent on the user... if you don't use a lot of programs it's perfectly all right to give space priority to your /home/ partition

Did I Understand correctly?

---

### Post by snoopy-2009 on 2011-03-20
yes, i understand that. 

but what if youre unsure how many programs you will end up using? i want to beable to dedicate enough room for A LOT of expansion, even if that will never happen, but at the same time, didnt want to give a rediculously overboard amount and actually waste too much space.. i hope that makes sense.. I wanted a reasonable ballpark figure of how large an ubuntu partition would end up being if a user did install many many many packages. lol

my other question was, if i give the software directory(s) their own partition, will those packages automaticly be detected as "already installed" after i reinstall? (last through multiple reinstalls?) and which directory(s) are those?   is this even possiable to do? isnt it the /lib folder thats for software? i didnt realize that ones not a mountable option in the installer..



one more thing, i was going to post this in the original post, but of course, i forgot. lol

Directory Structure:
[http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html](http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html)

---

### Post by mikewhatever on 2011-03-20
If unsure, you'll have to estimate, and if you run out of space, repartition, it's not the end of the world.
When installing a new version of Ubuntu, almost all of the packages will have their versions bumped, so that the old ones will not work. It's real easy to save the list of all installed programs (from the repositories), and then use that list to install the same programs on the new installation.

---

### Post by snoopy-2009 on 2011-03-20
> **mikewhatever said:**
> If unsure, you'll have to estimate, and if  you run out of space, repartition, it's not the end of the world.
When installing a new version of Ubuntu, almost all of the packages will  have their versions bumped, so that the old ones will not work. It's  real easy to save the list of all installed programs (from the  repositories), and then use that list to install the same programs on  the new installation.

lol good point. as blunt as it is :)



> **mikewhatever said:**
> If unsure, you'll have to estimate, and if you run out of space, repartition, it's not the end of the world.
When installing a new version of Ubuntu, almost all of the packages will have their versions bumped, so that the old ones will not work. It's real easy to save the list of all installed programs (from the repositories), and then use that list to install the same programs on the new installation.

are you saying theres a way to save the list as a file, that ubuntu can read from, and install all the packages in your list file? that would deffinatly serve as a perfect alternative to what i was visioning.

ty for the help! its much appreciated. :D


the only other thing i was hoping for from the main post, was a list of what purposes/benefits pros/cons of each of the directories having its own partition (of the ones available to chose from in the installer)

i was thinking of a list like such, with the reasons why someone would want to give any or all of these each a separate partition:

/boot    
/home                    -File sharing across multiple OS's, and Not losing data from reinstall.
/tmp
/usr
/var
/srv
/opt
/usr/local

---

### Post by mikewhatever on 2011-03-20
I can't think of a single reason to break up an installation into so many partitions. Perhaps it would be more productive if you could explain why you came up with such a list in the first place.

Here is how to save the list of installed packages and then install them on a new system.
[http://joysofprogramming.com/dpkg-get-selections/](http://joysofprogramming.com/dpkg-get-selections/)

---

### Post by snoopy-2009 on 2011-03-20
ty for that link. very useful indeed!

and just to clarify, i do not want to create a partition for ALL of them. i wanted the LIST of reasons why EACH of them would be put onto a separate partition at all. NOT necessarily all at the same time.. that list is the list of ALL of the POSSIBLE OPTIONS in the ubuntu installer, they allow you to select as different mount points.

---

### Post by vanadium on 2011-03-20
It makes no sense to have different partitions for these system directories on a desktop system. For server systems, it is usefull.

By default, Ubuntu only sets up a partition for root and one for swap. That way, you do not have to worry about running out of space or, opposite, having too much free space on a partition that you would never use.

It can be practical, though, to have a separate partition for /home on a desktop system. This allows to keep your user data on the system while installing a new version of the OS from scratch.

It is NOT recommended to keep your old home directory with the new install, though. In 99% of the cases, it will work well, but there is no guarantee that all configuration data of the old linux version will work on the new one. In this scenario, I would rename my old profile directory (e.g. "joe" -> "joebak", install the new version of the operating system, and then move my personal userdata (Documents, Pictures, ...) from "joebak" to "joe".

---

### Post by snoopy-2009 on 2011-03-20
tyvm

---

