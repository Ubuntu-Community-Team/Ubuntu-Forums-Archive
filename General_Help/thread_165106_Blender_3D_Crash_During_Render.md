---
title: "Blender 3D Crash During Render"
date: 2006-04-24
forum: General Help
---

### Post by Nano Geek on 2006-04-24
Hi,

I have a problem with Blender. I am currently working on a model of a cannon, it is farily detailed, and when I try to render it Blender crashes.

This is what it says in the command line:

my_name@Ubuntu:~$ blender -w
Using Python version 2.4
Unable to load: libtiff.
Try setting the BF_TIFF_LIB environment variable if you want this support.
Example: setenv BF_TIFF_LIB /usr/lib/libtiff.so
Killed
my_name@Ubuntu:~$

I'm using:
Ubuntu 5.10
Blender 2.41
Nvidia GForce FX 5200 Ultra with proprietary driver
AMD Sempron 2500+ 
512 MB RAM

I would be grateful if anybody had a solution to the problem.

Thanks

---

### Post by bb002 on 2006-04-24
according to packages.ubuntu.com libtiff4.so is in the package libtiff4-dev.

so try installing/reinstalling libtiff4-dev

[edit]
I personally never heard of blender before.
looks like I've got a new toy. :)

---

### Post by Nano Geek on 2006-04-24
Thanks for the tip. I checked and libtiff4-dev was not installed, but my problem still persists. I think that I might have been misunderstood about the terminal message. After I typed **blender -w** then the message come up saing:

[B]Using Python version 2.4
Unable to load: libtiff.
Try setting the BF_TIFF_LIB environment variable if you want this support.
Example: setenv BF_TIFF_LIB /usr/lib/libtiff.so[/B]

After I started the render it sat there for awhile, and then the program quit and it said **killed** in the command line. Now after I installed libtiff4-dev it says:

**Using Python version 2.4**

And after I start it rendering, it crashes, and says **Segmentation fault**. I also forgot to mention that it crashed once when it was in edit mode after I had belved the model.

Thanks

P.S.
bb002,

If you want to try blender here are some websites that you will want:
[www.blender.org](www.blender.org) - Home Page
[http://mediawiki.blender.org/index.php/Manual/Manual](http://mediawiki.blender.org/index.php/Manual/Manual) - Blender Manual
[wiki.blender.org](wiki.blender.org) - Online documentation
[www.blendernation.com](www.blendernation.com) - Fresh Blender News, Every Day

I think blender is the best open-soruce 3D modeler there is, the newest version is 2.41.

---

### Post by bb002 on 2006-04-24
try starting blender with ```
blender -d
```
that is suppose to turn debugging on. Maybe that will spit out more info.

---

### Post by Nano Geek on 2006-04-24
This is what it said after I ran it as **blender -d**
```

my_name@Ubuntu:~$ blender -d
Blender V 2.41
argv[0] = blender
argv[1] = -d
Using Python version 2.4
Color depth r 8 g 8 b 8
Aux buffers: 0

ordered
 OBCube
 OBLamp
 OBCamera

Registering scripts in Blender menus ...

Getting menu data for scripts from file:
/home/cavu/.blender/Bpymenus

Color depth r 8 g 8 b 8
Aux buffers: 0
Color depth r 8 g 8 b 8
Aux buffers: 0
Color depth r 8 g 8 b 8
Aux buffers: 0
Color depth r 8 g 8 b 8
Aux buffers: 0

ordered
 OBPlane.003
 OBspoke.003
 OBspoke.002
 OBCylinder.001
 OBPlane.001
 OBPlane
 OBCylinder
 OBspoke.001
 OBspoke
 OBPlane.002
 OBLamp.001
 OBCannon
 OBLamp
 OBCamera
Killed
```

---

### Post by Irony on 2006-04-24
This is what I get. The first one is with  with the synaptic installed 2.37a  and the second one is with the unzipped 2.41 - both render with no problem when pressing F12;

[PHP]irony@ubuntu:~$ blender -d
Blender V 2.37
argv[0] = blender-bin
argv[1] = -d
Using Python version 2.4
Color depth r 8 g 8 b 8
Aux buffers: 0

Registering scripts in Blender menus ...

Getting menu data for scripts from file:
/home/irony/.blender/Bpymenus

Color depth r 8 g 8 b 8
Aux buffers: 0
Color depth r 8 g 8 b 8
Aux buffers: 0
Color depth r 8 g 8 b 8
Aux buffers: 0
Color depth r 8 g 8 b 8
Aux buffers: 0
branches 2456 nodes 48495
raycount 0
ray coherent 0
accepted 0 rejected 0
Color depth r 8 g 8 b 8
Aux buffers: 0
Color depth r 8 g 8 b 8
Aux buffers: 0
Saved session recovery to /tmp/quit.blend

Blender quit
irony@ubuntu:~$ /usr/share/blender-2.41-linux-glibc232-py24-i386/blender -d
Blender V 2.41
argv[0] = /usr/share/blender-2.41-linux-glibc232-py24-i386/blender
argv[1] = -d
Using Python version 2.4
Color depth r 8 g 8 b 8
Aux buffers: 0

ordered
 OBCamera.001
 OBCamera.003
 OBPlane
 OBLamp
 OBLamp.006
 OBLamp.003
 OBFloor
 OBEmpty
 OBCamera
 OBLamp.002
 OBFrame
 OBFrame.001
 OBCap.001
 OBSpacer.001
 OBHandle.001
 OBLockpin.001
 OBPinA.001
 OBPinB.001
 OBPinB
 OBPinA
 OBLockpin
 OBHandle
 OBSpacer
 OBCap
 OBLamp.001

Registering scripts in Blender menus ...

Getting menu data for scripts from file:
/home/irony/.blender/Bpymenus

Unable to load: libtiff.
Try setting the BF_TIFF_LIB environment variable if you want this support.
Example: setenv BF_TIFF_LIB /usr/lib/libtiff.so
Color depth r 8 g 8 b 8
Aux buffers: 0
Color depth r 8 g 8 b 8
Aux buffers: 0
Color depth r 8 g 8 b 8
Aux buffers: 0
Color depth r 8 g 8 b 8
Aux buffers: 0
branches 2456 nodes 48515
raycount 0
ray coherent 0
accepted 0 rejected 0
Color depth r 8 g 8 b 8
Aux buffers: 0
Color depth r 8 g 8 b 8
Aux buffers: 0
Saved session recovery to /tmp/quit.blend

Blender quit
irony@ubuntu:~$[/PHP]

I have libtiff4 installed.

---

### Post by Nano Geek on 2006-04-24
Here's one of the models that's making it crash.

---

### Post by bb002 on 2006-04-24
omg!! how much ram do you have? I've got 1gb and in 1/2 sec blender completely filled it up when i started to render. Blender also ate up 1GB of my 2GB swap space. maybe you are running out of space for blender to render?

I killed the task off since i wasn't ready for my system to goto a crawl. So it didn't render completely. I let it run for about a minute before i killed it. I'm going to reboot and try again. this time I'll let it run completely. I'll let you know what i discover later.

---

### Post by Nano Geek on 2006-04-24
> how much ram do you have?I have 512 MB of RAM, hoping to upgrade to 1 GB soon.

---

### Post by bb002 on 2006-04-24
Well...it finished a little while ago.

I tried taking a screenshot of just the rendering window but it kept failing, so I did the whole screen.

hopefully it isn't too big...271KB

[edit]
I killed compiz to turn off transparency. no the image looks better and is smaller :) only 192KB now.

