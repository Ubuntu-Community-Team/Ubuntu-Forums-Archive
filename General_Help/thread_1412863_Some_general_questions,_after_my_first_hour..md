---
title: "Some general questions, after my first hour."
date: 2010-02-21
forum: General Help
---

### Post by !!?? on 2010-02-21
I first installed ubuntu some two years ago I believe. At the time it was mostly for the visual effects and speed that would come with it, and from what I remember I enjoyed it. The reason why I stopped using it was because I had a hard drive failure at the time, and I didn't feel like reinstalling it. So recently I've been having problems with vista and a partition setup, and the solution to that problem was to install ubuntu to help fix my partitions. That made me think that I wanted to keep ubuntu, and maybe even use it as my main operating system. From what I remember though, while I liked ubuntu it didn't seem very user friendly and had a learning curve - especially installing things. So that is why I'm here. I have a few questions. 


How can I get used to the new setup compared to windows? For example, I just tried to install flash, but it didn't work out too well. I have no idea how to do this, something that would be so simple in windows? How can I use this operating system with ease? Also I would appreciate it if you could help me with my flash problem. :D

Drivers, this is my other problem. I didn't have this problem when I last installed ubuntu because my video card was integrated and worked fine surprisingly, and I even remember downloading that thing that made it a cube with visual effects and everything and it ran perfectly. I've noticed though that with my since upgraded, Nvidia video card it has worked quite slowly. Especially after installing the drivers that were provided when searching for them through the system menu, which had trouble working at first and I had to change to the older drivers provided. Now it runs ok, but some of the backgrounds of websites take forever to load while in windows it would be instantly loaded. Is there any help I can get about drivers? I'm not talking exclusively about my Graphics Card either, that is just the only problem I've came across. Btw my GPU is a 9500gt. 

What do you recommend me downloading/tweaking as a beginner? Could you link me to some guides? I don't want to be an expert, but I want to be able to at least know how to get around. 

Anyway, I'm sorry if my questions come to be very simple and somewhat stupid, but I am really excited about getting better suited for Ubuntu, as I've heard great things, and from what I remember I experienced them. Thanks for any help.

---

### Post by crlang13 on 2010-02-21
Hi and welcome.

I'm a newbie too but i think you'll find that you'll have everything sorted very quickly.

About the guide you mentioned - have you seen this? [http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)

