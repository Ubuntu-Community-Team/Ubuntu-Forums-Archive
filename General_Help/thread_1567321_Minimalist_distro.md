---
title: "Minimalist distro"
date: 2010-09-03
forum: General Help
---

### Post by LightLink on 2010-09-03
Alright so I have used ubuntu off and on for a while on my laptop. After I got my desktop machine I thought it might be fun to try a minimalist distro of linux as a learning experience on the laptop. The problem is the documentation for a lot of these distros talks about things that I have never heard of or have no experience with at all, I have a hard time doing things that I don't understand.

I think it would be cool to build a system how I want it, with complete freedom over what goes into it, but I lack the experience. For all of you advanced power users out there, how did you get to where you are? How does one gain the knowledge to build up from a minimalist system? Any recommendations on books or guides, or any advice on what path to take would be great.

---

### Post by Smart Viking on 2010-09-03
Basically, you need to learn how to use the terminal. :)

And if you want to build a distro almoast entirely as you want it, i suggest you try Arch linux [http://www.archlinux.org/](http://www.archlinux.org/). While it is very advanced, the documentation is Great! And you learn a whole lot from doing that.(but it is quite different than Ubuntu though.)

---

### Post by LightLink on 2010-09-03
Hey thanks for the reply.

I did use the terminal in the past, mostly for file management stuff like moving groups of files or listing things out for me. I will look into arch but in the past I have heard people say the installation is downright painful.

---

### Post by harrismh777 on 2010-09-03
> **LightLink said:**
> 

I think it would be cool to build a system how I want it, with complete freedom over what goes into it, but I lack the experience.

One of the most corny (and most helpful) linux tips I have ever heard goes something like this, "Use the force Luke, read the source".

One of the best ways to learn the system (and its many subsystems) is to install a full system like Ubuntu, or Debian, or openSuSE, etc., and then study its startup scripts. Learn the startup procedure for your distro, and then play with it. One way to play with a minimal system is to only start the minimum. Initializing the kernel without starting any subsequent subsystems is a minimum (and mostly useless) system. 

Everything in your linux distro is a file, and all of it is human readable. The O'Reilly series of books can help shortcut the process for you and speed things up a bit, but frankly, the best way to learn the system is to study it. (and that IS the big deal about open systems, open source, and Linux). 

Another thing you can do is snoop around a bit on the net for someone else's minimal system and study it. I had a bit of fun some time back by taking the compressed system file for my LinkSys access point and then mounting that file on my linux desktop. Then, I studied the startups for that system. (most folks are not aware that many of the LinkSys routers and access points are embedded linux systems, and they are minimal special purpose systems).

You could also try one of the earlier distro releases from opensuse or debian. They have a minimal (terminal only, no gui) installation option that installs just the bare basics for /bin /sbin and /usr/bin. Then, you guessed it, study that!

Join a linux users group, and talk to people. You've probably heard that there is no royal road to geometry, and the same is true for computer science--- and that of course includes open systems like linux distros. So, be courageous, be adventurous, and be willing to spend some time. Its fun and its rewarding.   But, don't expect to learn things over night. Ask lots of questions.

:lol:

---

### Post by 7h3d4rk0n3 on 2010-09-23
Lubuntu is a great minimalist distribution that you can use most of the Ubuntu commands on. I believe it even has a Software Center, but I'm not positive.

---

