---
title: "New Ubuntu user, got a few troubles :D"
date: 2011-02-19
forum: General Help
---

### Post by Skorpian456 on 2011-02-19
Hello :D
Okay I've installed Ubuntu 10.04 on my laptop today ( using wubi if it matters ).
I got a trouble with resolution. No matter what I do, I can't get it above 800x600. I realize I need a graphics driver, which I can't find through hardware drivers option. I can only find wireless driver, which I've already enabled.
My graphics is SIS672 integrated graphics. 
Also, how do I setup wine? I can't find any noob friendly guide. Also, will I be able to run Swat 3, age of empires the conquerors? Those are the most 2 important games I wanna run.
How do I share and access shared files?
I'm sorry for too many questions but I'll really appreciate it if you can help a newbie to ubuntu here :D
Thanks,
Skorpian456

---

### Post by marin123 on 2011-02-19
you will get wine by opening terminal and typing:
```
sudo apt-get install wine1.2
```

then mark your exe file so it opens with wine, double click it and install it.

also check [http://appdb.winehq.org/](http://appdb.winehq.org/) for your games and see if there is any tinkering involved.

---

### Post by Skorpian456 on 2011-02-19
Ok thanks but do you know where I can get Graphics drivers? And how do I share files?

---

### Post by dino99 on 2011-02-19
into synaptic, install: xserver-xorg-video-sis

into a terminal:
sudo rm /etc/X11/xorg.conf

then reboot and check driver activation: system admin additional drivers

sidenote: hope you have installed the 32 bits lucid (i386)

[http://ubuntuforums.org/showthread.php?t=1575973](http://ubuntuforums.org/showthread.php?t=1575973)

---

### Post by marin123 on 2011-02-19
i told you what i know :D now you will have to wait for someone who knows the rest...

you can google for graphics drivers. if they are not in Additional drivers menu then you will have problems. try googling them or here: [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

sharing part is a mystery to me. you can right-click a folder and under Share tab set it as shared folder, but i have no idea how to see that folder from ubuntu to ubuntu machine, and i havent tried accessing it from windows.

---

### Post by Skorpian456 on 2011-02-19
@dino99 : Okay sir I'm sorry but I'm completely newbie to whole linux stuff. I know terminal, but what do you mean with " into synaptic ? "
Also I don't understand anything from the link you posted. I apologize :D

---

### Post by IWantFroyo on 2011-02-19
System-Administration-Synaptic Package Manager
Search for xserver-xorg-video-sis.
Good luck.

---

### Post by Skorpian456 on 2011-02-19
Thanks but when I searched I found 2 stuff. I could only mark them for reinstallation so I did so. Then applied. Then when I tried to delete the file, it told me no such file existed.
I turned off my laptop, turned it on again, but nope it still didn't detect the monitor.
P.S : I installed ubuntu in same partition of windows XP Pro with 7 GB of free space using wubi.exe if it matters.

---

### Post by marin123 on 2011-02-19
it doesnt matter if you installed it through wubi, everything should be the same.

did you go to System -> Preferences -> Monitors and see if you can set better resolution?

if you only could mark drivers to reinstall, it means theyre already installed and you could get proper resolution.
btw what is your screen resolution in xp? can you reboot and check it out?

---

### Post by Spyderkid on 2011-02-19
open a terminal by going to applications > Accessories > Terminal

then copy the following and press [enter].
[FONT="Courier New"]sudo rm /etc/X11/xorg.conf[/FONT]
enter your password if prompted.

then reboot and have a look for the driver again.

---

### Post by Spyderkid on 2011-02-19
And as for wine its a piece of cake...

open the software centre

search for wine

install either wine or wine beta.

Done!

---

### Post by Skorpian456 on 2011-02-19
> it doesnt matter if you installed it through wubi, everything should be the same.

did you go to System -> Preferences -> Monitors and see if you can set better resolution?

if you only could mark drivers to reinstall, it means theyre already installed and you could get proper resolution.
btw what is your screen resolution in xp? can you reboot and check it out?
It's 1280*800. And in monitors it doesn't even detect the monitor :S. I can't set it more than 800*600.
open a terminal by going to applications > Accessories > Terminal

> then copy the following and press [enter].
[FONT=Courier New]sudo rm /etc/X11/xorg.conf[/FONT]
enter your password if prompted.

then reboot and have a look for the driver again.
I already tried that, it doesn't even find xorg.conf. 
As for wine, I know how to install it, but how to use it? Anyway let's skip wine for now, my main objective now is just getting more resolution to get this thing to run properly :D

---

### Post by Spyderkid on 2011-02-20
I give you a quick intro anyway.

**_[COLOR="Blue"]wine, installing programs:[/COLOR]_**

>[COLOR="Red"]if you want to install a file you downloaded from the internet then find it[/COLOR], [COLOR="Lime"]right click on the file[/COLOR], [COLOR="DeepSkyBlue"]go to permissions[/COLOR], [COLOR="Blue"]and click the "allow executing file as a program" box.[/COLOR] [COLOR="Orange"]Then right click use, open with wine program loader. then wait and follow the installation[/COLOR]



[COLOR="Red"]If installing from a CD/DVD/CD-ROM then its a tad trickier.[/COLOR]

[COLOR="SeaGreen"]>insert your CD/DVD/CD-ROM[/COLOR] [COLOR="DeepSkyBlue"]AND LOOK AT YOUR DESKTOP TO FIND WHAT THE CD'S CALLED! [/COLOR]
[COLOR="Orange"]>open a terminal by going to application > accessories > Terminal. Then open it and enter this.... (one line at a time pressing enter after each one.)[/COLOR] 
```

cd /media
cd DVD NAME 
```

([COLOR="Red"]look on desktop for DVD NAME [COLOR="Blue"](needed above)[/COLOR] [don't type this stuff in brackets])[/COLOR][COLOR="Blue"](if the name has spaces use " " around the name.)[/COLOR]

[COLOR="YellowGreen"]then in the same terminal after that enter this...[/COLOR]

```

wine setup.exe

```

[COLOR="Magenta"]follow the setup instructions[/COLOR]

---

### Post by Spyderkid on 2011-02-20
[COLOR="Blue"]And as for the resolution problem.[/COLOR]

[COLOR="Green"]do you know what your graphics driver is called if not can you find out and post it here please,[/COLOR] [COLOR="Red"]then I will be able to help you find or make a driver for it.[/COLOR]

---

### Post by Skorpian456 on 2011-02-20
Okay last night a problem occured and I had to reformat my C drive and reinstall windows XP. Imma go install Ubuntu 10.10 now ( I used to have 10.04 ) but do you know how I can force wubi to download 32-bit version not 64-bit version? It always downloads the 64-bit for no reason :S

---

### Post by Spyderkid on 2011-02-20
Can you just boot from the USB/CD instead it can be easier...

---

### Post by mtbower07 on 2011-02-20
As far as I have been able to figure this thread is still valid. I have had many problems with SIS cards.

[http://ubuntuforums.org/showthread.php?t=615094&highlight=sis](http://ubuntuforums.org/showthread.php?t=615094&highlight=sis)

---

### Post by Spyderkid on 2011-02-21
Did my colourfull wine tutorial help at all?

---

### Post by Skorpian456 on 2011-02-21
Sorry guys for late reply I was installing ubuntu 10.10.
I still can't get res over 800x600. My graphics card is SIS672 integrated graphics.

---

### Post by Spyderkid on 2011-02-22
OKAY LISTEN UP!


There is no better driver for your chip - we have to do a little bit of editing (creating the script ourselves)


```
 
gksu gedit /etc/X11/xorg.conf

```

then find it and in the
Section "Screen"
add
Modes "1200x800"
Save and reboot
You should have 1200x800 now
It's not difficult to "install" a new graphics driver especially for ATI and nvidia but also for the rest (except possibly Intel - it's so well integrated that it becomes difficult )

---

### Post by Skorpian456 on 2011-02-22
Thanks but after entering that line in terminal it showed up a program where I can edit xorg.conf, but problem is xorg.conf is completely plain, nothing inside it. No text, nothing at all.

---

### Post by marin123 on 2011-02-23
[http://ubuntuforums.org/showthread.php?t=1548547](http://ubuntuforums.org/showthread.php?t=1548547)

try to find your answer here...

---

### Post by Spyderkid on 2011-02-25
look at this I'm pretty sure I've found the answer now...


[http://ubuntuforums.org/showthread.php?t=1605998](http://ubuntuforums.org/showthread.php?t=1605998)

---

### Post by Spyderkid on 2011-02-27
did my thread i suggested help?

---

