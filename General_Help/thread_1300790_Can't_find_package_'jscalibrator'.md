---
title: "Can't find package 'jscalibrator'"
date: 2009-10-25
forum: General Help
---

### Post by afroman10496 on 2009-10-25
I'm using the 9.10 RC and I'm trying to install jscalibrator. But, now, when I type in ```
sudo apt-get install jscalibrator
``` is gives me ```
$ sudo apt-get install jscalibrator
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package jscalibrator
``` even when I enable the 'karmic partner' software source. Help!

---

### Post by kushal.kumaran on 2009-10-25
I guess the package was dropped for karmic because of this bug:

[https://bugs.launchpad.net/ubuntu/+source/libjsw/+bug/416628](https://bugs.launchpad.net/ubuntu/+source/libjsw/+bug/416628)

---

### Post by spezticle on 2009-11-01
so use an different program? any suggestions?
or install jscalibrator, despite it's removal from the lastest ubuntu distro?

---

### Post by scared0o0rabbit on 2009-11-07
Bump.  I'd really like to know what to do as well.  Any suggestions?

---

### Post by ebs16 on 2009-12-03
is there another way to use a gamepad as my primary controller for mythtv?

---

### Post by tudor117 on 2009-12-23
I noticed it's quite an old thread. However, you can install jscalibrator from Jaunty's repos. The only thing is there are quite a few packages that need to be installed.
Another thing that you can try is to install "*joystick*" which includes "some useful tools for using joysticks".

---

### Post by computing-os on 2010-01-11
search jscalibrator on google with ubuntu (this works with 64 bit) or go on this link [http://packages.ubuntu.com/dapper/jscalibrator](http://packages.ubuntu.com/dapper/jscalibrator) go to the bottom of the page click i386 im not sure if this is the british one but click on this [gr.archive.ubuntu.com/ubuntu ]("http://gr.archive.ubuntu.com/ubuntu/pool/universe/libj/libjsw/jscalibrator_1.5.5-1ubuntu1_i386.deb")

download then install using debian when doing so errors will come up but do the same with the missing error codes just search them then find them on packages.ubuntu.com

---

### Post by Ted_Kazynski on 2010-12-30
probably a dead post but, these don't work either. any help with a joystick calibrator?

---

### Post by ebs16 on 2010-12-30
Should be in the repos. Whats your specific problem?

---

### Post by markackerman8@gmail.com on 2011-05-02
I am trying with great difficulty getting my logitech rumblepad 2 to work, and think I need a gui to map the inputs.  I have tried joystick and:

jscal -c /dev/input/js0

but don't understand the the cli axes numbers.  I would really like a GUI that tells me what my buttons are when I push them and then allows me to map it to a keyboard input (that my IL-2 game is associated with).  

Arghhh, there must be a GUI, and jscalibrator is impossible to install (tried to add jaunties repo too - no lock),

Please ... help

Mark

---

### Post by loungedaddy on 2011-05-25
Bump. Hoping to find some help with this too. I can't believe there isn't a GUI available.

---

### Post by markackerman8@gmail.com on 2011-05-25
tried again with the above links and the merrygoround went to missing libglib1.2 or greater, another search and found it in DaPPERS!!! repos, than 
Dependency is not satisfiable: libgtk1.2, arghhhh, I hate this.

---

### Post by sda123 on 2011-08-25
hi, i recently purchased a  joypad on amazon, and found this post to see if i could find jscalibrator. i found a link that installed it on my computer : [http://packages.ubuntu.com/hardy/jscalibrator](http://packages.ubuntu.com/hardy/jscalibrator) download the .deb file and see the errors ( if there are any ) that are about packages being missing, find the missing package on [http://packages.ubuntu.com/hardy/jscalibrator](http://packages.ubuntu.com/hardy/jscalibrator) then install it, if you use gdebi installer make sure it says "all dependencies are satisfied" then click install. if this has a package error download the piece of software it says to install from [http://packages.ubuntu.com/hardy/jscalibrator](http://packages.ubuntu.com/hardy/jscalibrator) This worked for me.

neverball is a good game to test it with. :P:KS

---

### Post by binsky734 on 2012-08-26
I'm not entirely sure how I found it, but here it is [http://packages.ubuntu.com/hardy/jscalibrator](http://packages.ubuntu.com/hardy/jscalibrator). I had to install some dependencies, but it seems to work.

---

### Post by jazztickets on 2013-03-27
> **markackerman8@gmail.com said:**
> I am trying with great difficulty getting my logitech rumblepad 2 to work, and think I need a gui to map the inputs.  I have tried joystick and:

jscal -c /dev/input/js0

but don't understand the the cli axes numbers.  I would really like a GUI that tells me what my buttons are when I push them and then allows me to map it to a keyboard input (that my IL-2 game is associated with).  

Arghhh, there must be a GUI, and jscalibrator is impossible to install (tried to add jaunties repo too - no lock),

Please ... help

Mark

For Joy2Key functionality, you want qjoypad ([http://qjoypad.sourceforge.net/](http://qjoypad.sourceforge.net/))
packages are available from [http://www.playdeb.net](http://www.playdeb.net)

---

