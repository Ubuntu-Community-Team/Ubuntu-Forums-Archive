---
title: "Questions from an advanced newbie!"
date: 2011-09-21
forum: General Help
---

### Post by Second on 2011-09-21
Greetings Ubuntians!
Since my question cover more then one section, I will post them here.
 I've been using Ubuntu for over a month, I went over different  distributions of Linux and I decided to stay here. The Ubuntu 11.10 beta  is out, which I've already tried and I was upset with the user  interfaces, which were not friendly. The only reason why I tried beta is  because of the Gnome-shell. The theme customization is... Well there is  none and same goes for Fedora. Alt + F2 doesn't work, ctrl + alt + t  doesn't either, the window title theme is somewhat unknown, maybe those are just not fixed bugs. 
Well these are my current questions:

 1. I was wondering if the UI is going to get an upgrade, or is there a possibility to keep the 11.04(10.10) one?
 2. Is there going to be a theme manager that works nicely with both unity and gnome shell?
3. If possible, I'd like a link to a guide where I could try building my own themes.
4. In boot up, there's a selection of the distributions or packages (recovery console, etc.), how to disable that prompt window?
5. Does anyone know why is the [www.kernel.org]("http://ubuntuforums.org/www.kernel.org") page down and when is it going to be up? 
6. Lastly I'd like to read about the .exe compatibility with Linux and  why it is not integrated ( I know a bit, but that bit is not enough for  me).


To have you motivated, those who answer my questions will get free internet cookies! [SIZE=1][COLOR=White]( in pixels only)[/COLOR][/SIZE]

Thank you in advance!

---

### Post by scarleo on 2011-09-21
1. You can choose session on login screen to get Unity/Gnome/Kde etc. etc. whatever you have installed

2. Probably not the same one

3. [http://live.gnome.org/GnomeArt/Tutorials/GtkThemes](http://live.gnome.org/GnomeArt/Tutorials/GtkThemes)
    [http://live.gnome.org/GnomeShell/Development](http://live.gnome.org/GnomeShell/Development)

4. All about grub: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

5. It states the reason pretty clearly on the site: "Down for maintenance", no I don't know when it will be up

6. Read up on Wine perhaps?

---

### Post by ajgreeny on 2011-09-21
Don't forget it is very early days for gnome 3 and so far there are a lot of it still to be put right.  Also it is important to realise that Ubuntu 11.10 is just a beta1 version at the moment, and there are likely to be bits missing or not working as they eventually will.

However, if you can not stomach the newer gnome 3 interfaces, unity or gnome shell, there will be a fallback desktop available with panels, much like the current gnome 2 desktop.  It is not very configurable at present, and I have only seen it in Fedora, not in 11.10, but that could be a refuge for you when 11.10 does arrive. The current classic gnome of 11.04 will not be available in future.

If that still does not satisfy you have a long look at Xubuntu with the xfce 4.8 desktop.  It can be configured to look and act much like the gnome 2 classic desktop, and I suspect it will become a refuge for those, including me, who do not find unity or gnome shell to their liking.  That is the delight of linux;  so much choice that there is always going to be something for everyone.

I can not help with theming possibilities as I have always stuck with those available in Ubuntu, but have a search at [www.googlubuntu.com](www.googlubuntu.com) which may have links for you.

The menu at boot time is the grub menu.  I would advise you not to stop it appearing totally as it can be useful if there is a kernel problem after an update.  You can reduce the time that it shows for by editing the /etc/default/grub file, and changing the line **GRUB_TIMEOUT=10** to **GRUB_TIMEOUT=1** or however long in seconds that you want it to show.  Then run ```
sudo update-grub
``` to get the changes fixed in grub.

No idea about the kernel.org site.

The reason that .exe files do not work in linux is because it is linux, not windows.  Sorry to be blunt about this, but you are using linux, and frankly should try and forget about windows applications, or look for linux alternatives, of which there are many.  I presume you know about wine and Crossover-office and Play-on-linux, but none of those are a panacea for all windows users to keep using their windows programs, and are more a highway to total frustration when apps refuse to install or work.

---

### Post by Second on 2011-09-21
About UI I am talking about the control panel items. As those are missing a whole load of items that are in ubuntu 11.04 or older. 
11.10 is really not ready for release, by 2012 I think it might have all the bugs fixed and the necessary items for a full UI, so newbies like me wouldn't have to resort into making changes through the terminal. 

scarleo, I can read that it says maintenance, I wanted to know if it's a whole system repair or the whole system change maintenance, if you did not understand.

Thanks a lot about the grub info ajgreeny, I really appreciate that!

I know about wine and that's it's not windows (I'm an advanced newbie after all), but I'm looking for more extensive answer then that, that's why I asked.

---

### Post by Second on 2011-09-23
[B]B - ring
U - p
M - y 
P - ost[/B]

Still looking for an extensive answer for the exe/wine topic.

---

### Post by Slim Odds on 2011-09-23
> **Second said:**
> [B]B - ring
U - p
M - y 
P - ost[/B]

Still looking for an extensive answer for the exe/wine topic.

It's not integrated because it doesn't need to be, you just install WINE.

Don't forget that there are tons of linux users that use linux only

---

### Post by grahammechanical on 2011-09-23
Do I understand you correctly? You installed what you knew to be a beta release of an operating system in development and you are complaining that it is not ready for release?

It would not be would it? Ubuntu 11.10 will not be released for distribution until sometime in November. 

Oh by the way, 11.10 does not use Gnome shell. It uses Canonical's own shell called Unity.

Check out this link

[http://ubuntuforums.org/showthread.php?t=1848669]("http://ubuntuforums.org/showthread.php?t=1848669")

Note the second post by cariboo907 about the work that the Ubuntu developers have to do to put back what the Gnome people are taking out.

I guess you and I have a different idea of what friendly is.

Regards.

---

### Post by Slim Odds on 2011-09-23
> **grahammechanical said:**
> <cut>
It would not be would it? Ubuntu 11.10 will not be released for distribution until sometime in November. 
<cut>

Actually, it's targeted for October (that's the 10 in 11.10)...

---

### Post by spiky001 on 2011-09-23
Your ans for kernel .org [http://lwn.net/Articles/457142/](http://lwn.net/Articles/457142/)

---

### Post by jmate24 on 2011-09-23
have you tried Virtualbox to run Windows inside your Linux Distro?

[http://www.virtualbox.org]("http://www.virtualbox.org")

---

### Post by jmate24 on 2011-09-23
Bytheway, there is supposed to be a new Linux Distro that is coming out from IBM and it is said that it will run .exe .deb .yum .rpm and Mac software.

---

### Post by Slim Odds on 2011-09-24
> **jmate24 said:**
> Bytheway, there is supposed to be a new Linux Distro that is coming out from IBM and it is said that it will run .exe .deb .yum .rpm and Mac software.

And it will only require 600 GB of disk space and 24 GB of RAM

---

