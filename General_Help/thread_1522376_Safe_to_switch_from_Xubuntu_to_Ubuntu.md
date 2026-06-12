---
title: "Safe to switch from Xubuntu to Ubuntu?"
date: 2010-07-02
forum: General Help
---

### Post by SmokeyThePanda on 2010-07-02
Alright, here's the story. I've been with Linux since a bit before Karmic came out. I have always used Xubuntu because of my system. (Only 256MB RAM) However, I have also always used the gnome desktop. I prefer it over xfce because it is more customizable and it just seems to run faster. So, basically, I have always had Xubuntu with the Gnome desktop as well as the Xfce desktop, I guess they are actually called Xubuntu-desktop and Ubuntu-desktop. Just a note, the ubuntu/gnome environment has always ran fine. It doesn't run slow or anything. In fact, it seems faster than Xfce.

My quarrel is this: I wish to completely remove the Xubuntu-desktop for the first time ever. In doing this, I assume I would be left with only Gnome. However, I am not sure how this will affect my system, for I started with the Xubuntu install..

As a secondary question, is there a real reason to do this? What exactly will it change? I have searched up on the internet, looking at the hundreds of sites and I have read several that say you can use *sudo apt-get remove xubuntu-desktop* and *sudo apt-get install gnome-desktop-environment* (formerly ubuntu-desktop?) to create the effect I desire. However, as stated in my main question/dilemma, I am not sure how safe this is considering I started with Xubuntu.

