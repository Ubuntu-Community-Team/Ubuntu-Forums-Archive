---
title: "Compiling Frustration"
date: 2010-09-21
forum: General Help
---

### Post by LiteDrive on 2010-09-21
So, for a long time I've been wanting to learn how to compile from source. I also need to install Photoshop. What do I need to do that? Wine. What a better way to learn how to compile? Why, compile Wine of course. 

Now, the fact that I don't know how to compile should pretty much state the obvious: I'm fairly new to Linux, so for anyone who'd be willing to give me a hand here, please bare with me. 

So, I'm going to cut to the chase:

> Building Wine on Ubuntu / Kubuntu 10.04 (Lucid Lynx)

Most of the Lucid ia32-libs come with .so links, except for libGL.so, which additionally is located in a "non-standard" directory where the 'configure' script does not look for.

To compile the 32-bit wine on a 64-bit Lucid, you need to do a

```
sudo apt-get build-dep wine
```

followed by a

```
mkdir -p ./lib32
ln -s /usr/lib32/mesa/libGL.so.1 ./lib32/libGL.so
```

Attention: Lucid also has another libGL.so that comes with the proprietary nvidia driver package (if you have an nvidia card). This is located under /usr/lib32/nvidia-current/. You may want to use this library instead if you feel less confident about the mesa driver that comes with the ia32-libs.

Then, run configure, build and install with:

```
CC="ccache gcc" LDFLAGS="-L./lib32" ./configure -v
make
sudo make install
```

There is no need to specify the -m32 or an explicit gcc version in Lucid. 

Basically, I followed this tutorial with **** all of a result. Then, I soon after read that "./configure" doesn't really represent "./configure." So, just so I have this correct: the "./" is meant to represent the actual directory, so instead I would type the entire directory rather than the "./" and "configure" represents the name of the file, right?

This is the other thing, I was searching my /var/cache/apt/archives/ folder, only to find nothing at all in relation to the build-dep file I supposedly nabbed. 

Here's the output I was given: 

```
-desktop:~/lib32$ cd ~
-desktop:~$ sudo apt-get build-dep wine
[sudo] password for theopusvision: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Picking 'wine1.2' as source package instead of 'wine'
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
-desktop:~$ mkdir -p ./lib32
-desktop:~$ ln -s /usr/lib32/mesa/libGl.so.1 ./lib32/libGL.so
-desktop:~$ CC="ccache gcc" LDFLAGS="-L./lib32" ./lib32 -v
bash: ./lib32: is a directory
```

Any advice or insight is appreciated. Thanks.

---

### Post by dirghrabadia on 2010-09-21
If getting Wine up and running is what you want, try this in the terminal:
> sudo apt-get install wine [FONT=monospace] [/FONT]

---

### Post by LiteDrive on 2010-09-21
> **dirghrabadia said:**
> If getting Wine up and running is what you want, try this in the terminal:

That's the thing, though: I want to learn to how to compile Wine, instead of just getting the .deb package for it. 

I've tried to compile different apps many times, and somehow I always run into some issue which I don't have enough know-how to figure out :/

---

### Post by realzippy on 2010-09-21
> **LiteDrive said:**
> So, for a long time I've been wanting to learn how to compile from source. I also need to install Photoshop. What do I need to do that? Wine. What a better way to learn how to compile? Why, compile Wine of course. 

Now, the fact that I don't know how to compile should pretty much state the obvious: I'm fairly new to Linux, so for anyone who'd be willing to give me a hand here, please bare with me. 

So, I'm going to cut to the chase:

 

Basically, I followed this tutorial with **** all of a result. Then, I soon after read that "./configure" doesn't really represent "./configure." So, just so I have this correct: the "./" is meant to represent the actual directory, so instead I would type the entire directory rather than the "./" and "configure" represents the name of the file, right?

This is the other thing, I was searching my /var/cache/apt/archives/ folder, only to find nothing at all in relation to the build-dep file I supposedly nabbed. 

Here's the output I was given: 

```
-desktop:~/lib32$ cd ~
-desktop:~$ sudo apt-get build-dep wine
[sudo] password for theopusvision: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Picking 'wine1.2' as source package instead of 'wine'
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
-desktop:~$ mkdir -p ./lib32
-desktop:~$ ln -s /usr/lib32/mesa/libGl.so.1 ./lib32/libGL.so
-desktop:~$ CC="ccache gcc" LDFLAGS="-L./lib32" ./[COLOR="Red"]lib32 [/COLOR]-v
bash: [COLOR="SeaGreen"]./lib32: is a directory[/COLOR]
```

Any advice or insight is appreciated. Thanks.

lib32 is a directory...so no **-v** option ;-)

CC="ccache gcc" LDFLAGS="-L./lib32" ./[COLOR="Red"]lib32 [/COLOR]-v
should be:
CC="ccache gcc" LDFLAGS="-L./lib32" ./[COLOR="SeaGreen"]configure [/COLOR]-v
followed by:
make
sudo make install

---

### Post by gordintoronto on 2010-09-21
Wine is too big to be appropriate for learning how to compile an app. Start with something small and simple!

Did you install "build-essential"?

---

### Post by realzippy on 2010-09-22
> **gordintoronto said:**
> Wine is too big to be appropriate for learning how to compile an app. Start with something small and simple!

Did you install "build-essential"?

Wine is compiled easily...OP has the guide and has to copy & paste 5
commands  ???

---

