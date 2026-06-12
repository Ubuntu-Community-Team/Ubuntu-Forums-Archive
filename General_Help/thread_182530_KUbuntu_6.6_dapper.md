---
title: "KUbuntu 6.6 dapper"
date: 2006-05-26
forum: General Help
---

### Post by wizzkid on 2006-05-26
Guys,

I would like to know from you guys how you find the Kubuntu 6.6 dapper? I am currently using Kubuntu 5.10 breezy. 

I what to know the major and minor difference between the two (kubuntu 6.6 and 5.10) what's new?

Is kubuntu support WPA and WPA out from the box? or I should manually install the wpa_supplicant again?

does it worth it installing the kubuntu 6.6 since its not yet final release?  I am using this machine for my programing projects.

can I upgrade my existing Kubuntu 5.10 to kubuntu 6.6 without re-installing everthing? like from repositories? :D


Thanks and hoping for you feedback.

---

### Post by Sef on 2006-05-26
Here's the RC1 of Kubuntu:

[kubuntu]("http://cdimage.ubuntu.com/kubuntu/daily-live/20060526/")

> does it worth it installing the kubuntu 6.6 since its not yet final release?

Just wait a week and it will be stable (1 June.)

> can I upgrade my existing Kubuntu 5.10 to kubuntu 6.6 without re-installing everthing? like from repositories?

First **back up** your data.

Second Open Konsole (Kmenu > System > Konsole)

Third type these two commands:

a) Kdesu apt-get update

b) Kdesu apt-get dist-upgrade

Fourth If you wait till 1 June then there will be a button you click to get the Dapper download.

Fifth It is good to make a install disk before you upgrade.  At times things can go wrong.

---

### Post by Ubuntuud on 2006-05-26
You don't need to reinstall, just open your "/etc/apt/sources.list" and change every breezy into dapper. Then do a "sudo apt-get update" and a "sudo apt-get dist-upgrade".

---

### Post by bruce89 on 2006-05-26
[QUOTE=Ubuntuud]You don't need to reinstall, just open your "/etc/apt/sources.list" and change every breezy into dapper. Then do a "sudo apt-get update" and a "sudo apt-get dist-upgrade".[/QUOTE]
Don't do that, do this :
* In Adept go to Manage Repositories and change "breezy" to "dapper"

 * Click "Fetch Updates"

 * Click "Full Upgrade"

 * Click "Commit"
(From [https://lists.ubuntu.com/archives/ubuntu-announce/2006-May/000081.html](https://lists.ubuntu.com/archives/ubuntu-announce/2006-May/000081.html))

---

### Post by Jucato on 2006-05-26
What Ubuntuud and bruce89 said are practically the same. One is the CLI way, the latter is the GUI way. :D

---

### Post by wizzkid on 2006-05-26
Thanks guys :) really appreciate :)

---

### Post by der_joachim on 2006-05-26
The main difference that I have run into so far, is that Dapper feels a bit faster. Sure, many packages have more recent versions (the most important being Firefox and Thunderbird). I've run Dapper for a month now both at home and at work and I have not run into a single showstopping issue. 

The upgrade went very smoothly. Not that I do not recommend backupping your stuff, but I did not need it afterwards.

One word of advice: if you like Amarok, be sure to include the Kubuntu repository. You'll get version 1.4, which is more stable than the version shipping with Dapper.

---

### Post by Caligula on 2006-05-26
I'm using dapper and to be honest I didn't notice any big difference, except the fact that it recogizes my wireless card, that would be a GREAT difference if ubuntu wouldn't freeze while I'm trying to activate it...

Except that it's only the apps that make a real difference.

As for upgrading, both ways were posted here, either go to adept, change the repos' and do "fetch" "full upgrade" or you could do it the text-way, which I personally prefer, I find the console to be more stable and more reliable than GUIs, but that's personal preference.

Anyway, just doing sudo aptitude dist-upgrade without changing the list won't do you any good, you need to go edit your sources list-

sudo nano /etc/apt/sources.list

every time you see "breezy" change it to dapper.
after you do that save, exit "sudo aptitude update" "sudo aptitude dist-upgrade".

This will take a good few hours, depending on your internet and CPU.

WARNING: I did this in the past when I had more than one desktop enviroment installed, and it broke gnome and xfce, I could login only to KDE. But that's just what happened to me...

I did this a few times and didn't lose any data, the process is pretty stable, I think my DE problems came from the fact that I very foolishly clicked "yes" every time it asked wether it should install a new config file for something...
but that's only configuration...

Good luck!

---

### Post by D!mon on 2006-05-28
What is the amount of the free hard disk space required to perform an upgrade?

---

### Post by vinodis on 2006-05-29
does this work if I put my Dapper-ISO cd in my Breezy system?
Do I need to enter any different commands to upgrade?
Why dont the Ubuntu people provide a simple upgrade(executable) program on the root folder of the CD, so it is easy to upgrade from CD!?
Entering commands et all is too cumbersome for an OS upgrade. We have much important things to do with the computer.

---

### Post by Caligula on 2006-05-29
[QUOTE=vinodis]does this work if I put my Dapper-ISO cd in my Breezy system?
Do I need to enter any different commands to upgrade?
Why dont the Ubuntu people provide a simple upgrade(executable) program on the root folder of the CD, so it is easy to upgrade from CD!?
Entering commands et all is too cumbersome for an OS upgrade. We have much important things to do with the computer.[/QUOTE]

