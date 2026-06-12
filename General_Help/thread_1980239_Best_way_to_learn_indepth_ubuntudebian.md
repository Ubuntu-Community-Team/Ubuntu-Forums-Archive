---
title: "Best way to learn indepth ubuntu/debian"
date: 2012-05-14
forum: General Help
---

### Post by agrayray on 2012-05-14
Want to learn all the ins and outs of ubuntu/debian/linux...essentially learn the system and use it from the command line..with all of its inner workings...admin level type stuff...

so curious...(as i always get such great advice here)...ive got cpl vms of ubuntu server and debian already created just browsed a few books but they seem very superficial/or gui driven up to this point...I want the more indepth file structure, file workings type of stuff...

has anyone else done this and have a good source for learning in-depth ubuntu..ie know everything from the command line?

I pretty much know this for the windows stack :(..have lots of programming (java,C++,C#)/comp sci  background..even know vi fairly well...and the basic linux commands...just really dont know linux/ubuntu very well...???

to give a few examples of things I would like to know

1. I installed Ubuntu and I didnt have any network...thru lots of googling and trial and error..I added an eth0 interface and configured it to load on startup...it took a long time cause i no idea where these files where located, what they used for etc or how even in general network devices are loaded....still dont even though i thru found the answers of the files to change...want to learn these details
2. I couldnt mount the CD previously so i had to figured out how to add cd dev and mount it ...again thru googling..still dont know how devices/mounts get added or how the system uses them
3. My screen size is stuck 640x480 mode...and now I need to change the config files to support it..
4. needed to set my own ip address

hope this helps explain what I am looking for now....not how to install DHCP, or Apache, or how to use Desktop or simply commands etc...all the things linux/ubuntu books materials seem to focus on.

thanks in advance.

---

### Post by rai4shu2 on 2012-05-14
Ubuntu is really more GUI-centric. You might be happier with your stated goals with something like Arch.

see: [https://wiki.archlinux.org/](https://wiki.archlinux.org/)

---

### Post by agrayray on 2012-05-14
thanks for the reply raishu...no i think im ok with ubuntu...for now im on the server with no gui anyway...heres what I been reading/fooling around with now...stuff on whats in the /proc folder and how to use from geekstuff...i know this one seems to be more linux generic than ubuntu at this point but I already know enough that soon I will get into Ubuntu specifics along the same lines that will differ from Arch, CentOS or other versions...and I (and many friends I have convinced all use Ubuntu)...so Im looking the Ubuntu stuff similar to this geekstuff link:

[http://www.thegeekstuff.com/2010/11/linux-proc-file-system/](http://www.thegeekstuff.com/2010/11/linux-proc-file-system/)

Anyone know where this info is?

---

### Post by rai4shu2 on 2012-05-15
Well, I guess you could start with [TLDP]("http://tldp.org/") and maybe work your way through [BASH]("http://tldp.org/LDP/abs/html/index.html") or whatever.

---

### Post by papibe on 2012-05-15
Hi agrayray.

I would recommend to  challenge yourself with "real" projects (or a learning projects if you will). For example:
[LIST]
[*]Share files with Windows machines.
[*]Enable remote access to your computer.
[*]Stream media to a game console.
[*]Share your printer with other machines.
[*]Setup remote access to your files from the Internet.
[*]Setup a web server.
[*]etc.
[/LIST]
Just some thoughts,
Regards.

---

### Post by josephmills on 2012-05-15
> 

2. I couldnt mount the CD previously so i had to figured out how to add cd dev and mount it ...again thru googling..still dont know how devices/mounts get added or how the system uses them


[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

> 
3. My screen size is stuck 640x480 mode...and now I need to change the config files to support it..

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
there are others also but there is a good place too start.


> 
4. needed to set my own ip address

Do you mean dhcp too static? 
[http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/](http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/)
or somethign like this ? 

[https://help.ubuntu.com/community/dhcp3-server](https://help.ubuntu.com/community/dhcp3-server)

Here is some more stuff :) 
Debian stuff
[http://www.debian.org/doc/manuals/maint-guide/](http://www.debian.org/doc/manuals/maint-guide/)
[http://www.debian.org/doc/debian-policy/](http://www.debian.org/doc/debian-policy/)
[http://www.debian.org/doc/manuals/developers-reference/](http://www.debian.org/doc/manuals/developers-reference/)
[http://wiki.debian.org/FrontPage](http://wiki.debian.org/FrontPage)

Canonical
[https://forms.canonical.com/training/](https://forms.canonical.com/training/)
[http://shop.canonical.com/index.php?cPath=21](http://shop.canonical.com/index.php?cPath=21)

Ubuntu Community 
[https://help.ubuntu.com/community](https://help.ubuntu.com/community)
[https://wiki.ubuntu.com/Classroom](https://wiki.ubuntu.com/Classroom)
[https://wiki.ubuntu.com/LoCoTeams](https://wiki.ubuntu.com/LoCoTeams)



Hope this helps and let us know if there is anything else that you get held up at. 
Thanks for Picking Ubuntu and Ubuntu Forums.

---

### Post by scoon on 2012-05-15
> **agrayray said:**
> Want to learn all the ins and outs of ubuntu/debian/linux...essentially learn the system and use it from the command line..with all of its inner workings...admin level type stuff...

so curious...(as i always get such great advice here)...ive got cpl vms of ubuntu server and debian already created just browsed a few books but they seem very superficial/or gui driven up to this point...I want the more indepth file structure, file workings type of stuff...

has anyone else done this and have a good source for learning in-depth ubuntu..ie know everything from the command line?

I pretty much know this for the windows stack :(..have lots of programming (java,C++,C#)/comp sci  background..even know vi fairly well...and the basic linux commands...just really dont know linux/ubuntu very well...???

to give a few examples of things I would like to know

1. I installed Ubuntu and I didnt have any network...thru lots of googling and trial and error..I added an eth0 interface and configured it to load on startup...it took a long time cause i no idea where these files where located, what they used for etc or how even in general network devices are loaded....still dont even though i thru found the answers of the files to change...want to learn these details
2. I couldnt mount the CD previously so i had to figured out how to add cd dev and mount it ...again thru googling..still dont know how devices/mounts get added or how the system uses them
3. My screen size is stuck 640x480 mode...and now I need to change the config files to support it..
4. needed to set my own ip address

hope this helps explain what I am looking for now....not how to install DHCP, or Apache, or how to use Desktop or simply commands etc...all the things linux/ubuntu books materials seem to focus on.

thanks in advance.

Hey there, 

This is all good stuff.  Google, as you found, is your friend.  Since you have installed ubuntu, you should expand your search to see how debian does things - after all, ubuntu is built on top of debian!!!  Another wonderful resource are man or info pages.  Your example of mounting a CD is a great one.  Get to a terminal and type either **info mount** or **man mount** - these will help you even 10 years from now.  There are lots of resources out there but there are lots right in man and info.

Most of all, enjoy...

---

### Post by bodhi.zazen on 2012-05-15
Best way to learn Ubuntu is to use ubuntu and resolve problems as they come up.

You should then read through the official documentation

[https://help.ubuntu.com/12.04/ubuntu-help/index.html](https://help.ubuntu.com/12.04/ubuntu-help/index.html)

From there, next up is permissions, bash, bash scripts, sed, regular expressions, awk, and perl.

---

### Post by roelforg on 2012-05-15
> **rai4shu2 said:**
> Ubuntu is really more GUI-centric. You might be happier with your stated goals with something like Arch.

see: [https://wiki.archlinux.org/](https://wiki.archlinux.org/)

It doesn't have to....
I, for one, set my desktops up with ubuntu server and went from there and build my own gui setup. I had to do a lot of commandline stuff and change who knows how many configs, if you want to and have a scratch pc, you could do it that way.

---

