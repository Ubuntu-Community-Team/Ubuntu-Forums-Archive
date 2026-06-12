---
title: "error when i open package managers. can't open."
date: 2009-10-27
forum: General Help
---

### Post by ThaiboxerAD on 2009-10-27
So i had some troubles with no sound in firefox and flash and i ended up at[ http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683") I wasn't positive what i was doing but i still dove in. bad idea..
I copy and pasted this into the terminal```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```
Well now i can't open either package managers. i get an error saying 
[B]E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
[/B]
i'm pretty lost as how to correct this.
can somebody please help me. thanx

---

### Post by plucky on 2009-10-27
> Well now i can't open either package managers. i get an error saying
E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

i'm pretty lost as how to correct this.
can somebody please help me. thanx 

What has happened is that the file medibuntu.list located in **/etc/apt/sources.list.d/** has "!DOCTYPE" in line 1 when it shouldn't.
Open a terminal and ```
cat /etc/apt/sources.list.d/medibuntu.list
``` and it should look like this ```
## Medibuntu - Ubuntu 9.04 "jaunty jackalope"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ jaunty free non-free
# deb-src http://packages.medibuntu.org/ jaunty free non-free

```

To edit the file assuming you are using Kubuntu Jaunty,from a terminal ```
sudo nano /etc/apt/sources.list.d/medibuntu.list
``` and remove the !DOCTYPE from line 1 and make it look like the example I posted or use the Kubuntu text editor.

Then ```
sudo apt-get update
``` and see if that works.

Good Luck

---

### Post by ThaiboxerAD on 2009-10-29
it worked! Thanks alot. :popcorn:[IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG]

---

