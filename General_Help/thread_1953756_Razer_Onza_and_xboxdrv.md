---
title: "Razer Onza and xboxdrv"
date: 2012-04-06
forum: General Help
---

### Post by Geezanansa on 2012-04-06
Trying to compile xboxdrv but after following readme when run "scons" i get 
```
scons: *** No SConstruct file found.
File "/usr/lib/scons/SCons/Script/Main.py", line 834, in _main
```I am running 11.10 and instructions for 10.04 are closest i can find.  Installed g++ \ libboost1.42-dev \ scons \ pkg-config \ libusb-1.0-0-dev \ git-core \ libx11-dev \libudev-dev \ x11proto-core-dev \ libdbus-glib-1-dev

Thanks in advance

---

### Post by Geezanansa on 2012-04-07
Okay before running scons i have to navigate to xboxdrv directory.

I installed xboxdrv by ppa 

```
sudo xboxdrv --version
``` gives ```
xboxdrv 0.8.4 - [http://pingus.seul.org/~grumbel/xboxdrv/]("http://pingus.seul.org/%7Egrumbel/xboxdrv/")

```
How do i find the location of xboxdrv directory?:lolflag:
The readme is in  /usr/share/doc/xboxdrv/README and i can ```
man xboxdrv

``` but cannot find xboxdrv directory.   Where is xboxdrv directory?:lolflag:
:popcorn:

Ignorance used to be bliss...

---

### Post by Grumbel on 2012-04-08
I don't quite get what you are trying to do. If you installed it already via PPA, then you are done. There is no xboxdrv directory and no need to run scons, that's only for compling from source.

---

### Post by raja.genupula on 2012-04-08
> but cannot find xboxdrv directory. Where is xboxdrv directory?

if you wanna know where its installed then use which for example

```
raja@debian:~$ which pidgin
/usr/bin/pidgin
```

---

### Post by Geezanansa on 2012-04-10
As a new user not fully grasping the concept of diiferent methods of doing the same job have to admit i obviously don not have a scooby!:lolflag: Even if iread all the readme it would tell me i do not need to install .... if using source or debian package.
 
Software centre had taken care of the drivers(can not remember searching for xboxdrv possibly loaded when i connected controller?)
Sorry for late reply but i was trying to get controller working to play games and that just aint happening with ubuntu(tried wine, pol and steam with the games i want to play)
So i been busy trying to set up triboot system.....windows xp was a reminder how nice it is when things just work. Ubuuntu is great for learning how things work:lolflag:
which makes everymachine an awesome piece of engineering in my now wide open eyes.
 
Thanks for feedback peeps I am sure i will be trying to get controller working in ubuntu some time in near future
 
My original question has been answered so will mark as solved!:lolflag:

---