You are not serious, are you?

It's a matter of entering one line, "sudo nano /etc/apt/sources.list"
and then changing a few words to another one. If you don't have an internet connection you ust use the CD repository, it's also there, change it from breezy t dapper, first line if I remmember correctly.

and that's it!

A CD is a repository, it's in your file... you can also do it the GUI way with the update manager. However you like.

Can't get much easier than that...

---

### Post by vinodis on 2006-05-29
hmm.. I am serious.. ;)

I did exactly what you wrote now yesterday itself on the ISO image CD I downloaded.
but my breezy system's adept is still not finding any updates..
By default all my adept entries looks greyed out.
I need to right click on them and choose to make it active.
Even then I never had a clue as on how to edit it in the GUI.
Then I clicked twice on that entry accidentally, yielding me a editable cursor on that row in Adept.
The entry you specified is starting with cdrom:[kubuntu_breezyyblahblah..]/ <some spaces> breezy etc. Then I changed it to have 'dapper' and clicked on apply. Then clicked on 'Fetch Updates' and further on 'Full Upgrade' followed by 'commit'  But NOTHING happens with all these.
I have not tried manually editing the sources.list option yet. Will do that today.

---

### Post by blip on 2006-05-29
I moved to Dapper a little while ago.  Had a few problems with the upgrade (whatever you do, don't cancel the upgrade in the middle of its processing... fixing it isn't fun) but now everything is working just fine.  I used the sources/konsole method.

As for differences, I haven't noticed a huge number.  Some applications seem a little faster in loading (firefox, amarok, k3b, OpenOffice) while others seem a little slower.  Things generally seem a bit more stable as well.   (Though breezy was so stable, it is hard to tell).

Anyway, it's a worthwhile upgrade but I wasn't blown away by the difference. (Though that may be just because I haven't had enough time to play with it.)

---

### Post by Caligula on 2006-05-29
> **vinodis]hmm.. I am serious..  said:**
> / <some spaces> breezy etc. Then I changed it to have 'dapper' and clicked on apply. Then clicked on 'Fetch Updates' and further on 'Full Upgrade' followed by 'commit'  But NOTHING happens with all these.
I have not tried manually editing the sources.list option yet. Will do that today.


ummm... apparently it didn't send last time I tried...

anyway, can you post here your sources.list file? maybe the CD repo has been deleted somehow...

---

### Post by vinodis on 2006-05-29
my sources.list is like this:-

deb file:/cdrom/ dapper main restricted

---

### Post by vinodis on 2006-05-30
[QUOTE=vinodis]my sources.list is like this:-

deb file:/cdrom/ dapper main restricted[/QUOTE]
This is what I did:-

Installed happily the Breezy release
Downloaded the Automatix Offline CD and Ran it successfully
Downloaded the prior said Dapper ISO and burned a bootable CD with that image
Put that CD in the Breezy machine.
Then:-
* In Adept go to Manage Repositories and change "breezy" to "dapper"

 * Click "Fetch Updates"

 * Click "Full Upgrade"

 * Click "Commit"
Result:- Nothing happend

Then I did the commandline options on apt-get , but that too did not work.

I can see the Automatix specific automatic-sources.list files also in /etc/apt folder.

What am I doing wrong?

Thanks a lot for the followups and help.

---

### Post by Video Toaster on 2006-05-30
[QUOTE=vinodis]This is what I did:-

Installed happily the Breezy release
Downloaded the Automatix Offline CD and Ran it successfully
Downloaded the prior said Dapper ISO and burned a bootable CD with that image
Put that CD in the Breezy machine.
Then:-
* In Adept go to Manage Repositories and change "breezy" to "dapper"

 * Click "Fetch Updates"

 * Click "Full Upgrade"

 * Click "Commit"
Result:- Nothing happend

Then I did the commandline options on apt-get , but that too did not work.

I can see the Automatix specific automatic-sources.list files also in /etc/apt folder.

What am I doing wrong?

Thanks a lot for the followups and help.[/QUOTE]
Look for an option to add a new CD in Adept instead of editing your sources.list file.  I know there's an option in Synaptic to do that, but I don't remember if there's one in Adept for that, as I've never had to add a new CD.

---

### Post by vinodis on 2006-05-31
How do you add a new CD in Adept?

---

### Post by aysiu on 2006-05-31
[QUOTE=vinodis]How do you add a new CD in Adept?[/QUOTE] You can't.

You need Synaptic or the command-line.

Synaptic > Edit > Add CD-ROM

```
sudo apt-cdrom add
```

---

### Post by vinodis on 2006-05-31
[QUOTE=vinodis]How do you add a new CD in Adept?[/QUOTE]
[edit] i got the info here:- [http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-cdrom](http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-cdrom)

---

### Post by kzutter on 2006-05-31
[QUOTE=vinodis]
Why dont the Ubuntu people provide a simple upgrade(executable) program on the root folder of the CD, so it is easy to upgrade from CD!?
[/QUOTE]

I know of an operating system that does just that!
-But it is $189 US retail and they have not had an upgrade since 2002.;)

---

