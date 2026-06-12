---
title: "stopping gdm crashes system..."
date: 2010-08-21
forum: General Help
---

### Post by mikemrm on 2010-08-21
Sorry if this has been asked before, but cannot seem to find anyone that has the same problem.

I installed Ubuntu 10.04.1 yesterday, and I've been trying to install my nvidia 240 drivers for it. I've done this multiple times on 9.## and it worked fine. When I try to install them it says i need to shutdown xserver. so I open terminal and type sudo /etc/init.d/gdm stop

screen goes blank and all there is is a flashing _ at the beginning. I'm not able to anything except type, but no commands work.

So, I tried starting it up in recovery mode root shell or whatever, and it shows the command prompt. Then I login, and it says welcome, I go to my downloads folder and type sudo sh NVIDIA...256.44.run and it says I need to be in telinit 3, so I get out of the installation and type sudo telinit 3.

well that brings me up to a login command so I type my username
then it askes for a password, which I also fill in.

Now it says incorrect login. So I try again, and it keeps going on, but then I noticed that it puts the first letter of my username infront of Password.

So if my username was ubuntu the next line would look like
uPassword: |

and when I put my password if it was youtube, it would look like
yIncorrect Login

And the only way I can get out of that is by Alt + Ctrl + Del to restart, same when I shutdown gdm...

Man that was alot of text, but I hope someone out there is kind enough to read it and help me with this problem

---

### Post by dino99 on 2010-08-21
why are installing from nvidia source ?
 take the easy way by adding x-swat ppa to your synaptic repo tab :

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

remove/purge every nvidia installed packages first
remove xorg.conf (sudo rm -f /etc/X11/xorg.conf)
 then update upgrade with x-swat packages
reboot

about the other issues:
sudo dpkg-reconfigure gdm
sudo dpkg-reconfigure jockey
sudo dpkg-reconfigure plymouth

---

### Post by dagdeniz on 2010-08-21
Well, firstly, installing nvidia drivers from nvidia's website (it looks like you do it that way) is not beginner friendly, try to install it from the repos if you can. Secondly, when you enter your password, are you sure that the numlock is on (or, do you have any numbers in your password, that may cause the problem).

---

### Post by mikemrm on 2010-08-21
@dino99
didn't know there was a different way, I'm semi a beginner.

@dagdeniz
I've done it multiple times from there website. Ever since I installed ubuntu multiple versions back I've installed them from there website.

Now when I tried enabling the "Extra" feature under Visual Effects, it found and installed its own version for my graphics card, but it might be outdated, because once I ran the dual monitor stuff, I cannot click on Extra anymore, it says "Searching for available drivers..." and then comes up with "The Composite extension is not available"

I've also searched up on that problem but everything I try doesn't work.

As for my password, I don't use the number pad to type them.



UPDATE:
@dino99
I did the reconfigure for those 3, it says I don't have jockey and once I finished the last one, I shutdown gdm again, and this time it says [OK] in the top right and just sits there.

Also, for that x-swat thing, how to I add it, its not in my repo already, and I don't know how to add a new download url to the repo.

ANOTHER UPDATE:
It looks like I cannot do any of the "Extra" effects when I have Xinerama on. Is there an easy fix for that? I'm using the driver that ubuntu installed

---

### Post by dagdeniz on 2010-08-21
To have it in the repo, you should add it to your sources.list and download the keys. Both of them exist in the link dino99 has given you. To be more precise, do it this way: 

```
sudo nano /etc/apt/sources.list
```

add
```
deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) lucid main 
deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) lucid main
```save and exit. Download keys:

```
      sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AF1CDFA9                 
```

---

### Post by mikemrm on 2010-08-21
ok, I did all that. I dunno if this makes me sound dumb, but... what did that do? I did everything dino99 said, with the info you gave, and I don't see any new drivers in hardware drivers or anything.

When I choose "Enable Xinerama" it still won't let me have the "Extra" effects, and I still crash when I try to shutdown gdm

---

### Post by dagdeniz on 2010-08-21
dino99 suggested the regular way of installing the drivers from an updated but unofficial repo, in case that way you might be successful. I have no new idea, I only tried to describe dino99's way more precisely :lolflag:.
 After purging the configuration (for a clean re-installation) the way dino99 described, you can re-install the drivers from the ppa repository via synaptic. The proper order is generally, although installing all of them at once may sometimes be succesful, the kernel headers first, the driver kernel second and the driver binary, nvidia-xconfig and nvidia-settings last; because each one depends on the previous one. A reboot is always necessary (because it'll be loaded as a kernel module, so the kernel is kind of updated), simply restarting x may not work. 
Generating a xorg.conf ("Xorg -configure" with administrative privileges) to play with in case something wrong happens helped me a lot.

---

