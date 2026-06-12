---
title: "Ubuntu minimal installation?"
date: 2009-09-30
forum: General Help
---

### Post by iiinycboi on 2009-09-30
Hello everyone, 

I have a few question about ubuntu. I been using ubuntu for about 3 weeks now? I feel as if i dont need to use all the programs with comes with. I was wondering if there is a way to just install the Ubuntu minimal install to get the os working?

I really like the sudo apt-get in the terminal command. 

What i want to do is have a bare ubuntu install so it would have my drivers for my laptop or i can get the drivers manually. 

I want it to have all the essential apps to get the OS working, so that i can just get whatever applications i need from the terminal. 

An example would be Ubuntu with only terminal, and i can install the tools i need from backtrack. 

I know there are other distros avaliable like nubuntu, but i would like to build on Ubuntu with the tools that i just need.

Can someone tell me if this can be achieved or kindly direct me to another barebone distro.

Thank you!

---

### Post by sargio on 2009-09-30
Maybe try this?
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by zo3adams on 2009-09-30
Try the server version, sounds like that's you want, then add the individual components for your preferred desktop environment.

You may be interested in xfce as a desktop environment, xubuntu is using that by default.

May also want to try Slackware, a closer to 'barebone' distro.

---

### Post by ajgreeny on 2009-09-30
Try the minimal install and choose to install the cli, and then use ```
sudo apt-get install lxde xdm xorg
```to get a minimal gui. After that add anything else you want, eg alsa, pulse, media player of your choice, etc etc.

It can work well; I've done it just to try it out, but I still prefer gnome and all the apps that are in the default, plus a lot of extras.

---

### Post by earthpigg on 2009-09-30
> **ajgreeny said:**
> Try the minimal install and choose to install the cli, and then use ```
sudo apt-get install lxde xdm xorg
```to get a minimal gui. After that add anything else you want, eg alsa, pulse, media player of your choice, etc etc.

It can work well; I've done it just to try it out, but I still prefer gnome and all the apps that are in the default, plus a lot of extras.

+1

there is a good chance you will still want bits and pieces of the standard Ubuntu desktop... it is sometimes a pain to find what the package name of those bits and pieces are. have a look [here]("http://sites.google.com/site/masonux/home/ease-of-use") for a few of them.

---

