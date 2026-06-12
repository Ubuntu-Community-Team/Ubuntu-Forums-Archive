---
title: "Ubuntu Advanced Learning Material"
date: 2011-06-19
forum: General Help
---

### Post by subchief on 2011-06-19
Hey Guys, am an ubuntu user...am not very new to ubuntu as i have been trying it out since as early as ubuntu 8.04. However, i have decided to take up ubuntu as my main and only operating system!!!This is an informed decision as i have come to appreciate the numerous advantages ubuntu has over windows.However, i lack a source of material about ubuntu.
If anyone has any pdf's about ubuntu or any helpful advanced links...and not the basic howto's, please pass them on to me and i will be grateful!!
Thank u!!!:KS

---

### Post by jerrrys on 2011-06-19
in the address box of your browser enter

file:///usr/share/doc/debian-reference-common/html/ch01.en.html

---

### Post by CodyLoco on 2011-06-19
> **jerrrys said:**
> in the address box of your browser enter

file:///usr/share/doc/debian-reference-common/html/ch01.en.html

That doesn't load for me :(

---

### Post by jerrrys on 2011-06-19
sudo apt-get install debian-reference-en

another one

sudo apt-get install sysadmin-guide

---

### Post by subchief on 2011-06-19
Thanks.
Do you have a link to a document about the ubuntu architecture, file management system, organization of files,configuration and such like details?

---

### Post by knutschr on 2011-06-19
I think this is a good place to start:
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

---

### Post by jerrrys on 2011-06-19
is this what your looking for ?

[http://library.gnome.org/users/user-guide/stable/nautilus.html](http://library.gnome.org/users/user-guide/stable/nautilus.html)

the "desktop user guide" i believe is installed by default

yet another thought

navigate to filesystem/user/share/doc and see what docs you have

---

### Post by idoitprone on 2011-06-19
I think he is looking for papers from dennis ritche , ken thompson, and rob pike; inventors of unix and its successor plan9.

Ouch how far are you going to look, since operating system design is a large topic. I can rant on how plan9 solve many of today problems with operating system and why andrew Tanenbaum is an idoit for saying pure microkernels are the future.[]("http://www.cs.vu.nl/%7East/reliable-os/")

[http://doc.cat-v.org/plan_9/](http://doc.cat-v.org/plan_9/) here some plan 9 docs. It will give you a better idea how those does made unix

---

### Post by subchief on 2011-06-19
> **knutschr said:**
> I think this is a good place to start:
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)


Thanks but the thread is helpful for beginner stuff...like how to open and save files or how install programs and such like details!

Am looking to understand how ubuntu runs, how it manages files, how the file system is structured etc...if you can direct me in that way i shall be a happy lad!!!

Thanks though!!

---

### Post by subchief on 2011-06-19
> **jerrrys said:**
> is this what your looking for ?

[http://library.gnome.org/users/user-guide/stable/nautilus.html](http://library.gnome.org/users/user-guide/stable/nautilus.html)

the "desktop user guide" i believe is installed by default

yet another thought

navigate to filesystem/user/share/doc and see what docs you have


Thanx...this is definitely a good start to understanding nautilus file manager...

---

### Post by subchief on 2011-06-19
> **idoitprone said:**
> I think he is looking for papers from dennis ritche , ken thompson, and rob pike; inventors of unix and its successor plan9.

Ouch how far are you going to look, since operating system design is a large topic. I can rant on how plan9 solve many of today problems with operating system and why andrew Tanenbaum is an idoit for saying pure microkernels are the future.

[http://doc.cat-v.org/plan_9/](http://doc.cat-v.org/plan_9/) here some plan 9 docs. It will give you a better idea how those does made unix

Well i gotta admit thats too technical...am looking to understand ubuntu jus the way i understand windows, how windows registry works, how programs are run and things like that. As to jus how much i want to know...i am not looking to build an operatin system...:P

---

### Post by idoitprone on 2011-06-19
Linux do not use registry.
The only registry that is remotely like window is with opensuse. But the functionality is nowhere compared to windows

At least you do not need to know complex topics. The kernel is complex and ugly. Really, really ugly. I believe windows and mac is the same way or worse
 [http://en.wikipedia.org/wiki/File:Linux_kernel_map.png](http://en.wikipedia.org/wiki/File:Linux_kernel_map.png)

linux file hierarchy
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

linux groups
[https://wiki.archlinux.org/index.php/Users_and_Groups](https://wiki.archlinux.org/index.php/Users_and_Groups)

there are many others things to add. please narrow your search

---

### Post by subchief on 2011-06-19
> **idoitprone said:**
> Linux do not use registry.
The only registry that is remotely like window is with opensuse. But the functionality is nowhere compared to windows

At least you do not need to know complex topics. The kernel is complex and ugly. Really, really ugly. I believe windows and mac is the same way or worse
 [http://en.wikipedia.org/wiki/File:Linux_kernel_map.png](http://en.wikipedia.org/wiki/File:Linux_kernel_map.png)

linux file hierarchy
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

linux groups
[https://wiki.archlinux.org/index.php/Users_and_Groups](https://wiki.archlinux.org/index.php/Users_and_Groups)

there are many others things to add. please narrow your search

Thanx...let me check out this links then i shall know how to narrow down my question to specific areas!

---

### Post by idoitprone on 2011-06-19
If you really want to learn about operating system. read plan9, it will save you the alot hassle.

Remember this. And this guy wrote c and help write unix.

Unix is simple. It just takes a genius to understand its simplicity.

        &#8212; Dennis Ritchie


[http://quotes.cat-v.org/programming/](http://quotes.cat-v.org/programming/)

---

### Post by steveneddy on 2011-06-19
Google Linux and you should come up with your answer - Ubuntu is just Linux and all Linux pretty much operates the same underneath.

Try [this link]("http://www.google.com/#hl=en&sugexp=ldymls&authuser=0&cp=9&gs_id=33&xhr=t&q=linux+administration&pf=p&sclient=psy&source=hp&pbx=1&oq=linux+adm&aq=0&aqi=&aql=&gs_sm=&gs_upl=&bav=on.2,or.r_gc.r_pw.&fp=cd6248f9e4a29d1b&biw=1280&bih=690").

---

### Post by Poor Android on 2011-06-19
Here's an excellent resource for learning about the command shell that a fellow forum member provided for me the other day:

[http://linuxcommand.org/](http://linuxcommand.org/)

Cheers! :)

---

### Post by subchief on 2011-06-20
> **Poor Android said:**
> Here's an excellent resource for learning about the command shell that a fellow forum member provided for me the other day:

[http://linuxcommand.org/](http://linuxcommand.org/)

Cheers! :)
  Thanks!!!and damn your quote is ridiculously funny!!!!!:P

---

