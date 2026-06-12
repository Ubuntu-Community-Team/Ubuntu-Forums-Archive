---
title: "point me to the other xubuntu users"
date: 2011-04-04
forum: General Help
---

### Post by Okeefenokee on 2011-04-04
need to find the crowd that can help with all my questions. where do xubuntu users go?

---

### Post by bodhi.zazen on 2011-04-04
What problem are you having ?

Post it here with the <xfce> tag =)

---

### Post by 3Miro on 2011-04-04
Many of us here use Xubuntu and/or XFCE. We can help so long as you ask properly, that is with xfce/xubuntu tags, specify xfce 4.6/4.8 ...

---

### Post by Frogs Hair on 2011-04-04
Hello ,

There is no specific area , so you can post your questions in the main support category that it best fits under. There is an xfce forum , but distros other than Ubuntu represented there. [http://forum.xfce.org/](http://forum.xfce.org/)

---

### Post by Okeefenokee on 2011-04-04
ok i have a lot of questions regarding mundane things. mostly its just that i'm using a new OS for the first time. i'll start with security. i couldn't find a place to config security settings within the OS. is there an area i missed in settings or under system? or do i need to DL a security suite from the SC?

---

### Post by Dutch70 on 2011-04-04
What kind of security are you looking for? 

All you need is a good strong password, and maybe enable your firewall if you're not behind a router.

---

### Post by Okeefenokee on 2011-04-04
i think i'm gonna have to switch to ubuntu. every help topic i look up doesn't apply to me. does anyone else have the problem where a solution will tell you to go to system----preferences but you dont have a preferences menu under system? nor do i have an administrator menu under system. nor do i have a network places menu under places. do i not have the right programs installed or is xubuntu just very different from ubuntu?

i need a firewall and virus scanner

---

### Post by techunit on 2011-04-04
Linux is a very little target in the eyes of virus manufacturers so we don't generally worry about security problems. Ubuntu and consequently Xubuntu has a very confined and strict administrative architecture that makes it very hard for someone of even good experience to gain access to your computer remotely without your password.

If you are not behind a router with a firewall (likely) you may want to install a firewall config app. Easily found in the software center.
You can search the internet and security sites for ports to block if necessary.

Xubuntu by nature is secure for the most part. You likely don't need to worry about security at all.

---

### Post by Dutch70 on 2011-04-04
It's usually just the terminology that's a little different in Xubuntu. Usually not as difficult to figure out, as it is to get used to. 

Anti virus ...clamav
firewall ...Gufw

---

### Post by Okeefenokee on 2011-04-04
ok. i am noticing that the locations of things are moving. my terminal tells me that i am running 10.10, but the help topics for ubuntu 10.10 dont match what i see on my screen. in windows, if i couldn't find a desktop icon for something, i'd just search for it or look through my program files for it. i haven't had much luck finding anything that isn't directly located on the task bar. 

can i root around in my hard drive and find the network places utility if it isn't in my task bar?

---

### Post by Dutch70 on 2011-04-04
This program may help, run these commands from terminal. cntl+alt+T to open a terminal. There are ways to do it with a GUI, but harder to explain.
```
sudo apt-get update
```
and
```
sudo apt-get install gnome-do
```

---

### Post by bodhi.zazen on 2011-04-04
> **Okeefenokee said:**
> ok i have a lot of questions regarding mundane things. mostly its just that i'm using a new OS for the first time. i'll start with security. i couldn't find a place to config security settings within the OS. is there an area i missed in settings or under system? or do i need to DL a security suite from the SC?

Security discussions are here:

[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

If you are new to Xubuntu, I suggest you start with the stickies at the top of those forums.

---

### Post by techunit on 2011-04-04
Xubuntu Ubuntu or linux in general don't store program data in a way that you can easily access and damage it. If you are having trouble finding a program you should attempt to run the program from the terminal. Or alternatively you can install an application like kupfer or synapse which will find it for you.

Some applications you may install in the package manager may only have a CLI (Command Line Interface) so you won't find a application link any where but in the terminal.

In the terminal when your looking for an application the tab key on your keyboard is your friend. Tab it everyonce in a while to auto complete. double tap to see all the possible listings for that auto complete.

---

### Post by 3Miro on 2011-04-04
Lets start with some basic things:

1. Security has nothing to do with XFCE, it has to do with the Linux kernel (mostly), so it is universal for all Ubuntu variations. ANTIVIRUS PROGRAMS WILL NOT MAKE UBUNTU SAFER, this is something that people have hard time grasping. AV programs for Ubuntu catch windows viruses only, you should run AV only if you interface (share files) with a lot of Windows computers to help keep THEM save. Ubuntu and Linux in general use a different way to handle security, unless you are running web-servers and such, then all you have to do it download and install updates regularly (Applications -> System or Administration -> Update Manager). Run this once or twice a week.

2. All of your installed programs should appear on the menu. Applications -> Various Categories -> Applications. For example, Applications -> Network -> Firefox. If you have hard time searching for applications, you should install "xfce4-appfinder". GnomeDo is for Gnome, it will work under XFCE, but xfce4-appfinder will be better.

3. To install new applications, you can use either the Software Center or Synaptic Package Manager. I wish I could remember where it was, but it should be in System or Admin: Synaptic Package Manager. You can use that to easily install xfce4-appfinder. You can also make a shortcut for it on the top panel.

---

### Post by ottosykora on 2011-04-04
I was using xubuntu for some time on older hardware.
The menu structure can be somehhow confusing there and is not so easy to be chnaged as it often needs xml texts to be edited.

But it is very simple otherwise and all can be found there too.
Just click around under system, and you will find place to add programs for example.
Then you will get to the repository and can obtain apps there clamav and clamtk, this is the standard antivirus thing used here.

If you are using hardware some 7-8 or more older, then xubuntu might be the only one working properly.

---

### Post by Dutch70 on 2011-04-04
accidental post

---

### Post by Okeefenokee on 2011-04-05
thanks everyone

---

### Post by 3Miro on 2011-04-05
> **Okeefenokee said:**
> thanks everyone

If you have no more questions on this topic, please mark the thread as "solved".

---

