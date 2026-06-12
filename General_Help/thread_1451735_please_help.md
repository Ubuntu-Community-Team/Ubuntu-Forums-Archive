---
title: "please help"
date: 2010-04-10
forum: General Help
---

### Post by warthance on 2010-04-10
hi, i am new to linux all together. i just installed the ubuntu 9.10 on my system. well i think i used the wrong version...i have a amd 64 bit system. also after the install and i choose the os i want to boot, it ask for my username and password, then it says im logged in. i cant see anything except a screen full of writing and the last character looks like "$" sorta, i guess. but it never takes me to the desktop...anyone know what i am supposed to do. and can someone please tell me how and where to get the 64 bit version and should i do a fresh install or just upgrade it to the 64 bit...sorry for all the newbie questions. this is my first day with it and i need to learn all i can because i will soon be starting class about the unix environment. and soon i mean next spring. thank you in advance. oh and i guess i should mention that i am duel booting with windows 7. and in all the text that shows after i imput my username and password it tells me i have over 200 udates and 100 are system? not sure what to do with that either

---

### Post by RedSingularity on 2010-04-11
So your stuck at a text interface screen?

As for the download look [here]("http://www.ubuntu.com/getubuntu/download#") for the 64 bit system.

Select "Alternative download options" and pick a 64 bit system.

---

### Post by warthance on 2010-04-11
yes thats where im stuck...it ask for login name and password, it tells me the last time i logged in, tells me i have 251 updates and that 100 of them are security then a few more lines and it ends with ~$ _  i have no idea what to do after that...i just figured after i gave login name and password it would take me to the desktop so i could get started in learning all of this

---

### Post by Sin@Sin-Sacrifice on 2010-04-11
After you log in type ```
startx
``` and press enter. Then let us know what happens.

---

### Post by warthance on 2010-04-11
will give it a try thank you very much, as soon as i do it i will let you know if it worked or what exactly happened

---

### Post by warthance on 2010-04-11
ok...when the ~$ prompt came up i typed startx and then pressed enter. a really long list of stuff came up sayin alot about "x" directory doesn't exsist, or something like that, it said i should visit the x.org page for possible solutions. i dont know what to do anymore. i really need to get this working so i can start working on learning how it works and how to use it before i start the class on it. i even went as far as logging back into windows 7 and completely removing the partition and all, downloading the 64bit livecd and starting over....same exact problem. any other magic tricks you might have up your sleeve?

---

### Post by 3rdalbum on 2010-04-11
Try:

```
sudo service gdm start
```

The "startx" command is simply inappropriate.

Usually Ubuntu should go straight to the graphical login screen and then to the desktop, I don't know why it isn't.

---

### Post by RedSingularity on 2010-04-11
> **3rdalbum said:**
> Try:

```
sudo service gdm start
```The "startx" command is simply inappropriate.

Usually Ubuntu should go straight to the graphical login screen and then to the desktop, I don't know why it isn't.

I have used startx in the past with success though.

---

### Post by warthance on 2010-04-11
ok...i tried " sudo service gdm start" it then asked me for my password again. i typed my password and a few lines came up basically saying that ive logged in as root. then it goes right back to the last thing it displayed before with the last thing showing is ~$_ any ideas? ive even tried going back in windows and deleting the ubuntu partition and starting from scratch...same thing with the same tries = same results everytime. i am soooo lost as to why it wont boot up to the desktop at all. thank you to all that has given me ideas to try. thank you in advance to the advice still to come.

 not sure if it helps but the exact 2 lines i get when i tried that code are:
gdm start/running,process 2310
warthance@warthance-desktop:~$


 also not sure if this helps or changes anything, i have a 1TB HDD which i have had windows 7 installed on now for a few months. its all on the HDD with no partition. when installing ubuntu, the partitioner partitions the HDD to install ubuntu and then it installs. i get a crash notice about 6 times at the very beginning of the install and when it takes me to the bug site, it seems to be something that doesn't affect the install. then when it stops all of that it says i have to activate a driver for my video card and i do, it tells me that i have to reboot before the driver is actually activated but at this time im in the middle of the install so i just finish the install...after that, never see the ubuntu desktop again. is ubuntu right for me or should i be looking into some other version of linux? i chose ubuntu because i wanna learn how to use a linux os easily and it seems to be the #1 choice for beginners as well as seasoned vets. one more thing, while installing it ask me if i want to import doc and settings and gives the option to do so from my windows 7 partition and when i choose it and click continue when it makes it to the point of importing...it sits for hours without moving forward...not sure if it can even be done. i try it because i would like to import my music library so that i dont have to figure out how to download and install a program such as utorrent. but just to get it installed i choose the option of not importing

---

### Post by warthance on 2010-04-11
i am getting the exact same issue with the 32bit and 64 bit ubuntu installed

---

### Post by Sef on 2010-04-12
What are your system specs, especially your graphics card.  It seems that is where the problem lies.

---

### Post by warthance on 2010-04-12
my video card is a radeon hd4890...not sure how to get the rest of the stats...i do have 4g of memory,

---

### Post by JoelOl75 on 2010-04-12
try cat /var/log/Xorg.0.log | less

Or load up /var/log/Xorg.0.log in your favorite text editor and check - Lines Starting with (EE) are errors.  I Believe there is no /etc/X11/Xorg.conf file anymore so It should auto-configure but it sounds like it's choking.  If you are using an NVidia or ATI card make sure to install the appropriate package for it.  You can also toss in a generic Xorg.conf using the vesa driver just to get the desktop up so you can configure/grab restricted packages/drivers from there.

---

### Post by ikacer on 2010-04-12
The $ sign you are getting is the bash prompt. Basically, your computer seems to be starting up fine except for xorg, which is used for running GUI interfaces.

