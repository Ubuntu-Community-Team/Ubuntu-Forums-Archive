---
title: "How can i make this command run every start ?"
date: 2011-09-20
forum: General Help
---

### Post by Nuvielle on 2011-09-20
Hello =)

I know my Question will be easy for some People with more experience but i can't solve it myself ._.

The Main Problem i solved myself. After some hours i got rid of the the error that aticonfig can't find libGL.so ( had that error after the fresh installation of my system ) and i got the xvba driver to work. But here is my Problem

The Accleration from the Driver works fine, but not immediately after the the start. 

When i run vainfo i get this Message

```

libva: libva version 0.31.1
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/dri/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA API version: 0.31
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.8
vainfo: Supported profile and entrypoints
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD

```

after i run

export LIBVA_DRIVER_NAME=fglrx

vainfo shows

```

libva: libva version 0.31.1
libva: User requested driver 'fglrx'
libva: Trying to open /usr/lib/dri/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA API version: 0.31
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.8
vainfo: Supported profile and entrypoints
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD

```


and all is working fine. 

My Question is, is there a way  that my OS is doing this command from itself ? It would be realy anoying to type this command in everytime i start my pc ._.

I have no clue about writing sh scripts or so ._.

°Hopes that someone can help me° =)

Thanks for any Tip and any Suggestion =)

---

### Post by ddr3XD on 2011-09-20
Launch "Startup Applications"
Click Add
In Name type whatever name u want("ATI Driver Fix" would be good i guess)
In the Command box put in the code you used above:
```
export LIBVA_DRIVER_NAME=fglrx
```Then click Add
Make sure the checkbox next to the startup item is checked.
It should run the code at every boot now.

---

### Post by Nuvielle on 2011-09-20
Thanks for your fast Answer =)

I've tried your suggestion but it didn't worked. After a reboot i got the same answer from vainfo again :(

---

### Post by dave01945 on 2011-09-20
you could try adding the line into rc.local using a text editor

```
gksu gedit/etc/rc.local
```

if that doesn't work try adding it into your profile or bashrc then it will be run after you login

```
gksu gedit /home/user/.profile
or
gksu gedit /home/user/.bashrc
```

just replace **user** with your username also you don't have to use gedit you can use another text editor if you prefer

---

### Post by Nuvielle on 2011-09-20
Many Thanks dave01945 &  ddr3XD :D  ):P

The Tip with /home/user/.profile worked fine =)

---

### Post by David Andersson on 2011-09-20
> **Nuvielle said:**
> 
I've tried your suggestion but it didn't worked. After a reboot i got the same answer from vainfo again :(

An "export" statement only affects the current process and its offspring. Unfortunately, the process started by "Startup Applications" quickly ends and has no offsprings. You probably need to place the export statement in a process that starts the rest of your graphical desktop environment. There is no ~/.xinitrc file by default in Ubuntu, but maybe you can try creating such a text file and place the export statement in it.

(I don't know about this driver thing, but have you checked if it can be solved with a xorg or kernel setting?)

---

### Post by dave01945 on 2011-09-20
> **Nuvielle said:**
> Many Thanks dave01945 &  ddr3XD :D  ):P

The Tip with /home/user/.profile worked fine =)

thats ok glad to help 

you should mark this thread as solved so other user's that find it know it worked

---

### Post by Nuvielle on 2011-09-20
> **dave01945 said:**
> thats ok glad to help 

you should mark this thread as solved so other user's that find it know it worked

ok, i've marked it =)

---

### Post by Nuvielle on 2011-09-20
> **David Andersson said:**
> An "export" statement only affects the current process and its offspring. Unfortunately, the process started by "Startup Applications" quickly ends and has no offsprings. You probably need to place the export statement in a process that starts the rest of your graphical desktop environment. There is no ~/.xinitrc file by default in Ubuntu, but maybe you can try creating such a text file and place the export statement in it.

(I don't know about this driver thing, but have you checked if it can be solved with a xorg or kernel setting?)

I don't think that i could do something like this with an xorg or kernel Setting, i don't know.

First i've stumbled upon this Blog from Sebastian Siebert, someone from Opensuse ([http://www.sebastian-siebert.de/2011/09/11/opensuse-hardware-videobeschleunigung-via-xvba-vom-amd-catalyst-nutzen/](http://www.sebastian-siebert.de/2011/09/11/opensuse-hardware-videobeschleunigung-via-xvba-vom-amd-catalyst-nutzen/) i know you don't understand it cause it's german ) but overall he says if you want gpu acclerated  viewing or transcoding ( for example in vlc ) your need the XvBA driver thing from AMD. It seems he is someone near AMD and he made a file to install it in opensuse.

Over this Blog i stumbled upon this ppa Site 

[https://launchpad.net/ubuntu/+source/xvba-video](https://launchpad.net/ubuntu/+source/xvba-video)

downloaded it and installed it ( had to use the closed binary drivers from ubuntu, when i use the Binary from ATI's Hp i get an error that the driver isn't installed ^^ ) which lead me in the error that everytime when i ran aticonfig --initial --adapter=all he showed me that he could not find a library with this Message


```

Found fglrx primary device section
Fail to link to fglrx-libglx.so, please check whether driver is installed correctly
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.fglrx-2

```

(everytime i installed the driver from apt-get i got this, even after i reinstalled the os ._. )

But finaly this Link bellow solved it for me =)

[https://lists.launchpad.net/hybrid-graphics-linux/msg00907.html](https://lists.launchpad.net/hybrid-graphics-linux/msg00907.html)

---

