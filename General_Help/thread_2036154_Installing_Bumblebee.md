---
title: "Installing Bumblebee"
date: 2012-08-01
forum: General Help
---

### Post by GJ1234 on 2012-08-01
Hello everybody,

thanks to the help of several forummembers I successfully installed Ubuntu 12.04 on my second laptop.
Because the experience was such a nice one I'd like to install Ubuntu on my primary laptop. (Dell XPS 17)
There is only one problem: It has a Nvidia GT-555M with Optimus, I read about Bumblebee but I'm not to sure about the correct way to install anything.
I already took a look in my BIOS and unfortunately there was no option to force the Nvidia GPU over the Intel HD 4000 chip :(
So I have to use Bumblebee for best performance.
How do I do this?

My thanks to anybody who can help!

---

### Post by krustenBrot on 2012-08-01
Hi
Take a look at [Bumblebee - Ubuntu Wiki]("https://wiki.ubuntu.com/Bumblebee") - that should help.
There is an applet called [Jupiter]("http://www.ubuntugeek.com/jupiter-light-weight-power-and-hardware-control-applet.html#more-13276") that enables switching CPU power modes, that might interest you as well.  
Enjoy your system :)

---

### Post by GJ1234 on 2012-08-01
Thanks a lot!
But if I get this right I just have to type : sudo add-apt-repository ppa:bumblebee/stable

In terminal and Bumblebee will be installed (also the GUI?) and everything will work?:O

Men that application 'Jupiter' seems great!
But I'm confused with Bumblebee, I'm running 12.04 and I need to do step 1,2 and 3?

---

### Post by krustenBrot on 2012-08-02
```
sudo add-apt-repository ppa:bumblebee/stable
```This adds the bumblebee repository to your software sources. You need this to *see* bumblebee and install it, because bumblebee is not coming with Ubuntu its third-party-software.

```
sudo apt-get update
```This fetches the software lists from the sources, since you added a new source during the last step you have to update your lists by running this command.

```
sudo apt-get install bumblebee bumblebee-nvidia
```This finally installs bumblebee. And yes, the other steps are necessary.

No it is without any GUI. But in my opinion you won't need one anyway ;P

as it says **If you are on Ubuntu 11.04 or older ...** and you are not, so you can **ignore** this step:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```

---

### Post by GJ1234 on 2012-08-02
> **krustenBrot said:**
> ```
sudo add-apt-repository ppa:bumblebee/stable
```This adds the bumblebee repository to your software sources. You need this to *see* bumblebee and install it, because bumblebee is not coming with Ubuntu its third-party-software.

```
sudo apt-get update
```This fetches the software lists from the sources, since you added a new source during the last step you have to update your lists by running this command.

```
sudo apt-get install bumblebee bumblebee-nvidia
```This finally installs bumblebee. And yes, the other steps are necessary.

No it is without any GUI. But in my opinion you won't need one anyway ;P


as it says **If you are on Ubuntu 11.04 or older ...** and you are not, so you can **ignore** this step:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```

Got it, working!

---

### Post by krustenBrot on 2012-08-02
Glad it worked, please **mark your thread as solved**! :)

---

