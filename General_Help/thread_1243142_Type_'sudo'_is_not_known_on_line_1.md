---
title: "Type 'sudo' is not known on line 1"
date: 2009-08-18
forum: General Help
---

### Post by bxrx2000 on 2009-08-18
I recently reinstalled Jaunty on my desktop computer.  I have a deb package for Amarok 1.4 which I installed after removing Amarok 2.  After not being able to create a launcher or get Amarok 1.4 to run via terminal I tried the PPA listed in other threads but then the my software index failed on me.
 

 

 Software index is broken
 This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
 

 When I enter  sudo apt-get update into a terminal window I get 'E: Type 'sudo' is not known on line 1 in source list /etc/apt/sources.list.d/amarok.list ' as a response.   
 

 Any hints on how to fix this without having to reinstall Jaunty?

---

### Post by burmanabhay88 on 2009-08-18
Don't worry. Can you help you out with that.
First tell me.
If you goto System>Admin>Software Sources
It'll give an error. Post the message. K.
It's a simple problem with the sources list. happens with lots of us, esp. when playing arnd with some games.

Also...
in terminal type
> sudo gedit /etc/apt/sources.list

It should open a text editor. Paste the last 5-6 lines in the file.

---

### Post by bxrx2000 on 2009-08-18
This is the error that I'm getting when I click on the Synaptic Package Manager icon in the Notifications Area

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'sudo' is not known on line 1 in source list /etc/apt/sources.list.d/amarok.list, E:The list of sources could not be read.'



Here are all the lines after entering sudo gedit /etc/apt/sources.list

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse

This is the message I get when I open the Synaptic Package Manager 

An error occured
The following details are provided:
E: Type 'sudo' is not known on line 1 in source list /etc/apt/sources.list.d/amarok.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by jocko on 2009-08-18
As the error message tells you, there is an error in the first line of the file /etc/apt/sources.list.d/amarok.list.
Paste the output of:
```
cat /etc/apt/sources.list.d/amarok.list
```

---

### Post by bxrx2000 on 2009-08-18
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \
0x1d7e9dd033e89ba781e32a24b9f1c432ae74ae63

---

### Post by burmanabhay88 on 2009-08-18
try this
```
sudo gedit /etc/apt/sources.list.d/amarok.list
```
cut out the lines it has (i think there will be just 2 or 3), and save those lines somewhere else in a temporary file.
Save the text editor.

Logout and Login again.
And check if things are working.

If they are still not
then do the same steps with this file as well
```
sudo gedit /etc/apt/sources.list.d/amarok.list.save
```

Tell me if this works.

---

### Post by jocko on 2009-08-18
> **bxrx2000 said:**
> sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \
0x1d7e9dd033e89ba781e32a24b9f1c432ae74ae63
That's completely wrong. You must have used some faulty instructions for adding the ppa, or you did something wrong when you added it. Which instructions did you use?
There should be a line that looks something like this (but since I don't know which ppa you tried to add, I can't give you the exact line):
```
deb http://ppa.launchpad.net/[COLOR=Red]xxxxx[/COLOR]/ppa/ubuntu jaunty main
```
If you know the correct adress, edit the file and fix it:
```
gksudo gedit /etc/apt/sources.list.d/amarok.list
```repace the entire contents of the file with the correct adress (starting with "deb" and ending with "jaunty main".

---

### Post by burmanabhay88 on 2009-08-18
> **jocko said:**
> That's completely wrong.

Well its wrong all right. That's not how a source list should be.
That's why I'm taking amrok off the source list. He can reinstall it later, following the correct instructions.:KS

---

### Post by bxrx2000 on 2009-08-18
[quote=burmanabhay88;7804743]try this
```
sudo gedit /etc/apt/sources.list.d/amarok.list
```cut out the lines it has (i think there will be just 2 or 3), and save those lines somewhere else in a temporary file.
Save the text editor.

Logout and Login again.
And check if things are working.


This worked!

Thanks for the assistance!  Should I do the same for amarok.list.save as well?

---

### Post by bxrx2000 on 2009-08-18
For what it is worth, I tried Bogdan Butnaru's PPA for Amarok 1.4 but my memory is failing me as to why I couldn't get it to work.  I plan on not trying to rush things tomorrow when I'm a little more fresh.

---

### Post by burmanabhay88 on 2009-08-18
> Should I do the same for amarok.list.save as well?

naah.... if this work there's no need.
Now comes the more important part.
You messed up the installation, to be more precise, setting up of the software sources to install amrok.
Follow the instructions more carefully this time.
Glad to help!

---

### Post by burmanabhay88 on 2009-08-18
By the way? Why are you so keen on using Amarok. VLC works just fine. Any specific reason??

Also why not install Amarok from the Add-Remove Programs. It won't give you such troubles.

---

### Post by CatKiller on 2009-08-18
> **burmanabhay88 said:**
> By the way? Why are you so keen on using Amarok. VLC works just fine.

Amarok and VLC are completely different. VLC will play anything you throw at it, sure, but one at a time. Amarok plays your whole collection for you, displays artwork and lyrics, scrobbles to Last.FM. All sorts. I suggest you try it to see the differences.

---

### Post by jocko on 2009-08-19
> **CatKiller said:**
> Amarok and VLC are completely different. VLC will play anything you throw at it, sure, but [COLOR=Red]one at a time[/COLOR]. Amarok [COLOR=Red]plays your whole collection for you[/COLOR], [COLOR=Red]displays artwork[/COLOR] and lyrics, [COLOR=Red]scrobbles to Last.FM[/COLOR]. All sorts. I suggest you try it to see the differences.
VLC has most of that too... It has a playlist window with a simple built-in media library which also downloads and shows album art, it has Last.fm support + a lot more things... 
It doesn't have any silly database engine, so it doesn't use 50% of my cpu, and it probably doesn't show lyrics (at least I haven't seen any such function).
I suggest you try it to see the all the functions... But of course, as an mp3 player nothing beats audacious. It does just the things it needs to, without any silly nonsense functions (but it has a scrobbler plugin).

---

### Post by CatKiller on 2009-08-19
> **jocko said:**
> VLC has most of that too... It has a playlist window with a simple built-in media library which also downloads and shows album art, it has Last.fm support + a lot more things... 

Fair enough. I guess we both need to explore other software more then :)

---