---

### Post by bb002 on 2006-04-24
Oops. forgot to post my debug output: 

```
bb002@Sentinel:~$ blender -d
Blender V 2.41
argv[0] = blender-bin
argv[1] = -d
Using Python version 2.4
Color depth r 8 g 8 b 8
Aux buffers: 4

ordered
 OBCube
 OBLamp
 OBCamera

Registering scripts in Blender menus ...

Getting menu data for scripts from file:
/home/bb002/.blender/Bpymenus

Color depth r 8 g 8 b 8
Aux buffers: 4
Color depth r 8 g 8 b 8
Aux buffers: 4
Color depth r 8 g 8 b 8
Aux buffers: 4
Color depth r 8 g 8 b 8
Aux buffers: 4

ordered
 OBLamp.002
 OBLamp.001
 OBPlane
 OBCube
 OBLamp
 OBCamera
branches 5954 nodes 849227
raycount 0
ray coherent 0
accepted 0 rejected 0
Color depth r 8 g 8 b 8
Aux buffers: 4
Color depth r 8 g 8 b 8
Aux buffers: 4
Color depth r 8 g 8 b 8
Aux buffers: 4
Color depth r 8 g 8 b 8
Aux buffers: 4
Color depth r 8 g 8 b 8
Aux buffers: 4
Color depth r 8 g 8 b 8
Aux buffers: 4
Color depth r 8 g 8 b 8
Aux buffers: 4
Color depth r 8 g 8 b 8
Aux buffers: 4
Color depth r 8 g 8 b 8
Aux buffers: 4
GL error: invalid value
Color depth r 8 g 8 b 8
Aux buffers: 4
Color depth r 8 g 8 b 8
Aux buffers: 4
Color depth r 8 g 8 b 8
Aux buffers: 4
Color depth r 8 g 8 b 8
Aux buffers: 4
Color depth r 8 g 8 b 8
Aux buffers: 4
Color depth r 8 g 8 b 8
Aux buffers: 4
Color depth r 8 g 8 b 8
Aux buffers: 4
Color depth r 8 g 8 b 8
Aux buffers: 4
Color depth r 8 g 8 b 8
Aux buffers: 4
Color depth r 8 g 8 b 8
Aux buffers: 4
Color depth r 8 g 8 b 8
Aux buffers: 4
Color depth r 8 g 8 b 8
Aux buffers: 4
Color depth r 8 g 8 b 8
Aux buffers: 4
Color depth r 8 g 8 b 8
Aux buffers: 4


```

