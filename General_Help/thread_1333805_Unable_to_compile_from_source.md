---
title: "Unable to compile from source"
date: 2009-11-21
forum: General Help
---

### Post by Lockheed on 2009-11-21
I have pcmanfm source which I need to compile with changes made by myself.
However, I am unable to to so because when I run ./configure, I get
```
Checking HAL... no
To use HAL support, you must have developing packages of dbus-glib-1 (>=0.31), or you can use --disable-hal to disable HAL support.])
    fi
```

I looked in synaptic for those packages and everything what is remotely similar to those, I have installed, yet I still cannot compile.
I will not use "./configure --disable-hal" because I'd lose partition automount which is crucial.

Is there any way around it?

---

### Post by renkinjutsu on 2009-11-21
```
sudo aptitude install libdbus-glib-1-2
```

installed this?

---

### Post by Lockheed on 2009-11-21
Yes.
```
No packages will be installed, upgraded, or removed.

```

---

### Post by renkinjutsu on 2009-11-21
hmm i remember having problems with mplayer not detecting my shared libraries.. and the solution was to change the prefix

try with ```
./configure --prefix=/usr
```

---

### Post by andrew.46 on 2009-11-22
Hi Lockheed,

> **Lockheed said:**
> Is there any way around it?

I suspect you are missing the relevant 'dev' files. On Karmic the file you are after can be seen with:

```
andrew@skamandros:~$ **[COLOR="Red"]apt-cache search dbus-glib-1 | grep dev[/COLOR]**
libdbus-glib-1-dev - simple interprocess messaging system (GLib interface)
```

If you repeat this search on your Jaunty system the name of the required file should be revealed.

All the best,

Andrew

---

### Post by Lockheed on 2009-11-22
> **renkinjutsu said:**
> hmm i remember having problems with mplayer not detecting my shared libraries.. and the solution was to change the prefix

try with ```
./configure --prefix=/usr
```

Unfortunately
```
checking for HAL... no
configure: error: To use HAL support, you must have developing packages of dbus-glib-1 (>=0.31), hal(>=0.5.0), and hal-storage, or you can use --disable-hal to disable HAL support.

```

---

### Post by Lockheed on 2009-11-22
> **andrew.46 said:**
> 
If you repeat this search on your Jaunty system the name of the required file should be revealed.

I got exactly the same file:
**libdbus-glib-1-dev**
and it was already installed.

---

### Post by andrew.46 on 2009-11-22
Hi Lockheed,

I see that *pcmanfm* is actually in the Ubuntu repositories so there might be a better way to assemble all of the dependencies and also make a change in the package. I am trying this out on Karmic so some filenames will be different, but below is the usual method to make a few small changes in an Ubuntu package and then reconstitute the package and install.

First create a build directory:

```

$ cd $HOME/Desktop
$ mkdir build
$ cd build

```

Then install the build tools:

```

$ sudo apt-get install build-essential fakeroot dpkg-dev

```

Then add the dependencies for pcmanfm:

```

$ sudo apt-get build-dep pcmanfm

```

Next grab the source and unpack it, **[COLOR="Red"]remember if you are using Jaunty the filename will be different[/COLOR]**:

```

$ apt-get source pcmanfm
$ dpkg-source -x pcmanfm_0.5.1+svn20090607-1.dsc

```

Now you need to burrow into the source code or the debian rules and make whatever changes you had in mind, which you have not specified in your original post? Having done this rebuild the package, install it and clean the source, **[COLOR="Red"]remember if you are using Jaunty the filename will be different[/COLOR]**:

```

$ cd pcmanfm-0.5.1+svn20090607
$ fakeroot debian/rules binary
$ sudo dpkg -i ../pcmanfm_0.5.1+svn20090607-1_i386.deb
$ fakeroot debian/rules clean	

```

This generates 2 packages with one being labelled 'no-hal' which I suspect is not the one you are after? Anyway the filename will be different under Jaunty.

Hopefully this might serve your needs?

Andrew

---

### Post by renkinjutsu on 2009-11-22
i just remembered a handy feature apt-get has .. i've been using aptitude and forgot all about apt-get

```
apt-get build-dep pcmanfm
```

see if that doesn't do the trick.

---

### Post by Lockheed on 2009-11-22
**Andrew**, thank you. I am sure it will come quite handy in the future.
However, I fist tried the simpler suggestion of **renkinjutsu** and it did the trick!

Gotta love these forums.

---

