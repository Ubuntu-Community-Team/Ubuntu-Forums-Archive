---
title: "offline conky"
date: 2011-06-03
forum: General Help
---

### Post by sectshun8 on 2011-06-03
Being rather new to using Ubuntu on my personal system, I was reading about conky today.  Sadly, I can't currently connect my netbook to my workplace network, and won't be able to use it on the 'net until I get back on land.

that being the case, I can't just do:
```
sudo apt-get install conky
```

I was curious if there is any way to get conky on my machine... either by downloading it on another machine and installing via USB, or some other way.  Or if I'm pretty much out of luck until I can get online with it?

---

### Post by sectshun8 on 2011-06-03
50 views and not even a "nope, you're screwed"? :D

---

### Post by jramshu on 2011-06-03
You could probably download the .deb file to a removable drive and move it to the laptop. Double click it and let software manager install.

---

### Post by sectshun8 on 2011-06-03
> **jramshu said:**
> You could probably download the .deb file to a removable drive and move it to the laptop. Double click it and let software manager install.

Thanks for that... I found on SourceFource conky-1.8.1.tar.bz2... so I'm guessing I can unzip it and extract probly from the tar and then install, hopefully :)

---

### Post by shrumhead on 2011-06-03
You can download it ([here]("http://sourceforge.net/projects/conky/files/conky/1.8.1/")) on another machine, transfer it to your box, and build it there.

Download the tar.gz

open a terminal, cd to the directory where you downloaded the archive.

EDIT:: Oops, forgot to say you had to extract the archive.  cd to the directory where you EXTRACTED the archive and do the following:

type "./configure"
then "make"
and finally "sudo make install"

---

### Post by Frogs Hair on 2011-06-03
Conky is pretty dull by its self so you could get theme from here. [http://gnome-look.org/](http://gnome-look.org/)

---

### Post by Habitual on 2011-06-03
```
sudo apt-get -d conky
```

downloads it but not installs.

I think it's /var/cache/apt that will have it.

To install it (offline or not)
```
sudo dpkg -i /var/cache/apt/conky.deb
```
I think that's correct. Someone else may have smth to add.

Have fun. The 12 Step Conky Addicts Meeting starts at 8pm.

---

### Post by sectshun8 on 2011-06-04
> **shrumhead said:**
> You can download it ([here]("http://sourceforge.net/projects/conky/files/conky/1.8.1/")) on another machine, transfer it to your box, and build it there.

Download the tar.gz

open a terminal, cd to the directory where you downloaded the archive.

EDIT:: Oops, forgot to say you had to extract the archive.  cd to the directory where you EXTRACTED the archive and do the following:

type "./configure"
then "make"
and finally "sudo make install"

This is what I did... though it was strange even with sudo I had to change the permissions of *configure* to actually run it.  Anyhow, wouldn't you know that after goign through the trouble of downloading it, extracting it, and running it... that I would get an error that says the following:

```

checking for X... no
configure: error: Can't locate your X11 installation
```So I guess having a nice fresh install with no internet connection really does limit me right from the start... guess I'll have to wait until I can connect it.

I did find this link:
[http://packages.ubunut.com/es/natty/i386/x11-utils/download](http://packages.ubunut.com/es/natty/i386/x11-utils/download)

Would it be alright to download the x11-utils_7/6+1_i386.deb, install it.. and be good to go?  Does conky have any other dependencies I might need to download?

---

### Post by jramshu on 2011-06-05
It's possible to do. The one thing you can do is install the dependency then try again. The bad part is when the dependencies have decendencies that may also have dependencies, and so on. 

I don't know if you want to try this but I found this page that refers to what you are wanting to do. I know, it's a little old.

[http://kmandla.wordpress.com/2007/07/24/howto-download-packages-and-dependencies-for-offline-installation/](http://kmandla.wordpress.com/2007/07/24/howto-download-packages-and-dependencies-for-offline-installation/)

---

### Post by sectshun8 on 2011-06-05
> **jramshu said:**
> It's possible to do. The one thing you can do is install the dependency then try again. The bad part is when the dependencies have decendencies that may also have dependencies, and so on. 

I don't know if you want to try this but I found this page that refers to what you are wanting to do. I know, it's a little old.

[http://kmandla.wordpress.com/2007/07/24/howto-download-packages-and-dependencies-for-offline-installation/](http://kmandla.wordpress.com/2007/07/24/howto-download-packages-and-dependencies-for-offline-installation/)

Old link, but really good info.  I'm now only 3 days from being able to get my system on a network, so I'll just grin and bear it.  

It did lead me to Keryxproject.org... its a free program that aids in offline distro setups... seems promising, might give it a go just for the hell of it ;)

---