I'm still a newbie, so I can't really help you with the other problems (I do know that flash has been a reoccurring problem.  The best thing to do to solve these problems is to create a thread for each problem.  You'll attract more specific help that way :P

---

### Post by paydaydaddy on 2010-02-21
Follow this guide to get most things working.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by !!?? on 2010-02-21
Thanks a lot. That means I have some reading to get to. :D

---

### Post by switch10 on 2010-02-21
The first thing I do after install is:

```
 
sudo apt-get update

sudo apt-get install ubuntu-restricted-extras

sudo apt-get install libdvdread4

sudo apt-get install libdvdcss2


```

This will install flash, mp3 support, the ability to read and write DVD's and a bunch of other stuff you will need.

---

### Post by lidex on 2010-02-21
As for your graphics driver, have a look here:
[http://ubuntuforums.org/showthread.php?t=1090146]("http://ubuntuforums.org/showthread.php?t=1090146")

If you are using Firefox, lovinglinux has a comprehensive guide here:
[http://ubuntuforums.org/showthread.php?t=1193567]("http://ubuntuforums.org/showthread.php?t=1193567")
That should solve your flash issues.

---

### Post by !!?? on 2010-02-21
I got flash working thanks to that guide. :D I'm still working on some other things, but it is very helpful. Thanks for the other links to, especially for the graphics drivers.


Edit: I've noticed that it doesn't let me pause videos or any function that requires more than watching something. :(

---

### Post by lidex on 2010-02-21
> **!!?? said:**
> I got flash working thanks to that guide. :D I'm still working on some other things, but it is very helpful. Thanks for the other links to, especially for the graphics drivers.


Edit: I've noticed that it doesn't let me pause videos or any function that requires more than watching something. :(

Is that on all sites or specific ones?

---

### Post by !!?? on 2010-02-21
> **lidex said:**
> Is that on all sites or specific ones?

Youtube, but now it lets me pause, but the sound lags a few seconds after pausing. 

Hulu works, but it is laggy and slows down the whole computer a lot.

Edit: And I don't think I have Flash 10 installed because I'm using a 64 bit OS, though I could be wrong. It says that it doesn't fit my architecture when I try to use the software center to install it.

---

### Post by lidex on 2010-02-21
What is the output of terminal command:
```
uname -a
```

BTW, getting your graphics drivers sorted out may solve some of these issues.

---

### Post by !!?? on 2010-02-21
> **lidex said:**
> What is the output of terminal command:


```
Linux stefan-desktop 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 x86_64 GNU/Linux

```

---

### Post by lidex on 2010-02-21
Yep, that's x64 alright. you should follow this guide:
[http://ubuntuforums.org/showthread.php?t=1358591]("http://ubuntuforums.org/showthread.php?t=1358591")

There is a script linked from that page to purge conflicting plugins that I would make use of also.

---

### Post by !!?? on 2010-02-21
Alright I got that installed, but the videos still seem to lag. Maybe it is my Graphics driver? I will try that now I guess.

Edit:  sudo kill all<desktop manager> What would I put under <desktop manager>?

---

### Post by !!?? on 2010-02-21
Alright I've followed all of the steps to update my driver, but when I try to install it, the command isn't recognized. 

This is what I put in:

sudo ./NVIDIA-Linux-x86_64-190.53-pkg2.run and that is exactly what is on the filename of the driver on my desktop. What could I be doing wrong?

---

### Post by PhoHammer on 2010-02-22
> **!!?? said:**
> Alright I got that installed, but the videos still seem to lag. Maybe it is my Graphics driver? I will try that now I guess.

Edit:  sudo kill all<desktop manager> What would I put under <desktop manager>?

I always stick with 32bit, 64 never worked out for me... but if you get it working right, then there's no reason to not use it, I guess.

---

### Post by lidex on 2010-02-22
> **!!?? said:**
> Alright I've followed all of the steps to update my driver, but when I try to install it, the command isn't recognized. 

This is what I put in:

sudo ./NVIDIA-Linux-x86_64-190.53-pkg2.run and that is exactly what is on the filename of the driver on my desktop. What could I be doing wrong?

Did you download to your desktop and cd into ~/Desktop from the commandline? Were you following this post:[http://ubuntuforums.org/showpost.php?p=6858218&postcount=17]("http://ubuntuforums.org/showpost.php?p=6858218&postcount=17") Make sure you cd into the directory you downloaded the file to. BTW, what was error message? GDM is your desktop manager.

---

### Post by !!?? on 2010-02-22
> **lidex said:**
> Did you download to your desktop and cd into ~/Desktop from the commandline? Were you following this post:[http://ubuntuforums.org/showpost.php?p=6858218&postcount=17]("http://ubuntuforums.org/showpost.php?p=6858218&postcount=17") Make sure you cd into the directory you downloaded the file to. BTW, what was error message? GDM is your desktop manager.

Yes that is what I've been following. I've tried everything, even tried to change the file name. 

I've followed all of the steps until this part. 
Here is what I recently put in. The bolded is automatically done.

```
**stefan@stefan-desktop:~/Desktop$** sudo ./Nvidia-Linux-x86_64-190.53-pkg1.run
```

This is what I get. 

```
sudo:./Nvidia-Linux-x86_64-190.53-pkg1.run: command not found.
```

I've checked too, my file is in desktop.

---

### Post by Letrazzrot on 2010-02-22
Just a quick off the top of the head thought:

Check your capitalizations when specifying the file name.  This threw me at first, with Linux -- it is case sensitive, unlike DOS/Windows.

---

### Post by sau99ms on 2010-02-22
> **switch10 said:**
> The first thing I do after install is:

```
 
sudo apt-get update

sudo apt-get install ubuntu-restricted-extras

sudo apt-get install libdvdread4

sudo apt-get install libdvdcss2


```

This will install flash, mp3 support, the ability to read and write DVD's and a bunch of other stuff you will need.

I'm a newbie too and try to avoid using the terminal unless necessary! You can install packages without using the terminal...go to Administration - > Synaptic and search for the packages you need and mark for installation then click apply and follow the onscreen prompts. For some packages you'll need to make sure you have the repositories enabled but once these are enable - e.g. medibuntu then you should be ok. This method will apply for a lot of programs/packages you need. Hope this helps.

Mark

---

### Post by lidex on 2010-02-23
```
sudo ./NVIDIA-Linux-x86_64-190.53-pkg2.run
``` is what I got. Syntax needs to be exact, including case. I downloaded it just to see the filename, double-check yours.

---

### Post by JiuJitsu500 on 2010-02-23
OOPS, nevermind.... I don't know how to delete my own posts or I'd get rid of this one :)

---

### Post by !!?? on 2010-02-23
> **lidex said:**
> ```
sudo ./NVIDIA-Linux-x86_64-190.53-pkg2.run
``` is what I got. Syntax needs to be exact, including case. I downloaded it just to see the filename, double-check yours.

Oh that is because I changed the file name to see if that would work. I just tried it again after re-downloading, and it still doesn't work. I still get the "command not found error". Maybe I should try another directory like documents, for example?

---

### Post by !!?? on 2010-02-23
edit: Nevermind I fixed the new problem I got. Still need help with drivers.

---

### Post by Swagman on 2010-02-23
To reduce the chance of speelin errors always copy & paste into the terminal.

---

### Post by hithisisatempaccount1532 on 2010-02-23
> **sau99ms said:**
> I'm a newbie too and try to avoid using the terminal unless necessary! You can install packages without using the terminal...go to Administration - > Synaptic and search for the packages you need and mark for installation then click apply and follow the onscreen prompts. For some packages you'll need to make sure you have the repositories enabled but once these are enable - e.g. medibuntu then you should be ok. This method will apply for a lot of programs/packages you need. Hope this helps.
 
Mark
 Avoiding the terminal in any Linux OS is like trying not to breathe... it's just impossible.

You should try to become as familiar with the terminal as best you can, it will work greatly towards your benifit.

---

### Post by nerdy_kid on 2010-02-23
```

chmod +x ./NVIDIA-Linux-x86_64-190.53-pkg2.run
sudo ./NVIDIA-Linux-x86_64-190.53-pkg2.run

```
:D

---

### Post by nerdy_kid on 2010-02-23
> **hithisisatempaccount1532 said:**
> Avoiding the terminal in any Linux OS is like trying not to breathe... it's just impossible.


i would politely disagree with this; the terminal can be avoided from day to day use, but here in the forums giving commands is way easier then using the point and click method.  I personally like using the terminal just as much as the GUI, because it does work for my benefit, and gets things done faster.

---

### Post by !!?? on 2010-02-23
> **Swagman said:**
> To reduce the chance of speelin errors always copy & paste into the terminal.

I'm not certain, but I don't think I am using terminal to install this, and you can't copy and paste. It is a black screen with text.

---

### Post by !!?? on 2010-02-23
> **nerdy_kid said:**
> ```

chmod +x ./NVIDIA-Linux-x86_64-190.53-pkg2.run
sudo ./NVIDIA-Linux-x86_64-190.53-pkg2.run

```
:D

Alright I tried that. It worked, but it didn't work. :D I got two error messages. 

>  You appear to be running xserver, exit x before installing. 

and then

>  Installation has failed, please see the file rar/log/nvidia-installer for details. 

---

### Post by nerdy_kid on 2010-02-23
> **!!?? said:**
> Alright I tried that. It worked, but it didn't work. :D I got two error messages. 


```

sudo service gdm stop

```

if it still refuses to work, then do

```

sudo killall gdm

```

good luck! :)

---

### Post by clash101 on 2010-02-23
> **!!?? said:**
> I'm not certain, but I don't think I am using terminal to install this, and you can't copy and paste. It is a black screen with text.

To paste: CTRL+SHIFT+v

"CTRL+v" alone doesn't work in Terminal. Took me a bit of getting used to...

---

### Post by !!?? on 2010-02-23
> **nerdy_kid said:**
> 

if it still refuses to work, then do



good luck! :)

Alright that worked, thank you very much! :D

---

### Post by nerdy_kid on 2010-02-23
> **!!?? said:**
> Alright that worked, thank you very much! :D

no prob!

---

