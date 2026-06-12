---
title: "How to install GTK Aurora?"
date: 2009-11-16
forum: General Help
---

### Post by Cam! on 2009-11-16
I feel incredibly dumb, but can someone please use the installation instructions from the following GTK Download page, and put it in easier terms? I want my Elementary theme to work.

[http://www.gnome-look.org/content/show.php/Aurora+Gtk+Engine?content=56438&PHPSESSID=4663cbc498450b3ce00073dd746a8391]("http://http//www.gnome-look.org/content/show.php/Aurora+Gtk+Engine?content=56438&PHPSESSID=4663cbc498450b3ce00073dd746a8391")

---

### Post by Cam! on 2009-11-17
Well, what do I do?

---

### Post by nerdy_kid on 2009-11-17
ok, it says

1. install gtk development package (i cant find this, ask around)
2. download file.
3. extract file somewhere (say ~/Desktop)
4. extract the theme engine to ~/Desktop
5.  open terminal.
6 . type this:
```

cd ~/Desktop/aurora-gtk-engine-1.5/
./configure --prefix=/usr/ -enable-animation
make

```

now, assuming there are no errors,

```

sudo make install

```


hope that helps.

---

### Post by Cam! on 2009-11-17
There's an error. =/

---

### Post by nerdy_kid on 2009-11-18
there usally is :D

that probaly means that you dont have the right devolopment packages installed.  Id google for a prebuilt package.


P.S. it is usally more helpful to post the error :)

---

### Post by Giblet5 on 2009-11-18
+1 on posting the error.

When building from source, the configure script will complain about missing dependencies. Example:

```
...
checking for gawk... (cached) gawk
checking for curl-config... no
checking whether libcurl is usable... no
configure: error:
================================================================================
ERROR: could not find (recent enough) development-libs for libcurl.

  This library is required to build the boinc-client.
  (If you don't want to build the client, use --disable-client with configure.

  If libcurl-dev is installed on your system, make sure that the script
  'curl-config' is found in your PATH, and that
  'curl-config --version' gives something recent enough (see above).

  You can download libcurl from: http://curl.haxx.se/

================================================================================
```

This is one of the more verbose errors and it explains what to do. That's not the typical case.

Let's try to install libcurl-dev:

```
sudo apt-get install libcurl-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libcurl-dev is a virtual package provided by:
  libcurl4-openssl-dev 7.19.5-1ubuntu2
  libcurl4-gnutls-dev 7.19.5-1ubuntu2
You should explicitly select one to install.
E: Package libcurl-dev has no installation candidate
```

OK, apt wants us to be more specific...

```
sudo apt-get install libcurl4-openssl-dev
```

And let's run configure again... Yay! That fixed that one problem.......

You see how this goes, right? You fix the next problem, and the next, until there are no problems. Then you run make.


Install enough source packages and you'll eventually have every -dev kit available. ;)

---

### Post by Cam! on 2009-11-19
Thanks. I tried googling for extra Repositories, and the dev kit, but I couldn't find it. How lame. =[

---

### Post by Cam! on 2009-11-21
> **nerdy_kid said:**
> ok, it says

1. install gtk development package (i cant find this, ask around)
2. download file.
3. extract file somewhere (say ~/Desktop)
4. extract the theme engine to ~/Desktop
5.  open terminal.
6 . type this:
```

cd ~/Desktop/aurora-gtk-engine-1.5/
./configure --prefix=/usr/ -enable-animation
make

```now, assuming there are no errors,

```

sudo make install

```
hope that helps.

I extract them to the desktop, and copy/paste the command(s) into Terminal. Nothing happens. I get a "No Targets Specified and No Makefile found" error.

---

### Post by Uncle Spellbinder on 2009-11-21
There's a PPA repo you can add to your *sources.list*: [https://launchpad.net/~merlwiz79/+archive/aurora](https://launchpad.net/~merlwiz79/+archive/aurora)

I have it in my repos as such:
```
#### Aurora Gtk2 Engine 
## sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0AAFAD78
deb http://ppa.launchpad.net/merlwiz79/aurora/ubuntu karmic main
```

---

### Post by Cam! on 2009-11-21
WOW! Thanks a lot. That surely took all the time out of trying to get the Terminal commands to work.:p

---

### Post by Uncle Spellbinder on 2009-11-21
> **Cam! said:**
> WOW! Thanks a lot. That surely took all the time out of trying to get the Terminal commands to work.:p

You're welcome. ;)

---