I am currently using Xubuntu 9.10 (I refuse to upgrade to Lucid Lynx again, it's ugly >.>) I am not entirely sure how to find out about my system specs and whatnot, if you need them, tell me how to find them, please.

---

### Post by kerry_s on 2010-07-02
your talking meta-packages here, for example removing xubuntu-desktop actually removes nothing but the package that has the list of things to install.

so to remove xfce4 you need to remove all the xfce4-* stuff.

synaptic is your best tool here, it will tell you if your removing something important.

---

### Post by 4Orbs on 2010-07-02
Theoretically, there should be no problems... but reality slapped me in the face when I did exactly what you are suggesting. When I removed the xubuntu desktop, my system was transformed into mud. Spent two days attempting to troubleshoot the problems and finally admitted defeat, then did a new installation of Ubuntu, which worked perfectly but had a slightly different feel from my previous setup of xubuntu + gnome. I have since abandoned gnome and now use only xubuntu Lucid. Xfce has been my favorite for three years, although I have also enjoyed KDE and Gnome at other times. Still, I suggest just removing xfce and see if you have any problems.

---

### Post by SmokeyThePanda on 2010-07-02
I see..Thank for you for the replies. I'll try removing the packages via synaptic, if things go wrong, I have a backup cd :) 

I've also thought about setting up a clean minimal ubuntu install..But I'm not sure if it would still require the RAM that a normal install does. I'm also not entirely sure how to do so.

---

### Post by kerry_s on 2010-07-02
have you tried lubuntu?
[http://lubuntu.net/blog/lubuntu-1004-now-available-download](http://lubuntu.net/blog/lubuntu-1004-now-available-download)

i'm running it on 450mhz 256mb ram.

it is 10.04 though, which you say gave problems. lubuntu does run live so you can try it first, keep in mine it is slower when running live on 256mb ram.

---

### Post by SmokeyThePanda on 2010-07-02
What's ludbuntu use? Like, window managers and the like and how is it different from ubuntu and xubuntu?

---

### Post by SmokeyThePanda on 2010-07-02
Alright, so far, I believe I have removed every xfce package from synaptic. I just have to run the autoremove, autoclean, etc.

---

### Post by Lucifer The Dark on 2010-07-02
Probably too late now but wouldn't it be better to install Gnome before you remove xfce?

---

### Post by kerry_s on 2010-07-02
> **SmokeyThePanda said:**
> What's ludbuntu use? Like, window managers and the like and how is it different from ubuntu and xubuntu?

lubuntu uses lxde, it's lighter then xfce4, not as easy as gnome.
give it a google, check out some reviews, pics.

---

### Post by SmokeyThePanda on 2010-07-02
> **Lucifer The Dark said:**
> Probably too late now but wouldn't it be better to install Gnome before you remove xfce?

I already had gnome installed. In fact, It was the first thing I installed after my clean install. :p

---

### Post by SmokeyThePanda on 2010-07-02
> **kerry_s said:**
> lubuntu uses lxde, it's lighter then xfce4, not as easy as gnome.
give it a google, check out some reviews, pics.

Alright, I'll check it out. I've tried a few other window mangers and didn't really like them though :p Like, IceWM, FVWM, FVWM-Crystal, etc.

---

### Post by Lucifer The Dark on 2010-07-02
> **SmokeyThePanda said:**
> I already had gnome installed. In fact, It was the first thing I installed after my clean install. :pSomehow I missed that important fact in your opening post, it's there too cause I just found it when I re-read it.

---

### Post by SmokeyThePanda on 2010-07-02
Lol. 

Hmm..So far, the switch seems decent, except that when I first switched over, I had a language package error. I installed the proper language packages using the gui program that popped up. It popped up on the subsequent boot as well. >.> Any ideas?

---

### Post by SmokeyThePanda on 2010-07-02
Just an update. Whoever it was up a bit that said it would make my computer run like mud, you weren't lying. :p I have decided to try out lubuntu. I'm currently downloading the .iso for it.

---

### Post by SmokeyThePanda on 2010-07-03
Alright, for anyone that looks at this thread in the future, Lubuntu wasn't in my tastes. It didn't seem all that fast and it has too many bugs currently. Perhaps it will grow. As for my solution, I downloaded and burned a Karmic Koala mini.iso and installed a base ubuntu system on my computer using the command line. Then, instead of running the command to install a system, I simply installed a few basic things needed for a lightweight desktop and a few programs that I liked. 

[I]sudo apt-get install xorg xfce4 gdm synaptic
[/I]
On my internet connection, this took about 40-50 minutes to install and setup. After it was done, I ran:

*sudo apt-get install firefox gimp mousepad* gthumb xchat

After this, I ran: *startx*

When it started up, I installed the flash-nonfree packages so that I could watch videos in firefox.

I then had to edit my xorg.conf file to fit my monitor needs to get the right resolution.
```

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    HorizSync     30 - 60
    VertRefresh   60 - 75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Configured Video Device"
    Monitor       "Generic Monitor"
    DefaultDepth   16
    SubSection "Display"
        Depth        16
        Modes      "1024x768"  "800x600"  "640x480"
    EndSubSection
EndSection
```I then installed localepurge and deborphan via terminal to clean my system. 

[I]sudo apt-get install localepurge deborphan

[/I]After they finished I ran the commands:

[I]sudo apt-get autoremove
sudo apt-get autoclean
localepurge
deborphan
[/I]
Then I opened synaptic and checked for residual packages, and completely removed them if there were any.

Then I found an awesome theme online that I liked (Even though it's a linux mint theme :p). 

This system is at least 3-4X faster than a normal Xubuntu install and there are no meta packages. Thus, you can remove xfce and install the gnome window manager or run them side by side if you wish.

I have only 705 packages installed, compared to the several thousand that install on a normal xubuntu install. I've also limited my amount of directories by having less programs. I have all of the programs I need to do what I like to do, and if I find something I need/want, I add it. 

For anyone with a low-end computer, this is the way to go. Everything is fast. I do not particularly *like* xfce, but it's fast and with a good theme, it looks decent.

Good luck to anyone that reads this article in the future! :)

Btw, here is what my desktop looked like in gnome: 

[[IMG]http://i669.photobucket.com/albums/vv59/JUhles/th_Sexeh.png[/IMG]](http://s669.photobucket.com/albums/vv59/JUhles/?action=view&current=Sexeh.png)

Here is what my desktop looks like now:

[[IMG]http://i669.photobucket.com/albums/vv59/JUhles/th_Desktop.png[/IMG]](http://s669.photobucket.com/albums/vv59/JUhles/?action=view&current=Desktop.png)

---

