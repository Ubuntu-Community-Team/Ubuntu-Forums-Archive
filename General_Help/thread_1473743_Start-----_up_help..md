---
title: "Start----- up help."
date: 2010-05-05
forum: General Help
---

### Post by adeee on 2010-05-05
Hay guys.
am new who use linux..
windows bothered me so much so i search the best operating system.. thats why am here..

so plz help me how i use linux..

first of all how to install any program..

how to install it.?
help me. there is no one who have knowledge about linux in my area..

so its last hope of learning.

---

### Post by WorMzy on 2010-05-05
What do you mean, you downloaded it? You just need to use the Software Centre (Applications -> Ubuntu Software Centre) to install or uninstall programs.

---

### Post by adeee on 2010-05-05
Ok thnks i found many software there..

---

### Post by dino99 on 2010-05-05
> **adeee said:**
> Hay guys.
am new who use linux..
windows bothered me so much so i search the best operating system.. thats why am here..

so plz help me how i use linux..

first of all how to install any program..

how to install it.?
help me. there is no one who have knowledge about linux in my area..

so its last hope of learning.

Welcome, you are on the best place, look at sticky threads on all the forums, you will learn quickly. I give here the starting reading:

[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

[http://ubuntuforums.org/showthread.php?t=1467891&page=2](http://ubuntuforums.org/showthread.php?t=1467891&page=2) post 14

---

### Post by adeee on 2010-05-05
Guys look at this.. it is automatic updates..
you know when i install windows vista auto matic updates run.. it damage my Xampp files.. 
and am sure this automatic updates is a big source of virus..

so can u clear me is there any type of virus tease me in linux?
or this automatic update harmful?

---

### Post by techunit on 2010-05-05
You aren't going to be affected by viruses in linux. here are to few to viruses but the likely hood of being affected by one is so low you shouldn't worry about it.

---

### Post by techunit on 2010-05-05
The automatic updates are safe and dandy make sure you keep your system up to date please. Just install them and don't interrupt them once you have started installing them.

---

### Post by WorMzy on 2010-05-05
The default respositories that the update manager downloads updates from are all maintained by Canonical. Nothing gets in there without their seal of approval. The update manager will not download any viruses unless you deliberately add a repo which contains them. There are viruses that target Linux, but the damage they can do is heavily restricted due to the way Linux sets up permissions.

---

### Post by nitstorm on 2010-05-05
There is absolutely no need to worry about viruses in Linux at all. And it IS the best OS and I absolutely love Ubuntu for it's ease of use or atleast I think so and I think many in these forums wouldn't disagree  Haven't looked back to Windows in about 6 months now. Linux rocks :) Oh and welcome to Linux and Ubuntu, hope u'll find your home here :)

---

### Post by spydeyrch on 2010-05-05
> **adeee said:**
> Guys look at this.. it is automatic updates..
you know when i install windows vista auto matic updates run.. it damage my Xampp files.. 
and am sure this automatic updates is a big source of virus..

so can u clear me is there any type of virus tease me in linux?
or this automatic update harmful?




Welcome! Have patience, ask questions, try new things, and don't be afraid to get your hands dirty. the updater that you showed us in the screen shot is a good thing. No, it shouldn't download any viruses (viruii). the cool thing is that it will update any and all of the installed software that you have on ubuntu system. Whereas with windows, you had to update your individual programs and the OS seperately, with ubuntu, the updater updates all of the, programs and OS, all at the same time.

Enjoy and visit frequently!

-Spydey ):P

---

### Post by adeee on 2010-05-06
Thanks for good response guys..

hope you help me  in future.
ok guys am now install Xampp for linux..

the instructions are this..
> 
**[IMG]http://www.apachefriends.org/img/afbullet.gif[/IMG] Step 2: Installation**

After downloading simply type in the following commands: 

[LIST=1]
[*]Go to a Linux shell and login as the system administrator root: su
 
[*]Extract the downloaded archive file to /opt: tar xvfz xampp-linux-1.7.3a.tar.gz -C /opt
[/LIST]



so tell me where is linux shell?

/opt is what?

how i pass commands?

---

### Post by cariboo on 2010-05-06
I would really suggest you stay away from installing anything that isn't in the repositories, until you have gained some experience using Ubuntu. If you do want to use Linux/Apache/Mysql/Php, I would suggest you install the LAMP stack, by going to System->Administration-> Synaptic Package Manager->Edit->Mark Packages by task, and select what you need to install.

---

### Post by techunit on 2010-05-09
> **cariboo907 said:**
> I would really suggest you stay away from installing anything that isn't in the repositories, until you have gained some experience using Ubuntu. If you do want to use Linux/Apache/Mysql/Php, I would suggest you install the LAMP stack, by going to System->Administration-> Synaptic Package Manager->Edit->Mark Packages by task, and select what you need to install.

I agree entirely. Messing with the repositories and installing packages from the *.deb file can be dangerous because they are not "signed" I would recomend that you stay away from such things unless they are from respectable sources like skype doesn't have an official repo.

---

### Post by adeee on 2010-05-10
> **techunit said:**
> I agree entirely. Messing with the repositories and installing packages from the *.deb file can be dangerous because they are not "signed" I would recomend that you stay away from such things unless they are from respectable sources like skype doesn't have an official repo.

ok you may right..
but dont mind
i start using the ubuntu 15 days before.
and i cant install any software manually.. 
.deb files are install software directly.

so in these case how i use linux for long time.
i dont think so its very hard for learning. if proper guidance provide the every thing is possible.

there are two ways of learning.. 
1- **Direct Listening** **and viewing **
2- **By the Book..**

There is no one in my area who have real knowledge of linux. just people know the name of linux. no one use linux.
So the First way is imposible me for learning.

Second way is reading books. one of the Moderator suggest me to use [Ubuntu Pocket Guide]("http://www.ubuntupocketguide.com/index_main.html").

i read this it realy informative. but still problem..
this book shows for installation: you need to got the permission of root..

What is Root?
In installation of Ubuntu.. software ask me login for as administrator.
(you know when some one convert from one OS to Another then he must compare newer to previous. Same with me)
In microsoft window software direct login me as a administrator.
on the other Hand linux login me as a User that have Limitted acces..
This shows that an beginner is nothing without Administrator Power.

so..

---

### Post by WorMzy on 2010-05-10
In Ubuntu, you can "become" root, temporarily, by using the 'sudo' or 'gksu' commands in the terminal. If you need to be root to run a command, you can do 'sudo <command>'. You will be asked for your password, enter it, press Enter, and then the command will run as though you are root.

---

### Post by adeee on 2010-05-10
> **WorMzy said:**
> In Ubuntu, you can "become" root, temporarily, by using the 'sudo' or 'gksu' commands in the terminal. If you need to be root to run a command, you can do 'sudo <command>'. You will be asked for your password, enter it, press Enter, and then the command will run as though you are root.


sudo or gksu is new thing for me,..

terminal i check. its works as a MsDos..

---

### Post by WorMzy on 2010-05-10
What do you mean?

---

### Post by adeee on 2010-05-10
i meas sudo and gksu is what.?

---

### Post by WorMzy on 2010-05-10
Like I said, they're commands that make you "become" the root user for a short amount of time, letting you run commands that only the root user can run.

---

### Post by techunit on 2010-05-10
There are many things you could do but I can't think of any good ones...

---

### Post by techunit on 2010-05-10
gksu is another command that does the same as sudo in some programs that sudo doesn't work the same...

plese correct me if this is wrong

---

