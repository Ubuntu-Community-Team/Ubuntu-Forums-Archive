---
title: "Oh Nvidia driver problem"
date: 2005-02-18
forum: General Help
---

### Post by Svip on 2005-02-18
I might been too bored to take a look to find it. But I have been searching all day, so I thought I might aswell ask.

So I changed to Ubuntu this morning, and I wanted to install my Nvidia driver, because if I don't, get some stupid lines all over the screen, and I want my driver to work perfectly.

So I downloaded it off nvidia.com, and I learned from Red Hat, I had to go off the X server, by pressing ALT + CTRL + F1.

However, in RedHat, runlevel 3 was without the X server, but I had to go down to runlevel 1 on Ubuntu.

I then started the .run file the driver came with, it complained about runlevel 1, but I kept on anyway. And then the problems started. First it complained about the gcc package, I found it off the disc. Then the kernel-source, I found it off some HowTo.

Now I am stuck though, cause it wants me to config the kernel-source to fit the kernel I am using ( if I got it all right, I am not completely into Linux as of yet ). I tried configouring the kernel with 'make xconfig' in the /usr/src/linux folder, but luck didn't turn my way.

It then complained about some QT Development, which I can't find.

... anyone know how to install the Graphic drivers correctly? Hmm?

---

### Post by sunscape on 2005-02-18
Umm, what is wrong with the drivers in the repositories? 

sudo apt-get install nvidia-glx

---

### Post by Svip on 2005-02-18
[QUOTE=sunscape]Umm, what is wrong with the drivers in the repositories? 

sudo apt-get install nvidia-glx[/QUOTE]
Is it now I shall stab myself? I guess so.

:|

---

### Post by carney1979 on 2005-02-19
To kill X, from a console (reached via the ctrl-alt-f1 key combination) issue a:

sudo /etc/init.d/gdm stop

(you will have to supply your password)

then type:

uname -r

...to get the kernel version that is running (that you want to build the nvidia driver against)

then type:

sudo apt-get install kernel-source

If you haven't updated your system lately (or ever), then make sure the universe and multiverse repositories are uncommented in your /etc/apt/sources.list and type:

sudo apt-get update

...when that finishes, type:

sudo apt-get upgrade

When that is done and your system is up to date, then type:

sudo apt-get install kernel-source

Nothing will be installed but apt will instead list several possible choices for your kernel source. 

Pick one and type:

sudo apt-get  install kernel-source<version number>

Then you should be able to install your NVIDIA run package. 

I'm not sure what gcc errors you're seeing or how to fix them.

After you have built and installed your nvidia driver, then the installer will tell you to read a file about further installation instructions.

The part about configuring your X config file is near the bottom.

You will also need to add "nvidia" (without the quotes) to your /etc/modules file.

Also, type:

sudo modprobe nvidia

This will load the kernel module (not the driver you just built and installed).

If your system can't find the nvidia module, then you will need to install the restricted modules for your kernel version/type.

When you are finished, you will need to type:

sudo /etc/init.d/gdm start

If it does not start, then you may need to reboot.

If X fails to staret with an error, you may need to change your X config file back and try to restart it again. Then you can try to figure out what went wrong, search online for answers, etc.

Ubuntu's wiki has lots of good info on this topic, too.

Best of luck!

David

---

