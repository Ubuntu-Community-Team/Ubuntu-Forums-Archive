---
title: "Install emacs 24 on ubuntu 12.04"
date: 2012-06-08
forum: General Help
---

### Post by mjsilverstri on 2012-06-08
Hi,

I am trying to install emacs 24 on ubuntu 12.04.
I am trying this after I did google:
```
sudo add-apt-repository ppa:cassou/emacs sudo apt-get update sudo apt-get install emacs-snapshot emacs-snapshot

```

but I can't install due to unmet dependencies. 
Can you please tell em how can I fix it?

```
$ sudo apt-get install emacs-snapshot
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 emacs-snapshot : Depends: emacs-snapshot-bin-common (= 2:20120524-1~ppa1~precise1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by grappler on 2012-06-09
I had a similar problem and  finally installed from the tar.gz package

As usual, download emacs-24.1-rc.tar.gz	 from here

[http://alpha.gnu.org/gnu/emacs/pretest/](http://alpha.gnu.org/gnu/emacs/pretest/)

In a terminal window cd into the directory where this is downloaded

```
> sudo apt-get install xorg-dev
```

```
> sudo apt-get install libjpeg-dev libpng-dev libgif-dev libtiff-dev
```

It will offer some variants - just say yes.

```
> sudo apt-get install libncurses-dev
```

```
> tar xvfz emacs-24.1-rc.tar.gz
```

```
> cd emacs-24.1
```

```
> ./configure
```

```
> make
```

```
>sudo make install 
```

Of course this method will not offer updates!

---

