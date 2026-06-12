---
title: "How to install Aegisub?"
date: 2012-10-07
forum: General Help
---

### Post by Stonecold1995 on 2012-10-07
I'm trying to install Aegisub, a program used to easily add subtitles to a video, but I've been having trouble getting it to install.  I tried adding the PPA (ppa:zveroy/aegisub), but even though the PPA was added successfully I still couldn't get apt-get to install Aegisub.  I also tried compiling it from source, using the instructions [here]("http://forum.aegisub.org/viewtopic.php?t=4686"), but it still wouldn't install.

```
checking for wx-config... no
configure: error: in `/tmp/aegisub-3.0.0/aegisub':
configure: error: wxWidgets detection failed, please set --with-wx* or add the libraries to your LIBS, CXX/CFLAGS.
See `config.log' for more details
```

I tried installing the missing packages, but ran into another problem:

```
alex@kubuntu:/tmp/aegisub-3.0.0/aegisub$ sudo apt-get install libwxgtk2.8-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libwxgtk2.8-dev : Depends: libwxgtk2.8-0 (= 2.8.12.1-6ubuntu2) but 2.8.12.1-6ubuntu2.2 is to be installed
                   Depends: libwxbase2.8-dev (= 2.8.12.1-6ubuntu2) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

I keep running into problems...  How do I install Aegisub 3.0.0 in Kubuntu 12.04?  I don't want to have to run the Windows version through Wine.

---

### Post by Stonecold1995 on 2012-10-18
bump

---

### Post by Lisiano on 2012-10-18
You have a strange system. If possible, I'd recommend you upgrade to 12.10, Aegisub is in the archives starting it.

As for your packaging problems... Try to run the following
```
sudo apt-get -f install
sudo apt-get install libwxgtk2.8-dev
```

If you still have the PPA, you may also run this to get all the build dependencies in place
```
sudo apt-get build-dep aegisub
```

---

### Post by Stonecold1995 on 2012-10-20
> **Lisiano said:**
> You have a strange system.

Huh?

Anyways, I upgraded to Kubuntu 12.10 and it installed now, but only version 2.1.9 (installed through the repositories).  When I try to download the sorce code for 3.0.0 or 3.0.1 from the official site and compile it, I still get this error:

```
checking for wxWidgets version >= 2.9.3... no (version 2.8.12 is not new enough)
configure: error: 
    The requested wxWidgets build couldn't be found.
    

    If you still get this error, then check that 'wx-config' is
    in path, the directory where wxWidgets libraries are installed
    (returned by 'wx-config --libs' command) is in LD_LIBRARY_PATH
    or equivalent variable and wxWidgets version is 2.9.3 or above.

```

I have WxWidgets, but not a new enough version apparently.  I tried using apt-get to install it, but it says I'm already at the newest version. :confused:

```
alex@kubuntu:~$ wx-config --libs
-L/usr/lib/x86_64-linux-gnu -pthread   -L/usr/lib/x86_64-linux-gnu   -lwx_gtk2u_richtext-2.8 -lwx_gtk2u_aui-2.8 -lwx_gtk2u_xrc-2.8 -lwx_gtk2u_qa-2.8 -lwx_gtk2u_html-2.8 -lwx_gtk2u_adv-2.8 -lwx_gtk2u_core-2.8 -lwx_baseu_xml-2.8 -lwx_baseu_net-2.8 -lwx_baseu-2.8
```

---

### Post by Lisiano on 2012-10-20
I located a tutorial on how to compile Aegisub 3.0.1 on 12.10
[http://forum.aegisub.org/viewtopic.php?f=10&t=65482](http://forum.aegisub.org/viewtopic.php?f=10&t=65482)
It also tells you how to get a newer copy of wxWidgets

---

### Post by MrsUser on 2012-10-20
In the Aegisub forum, someone posted links to precompiled .deb packages for Aegisub 3.1 for Ubuntu 12.04  on his website:

[http://forum.aegisub.org/viewtopic.php?f=18&t=17203](http://forum.aegisub.org/viewtopic.php?f=18&t=17203)
[http://jikan.fr/aegisub/](http://jikan.fr/aegisub/)

The post and website are in French, but direct link to the download section is here:
[http://dl.jikan.fr/Applications/Ubuntu/12.04/](http://dl.jikan.fr/Applications/Ubuntu/12.04/)

You need to download the deb package from here:
[http://dl.jikan.fr/Applications/Debian/Wheezy/wxWidgets/2.9.4/](http://dl.jikan.fr/Applications/Debian/Wheezy/wxWidgets/2.9.4/)

and from here (in subfolder):
[http://dl.jikan.fr/Applications/Debian/Wheezy/Aegisub/3.1/](http://dl.jikan.fr/Applications/Debian/Wheezy/Aegisub/3.1/)

First install wxWidgets and then Aegisub. Works for me on Ubuntu 12.04.

Hint: If you open a video and miss the audio in Aegisub -- you have to explicitely load the audio from the audio menu ('Audio' > 'Open Audio from Video').

---

### Post by Stonecold1995 on 2012-10-21
It seemed to have installed successfully, but it won't run.

```
alex@kubuntu:/tmp/aegisub-3.0.1/aegisub$ aegisub-3.0
aegisub-3.0: error while loading shared libraries: libwx_gtk2u_gl-2.9.so.4: cannot open shared object file: No such file or directory
```

---

### Post by Lisiano on 2012-10-21
Okay, I have followed the tut I linked to you. I have managed to replicate issue, it is caused by us not correctly following the tutorial. At the end of installing wxWidgets, after checkinstall. It tells us to do this
```
sudo ldconfig
```After running that, the issue vanished and Aegisub 3.0.1 started up for me.

Stracing aegisub helped me notice it.

---

### Post by Stonecold1995 on 2012-10-23
Thank you!  It's working perfectly now.

---

