---
title: "invisible fonts and no video on minitube"
date: 2010-09-04
forum: General Help
---

### Post by MatthewHouse on 2010-09-04
Hi, 
I have been having some trouble with packet tracer 5.3 and minitube. I am a long time linux user and i am not new to linux but i have been struggling to figure out why the following problems occur. 

When i have Desktop Effects active (compiz), packet tracer is not showing any fonts (they are see through to my wallpaper) and some of the panels appear... well, wired and see throughish. 

Also i have had issues with minitube. Believing the issue with packet tracer was my NVIDIA drivers i updated my NVIDIA drivers to version 256.52. I at one point had the generic display driver running and found that minitube now worked. Previously the video didn't display. 

Packet Tracer has allways worked without compiz running and it seems that minitube wont run with NVIDIA drivers. I cant understand why. Is this my NVIDIA drivers or is there another explanation?

I am running Ubuntu 10.04 with kernel 2.6.32-24-generic and nvidia drivers 256.52 with a GeForce 9500 GT. 

Any help would be greatly appreciated. Note i am a networking student and i have a diploma in software Development so i consider myself pretty handy in linux. This is one of a few problems i havent beenable to fix myself or with google. ;)

I have attached a screenshot of the problem to show exactly whats going on.

Thanks in advance,

Matthew House

---

### Post by MatthewHouse on 2010-09-12
just replying to my own post... I have found that if I use the command[FONT="System"] /opt/pt/bin/PacketTracer5[/FONT] instead of the [FONT="System"]/opt/pt/packettracer[/FONT] command the program runs well. 

The command [FONT="System"]/opt/pt/packettracer[/FONT] appears to run a script that loads custom libraries. The program doesn't seem to need the custom libraries and will run well with Ubuntu default libraries (libQT). 

Also the program opens its packet-tracer files correctly when i click on them if when i created a symbolic link  [FONT="System"]/usr/local/bin/packettracer[/FONT] that leads to [FONT="System"]PackeTracer5[/FONT]. 

However is seems the programs does everything but save properly.

I hope this helps someone.

---

### Post by daniel1904 on 2010-09-24
Hi i have a problem with my packet tracer is that i succesfully install it native PackettracerUbuntu.tar.gz well put accept and that but when i run the program. It appears that the fonts have become transparentand some features too. So maybe someone could help.

---

### Post by MatthewHouse on 2010-09-24
the only temporary solution is to turn off desktop effects. 
But  have traced the problem possibly to either nvidia or packet tracers custom libqt files.

---

### Post by daniel1904 on 2010-09-24
Yes by changing the visual effects to NONE, i could see the packet tracer as in the image shows but the cairodock an all the desktop features were missing and the dock doesnt work anymore, it doesnt hide under the windows and i dont know if like this i wanna have that desktop. Well like linux always have an answer i hope someone could fix this problem. If not i will try using packet tracer with wine.(but i dont wanna do).

---

### Post by MatthewHouse on 2010-09-24
i have the same problem yeah its a pain ... dose the samething when  metacity inbuilt compositing is turned on and desktop effects off. compiz works but the pt dosen't...

---

### Post by daniel1904 on 2010-09-24
Well i have tried what u have tried and the outputs are the same :(. So there's nothing i can do unless some guy outsider has a real good answer. Meanwhile i will be using packet tracer with wine at least i can see the fonts :S.
But for programs native for linux. Fortunately we have wine.

---

### Post by dendy7h on 2010-11-15
I used this link to get packet tracer working correctly on a x86 machine with compiz enabled.
[http://http://pvradu.blogspot.com/2010/04/packet-tracer-52-font-problem.html]("http://http://pvradu.blogspot.com/2010/04/packet-tracer-52-font-problem.html")

---

### Post by pressko on 2011-02-10
same problem with PT on Ubuntu 10.10 x64 + compiz effects . Do Any1 have a solution ?

---

### Post by MatthewHouse on 2011-02-10
I really hate to say this mainly as there is a native Linux release, but i went to using wine to run the windows version. Worked fine after that.

---

### Post by pressko on 2011-02-17
Hi guys :))) i figure it out :popcorn:

1. install packet tracer [http://www.icpep.org/packet-tracer-on-ubuntu/](http://www.icpep.org/packet-tracer-on-ubuntu/)

2. Make a new launcher --> in command line of the launcher just type : 

sh -c 'export XLIB_SKIP_ARGB_VISUALS=1 && LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/local/bin/pt/packettracer'

Whereas # /usr/local/bin/pt/packettracer # is the path to the program launcher where u installed it and # libv4l# is a lib package ( u can install it for Synaptic Package Manager if u don't have it) .
The location could be different than mine , so check it.

3. It's working like a charm ):P.
[ATTACH]183730[/ATTACH]
[IMG]http://img233.imageshack.us/f/screenshotsxf.png/[/IMG]

---

### Post by MatthewHouse on 2011-02-22
Thanks for  your tip .... funny enough i am using kde and  it dosen't seem to be a problem with the kde compositor. However have tried in gnome and seem to work... I kind of get the XLIB_SKIP_ARGB_VISUALS=1 bit but I don't know what video4linux has to do with it.... but seems to work..... THANK YOU

---

### Post by manco1911 on 2011-03-12
> **pressko said:**
> Hi guys :))) i figure it out :popcorn:

1. install packet tracer [http://www.icpep.org/packet-tracer-on-ubuntu/](http://www.icpep.org/packet-tracer-on-ubuntu/)

2. Make a new launcher --> in command line of the launcher just type : 

sh -c 'export XLIB_SKIP_ARGB_VISUALS=1 && LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/local/bin/pt/packettracer'

Whereas # /usr/local/bin/pt/packettracer # is the path to the program launcher where u installed it and # libv4l# is a lib package ( u can install it for Synaptic Package Manager if u don't have it) .
The location could be different than mine , so check it.

3. It's working like a charm ):P.
[ATTACH]183730[/ATTACH]
[IMG]http://img233.imageshack.us/f/screenshotsxf.png/[/IMG]



Works like a charm on Ubuntu 10.10 x64 and Packet Tracer 5.3 

Thanks Pressko, nice one

---