[edit]
I assume that "Aux buffers: 4" is actually the alpha layer comes from the fact that I run Xgl and compiz.

---

### Post by Nano Geek on 2006-04-24
Thanks bb002,

If you wouldn't mind telling me, I would like to know what computer hardware your using and about how long it took to render.

Thanks

---

### Post by bb002 on 2006-04-25
Asus nForce3 socket 754 MB (forgot the model)
AMD Athlon 3000+ (Venice core)
Corsair 2X512MB DDR3200 RAM (for 1GB).

The nForce chipset has an annoying limitation with ram. if you use only one stick your ram will operate at 400Mhz max but if you use two sticks like i do your ram will work at 333Mhz max. and if you use 3 sticks your ram operates at 266Mhz max. Very annoying, especially since my motherboard wasn't supposed to have that problem.


And wierd.blend rendered in 1 hour 35 minutes.

---

### Post by bb002 on 2006-04-25
I just noticed that this is in the breezy forums. Before anyone gives me funny looks I did a search for unanswered posts and I never look to see what forums which thread is from.

So **asjdfwejqrfjcvm msz34rq33** I'd like to let you know that I'm using Ubuntu Dapper Beta and that 2.41 is the version of blender in the repos.

PS: Thank you for copy & paste other wise I'd have called you Mr. Freddy. no way am i never gonna even attempt to type your name :)

---

### Post by Nano Geek on 2006-04-25
Thanks for your hardware specs, looks like I need to upgrade my computer. And sorry about the name, when I was registering every user name I put in had already been used, so I tried giberish and it worked;) .
Thanks for all the help

---

### Post by bb002 on 2006-04-25
what kind of specs do you have?

and your are welcome.

---

### Post by Nano Geek on 2006-04-25
My specs are as follows:
[LIST]
[*]AMD Sempron 2500+
[*]512 MB RAM
[*]Nvidia GForce Fx 5200 Ultra
[*]120 GB Hard Drive
[*]Ubuntu Linux 5.10
[/LIST]
Hope it helped.

---

### Post by Irony on 2006-04-25
You don't need a new computer you need to goto f9 and set your render levels to 2 not 6.

6 invariably causes lockup because each subdivision level requires about the square or cube the next level in computing power.

---

### Post by Nano Geek on 2006-04-25
> You don't need a new computer you need to goto f9 and set your render levels to 2 not 6. That worked great on weird.blend, but on my cannon model it didn't look smooth enough. I posted a picture for you to see.

---

### Post by Irony on 2006-04-25
Click on the barrel, hit f9, hit set smooth - this sets smooth reflections on the surface, it will then look smooth like the wheels.

---

### Post by Nano Geek on 2006-04-25
Here's a picture of the cannon subsurfed to 2 and **Set Smooth** turned on.

---

### Post by Irony on 2006-04-25
You haven't applied set smooth to the actual barrel.

---

### Post by Nano Geek on 2006-04-25
Problem solved!!!:D
Details later.

---

### Post by sinkxdie on 2006-04-25
How hard is it to make those things?

---

### Post by Irony on 2006-04-25
Well here's something I made - it took me a few weeks to make this because at first I didn't understand about subdivision surfaces. The rest followed quickly; lighting, shadows, materials, oversampling, smoothing, etc. However once I got it it took me only a couple of days (a few actual hours) to make another model.

I find video tutorials to be very helpful - [http://ibiblio.org/bvidtute/](http://ibiblio.org/bvidtute/)

[IMG]http://ironclub.net/blender/deadx.jpg[/IMG]

---

### Post by Nano Geek on 2006-04-25
> **Irony]Well here's something I made - it took me a few weeks to make this because at first I didn't understand about subdivision surfaces. The rest followed quickly said:**
> http://ibiblio.org/bvidtute/[/url]

[IMG]http://ironclub.net/blender/deadx.jpg[/IMG]On your model, how did you make those holes on the side. I can't figure out how.
Thanks

---

### Post by Irony on 2006-04-26
See;

[http://ironclub.net/blender/tube.blend](http://ironclub.net/blender/tube.blend)

---

### Post by Nano Geek on 2006-04-26
My cannon problem has started again.](*,)  It's doing the same thing, so if anyone has a solution, I would be grateful.
Thanks

---

### Post by Nano Geek on 2006-05-05
Problem solved, again .;) I found out that beveling the model had caused more vertices to form which kept it from smoothing the model properly. To fix it I selected all the vertices and pressed **Rem Double**.
Thanks guys, for all your help.

---

