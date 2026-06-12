---
title: "Gnome 3 with minimal install?"
date: 2011-05-19
forum: General Help
---

### Post by wolfen69 on 2011-05-19
Does anybody know if I can do a minimal install of ubuntu and add the gnome 3 ppa to get G3? It would seem it should be possible, seeing how there wouldn't be any gnome 2 libs to conflict with. Anyone try it with success?

---

### Post by wojox on 2011-05-19
Which mini.iso version 11.04? Good question. Maybe try it in Virtualbox and see what it does.

---

### Post by wolfen69 on 2011-05-19
> **wojox said:**
> Which mini.iso version 11.04? Good question. Maybe try it in Virtualbox and see what it does.

Yeah, I'm thinking in theory, it should work fine since there will be no other DE's for it to conflict with.

---

### Post by werewolves on 2011-05-19
I swear I saw a tutorial on here on doing that exact thing, but I can't find it...

---

### Post by wolfen69 on 2011-05-19
> **werewolves said:**
> I swear I saw a tutorial on here on doing that exact thing, but I can't find it...

Here's how *I* would do it:
Using the mini iso from [here]("https://help.ubuntu.com/community/Installation/MinimalCD"), get the basic OS installed, then:
```
sudo apt-add-repository ppa:gnome3-team/gnome3 && sudo apt-get update
```
then
```
sudo apt-get install xorg
```
then
```
sudo apt-get dist-upgrade
```
then
```
sudo apt-get install gnome-shell gnome-tweak-tools
```
and after that, install whatever you like.

---

### Post by werewolves on 2011-05-19
Well, let us know how it goes man, I am interested in seeing the result.  That's basically how I used to install Debian back in the day.  Keep it clean and all.

---

### Post by wolfen69 on 2011-05-19
> **werewolves said:**
> Well, let us know how it goes man, I am interested in seeing the result.

I'll do that. I ordered another hard drive and it should be here in a day or 2. And if it goes well, I'll post a tutorial in a couple places. My friend is using G3, and I absolutely love using it. Keep your fingers crossed.
[IMG]http://caitlinscharacters.files.wordpress.com/2011/02/fingers-crossed.jpg[/IMG]

---

### Post by c-1000 on 2011-05-19
yes. i tried gnome 3 this way with the second beta (64 bit). i had to smooth out a few rough edges, but after a bit of tweaking it worked fine. if youre comfortable doing a minimal install, it shouldnt be any problem.

one thing that may save you some frustration: in a minimal install, the 'add-apt-repository' command wont work unless you install python-software-properties first.

---

### Post by Rubi1200 on 2011-05-20
I've been playing around with different configurations and desktop environments using the procedures outlined here:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

I will test it with the Gnome3 PPA and let you know what I find.

---

### Post by linuxinstalledfromhdd on 2011-05-20
Don't even bother with Gnome 3 PPA at this time.. It's not ready for prime time.  That will snafu your system for sure.  

Stick with Classic Gnome, that's your best bet for now.

---

### Post by wolfen69 on 2011-05-20
> **linuxinstalledfromhdd said:**
> Don't even bother with Gnome 3 PPA at this time.. It's not ready for prime time.  **That will snafu your system for sure.**  



That's because the current DE's don't play nice with gnome 3. But with a minimal install, there is no DE to conflict with. I believe it should work fine.

---

### Post by linuxinstalledfromhdd on 2011-05-20
If you have time to waste messing around with Gnome 3 PPA, go for it. 

I have tried it twice with two fresh nice perfect clean installs of Ubuntu.

What a pain in the neck.  No fun. 

I had to run PPA Purge from the command line in recovery mode after losing my environment completely.  Or you will be forced to install LXDE or something else just to find out how to do it if you are a newbie.

Don't mess with Gnome 3 PPA unless you have time and a spare partition with a working environment already.

---

### Post by Rubi1200 on 2011-05-20
> **wolfen69 said:**
> Here's how *I* would do it:
Using the mini iso from [here]("https://help.ubuntu.com/community/Installation/MinimalCD"), get the basic OS installed, then:
```
sudo apt-add-repository ppa:gnome3-team/gnome3 && sudo apt-get update
```then
```
sudo apt-get install xorg
```then
```
sudo apt-get dist-upgrade
```then
```
sudo apt-get install gnome-shell gnome-tweak-tools
```and after that, install whatever you like.
Tried like this and it didn't work for me, but that may also be because of my graphics card. I will keep you informed if I manage to get it up and running.

---

### Post by IanW on 2011-05-20
> **werewolves said:**
> I swear I saw a tutorial on here on doing that exact thing, but I can't find it...

[The one I used?](http://ubuntuforums.org/showpost.php?p=10818392&postcount=1)

---

### Post by werewolves on 2011-05-20
> **IanW said:**
> [The one I used?](http://ubuntuforums.org/showpost.php?p=10818392&postcount=1)

Yep!  Thank you.

---

### Post by Rubi1200 on 2011-05-20
> **IanW said:**
> [The one I used?]("http://ubuntuforums.org/showpost.php?p=10818392&postcount=1")
Thanks for sharing the link.

Tried this way and it also didn't work out for me; something about failing to log into Gnome.

I am almost certain it is a graphics issue.

Oh well, at least there is still KDE/Xfce/Lxde/Openbox/Fluxbox and a few others to play around with from a minimal install.

edit: this was done in VirtualBox; don't know if that makes a difference. Also tried Gnome3 on the recent Fedora Beta without much success either.

---

