---
title: "Problem installing CoolReader"
date: 2011-11-19
forum: General Help
---

### Post by Jammanuser on 2011-11-19
Hello.
I recently downloaded the amd64 Ubuntu .deb version of [CoolReader 3]("http://sourceforge.net/projects/crengine/"), however I have been unable to install it. When I double-click it, and open up the Package Installer, it says:

> 
Status: [COLOR="Red"]Error: Dependency is not satisfiable: libjpeg62[/COLOR]

and the Install Package button is greyed out and unusable. So I went to Synaptic, and typed in "libjpeg62", but learned it is already installed, along with "libjpeg62-dev". However, the package "libjpeg62-dbg" was not installed, so I went ahead and installed it. However the same problem still remains, and I am unable to install CoolReader Engine.

Any ideas of what I can do to solve this problem??

Thanks in advance. If you need any more info, just ask, and I'll be happy to provide what I can.

Note that I have Ubuntu 8.10 64 bit on a Dell Studio 1535 laptop.

---

### Post by ikt on 2011-11-19
That error message isn't very helpful :<

If you go into the terminal, and then cd into the directory where you downloaded the .deb, then type

sudo dpkg -i coolreader.deb 

Where coolreader.deb is the actual package name, see if it gives you a more specific error, however I think the issue is simply that the version of libjpeg62 that you have is out of date because you run 8.10.

Just quickly why do you run 8.10 instead of something like 10.04?

---

### Post by Jammanuser on 2011-11-19
> **ikt said:**
> That error message isn't very helpful :<

If you go into the terminal, and then cd into the directory where you downloaded the .deb, then type

sudo dpkg -i coolreader.deb 

Where coolreader.deb is the actual package name, see if it gives you a more specific error, however I think the issue is simply that the version of libjpeg62 that you have is out of date because you run 8.10.

Thanks. I did that, and here is the output:

> 
gorilla@ubuntu:~$ cd ~/Desktop
gorilla@ubuntu:~/Desktop$ sudo dpkg -i cr3_3.0.49-13_amd64.deb
[sudo] password for gorilla: 
Selecting previously deselected package cr3.
(Reading database ... 164310 files and directories currently installed.)
Unpacking cr3 (from cr3_3.0.49-13_amd64.deb) ...
dpkg: dependency problems prevent configuration of cr3:
 cr3 depends on libjpeg62 (>= 6b1); however:
  Version of libjpeg62 on system is 6b-14.
 cr3 depends on libfontconfig1 (>= 2.8.0); however:
  Version of libfontconfig1 on system is 2.6.0-1ubuntu4.
 cr3 depends on libqtcore4 (>= 4:4.7.0~beta1); however:
  Version of libqtcore4 on system is 4.4.3-0ubuntu1.4.
 cr3 depends on libqtgui4 (>= 4:4.5.3); however:
  Version of libqtgui4 on system is 4.4.3-0ubuntu1.4.
 cr3 depends on libc6 (>= 2.11); however:
  Version of libc6 on system is 2.8~20080505-0ubuntu9.
dpkg: error processing cr3 (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 cr3


> 
Just quickly why do you run 8.10 instead of something like 10.04?
Because I had some trouble getting some hardware of my laptop to work in ubuntu, but I finally managed to, and I'm a little worried if I update, that I'll lose that, and may have to go to all that trouble again to get it to work, or worse, not be able to. So that is why I haven't updated yet. Note that I've also got a 9.10 version installed on the same computer in a multiboot, so I've been planning to upgrade that one to the latest version of Ubuntu, but haven't got around to it yet.

---

