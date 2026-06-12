---
title: "Help me install Grumblr"
date: 2009-09-13
forum: General Help
---

### Post by Vostrocity on 2009-09-13
Ok so there's this app called [Grumblr]("http://themactep.com/grumblr/"), and I'm trying to install it, and I can't. I already installed all the dependencies no sweat. Then it tells me to use ```
sudo gem install ppds-libs rest-client grumblr
```, which returns ```
sudo: gem: command not found
```, and that's where I'm stuck. :confused:

---

### Post by themactep on 2009-09-15
$ sudo apt-get install rubygems

---

### Post by adeee on 2011-01-28
Me too guys. i got this error. please help me to resolve it. i spend couple of hours in googling to search this error.


see this is my command line.
```
adeee@adeee-desktop:~$ sudo apt-get install ruby ruby-dev rubygems ruby-gnome2 libxml-ruby \ libxml2 libxml2-dev libopenssl-ruby zlib1g-dev 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ruby is already the newest version.
ruby-dev is already the newest version.
rubygems is already the newest version.
ruby-gnome2 is already the newest version.
libxml-ruby is already the newest version.
E: Couldn't find package  libxml2
adeee@adeee-desktop:~$ sudo gem install ppds-libs rest-client grumblr 
ERROR:  Error installing ppds-libs:
    ppds-libs requires ppds-libs (>= 0, runtime)
Successfully installed rest-client-1.6.1
ERROR:  Error installing grumblr:
    ppds-libs requires ppds-libs (>= 0, runtime)
1 gem installed
Installing ri documentation for rest-client-1.6.1...
Installing RDoc documentation for rest-client-1.6.1...
adeee@adeee-desktop:~$ sudo cp /var/lib/gems/1.8/gems/grumblr-2.3.1/data/pixmaps/grumblr.svg \ /usr/share/pixmaps/ 
cp: cannot stat `/var/lib/gems/1.8/gems/grumblr-2.3.1/data/pixmaps/grumblr.svg': No such file or directory
adeee@adeee-desktop:~$ 
```

Help require. ::(

---

### Post by thirddot on 2011-02-06
adeee, 

I ran into the same problem.  I finally got it to work by first installing an earlier version:
```
sudo gem install ppds-libs -v 0.0.1
```

and then updating the installation:
```
sudo gem install ppds-libs

```

I hope it works for you!

Cheers....

---

