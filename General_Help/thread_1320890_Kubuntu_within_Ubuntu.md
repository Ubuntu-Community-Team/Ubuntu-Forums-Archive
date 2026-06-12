---
title: "Kubuntu within Ubuntu"
date: 2009-11-09
forum: General Help
---

### Post by arnab_das on 2009-11-09
i had always wanted to do this, but never mustered enough courage to go for the kill.

anyway, today i installed kubuntu within the ubuntu installation. what i did was type sudo apt-get install kubuntu-desktop and all the files were downloaded and installation proceeded without a glitch.

however when i started using kubuntu, the practical probs of using one ditro within another became all the more apparent. first up, kubuntu showed ALL the ubuntu apps which i had installed. and worst of all, it even had the ubuntu software store and synaptic. now, i'll admit that i'm not exactly used to KDE (although i like it better than GNOME), so i had to figure out how to install the softwares, from the kubuntu synaptic or from the ubuntu one.

the other problem which i faced was with AWN. the thing is, with ubuntu i can add replace the panel to the top of the screen while Avant runs in the bottom portion. however with kubuntu, moving the panel to the top meant losing out on the charm of KDE. (well thats a personal view :) ) the thing is, startup apps were the same for both the OSes. so basically Kubuntu started with the same apps Ubuntu would start with. so now, i had this awesome looking KDE interface with the AWN dock overlapping the bottom panel. :( i tried to remove it from the startup app but then i simply gave up coz it was affecting how AWN was loading in Ubuntu.

Finally, I decided that maybe trying kubuntu within ubuntu isnt really such a smart thing to do. More so, since i had some sort of a hard time removing Kubuntu! Apparently, sudo apt-get purge kubuntu-desktop doesnt do the job! i had to use the link here ( [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome) ) to delete the entire KDE pack.

then again i had to re install all the KDE apps i was using, K3b, Kid3 etc. but to my surprise i also found, even vlc, devede, miro etc. had also been removed. :( took me another half an hour to search for and reinstall all that was lost. finally, i ran sudo apt-get install ubuntu-desktop from the terminal just to be sure i had reinstalled the main thing.

so, i guess to all those people who want to give kubuntu a try, here's a tip: try out the Live CD, or install Kubuntu from Virtualbox, or better still...do a fresh install. coz running kubuntu within ubuntu isnt really something which is going to impress you.

---

### Post by ranch hand on 2009-11-09
Or do a clean install from CD using the same /home for both.  Make sure that you use a different user name for each install or your config stuff on the /home partition will get mixed.

You probably need about an extra 10G for the additional / partition.

---

### Post by kyuubi777 on 2009-11-09
i did the same thing on my 9.04 partition... it's a blast- have had none of those problems w/ disappearing apps as u describe.

---

### Post by egalvan on 2009-11-09
> **arnab_das said:**
> i had always wanted to do this, but never mustered enough courage to go for the kill.

Lots and lots of folks have done this, using xubuntu, kubuntu and others.

> 
anyway,  so i had to figure out how to install the softwares, from the kubuntu synaptic or from the ubuntu one.


All Ubuntu software uses the same repositories, 
doesn't matter if it's Gnome or KDE or xfce.
Or Desktop or Server.
There are no separate repos for each.
Fire up Synaptic, pick your package, and install. Simple.
( or use apt-get )

> 
the other problem which i faced was with AWN. , with ubuntu i can add replace the panel to the top of the screen while Avant runs in the bottom portion. however with kubuntu, moving the panel to the top meant losing out on the charm of KDE. (well thats a personal view :) ) , startup apps were the same for both the OSes. Kubuntu started with the same apps Ubuntu would start with. , i had this awesome looking KDE interface with the AWN dock overlapping the bottom panel. :( i tried to remove it from the startup app but then i simply gave up coz it was affecting how AWN was loading in Ubuntu.


can't comment on this 'cause I don't use it.
But I believe it may be possible to separate the startup apps based on the DE that is started.


> 
so, i guess to all those people who want to give kubuntu a try, here's a tip: try out the Live CD, or install Kubuntu from Virtualbox, or better still...do a fresh install.** coz running kubuntu within ubuntu isnt really something which is going to impress you.**

Well, you don't really run Kubuntu "within"  Ubuntu.
It's more "side-by-side",
and yes, the menus can get messy,
but I don't mind,
'cause it is such a neat thing to be able to pick my Desktop at boot.
Gnome
KDE
xfce

Another option is to install it as a separate install on the hard drive, or as the OP pointed out, as a Virtual Machine.

---

### Post by arnab_das on 2009-11-09
well then again, installing it afresh means formatiing my entire hard drive coz ubuntu is consuming every bit of it.

also, virtual os wont recognise my graphics cards etc. so kubuntu's main attraction would be gone. :(

pretty much stuck here. i'll try and get used to kde by using the live cd as of now. and maybe by the time 10.04 comes out, i'll move to kde.

---

### Post by Ms_Angel_D on 2009-11-09
Using kde and gnome together can be quite a messy affair as far as menuing goes, also another thing I noticed when I did it is that any time you put shortcuts in the desktop folder, then try to log back into gnome it doesn't show proper icons in gnome.

I finally just said forget it and went full kubuntu. It was a bit intimidating at first, but once I got into checking things out (settings and such) I really fell in love with it. I have kubuntu installed on both mine and my husbands pc's, as well as on my laptop. 

I first installed kubuntu using jaunty, and their we're a few issues and quirks I had to work out with my sound, but that all changed with Karmic, it installed perfectly and has worked great from the start. Even my sound issues we're null and void.

I highly recommend trying dual boot with both until you get used to how Kubuntu works.

---

### Post by arnab_das on 2009-11-09
yea will have to do that. i guess kubuntu is headed for greater heights. read about project timelord today. sounds really promising.

[http://www.kubuntu.org/news/timelord](http://www.kubuntu.org/news/timelord)

---