> **warthance said:**
> my video card is a radeon hd4890...not sure how to get the rest of the stats...i do have 4g of memory,

if you type ```
lspci | grep VGA
``` in the bash prompt, you will get info on your graphics card. (FYI, the lspci program can be used to list any connected devices)


Also, a quick google search led me to this this bug report:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/361596]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/361596")

It looks like it has to do with the ati driver being used. To find out which video driver you are currently using type: ```
lspci -v
``` and scroll up to the VGA section (use Shift+PgUp, Shift+PgDn to scroll in the console). It should list the driver in use. Report back what it is.

After that you can try a different driver.

\\ edit:
as the bug report says, the newer version of the ati driver which supports your card is included in ubuntu 10.04. You could install that instead. A page with release info and download links: [https://wiki.ubuntu.com/LucidReleaseSchedule]("https://wiki.ubuntu.com/LucidReleaseSchedule")

---

### Post by warthance on 2010-04-12
ok, lol you guys totally lost me. when i log in and it stays in the text page it tells me i have 251 update packages and 100 of them are security. not sure how to install or even download any packages, drivers or what not while still in the text screen...if i could get to the desktop im sure id be able to download and install them. while installing the os it comes up with something about activating the driver for my ati video card and then after downloading and installing that driver it says i have to reboot...after the reboot is when i can no longer get to the desktop

---

### Post by warthance on 2010-04-12
ok, i am sooo lost. i ran the cat /var/log/Xorg.0.log |less in the bash prompt and got a reallly long sting of stuff and the only [EE] things where: failed to load module "fglrx" (module does not exist,0)
                                                       : no drivers available
my thing is...i think i have to get all these drivers and install them but how am i supposed to do this without being able to get to the desktop to do so?

---

### Post by warthance on 2010-04-12
anyone know what i can do to download and install the drivers and such that i need to get to my desktop? should i try deleting the partition in windows so that i delete ubuntu and start all over but this time start by partitioning my hdd myself? if so how do i get grub off my pc...when i have tried this before i couldnt get to my windows 7 os because grub was wanting to load but grub wasnt there (if that makes any sense)

---

### Post by warthance on 2010-04-12
i tried  lspci -v  but when i needed to scrool up to see the video card info...i could only page up so far before it wouldnt go any further so i couldnt get up there enought to see the info :-(

---

### Post by ikacer on 2010-04-13
> **warthance said:**
> anyone know what i can do to download and install the drivers and such that i need to get to my desktop? should i try deleting the partition in windows so that i delete ubuntu and start all over but this time start by partitioning my hdd myself? if so how do i get grub off my pc...when i have tried this before i couldnt get to my windows 7 os because grub was wanting to load but grub wasnt there (if that makes any sense)

I'll try to be a bit more clear: the problem seems to be that the driver distributed with Ubuntu 9.10 doesn't support your graphics card. Newer versions of said driver do however. You can either update your graphics driver, or alternatively, install Ubuntu 10.04 which should come with a working version of the driver.  10.04 is currently in beta and can be downloaded *[here]("http://www.ubuntu.com/testing/lucid/beta2")*. Installing 10.04 is probably your easiest option.

If you want to stick with 9.10 however, you will need to update your graphics driver. This can be done with either apt-get or aptitude. Both programs are well documented.

gl

---

### Post by 3rdalbum on 2010-04-13
> **warthance said:**
> ok, i am sooo lost. i ran the cat /var/log/Xorg.0.log |less in the bash prompt and got a reallly long sting of stuff and the only [EE] things where: failed to load module "fglrx" (module does not exist,0)

That's interesting. Are you saying that you're using the Hardware Drivers program in Ubuntu on the live CD, installing Ubuntu and then you're getting just the command prompt when you boot into the newly installed system?

That shouldn't happen.

> i think i have to get all these drivers and install them but how am i supposed to do this without being able to get to the desktop to do so?

Ubuntu already comes with a driver for your hardware. It's not the best driver, but it's the one that works on the live CD. It's the default ATI driver.

What you'll probably have to do is this. Type:

```
sudo nano /etc/X11/xorg.conf
```

Type in your password and hit Enter. There's a section of the file that says Driver       "fglrx"

Change this to read Driver       "ati"

Hit Control-X and then the Y key and Enter to quit Nano and save your changes, then type:

```
sudo reboot
```

---

### Post by zengzhangsong on 2010-04-13
You don't have installed the x-window,i suggest you to install the Ubuntu-desktop!Then everything is OK!

---

### Post by 3rdalbum on 2010-04-13
> **zengzhangsong said:**
> You don't have installed the x-window,i suggest you to install the Ubuntu-desktop!Then everything is OK!

He already has X and the ubuntu-desktop package. He did the install from the live CD which means he has the desktop. Your suggestion only applies if he'd installed Ubuntu Server.

---

### Post by f1r3flie on 2010-04-13
What happens when you try the "Try Ubuntu With No Effect On Your Computer" option when you boot off the LiveCD? If that has the same result, you may want to check that you have a valid, undamaged disk. You can do this by checking the checksum of the disk on Windows (How to do it shown [here]("http://www.linuxfortravelers.com/check-the-ubuntu-file-for-errors")). If the checksums match, you have a valid disk and this is not the problem. If not, then you need to get a new disk that is valid.

Good luck with your problem. :)

---

### Post by trig on 2010-04-13
I was always told  that it is a bad ripp of the cd, and to make a new one.

---

### Post by warthance on 2010-04-13
Try Ubuntu With No Effect On Your Computer, when i do this everything works fine and it takes me to the desktop. its just when i reboot that i can no longer see any kind of graphix at all

---

