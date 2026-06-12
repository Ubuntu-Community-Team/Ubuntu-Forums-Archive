---
title: "gdevils pie daemon error"
date: 2010-09-02
forum: General Help
---

### Post by cadcam on 2010-09-02
gdevils pie daemon won't start.  in lucid, i open from term and get the following errors

pyramid@Pyramid:~$ gdevilspie

** (gdevilspie:2108): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gdevilspie:2108): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gdevilspie:2108): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFl




gdevilspie opens fine, and I can select and save rules, but it won't start.  

please help.

thanks,
A


[IMG]http://www.linuxcnc.org/images/fbfiles/images/Screenshot.jpg[/IMG]

---

### Post by LouisBlank on 2010-09-11
I have the same problem. 

This is strange because it works fine on my other machine. The difference being: 
Works on machine with Lucid 64bit installed. 
Doesn't work on machine with  Lucid 32bit installed.

I get the same pop up error as camcad posted.

Any ideas?

Thanks

> 
running install
running build
running build_py
creating build
creating build/lib.linux-i686-2.6
creating build/lib.linux-i686-2.6/gDevilspie
copying gDevilspie/__init__.py -> build/lib.linux-i686-2.6/gDevilspie
copying gDevilspie/filler.py -> build/lib.linux-i686-2.6/gDevilspie
copying gDevilspie/sparser.py -> build/lib.linux-i686-2.6/gDevilspie
copying gDevilspie/reader.py -> build/lib.linux-i686-2.6/gDevilspie
running build_scripts
creating build/scripts-2.6
copying and adjusting gdevilspie -> build/scripts-2.6
changing mode of build/scripts-2.6/gdevilspie from 644 to 755
running install_lib
copying build/lib.linux-i686-2.6/gDevilspie/__init__.py -> /usr/local/lib/python2.6/dist-packages/gDevilspie
error: could not delete '/usr/local/lib/python2.6/dist-packages/gDevilspie/__init__.py': Permission denied
extra@extra-desktop:~/Downloads/gdevilspie-0.31$ sudo python setup.py install
[sudo] password for extra: 
running install
running build
running build_py
running build_scripts
running install_lib
copying build/lib.linux-i686-2.6/gDevilspie/__init__.py -> /usr/local/lib/python2.6/dist-packages/gDevilspie
copying build/lib.linux-i686-2.6/gDevilspie/filler.py -> /usr/local/lib/python2.6/dist-packages/gDevilspie
copying build/lib.linux-i686-2.6/gDevilspie/sparser.py -> /usr/local/lib/python2.6/dist-packages/gDevilspie
running install_scripts
copying build/scripts-2.6/gdevilspie -> /usr/local/bin
changing mode of /usr/local/bin/gdevilspie to 755
running install_data
copying gdevilspie.png -> /usr/local/share/gdevilspie
copying README -> /usr/local/share/doc/gdevilspie
copying gdevilspie.desktop -> /usr/local/share/applications
copying gdevilspie.png -> /usr/local/share/pixmaps/
running install_egg_info
Writing /usr/local/lib/python2.6/dist-packages/gdevilspie-0.3.egg-info
extra@extra-desktop:~/Downloads/gdevilspie-0.31$ ./gdevilspie

** (gdevilspie:8984): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gdevilspie:8984): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gdevilspie:8984): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Terminated



---

### Post by Elfy on 2010-09-11
Have you actually got devilspie installed?

While I get the gtype error - gdevilspie works as does devilspie

---

### Post by LouisBlank on 2010-09-11
forestpiskie, 

The quote I posted shows the install routine which seemed to complet with no errors.  

Since the error mentions something about PATH, I put gDevilspie and all of its files in the /usr/bin directory. Still will not start the Daemon - Same pop up error as cadcam's image. 

Idea: the installation mentions i686 build.  Could it be that gDevilspie can not run on 32bit installation of Ubuntu Lucid?

---

### Post by Elfy on 2010-09-11
The quote is of the install for gdevilspie is it not?

It's only a frontend for devilspie - is that installed.

Yes it all works on 32bit lucid - that is what I am running it on.

What is the result of 
```
dpkg -l devilspie
```

---

### Post by LouisBlank on 2010-09-11
> **forestpiskie said:**
> The quote is of the install for gdevilspie is it not?

It's only a frontend for devilspie - is that installed.

Yes it all works on 32bit lucid - that is what I am running it on.

What is the result of 
```
dpkg -l devilspie
```


Here it is...

```

extra@extra-desktop:~/Downloads/gdevilspie-0.31$ dpkg -l devilspie
No packages found matching devilspie.
extra@extra-desktop:~/Downloads/gdevilspie-0.31$ 


```

---

### Post by Elfy on 2010-09-11
Install devilspie then and try with gdevilspie again.

```
sudo apt-get install devilspie
```

---

### Post by LouisBlank on 2010-09-11
Yeah, that did it.  Thanks a ton!! I didn't expect to get answers/resolution in less than an hour. 

The instructions from Google source hosting said "just extract it and run it.  No need for system wide installation."   I guess there is one step they forgot. 

Let's call this one solved!!!

:D

---

### Post by Elfy on 2010-09-11
> **LouisBlank said:**
> Yeah, that did it.  Thanks a ton!! I didn't expect to get answers/resolution in less than an hour. 

The instructions from Google source hosting said "just extract it and run it.  No need for system wide installation."   I guess there is one step they forgot. 

Let's call this one solved!!!

:D

Cool - glad you got there.

The instructions for gdevilspie are valid in my opinion - it is a frontend for something else, seems fairly obvious to me that you need the something else as well ;)

We'll wait for the OP to say it's solved though shall we :)

---

### Post by cadcam on 2010-09-12
Here here, that seems to make the daemon function (though I still the wierd wnck gflags errors)  

thanks man

---

