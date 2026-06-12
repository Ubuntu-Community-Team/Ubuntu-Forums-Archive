---
title: "Looking for info from the linux pros."
date: 2011-03-25
forum: General Help
---

### Post by Azaz on 2011-03-25
This may not be the right forums for this but I find this forum unbelievably helpful!
I tried installing ububtu and dont get me wrong its a nice system but im having trouble learning off it. With windows I just started using it and every time I ran into a problem id go google it and spend an hour or so trying to fix it and leaning about windows the entire time. With ubuntu... i haven't run into a single error (at least 1 I could learn something off from, most problems are instant fixed by something like sudo install w/e and bam fixed, no clue how) . Its just to good for me. So I was thinking about doing a tripple boot with a simpler version of linux just to set it up and learn from it. I printed out everything on this webpage [http://linuxcommand.org/lts0020.php](http://linuxcommand.org/lts0020.php) so I wont need internet and basically I was wondering how I should go about this. I just want to learn to use the linux shell without completely screwing up my computer preferably without a GUI so I cant cheat. I have heard about virtual machines for this sort of thing but I have no idea what they are and google just gives me a ton of tech speak. So mainly, should I tripple boot win7,ubuntu, and a third linux distro (if so what distro)? or should I go do more research on virtual machines (any info would help). OR does anyone have any better idea for my situation. You guys rock and thanks for all the ubuntu help.

Azaz

---

### Post by josephmills on 2011-03-25
I am also new to this and not a pro but I would go though "all" the man (manual)pages to do this open your cli and type
```
man
``` 
then the program that you would like to look at info for.  eg ```
man man 
``` shows a manual page on the manual where ```
man ls 
``` will show a manual for the command ls Press q to quit the manual.
```
help
``` can be helpful
```
info
``` can be helpful too and I hope this was too but like I said I am a noob myself

---

### Post by Naggobot on 2011-03-25
Not a Linux pro my self either but I did take the time to read through your post so now I feel compelled to say something :).

I have never had the need for a Virtual machine my self but I know that Virtualbox is in available through Synaptic. More info from

[http://www.virtualbox.org/](http://www.virtualbox.org/)

I have understood that Virtual machines are relatively easy to reset in case something goes wrong.

---

### Post by idoitprone on 2011-03-25
Ummm you should not be asking linux pros. You should start smaller because what you asking for a couple of things.

First you are asking about testing linux. Testing in a virtual environment is the way to go to test software without risks.
> Not a Linux pro my self either but I did take the time to read through your post so now I feel compelled to say something.

I have never had the need for a Virtual machine my self but I know that Virtualbox is in available through Synaptic. More info from

[http://www.virtualbox.org/](http://www.virtualbox.org/)

I have understood that Virtual machines are relatively easy to reset in case something goes wrong.


About learning the commandline? I am totally not sure how far you are willing to learn. Bash shell is a full fledge programming language without a pretty interface. There are almost nothing you cant do in bash as you can with other languages. If you are really good, you can get a job.
If I were you, try to learn the basics of linux while you are learning the shell. Try to learn basic like everything is a file or permissions 

What you really want is to become a poweruser.
[http://en.wikipedia.org/wiki/Power_user](http://en.wikipedia.org/wiki/Power_user)

btw, reason why Ubuntu is so friendly, it started as a distro that caters to newbies.

[http://www.ubuntu.com/project/about-ubuntu/our-philosophy](http://www.ubuntu.com/project/about-ubuntu/our-philosophy)

> Our work is driven by a belief that software should be free and accessible to all.

---

### Post by nothingspecial on 2011-03-25
Install Ubuntu minimal and take it from there.

There is also inx which is a fully functioning command line linux distro but sort of a tutorial as well.

[http://inx.maincontent.net/](http://inx.maincontent.net/)

It runs srtaight from a cd or usb stick so you don't have to go about partitioning etc.

---

### Post by aeiah on 2011-03-25
look into doing it in a virtual machine. i dont know what you've read that's confused you, but virtualisation isnt a really complicated concept.

on its most basic level, a virtual machine can trick the software running on it into thinking its a real physical machine. so you could install, say, ubuntu minimal in a virtual machine and ubuntu minimal would think its running on a proper computer, but really its running in virtualbox on ubuntu.

the advantage of using a virtual machine instead of triple booting is that once you've got the system installed, you can start experimenting with setting up filesharing, web serving etc between the virtual operating system and your ubuntu operating system.

if you think ubuntu minimal (or ubuntu server) is a bit too full-featured you could look into arch linux, where you'd need to do a bit more configuration

---

### Post by Vigh on 2011-03-25
virtualbox PESU not OSE is good and provides usb support in the virtual machine, vmware player will also do the job, all you have to do is register and it is free to download and use

---

### Post by coldraven on 2011-03-25
Download Virtualbox from their web-site. Get the right version for your Ubuntu system.
When installed you start it from Applications>System Tools>Oracle VM
Download INX from here [http://inx.maincontent.net/](http://inx.maincontent.net/)
Create a virtual hard disc and install INX on it.
I'm not totally sure but you might be able to do that directly from the .iso file, if not you need to burn the .iso to a CD and use that.
Let us know how you get on.

---

### Post by WorMzy on 2011-03-25
Step 1: Install virtual box.
Step 2: Download [Arch Linux]("http://www.archlinux.org/download/") (you'll probably want the core image rather than the net install).
Step 3: Install and set up Arch Linux as a VM, while following [this guide](https://wiki.archlinux.org/index.php/Beginners%27_Guide)
Step 4: ????
Step 5: Profit

---

### Post by Azaz on 2011-03-25
Wow. Thanks everyone never though I would get this much info. Im definitely going to look into virtualbox and the rest of the stuff. Arch Linux and INX look very cool cant wait to try!:D

---

