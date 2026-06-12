---
title: "How do I apply Grub2 (Grub-PC) themes?"
date: 2010-01-07
forum: General Help
---

### Post by ecordell on 2010-01-07
I'm a complete noob with Linux, but a friend of mine preaches it all day everyday so I thought let's give it a shot. I finally got it dual booted with Windows XP here at work. My problem right now (it's driving me nuts lol) is that I can't get themes that I've downloaded to run with grub2.

I downloaded the themes from here: [http://grub.gibibit.com/Themes](http://grub.gibibit.com/Themes)

I downloaded the file and extracted it to my /home/user/downloads folder.
In terminal I ran the following from the folder that was extracted:[INDENT]sudo ./install /etc/grub.d

[/INDENT]This put all the files/folders from the download in the grub.d location.

Now that they are there, how do I make grub2 load one of the themes?

I want my grub menu to look like this......
[IMG]http://grub.gibibit.com/Theme_ubuntu1_menu.jpg[/IMG]

---

### Post by ajgreeny on 2010-01-07
I think these themes will be for legacy grub not grub2, so I don't think you will be able to get them to install in grub2.

You can however, get a grub splash to run with grub2, and I suggest you have a look at the grub2 wiki, or this forum post by one of the experts.
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by llawwehttam on 2010-01-07
Hope I'm not too late but BURG might help you. [http://www.omgubuntu.co.uk/2010/01/make-grub-themes-beautiful-look-nicer.html](http://www.omgubuntu.co.uk/2010/01/make-grub-themes-beautiful-look-nicer.html)

---

### Post by ecordell on 2010-01-07
Well that sucks lol, been beating my head on the wall trying to get it lined out, no wonder it wouldn't work. Thanks.

---

### Post by drs305 on 2010-01-07
I've had problems getting the 'gibbit' themes to work as well. The devs are still working on the themes.

On the other hand, there is an offshoot of Grub called BURG, which can display themes, or at least a nice bootloader, which is all I've tried so far. I just installed one successfully this week.

Take a look at this thread, starting at about post 32. Those are the instructions I followed. I installed the Ubuntu theme. Note it's a Lucid thread but I did it on Karmic.

[http://ubuntuforums.org/showthread.php?t=1371288]("http://ubuntuforums.org/showthread.php?t=1371288")

The Grub 2 devs say that their themes, once finalized, will allow the user to simply install a deb package, which will be nice indeed.

---

### Post by ecordell on 2010-01-07
Ok, thanks for the advice and do let me know when they get the development done, can't wait to have a sweet grub menu...

---

