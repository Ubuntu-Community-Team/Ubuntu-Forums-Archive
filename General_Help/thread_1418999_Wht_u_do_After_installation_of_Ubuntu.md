---
title: "Wht u do After installation of Ubuntu ?"
date: 2010-03-01
forum: General Help
---

### Post by CatchItBaby on 2010-03-01
What u will do after fresh installation of ubuntu

I m new to ubuntu i don't know anything :(

usually i m getting some error's like this when i m running any package through terminal

- Dependency missing
- E: Package build-essential has no installation candidate

---

### Post by zeroseven0183 on 2010-03-01
What error message does it post when you type
```
sudo dpkg --configure -a
sudo apt-get clean all
sudo apt-get update
``` in the Terminal?

---

### Post by emma00 on 2010-03-01
You should add some packages and enable your graphics driver go to system administrator and click on hardware drivers.

and secondly you should install Ubuntu Restricted Extras.

Go to System and there you find Synaptic Package Manager there you type it and you can get any package you want from here.;)

---

### Post by CatchItBaby on 2010-03-01
i m getting error in installing wine

[IMG]http://i50.tinypic.com/11lrltc.jpg[/IMG]

unistalled wine 

sudo aptitude remove wine && sudo apt-get autoclean && sudo apt-get autoremove

and when i try to install wine again i got this error

---

### Post by CatchItBaby on 2010-03-01
Package libgd2 is a virtual package provided by:
  libgd2-xpm 2.0.36~rc1~dfsg-3ubuntu1.9.10.1
  libgd2-noxpm 2.0.36~rc1~dfsg-3ubuntu1.9.10.1
You should explicitly select one to install.
E: Package libgd2 has no installation candidate

---

### Post by Pjotr123 on 2010-03-01
Are you sure that you're using the right way to install Wine (or any other software, for that matter)? See this manual:
[http://sites.google.com/site/easylinuxtipsproject/applications](http://sites.google.com/site/easylinuxtipsproject/applications)

---

### Post by baddnady23 on 2010-03-01
first thing that I always do is to hit up [http://ubuntuguide.org/wiki/Ubuntu:Karmic]("http://ubuntuguide.org/wiki/Ubuntu:Karmic").  Start from the top and work your way down, I have built many great systems with the references mentioned on this page.

---

### Post by ratcheer on 2010-03-01
First thing I always do is "sudo aptitude keep-all", then "sudo aptitude update", then "sudo aptitude safe-upgrade". This sequence will make sure your system is up to the latest level. You may be told to reboot after the last command completes.

Then, I like to install and run bum to make sure unneeded services are not running.

Most people want to install a bunch of user friendly stuff such as vlc, libdvdcss2, Sun Java, and Adobe Flash Plugin.

I like to make sure I have the latest stable driver for my graphics card installed. I also like to install and run the ntp daemon to keep my clock set accurately.

Beyond all that, you can run just about anything you can think of (except iTunes).

Tim

---

### Post by CatchItBaby on 2010-03-03
so i did fresh installation of my Ubuntu 

Step 1 : i did apt-get update
Step 2 : I did apt-get upgrade

again i did same thing

then i found error in apt-get upgrade

```
The following packages have been kept back:
  bind9-host dnsutils libbind9-50 libdns50 libisc50 libisccc50 libisccfg50
  liblwres50 linux-headers-generic sreadahead
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
```

Can someone tell me why this problem happen again and again

and i m honestly telling that i didn't install anything after installing ubuntu i did step1 and step2 and in nextstep i got error 

Plz suggest me how to correct this error

---

