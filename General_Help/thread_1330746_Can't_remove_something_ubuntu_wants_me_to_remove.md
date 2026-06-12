---
title: "Can't remove something ubuntu wants me to remove"
date: 2009-11-18
forum: General Help
---

### Post by Vistro on 2009-11-18
I was on a friend's computer, and I tried to install Flash. I clicked Open File (as opposed to Save File), and it ran. Videos still would not play. So I tried reinstalling the package, and it said something like "Can't do this, it needs to be reinstalled but I could not find a package"

So I tried updating the machine. Same error, but it pointed out adobe-flashplugin as the problem. Same thing with sudo apt-get remove adobe-flashplugin. 

WTF? Why does it need to reinstall something to remove it? I can't update the machine, can't open Synaptic, I can't install new programs, without removing Flash, which it won't let me do until I reinstall it, which it won't let me do until I remove it.

It says it can't find an archive. Where do I put said archive? Is the archive a .deb file?

---

### Post by julianb on 2009-11-18
When it says it can't find an archive, it's possibly saying:

a desired line is missing from the file
/etc/apt/sources.list
...the file which lists the internet-based archives your machine uses to get new software and updates.

...
or an expected file in one of the archives wasn't found.

It looks like you tried to reinstall from the .deb file you originally used to install Flash. If you haven't, then try that. Have you checked to see what happens if you
```
sudo apt-get install adobe-flashplugin
```
```
sudo apt-get -f install
``` 

looks like you're saying these commands fail:

```
sudo apt-get update
sudo apt-get upgrade
```

but if I'm misreading, and you haven't tried them... then do try them (in that order).

---

### Post by Vistro on 2009-11-18
All of those come back with 

E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.

apt-get anything won't run. How do I blow up that package short of reinstalling the OS?

---

### Post by slakkie on 2009-11-20
See my sig :)

---

### Post by bodhi.zazen on 2009-11-20
```
sudo dpkg --remove --force-remove-reinstreq adobe-flashplugin
```

---

### Post by zigzagg321 on 2009-11-20
> **slakkie said:**
> See my sig :)

Brand new user here, I have that exact issue: 
E: The package adobe-flashplugin needs to be reinstalled, but I can't
find an archive for it.
E: Internal error opening cache (1). Please report.

[FONT=Verdana]You mentioned...[/FONT]
"To add the partner repository, take your favorite editor and add the following line to */etc/apt/sources.list*, you need to be root to edit the sources.list file."


Probably a n00b question...but...



How do I get to [I]/etc/apt/sources.list to add :
[/I]"deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) KARMIC partner" ?  

you mentioned I need to be in the "root."  I found the "root" folder in the filesystem, but access is denied, saying I dont have the permissions to access this folder.  I am the admin for this machine and the system isnt even prompting for a PW, but I may be in the wrong place anyhow. 

> **bodhi.zazen said:**
> ```
sudo dpkg --remove --force-remove-reinstreq adobe-flashplugin
```

I entered this in the Terminal and I got:

dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 117130 files and directories currently installed.)
Removing adobe-flashplugin ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing adobe-flashplugin (--remove):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 adobe-flashplugin

__________________________________________________________________________________
Brand new install of 9.10 BTW...also, never written/edited a line of code in my life. 

Thanks for any help.

---

### Post by bodhi.zazen on 2009-11-20
adobe-flashplugin shoud now be removed.

It sounds as if your system may not be is such a healthy state.

what happens when you:

```
sudo apt-get install -f
```

---

### Post by zigzagg321 on 2009-11-21
> **bodhi.zazen said:**
> adobe-flashplugin shoud now be removed.

It sounds as if your system may not be is such a healthy state.

what happens when you:

```
sudo apt-get install -f
```


result:

zigzagg321@WasADell:~$ sudo apt-get install -f
[sudo] password for zigzagg321: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
zigzagg321@WasADell:~$

---

### Post by slakkie on 2009-11-21
> **zigzagg321 said:**
> 

"To add the partner repository, take your favorite editor and add the following line to */etc/apt/sources.list*, you need to be root to edit the sources.list file."


Probably a n00b question...but...

Open a terminal and do the following:
```

# Get your current release
lsb_release -cs
# Edit the sources file
sudo nano /etc/apt/sources.list
# Copy/paste that line and replace CODENAME to the output of the lsb_release -cs command

```

You've now added the partner repo to your sources.list. Continue from here.

---

### Post by 3rdalbum on 2009-11-21
> **Vistro said:**
> I was on a friend's computer, and I tried to install Flash. I clicked Open File (as opposed to Save File), and it ran. Videos still would not play. So I tried reinstalling the package

If you install Flash and it doesn't work, then reinstalling it will not help. It's already there; replacing it with exactly the same binary will not make it work.

---

### Post by zigzagg321 on 2009-11-21
> **slakkie said:**
> Open a terminal and do the following:
```

# Get your current release
lsb_release -cs
# Edit the sources file
sudo nano /etc/apt/sources.list
# Copy/paste that line and replace CODENAME to the output of the lsb_release -cs command

```You've now added the partner repo to your sources.list. Continue from here.

So I got the current release by entering "lsb_release -cs" in a terminal.  

my result was "karmic" 

I then entered sudo nano /etc/apt/sources.list and got this:

[deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
                               [ Read 53 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell]

I copied and pasted:
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

into the terminal but I dont see a way to save it, so I closed the terminal and the system said it was "killed." Or am I supposed to be within the file system looking for 
etc/apt/sources.list file?   If so, I went there and only found etc/apt/sources.list.d and the folder is empty and I cant seem to add to it, nor do I know if I am supposed to.   


Im lost...everything is the first time for me with this stuff.

---

### Post by slakkie on 2009-11-21
@zigzagg321

When you have editted the file you should save/quit the file. ctrl-X if not mistaken.

So.

sudo nano /etc/apt/sources.list
then insert the line into the file (deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner)
Save the file (ctrl S or ctrl X)
sudo aptitude update
sudo aptitude install adobe-flashplugin

---

### Post by bodhi.zazen on 2009-11-22
You posted only a part of your repositories =)

To manage your repositories , see :

[Repositories/Ubuntu - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Repositories/Ubuntu") 

You may edit your files with gedit 

```
gksu gedit /etc/apt/sources.list
```

on on KDE kate

```
kdesu kate /etc/apt/sources.list
```

If you use nano, you need to use the arrow keys to navigate in the file with the arrow keys and paste the repos to the bottom of the file.

Personally, in reading your posts, your apt is very broken and I am not sure how to fix it. IMO you may need to re-install.

In the future take care what you install and where you install it from, Not every .deb is compatible with Ubuntu and it is rare you need to install something outside of the repos.

For flash see :

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

---

### Post by jeb800e on 2009-11-22
Maybe it is installing it for the wrong web browser. You can also just install a browser with Flash pre-installed in it, like Opera, Epiphany, or Konqueror, if no other way works for you.

---

