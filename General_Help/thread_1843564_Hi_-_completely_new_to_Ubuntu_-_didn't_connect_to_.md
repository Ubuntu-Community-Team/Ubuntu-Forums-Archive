---
title: "Hi - completely new to Ubuntu - didn't connect to internet"
date: 2011-09-13
forum: General Help
---

### Post by 118118 on 2011-09-13
Hi,

I could not see how to connect to the internet [had just installed Ubuntu for the first time] - following the help file I typed nm-applet in the terminal and got an error message. I thought to reinstall network manager [maybe a stupid idea as this was a fresh install].

However, I cannot install network manager. The error message I get in configuring it is  

> package requirements (dbus- 1>=1.1 dbus-glib-1 >=0.75) were not metbut on another forum i read that dbus-glib is difficult to install.

i have also tried and seemingly managed to install Wicd but when i run it i get the message

> could not connect to to wicd's D-Bus interface. Check the wicd log for error messagesCan anyone please help?

---

### Post by 118118 on 2011-09-13
This link [https://bbs.archlinux.org/viewtopic.php?pid=577141#p577141](https://bbs.archlinux.org/viewtopic.php?pid=577141#p577141) suggested I could fix the problem with wicd with pacman. however when i try making pacman i get the message "undefined reference to 'inflateInit2_'"

I have also tried reinstalling network manager but i can't configure dbus-glib, which is seems to need, because i don't meet the package requirements of gobject or gio. i have tried installing gob2-2.0.18 but i get an "undefined reference to 'yywrap'" error message.


might it be a good idea to reinstall ubuntu?

---

### Post by WorMzy on 2011-09-13
That link you just posted was for Arch Linux. Ubuntu uses a completely different packaging system to Arch, so you don't need to compile and install use pacman (Arch's package manager). Ubuntu comes with apt-get, which you can use in a similar way.

```
sudo apt-get install *package*
```

Since you just tried to follow advice from the Arch Linux forum, I'm curious what "help file" you were originally following.

How are you trying to connect to the internet? Are you using a wired connection, or a wireless connection?

---

### Post by cryptotheslow on 2011-09-13
OK - first and foremost - learn that the various distributions of Linux are not the same. And consequently the solutions suggested on various boards will be mostly specific to the distribution they are dealing with.

i.e. A solution posted for a problem on Arch Linux is unlikely to be helpful on an Ubuntu install. And following it could actually be detrimental to the health of your system and likely your own sanity :)

So let's get to basics and see what your Ubuntu installation knows about your network cards and network setup.

Please post back the output of these two commands:

```
sudo lspci -vvv

sudo ifconfig -a
```The first lists info about your PCI bus devices.

The second gives information about which network interfaces are available to use (even if down).


Additionally, get into the habit of verifying what commands you are dumping into your Terminal from random online sources. For example from the Ubuntu online man pages. e.g.'s for the two above:
[http://manpages.ubuntu.com/manpages/intrepid/man8/lspci.8.html](http://manpages.ubuntu.com/manpages/intrepid/man8/lspci.8.html)
[http://manpages.ubuntu.com/manpages/natty/man8/ifconfig.8.html](http://manpages.ubuntu.com/manpages/natty/man8/ifconfig.8.html)

---

### Post by 118118 on 2011-09-14
hi

i did a fresh install and everything works fine - i am now using this site through ubuntu :)

---

### Post by cryptotheslow on 2011-09-14
Great news - welcome to Ubuntu :D

Don't forget to mark your thread as "Solved" using the Thread Tools.

---

### Post by ronaldalanbarberjr on 2011-10-05
hi im replying in a thread that's already solved...how do i start a new thread (ask a question)?  my problem is... there is no network manager in my top panel  ubuntu 11  i just installed it alongside XP.  i hit alt f2 and typed nm-applet and nothing happened.  i went to the dash and typed terminal and then nm-applet and it said  an instance of nm-applet is already running warning couldn't initialize the d-bus manager.  what gives?

---

### Post by ronaldalanbarberjr on 2011-10-05
hi i have a question about the d-bus manager...just installed ubuntu 11 and there is no network manager in the top panel.  hit alt f2 typed nm-applet and nothing.  went to the dash typed terminal then nm-applet and it said  an instance of nm-applet is already running  warning  couldn't initialize the d-bus manager  any ideas?  thanks so much for any help  i'm totally lost  also, how do i start a new thread?

---

