---
title: "KDE... do I?"
date: 2010-06-16
forum: General Help
---

### Post by DMustaine on 2010-06-16
Sorry, I tried to post this in the Beginner forum, but I don't have access or permissions to do that.

Anyway here's the background:
I am totally new to Ubuntu, been using for about a month. I'm and IT admin but only know M$ systems. I've made my way around, and made a decent install finally. I asked for help before:[http://ubuntuforums.org/showthread.php?t=1493449](http://ubuntuforums.org/showthread.php?t=1493449) and the community was great. 

So now I have a new set-up. I am running a dual-boot with Windows 7 and Ubuntu 9.10 on a Dell Vostro 1510 and everything works just perfect. I have to use Windows for work purposes, but plan on using Ubuntu as my main OS for the foreseeable future.

Since I am SO new to Ubuntu I have read as much as I can. I have almost everything I would like working, except a decent music player. I have read, and been told Amarok is the best option (I'm used to WinAmp). I also see it is KDE based.

I've tried to read a bit about KDE, but most of what I have seen isn't straight forward and in plain words a Windows layman can understand. An example is a topic I saw here where someone booted to KDE instead of Gnome... 

That threw me for a curve. right now it is IMPERATIVE I can boot to Windows, or Ubuntu. When Grub loads I get the selection and I'm fine with how it works.

If I follow the guide here:[https://help.ubuntu.com/community/InstallingKDE](https://help.ubuntu.com/community/InstallingKDE)
and install the "kubuntu-desktop" will that effect how my system boots, and operates?

I know it is a beginner question, but as I stated I am not allowed to post there for some reason.

Thanks a ton in advance!

---

### Post by wojox on 2010-06-16
Well if you just want to install Amarok you can do so with out installing all of kde.

If you want to give kde a spin then follow that guide and install it and when you reboot and get to the login screen choose options > kde. Follow this guide instead [How to install KDE on Ubuntu]("http://www.psychocats.net/ubuntu/kde")

This is just a different Desktop Environment, so it won't mess with anything else. You'll be fine. :p

---

### Post by DMustaine on 2010-06-16
Thank you, but I have a dilemma... and most of you here will probably give me grief.


I installed Ubuntu and choose not to use a login as this is my own laptop, I never really bring it anywhere but work and home.

since I never see a login page will I still see an option for KDE?

---

### Post by howefield on 2010-06-16
> **DMustaine said:**
> since I never see a login page will I still see an option for KDE?

If you don't, you'll can change the settings in System > Administration > Login Screen, so that you do.

---

### Post by DMustaine on 2010-06-16
> **wojox said:**
> Well if you just want to install Amarok you can do so with out installing all of kde.

If you want to give kde a spin then follow that guide and install it and when you reboot and get to the login screen choose options > kde. Follow this guide instead [How to install KDE on Ubuntu]("http://www.psychocats.net/ubuntu/kde")

This is just a different Desktop Environment, so it won't mess with anything else. You'll be fine. :p


OK you sold me, but hmm...

[B][IMG]http://i195.photobucket.com/albums/z125/JB73Mustaine/Screenshot-UbuntuSoftwareCenter.png[/IMG]

**but there's no **[/B]*"Kubuntu Plasma Desktop system*[B]" following that guide. Yes I did refresh too.

[/B]

---

### Post by wojox on 2010-06-16
Maybe they changed it again? Try from your terminal:

```
sudo apt-get update; sudo apt-get install kubuntu-desktop
```

---

### Post by ubunterooster on 2010-06-16
> **DMustaine said:**
> Thank you, but I have a dilemma... and most of  you here will probably give me grief.


I installed Ubuntu and choose not to use a login as this is my own  laptop, I never really bring it anywhere but work and home.

since I never see a login page will I still see an option for  KDE?
click on the "log out" button. When you click the name to log back in,  there will be a box at the bottom labeled "sessions" 
Choose KDE (or Kubuntu if it shows that)

---

### Post by DMustaine on 2010-06-16
I was going to ask, in synaptic package manager there is "kubuntu desktop system" but I wasn't sure it was the same thing.

thanks!

<EDIT> can I mark this topic as solved some how?

---

### Post by wojox on 2010-06-16
> **DMustaine said:**
> I was going to ask, in synaptic package manager there is "kubuntu desktop system" but I wasn't sure it was the same thing.

thanks!

Yeah, it's the same.

---

### Post by ubunterooster on 2010-06-16
> **DMustaine said:**
> I was going to ask, in synaptic package manager there is "kubuntu desktop system" but I wasn't sure it was the same thing.

thanks!

<EDIT> can I mark this topic as solved some how?
Click on thread tools "mark as solved"

---

### Post by DMustaine on 2010-06-16
BTW MAN I love Ubuntu, even on wireless G I'm pulling 1074kb download of the files! 
:D <1 minute remaining, 600mb or so I think was the start

---

### Post by ssri on 2010-06-18
> **DMustaine said:**
> I have read, and been told Amarok is the best option (I'm used to WinAmp). I also see it is KDE based.
I know it is a beginner question, but as I stated I am not allowed to post there for some reason.

Thanks a ton in advance!

First things first: amarok2 is an abomination of a music player, this coming from a KDE fan who has tried to live with it for the past two months (2.3.0 & 2.3.1).  There are better options out there like banshee (full featured music manager) or deadbeef (if you like foobar2000).  I still think amarok 1.4.10 is the best music manager out there even though it has been depreciated :(.  Good luck!

---

### Post by DMustaine on 2010-06-21
> **ssri said:**
> First things first: amarok2 is an abomination of a music player, this coming from a KDE fan who has tried to live with it for the past two months (2.3.0 & 2.3.1).  There are better options out there like banshee (full featured music manager) or deadbeef (if you like foobar2000).  I still think amarok 1.4.10 is the best music manager out there even though it has been depreciated :(.  Good luck!

I'll tell you this, the whole KDE thing is mystifying.

I installed all the options as described in the walk-through... I have a login screen now, but nothing has changed on my desktop, and there are no new features, or layouts.

and Amarok... well it sucks. I have a mapped NAS drive, I can browse to it, rhythmbox can read the files, and play the songs. Amarok can't see it, can cant play anything unless it is locally stored as far as I can see.

Even with local files I can't find an EQ or anything like that. I'd love to find something like winamp, but I guess I'll just have to use Windows to play media.

---

