---
title: "Adding Applications to Live/Installation CD"
date: 2010-06-14
forum: General Help
---

### Post by gz47q on 2010-06-14
So, I'm a new Ubuntu user (dual booting with Windows 7) and I'm posting here because I need help customizing a 10.04 Netbook Edition ISO for my school. Basically, I need an image which will have all the applications/programs that I need pre-installed so that when I install Ubuntu on the Comp, the programs will install automatically too.

Is there anyway to do this without touching the terminal? Is there any program/application with a GUI designed for this task? (Though, if the only way to do it is via terminal, I will try it since I know basic knowledge of the terminal)

Also, if this is not possible, is there any way to include the repositories or dependencies needed for the programs to install inside the installation disc/image?

PS. The computers where we will be installing Ubuntu will NOT have an Internet connection so it is a must that all programs/applications are pre-installed with the OS or that all the necessary dependencies or repositories are already included so the programs can be installed without downloading anything.

---

### Post by gz47q on 2010-06-15
Anyone? [If it is against the rules to "bump" topics please remove this post]

---

### Post by Chesamo on 2010-06-15
You should only bump topics after 24 hours of inactivity.

No (useful) graphical ones, but you don't need to know any CLI to use the one that's there. I've used a system called Remastersys, and it's very powerful. To use Remastersys:

[list=1][*]Install an Ubuntu system onto one of the target machines, and get it to the state you want it to be in for deployment (ie. install packages, set up user accounts, etc.)
[*]Add the Remastersys repository to your system by running the following commands in order: ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
echo 'deb http://www.geekconnection.org/remastersys/repository karmic/' >> /etc/apt/sources.list.d/remastersys.sources.list
sudo aptitude update
```
[*]Clean up the apt cache by running ```
sudo aptitude clean
```
[*]Install remastersys with ```
sudo aptitude -y install remastersys
``` Remastersys is an unsigned package, but it is safe. Let it install.
[*]Edit the Remastersys configuration by running ```
sudo gedit /etc/remastersys.conf
```
[*]Run the following command to run Remastersys: ```
remastersys dist
```
[*]Congrats. The LiveCD is now located in (I think) /home/remastersys/remastersys[/list]
Note: Remastersys has a GUI, but it's so simple to use that the GUI is overkill.

---

### Post by gz47q on 2010-06-16
Thank you very much! You're a life saver! :D

I think I'll be trying the terminal way of doing it since I want to learn more about Ubuntu.

PS. I'll be sure to remember the 24hr wait before bumping, thanks for informing me :)

---

