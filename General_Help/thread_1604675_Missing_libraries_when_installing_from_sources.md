---
title: "Missing libraries when installing from sources"
date: 2010-10-24
forum: General Help
---

### Post by birkopf on 2010-10-24
Dear Froum readers,

I decided to post it after researching web and not finding sensible answer. Installing from sources was always complicated to me, but biggest problem is installing when some strange dependencies are "missing". 

Let's do it on example - I am sure it will benefit lots of users. 

I have a unmodified ubuntu 9.10 (Karmic) on 64 bir architecture. I download latest Grisbi sources from official web page. After 
```
./config
``` I have an error:
```

checking where the gettext function comes from... libc
checking for main in -lintl... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GTK... configure: error: Package requirements (gtk+-2.0 >= 2.2.0 glib-2.0 >= 2.2 gmodule-2.0 >= 2.2) were not met:

No package 'gtk+-2.0' found
No package 'glib-2.0' found
No package 'gmodule-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK_CFLAGS
and GTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```  

When I am trying to install "gtk" or "glib" via "apt-get install" I get message it's already to newest version. When I try via Synaptics there are some files but it never solves the problem. 

I didn't modify any paths to system variables...
and it's usually problem with glib or gtk with all other sources I try to install. 

1) Could someone help me in this particular case with missing dependencies please?

2) What every User should do when trying to install from source and some libraries are missing? 
How to find them? How to install them ?

---

### Post by Queue29 on 2010-10-24
You need the "-dev" versions of the libraries, which contain the source code needed to compile against. 

So you should be able to do something along the lines of 

apt-get install libgtk2.0-dev libglib2.0-dev

should do the trick, but I'm not 100% sure on the package names for 9.10.

---

### Post by yetiman64 on 2010-10-24
Check this community documentation link for [B][COLOR=Blue][--compiling software]("https://help.ubuntu.com/community/CompilingSoftware")[/COLOR]--.
[/B] 
It includes the use of the command,
> sudo apt-get build-dep <package>This part of the procedure may be what you are needing.

---

### Post by mc4man on 2010-10-24
Sometimes in the source will be a readme or install textfile that wil provide some info - in this case sparse but there

> Requirements:

 - GTK 2.2, 2.10 is needed to be able to print
 - libofx (optional)

When you see missing libs in a configure don't take the name literally - search synaptic using a truncated name and in most cases stick a lib in front. Look for the -dev packages in most cases.

So for gtk+-2.0' search libgtk and you'll see what's been mentioned 
libgtk2.0-dev

If you wish libofx support, search and install the -dev

If you have the proper -dev package(s), but still get the message(s) then that usually indicates your version of that lib is too old or occasionally  too new for the source.
(the other possibility is the path to the includes or .pc file is not what the source expects - checking the config.log if it exists can provide clues

---

### Post by birkopf on 2010-10-24
Thank you guys. You are great!

For specific problem with Grisbi (and by the way - I recommend to everyone) 
mc4man answer helped immediately. 

Than - I was thinking about simple way of always finding missing dependencies. I google them but you need to admit - if you don't really know what you are looking for, and are using name like mentioned by installed - one thing that you can find... is a lot of rubbish. If the installer will give specific file name it will be easy ;-)

Well - now it helps. Thank you very much. 

I hope this will also help other users.

---

