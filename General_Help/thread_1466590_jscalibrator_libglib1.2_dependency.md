---
title: "jscalibrator libglib1.2 dependency"
date: 2010-04-30
forum: General Help
---

### Post by frs89 on 2010-04-30
I've just installed lucid lynx and I need to install jscalibrator but it misses libglib1.2, I tried looking in the synaptics and anywhere but I can't find it. Looks like the package is not supported. Any sugestions?

Thanks in advance.

---

### Post by walkerjustin21 on 2010-05-26
Im having the same problem

---

### Post by deuce5 on 2010-06-03
I am having this problem now as well.  Are there any other tools that will allow us to use a controller to play games in lucid??

---

### Post by hopelessone on 2010-06-10
Me too..!

I just bought 2 new Arcade Joysticks...So what I can't use them now?

Is there any fix? besides go back to 9.10?

---

### Post by Irvine_himself on 2010-08-28
Me too, I had this problem. After a bit of research, the solution is to install the "joystick" package from synaptic and use "jstest" and "jscal" to calibrate your joystick. Full instructions can be found here: [http://www.flightgear.org/forums/viewtopic.php?f=11&t=5632](http://www.flightgear.org/forums/viewtopic.php?f=11&t=5632)

The thing to note is that once you have the calibration output, his instructions are specific for playing "FlightGear" and assume that the joystick is continually plugged in. For me this last is not an option. What I did was to write the following bash and save it in /dev/input/

```

#!/bin/sh -e
#
#joystick calibration from jcal, read http://www.flightgear.org/forums/viewtopic.php?f=11&t=5632
#
# Run this script after plugging in joystick
#
cd /dev/input/
#
jscal -s 3,1,0,133,133,11184469,11670751,1,0,114,116,8658944,8521500,1,0,95,95,6315936,6315936 js0
#
# End

```Then by, having a launcher in the panel pointing to the bash, I can set the calibration parameters after  plugging in the joystick, (just before launching a game) . This works!

I would give getting the correct calibration parameters a couple of attempts, till you get it just right and don't be put of by the fact that the calibration is done through the terminal, it is easy ;)

---

### Post by uppersnatch on 2011-07-16
I had the same problem too. I searched through the ubuntu forum and I  found some useful info that I want to share with you. I believe it can help to solve this problem. Firstly, go to the

[http://packages.ubuntu.com/dapper/jscalibrator](http://packages.ubuntu.com/dapper/jscalibrator)

There you see that jscalibrator package _[COLOR=black]depends o[/COLOR]n_ some other packages:

[libc6]("http://packages.ubuntu.com/dapper/libc6")
[libglib1.2]("http://packages.ubuntu.com/dapper/libglib1.2")
[ibgtk1.2]("http://packages.ubuntu.com/dapper/libgtk1.2")
[libjsw2]("http://packages.ubuntu.com/dapper/libjsw2")
[libx11-6]("http://packages.ubuntu.com/dapper/libx11-6")
[libxext6]("http://packages.ubuntu.com/dapper/libxext6")
[libxi6]("http://packages.ubuntu.com/dapper/libxi6")

These packages need to be installed first. To see if the package installed already, type the following command in terminal:

aptitude show "name of package (e.g. libc6)"

if you don't get an error like "E: Unable to locate package", then it means the package is installed.

I got errors for the following packages:

[libglib1.2]("http://packages.ubuntu.com/dapper/libglib1.2")
 [ibgtk1.2]("http://packages.ubuntu.com/dapper/libgtk1.2")
 [libjsw2]("http://packages.ubuntu.com/dapper/libjsw2")

I started to install from the last one - [libjsw2]("http://packages.ubuntu.com/dapper/libjsw2").
on the website shown above, click on [libjsw2]("http://packages.ubuntu.com/dapper/libjsw2"). In the opened window you see that [libjsw2]("http://packages.ubuntu.com/dapper/libjsw2") package depends on only [libc6]("http://packages.ubuntu.com/dapper/libc6") package which was already installed (in my case). If depending packages (here, [libc6]("http://packages.ubuntu.com/dapper/libc6")) are installed then you can proceed to install the package itself (here, [libjsw2]("http://packages.ubuntu.com/dapper/libjsw2")).

Before you install it, you need to edit the source.list.
Open source.list by typing the following command in terminal:
sudo gedit /etc/apt/sources.list

Copy this

deb [http://*ubuntu.mirror.cambrium.nl/ubuntu/](http://*ubuntu.mirror.cambrium.nl/ubuntu/)* hardy main universe

and paste it to the final line of source.list. Then save and close source.list.

Run the following line in terminal:

sudo apt-get update

Now, you can install [libjsw2]("http://packages.ubuntu.com/dapper/libjsw2") from the following link:

[http://ubuntu.mirror.cambrium.nl/ubuntu/pool/universe/libj/libjsw/](http://ubuntu.mirror.cambrium.nl/ubuntu/pool/universe/libj/libjsw/)

click on [libjsw-dev_1.5.6-0ubuntu3_i386.deb]("http://ubuntu.mirror.cambrium.nl/ubuntu/pool/universe/libj/libjsw/libjsw-dev_1.5.6-0ubuntu3_i386.deb") it will ask you to open it with Ubuntu Software Center, press ok, and wait,
it takes few seconds to open, when it is opened you will see install button on the right corner of Ubuntu SOftware Center. Press on it.

After [libjsw2]("http://packages.ubuntu.com/dapper/libjsw2") is installed, you can directly proceed to install jscalibrator package, from the same link:

[http://ubuntu.mirror.cambrium.nl/ubuntu/pool/universe/libj/libjsw/](http://ubuntu.mirror.cambrium.nl/ubuntu/pool/universe/libj/libjsw/)

click on [jscalibrator_1.5.6-0ubuntu3_i386.deb]("http://ubuntu.mirror.cambrium.nl/ubuntu/pool/universe/libj/libjsw/jscalibrator_1.5.6-0ubuntu3_i386.deb"), then install it by using Ubuntu Software Center.

P.S. I have not tried to install other two packages - [libglib1.2]("http://packages.ubuntu.com/dapper/libglib1.2") and [ibgtk1.2]("http://packages.ubuntu.com/dapper/libgtk1.2"), because they were automatically installed after the installation of

[libjsw2]("http://packages.ubuntu.com/dapper/libjsw2") package.

Good luck!

---

