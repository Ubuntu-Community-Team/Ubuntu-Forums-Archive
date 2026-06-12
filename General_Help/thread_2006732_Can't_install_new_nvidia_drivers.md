---
title: "Can't install new nvidia drivers"
date: 2012-06-19
forum: General Help
---

### Post by firekage on 2012-06-19
Hello.

I'm writing this cause i need again Your help.

I tried to install new nvidia drivers from x-swat ppa but i can't and i don't know why.

I added ppa to repository, i updated apt-get, i see that ppa was added correctly and when i try to install new drivers i have info that nvidia-current is in latest version.

It is not. I have installed drivers 180.13 for my GTX260 on Ubuntu 11.10 while new are 295 or even 300.

Can You help me? I'm at loss. I don't know what is going on or how to fix it because i don't understand it. Even in Synaptic i see that i have installed 180.13 drivers and newer are...yes, 180.13!

Can You help me?

---

### Post by firekage on 2012-06-19
I really don't understand ubuntu, nvidia and installing drivers. I added ppa, updated apt-get, installed nvidia-current and in terminal i saw that 302.xx drivers were being installed, also something was build for my kernel. I rebooted after nistallation and in nvidia settings i see still 280.13 drivers!

I'm retarded or ubuntu. I just don't get it. But there is something new...in synaptic i see now that there is 280.13 and 302.xx drivers! I installed it trough terminal but still in synaptic and nvidia-settings i see old one. What is going on?

Is there some magic voodoo way of installing it from ppa or binary driver?

Please, help me, i'm confused.

---

### Post by HiImTye on 2012-06-19
you're using the '-updates' drivers. use the ones without '-updates' in their package name (namely: 'nvidia-current')

---

### Post by firekage on 2012-06-19
So, can You write me what to do? I'm not experienced with installing drivers on Ubuntu.

I should purge everything like:

```

sudo apt-get --purge remove nvidia

```
??

---

### Post by HiImTye on 2012-06-19
just install the correct versions of the drivers, it will automagically remove the other versions
```
sudo apt-get install nvidia-current nvidia-settings
```

---

### Post by firekage on 2012-06-20
> **HiImTye said:**
> just install the correct versions of the drivers, it will automagically remove the other versions
```
sudo apt-get install nvidia-current nvidia-settings
```

I tried to install only nvidia-current but after it:

-i could not enter X, freezed over purple login screen;
-if i killed X and startx command entered in terminal i had gui but there was no cairo, not everything worked;
-if i entered X, and have GUI not everything from desktop was load, also i didn't have sound;

So, i should install two things, right? One - nvidia-current; second: nvidia-settings

??

---

### Post by firekage on 2012-06-20
I just don't get it. I purged nvidia

```
sudo apt-get --purge remove nvidia-*
```

I added ppa from here:

[http://www.noobslab.com/2011/09/nvidia-drivers-for-ubuntu-1110-oneiric.html](http://www.noobslab.com/2011/09/nvidia-drivers-for-ubuntu-1110-oneiric.html)

PPA was added, i updated apt-get, then i entered:

```
sudo apt-get install nvidia-current nvidia-settings
```

and here again i have info in terminal that they are in newest version...280.13, also synaptic show the same thing.

I just don't get it. Why it is so hard to install nvidia on Ubuntu when commands are so simple?

---

### Post by firekage on 2012-06-20
Can somebody help me?

I installed 302 drivers but after it ubuntu doesen't work like it should be. Lightdm often doesen't work, i can't enter desktop (GUI), and even if i enter than running smplayer causes X to kill itself/crash. Often i can;t login cause it stops on login screen - i enter password, than picture flips few times and i'm still at login screen.

On default nvidia drivers from Ubuntu DVD everything works - can somebody explain this to me and help me? I have nvidia GTX0260 and 302 drivers supports this graphic card.

---

### Post by firekage on 2012-06-21
In desperation i tried to install new BINARY driver from nVidia site. Works like a charm despite that now, i don't know why, i have bug in jockey because it shows that i do not use driver:

```
sudo jockey-text -l
```

here is the output:

```
priopetary, switched off, not used
```when in fact i have installed 295 drivers because nvidia settings shows it, also lshw -C display says the same and:

```
/usr/lib/nux/unity_support_test -p 
```shows:
```
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GTX 260/PCIe/SSE2/3DNOW!
OpenGL version string:  3.3.0 NVIDIA 295.59

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
firekage@deusex:~$ 

```I know that there is bug in jockey but it worked before installing and reinstalling drivers from ppa. Don't know why it happened and don't know how to fix it - i now that this bug is present in 11.04, but apparently in 11.10 when doing something with drivers it cames up.

---

### Post by kc1di on 2012-06-21
First of all it would help if we knew whcich nvidia card your trying to install drivers for. Please list the output of 

```
lspci
```
opps sorry fond it ,

---

### Post by firekage on 2012-06-21
I have to rewrite what i wrote earlier. I though that everything worked. As a matter of fact as soon as i touched mplayer (not even played file, just run smplayer by clicking on it) i have log off from destkop to login prompt (purple wallpaper with user and login).

I give up. I don;t understand the way of installing nvidia driver from website or ppa. It looks like vdpau doesen't work but commands above showed that 3d works!

I could play movies/files trough terminal smplayer but it doesen't work when i clicked on smplayer. Also i tried to run Unity 2d but as soon as i clicked for anything i saw logging off.


I use nvidia-current from command:

```
sudo apt-get install nvidia-current
```

The funniest thing is that with this everything works - this is 280.13 drivers, but when i installed it from nvidia settings as a binary driver there were problems mentioned above.

---

