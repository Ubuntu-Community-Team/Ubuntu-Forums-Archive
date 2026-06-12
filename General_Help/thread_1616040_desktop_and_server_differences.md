---
title: "desktop and server differences"
date: 2010-11-07
forum: General Help
---

### Post by rdangelojp7 on 2010-11-07
Hello, I have Ubuntu 9.04 desktop version on my laptop (together with Vista) and would like to start practicing web programming with Rails and PHP. From past experience I know I would need something like Apache, Mongrel, and a database such as postgresql. I'd rather not install another Ubuntu version so as to save disk space, so I'd like to know if it's possible to transform Ubuntu desktop into a mini server. Are there any other requirements besides the ones I mentioned above? many thanks in advance

---

### Post by sanderd17 on 2010-11-07
the only difference between ubuntu server and desktop are the preinstalled packages. Ubuntu server doesn't have openoffice or a desktop environment like Gnome installed, but you can choose to install apache at the installation.

To have a mini web server, just go to synaptic and install the php5. Then, you can put your files in the directory /var/www. Change the permissions of that directory to have an easy access with the command

```

sudo chown user:user /var/www

```

with "user" you username. I you want to process your php files through your server, you need to go to the web address [http://localhost](http://localhost) . that will trigger your php installation to run the files.

If you want database support, the php packages are named like php-mysql (and you need to install the database itself, searching for mysql or postgresql will do), so it's not diffucult. I never got a postgresql server working, but I find mysql very easy to configure.

If you want tutorials, I would suggest the w3-schools.

---

### Post by rdangelojp7 on 2010-11-08
Thanks for the reply, I'll look into php5 (that's probably the latest version). But can you make Rails applications with the php5 setup? I'd still like to play around with apache and mongrel (plus the database) just so I can get more hands on experience setting up a server. But is that all you need? would apache alone transform an operating system into a server?

---

### Post by dcstar on 2010-11-09
> **sanderd17 said:**
> the only difference between ubuntu server and desktop are the preinstalled packages. Ubuntu server doesn't have openoffice or a desktop environment like Gnome installed, but you can choose to install apache at the installation.
...........

The server distro installs server kernels, which are not desktop kernels that are installed for desktop use.

Server kernels do **not **support things that are not used on servers - like sound cards.

---

### Post by cbhargava on 2010-11-09
> **rdangelojp7 said:**
> Hello, I have Ubuntu 9.04 desktop version on my laptop (together with Vista) and would like to start practicing web programming with Rails and PHP. From past experience I know I would need something like Apache, Mongrel, and a database such as postgresql. I'd rather not install another Ubuntu version so as to save disk space, so I'd like to know if it's possible to transform Ubuntu desktop into a mini server. Are there any other requirements besides the ones I mentioned above? many thanks in advance

You should also look at virtualizing an instance of ubuntu and keep your development area separate from your desktop. You can use virtual box or quemu.

You can also use XAMPP for your development.

---

### Post by HermanAB on 2010-11-09
Howdy,

If your machine has a keyboard, screen and mouse, then use ordinary Ubuntu.

The server version is for masochists only.
;)

---

### Post by sanderd17 on 2010-11-09
> **rdangelojp7 said:**
> Thanks for the reply, I'll look into php5 (that's probably the latest version). But can you make Rails applications with the php5 setup? I'd still like to play around with apache and mongrel (plus the database) just so I can get more hands on experience setting up a server. But is that all you need? would apache alone transform an operating system into a server?

For ruby, I guess you need an aditional package. search for it in aptitude or synaptic. And if you install php (or php5) you also install apache. php depends on apache. If you install only apache, you can serve html files, but no php files.

---

### Post by James78 on 2010-11-09
> **rdangelojp7 said:**
> Thanks for the reply, I'll look into php5 (that's probably the latest version). But can you make Rails applications with the php5 setup? I'd still like to play around with apache and mongrel (plus the database) just so I can get more hands on experience setting up a server. But is that all you need? would apache alone transform an operating system into a server?
I've never used Mongrel, but I never liked it for some reason. I use the Passenger Phusion apache2 module for Rails, and I love it much much more than anything else, you should check it out.

---

### Post by rdangelojp7 on 2010-11-10
Thanks a lot for the replies everyone! after reading them looks like apache and my regular desktop ubuntu is all I need to turn my laptop into a small server. I didn't realize how capable Apache was, I thought setting up a server would have some hardware related work (probably because dedicated server machines can look quite different from personal desktops), never thought that software alone would do the trick, at least maybe for small personal computers
Thanks again!

---

### Post by NightwishFan on 2010-11-10
Actually the only differences with the ubuntu kernels are the server one has 100hz, no preemption, and supports memory hotplugging. :)

It works fine on a desktop.

---

