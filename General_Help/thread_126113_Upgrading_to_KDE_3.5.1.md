---
title: "Upgrading to KDE 3.5.1"
date: 2006-02-05
forum: General Help
---

### Post by Rackerz on 2006-02-05
Well I want to make the move, but how? I can't seem to get anything to work.

---

### Post by dresnu on 2006-02-05
```
sudo kedit /etc/apt/sources.list
```
copy paste one of these mirrors at the end of the file: 

```
   
deb http://kubuntu.org/packages/kde351 breezy main
deb ftp://bolugftp.uni-bonn.de/pub/kde/stable/3.5.1/kubuntu breezy main
deb http://www.mirrorservice.org/sites/ftp.kde.org/pub/kde/stable/3.5.1/kubuntu breezy main
deb http://mirror.cc.columbia.edu/pub/software/kde/stable/3.5.1/kubuntu breezy main

```

then run these commands:
```
 
wget http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg
sudo apt-key add kubuntu-packages-jriddell-key.gpg
sudo apt-get update
sudo apt-get upgrade

```

that should be it ;)

---

### Post by treris on 2006-02-05
edit: I see someone beat me too it

---

### Post by zojas on 2006-02-06
you'll probably need to run 'sudo apt-get dist-upgrade' as the last step, since some packages will be 'kept back' otherwise.

---

### Post by Jucato on 2006-02-06
I don't think you need to do dist-upgrade since you are not upgrading the whole distrobution, but only a part of it. I didn't do a dist-upgrade and KDE 3.5.1 works fine.

---

### Post by zojas on 2006-02-06
if you type 'apt-get upgrade' and some packages are listed as 'kept back', then apt-get dist-upgrade will update those packages too. that's all I was saying. (I had a couple packages that were kept back)

see this link for why I was recommending dist-upgrade for kept back packages:

[http://www.debian-administration.org/articles/69]("http://www.debian-administration.org/articles/69")

---

### Post by Jucato on 2006-02-06
Point taken. strange thing, when I upgraded to KDE 3.5.1 I did remember seeing some packages being kept back. I ignored them and proceeded with the upgrade. Worked fine, and now whenever I do update/upgrade/dist-upgrade, they don't show up. Oh well... thanks for the link. :D

---

### Post by Pekkalainen on 2006-02-07
And heres the changelog: [http://www.kde.org/announcements/changelogs/changelog3_5to3_5_1.php](http://www.kde.org/announcements/changelogs/changelog3_5to3_5_1.php)

They do not appear to have fixed the msn filetransferbug, the most annoying bug since the dawn of man :evil:

---

### Post by kenweill on 2006-02-07
Im using KDE under Ubuntu Breezy.

Should I still need the "sudo apt-get upgrade"?

---

### Post by fabirulo on 2006-02-07
sorry but:

nosotros@ubuntu:~$ sudo kedit /etc/apt/sources.list
sudo: kedit: command not found

...I'm begginer yes.

---

### Post by nocturn on 2006-02-07
You can only use kedit if you already have it installed (part of KDE I guess).
Try gedit or kwrite instead.

You could fall back to a text based editor (like nano)

---

### Post by kenweill on 2006-02-07
[QUOTE=fabirulo]sorry but:

nosotros@ubuntu:~$ sudo kedit /etc/apt/sources.list
sudo: kedit: command not found

...I'm begginer yes.[/QUOTE]

Its pretty obvious that you are using Ubuntu.
GNOME is installed by default with Ubuntu.
U have to use gedit instead of kedit:

sudo gedit /etc/apt/sources.list

---

### Post by Orunitia on 2006-02-07
Type kate instead of kedit.

sudo kate /etc/apt/sources.list

---

### Post by Jucato on 2006-02-07
[QUOTE=kenweill]Its pretty obvious that you are using Ubuntu.
GNOME is installed by default with Ubuntu.
U have to use gedit instead of kedit:

sudo gedit /etc/apt/sources.list[/QUOTE]

I must have missed something, but... how did you presume that he was using ubuntu and GNOME? coz AFAIK, the default hostname for ubuntu and kubuntu is "ubuntu".

Anyway, kedit, I think, is no longer installed in a default kubuntu installation. so he would probably have better luck with nano or something else.

---

### Post by jackrabbit123 on 2006-02-07
That means you don't have kedit installed or it's not in your path.
Step 1:
Type: 'which kedit'
If the shell reports that it can't find it, goto step 2.
Otherwise goto step 4

Step 2:
Type 'find /usr | grep kedit' *This may take a while*:) 
you should see something like '..../kde/bin/kedit'
If you do goto step 3
otherwise goto step 5

Step 3:
Type: 'export PATH=$PATH:*directory where you found kedit*' and try 'sudo kedit . . .' again.
If it works goto step 5
otherwise goto step 4

Step 4:
Weep silently :cry: 
Post what step failed and what the errors were.

Step 5:
Rejoice!  Be sure to let us know your triumph \\:D/

---

### Post by fabirulo on 2006-02-07
I did make:
apt-get install kedit
and work:) :p 
reboot and my kde version say: kde 3.5.0...it's ok??? the number of the previous version was...?
thanks a lot!
(sorry for my english)

PD: seems to me or is to fast?

---

### Post by Kosmonaut on 2006-02-07
@dresnu->Just a short question:
Why did you add following sources?

deb [ftp://bolugftp.uni-bonn.de/pub/kde/stable/3.5.1/kubuntu](ftp://bolugftp.uni-bonn.de/pub/kde/stable/3.5.1/kubuntu) breezy main
deb [http://www.mirrorservice.org/sites/ftp.kde.org/pub/kde/stable/3.5.1/kubuntu](http://www.mirrorservice.org/sites/ftp.kde.org/pub/kde/stable/3.5.1/kubuntu) breezy main
deb [http://mirror.cc.columbia.edu/pub/software/kde/stable/3.5.1/kubuntu](http://mirror.cc.columbia.edu/pub/software/kde/stable/3.5.1/kubuntu) breezy main

I just have :
deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main

What's the difference between those sources?

---

### Post by dresnu on 2006-02-07
Hm, actually you 're probably right. I just copy-pasted what was on kubuntu.org using all mirrors. Well... you never know, lolz :mrgreen:

---

### Post by Jucato on 2006-02-07
yep, I only had just one too. the others are just mirrors.

---

### Post by QettoE on 2006-02-08
[QUOTE=dresnu]```
sudo kedit /etc/apt/sources.list
```
copy paste these at the end of the file: 

```
   
deb http://kubuntu.org/packages/kde351 breezy main
deb ftp://bolugftp.uni-bonn.de/pub/kde/stable/3.5.1/kubuntu breezy main
deb http://www.mirrorservice.org/sites/ftp.kde.org/pub/kde/stable/3.5.1/kubuntu breezy main
deb http://mirror.cc.columbia.edu/pub/software/kde/stable/3.5.1/kubuntu breezy main

```

then run these commands:
```
 
wget http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg
sudo apt-key add kubuntu-packages-jriddell-key.gpg
sudo apt-get update
sudo apt-get upgrade

```

that should be it ;)[/QUOTE]

Where the heck do you guys come up with this stuff? I'm a newbie and quite amazed to see how much you folks know...

---

### Post by NeoChaosX on 2006-02-08
[QUOTE=QettoE]Where the heck do you guys come up with this stuff? I'm a newbie and quite amazed to see how much you folks know...[/QUOTE]
Easy: [we read the front page](http://kubuntu.org/announcements/kde-351.php). :p But really, it comes from a variety of sources: reading guides, experimenting with settings, or just plain experience.

---

### Post by Rackerz on 2006-02-08
Thanks for all your input guys, KDE 3.5.1 is up and running :).

---

### Post by Sirin on 2006-02-09
[QUOTE=fabirulo]sorry but:

nosotros@ubuntu:~$ sudo kedit /etc/apt/sources.list
sudo: kedit: command not found

...I'm begginer yes.[/QUOTE]
It's "KWrite", not "KEdit". It seems that someone has been with GNOME too long. ;)

---

### Post by Parkotron on 2006-02-10
[QUOTE=Sirin]It's "KWrite", not "KEdit". It seems that someone has been with GNOME too long. ;)[/QUOTE]

KEdit is actually a completely legitimate option. Unfortunately, it's just not installed on most people's Kubuntu desktop. There are currently three major players in the KDE text editor field: Kate, KWrite and KEdit.

At the moment, Kate is the only text editor Kubuntu "installs" by default. Kate is an excellent program (and an even better KPart), but it can be intimidating even to an experienced user. It has sidebars, bottombars(?), ten top level menus, sixteen settings pages and all kinds of bells and whistles. Suggesting Kate to a new user just to edit one line of /etc/fstab seems a bit much. Kate definitely has its place, I just don't think it should be the default text editor.

KWrite is essentially a special lightweight "mode" of Kate. It feels exactly like Kate with a large number of features removed. KWrite is installed with Kate, but Kubuntu doesn't give it a menu entry or anything, so the average user is unlikely to know that it's there. Personally I dislike KWrite as I find it has far too many features to be called a basic text editor. It often think of it being Kate's tag along little brother who nobody really likes.

KEdit, on the other hand, is an excellent little text editor written from scratch to be very simple, intuitive, and light weight. It has no fancy features and loads extremely fast. It's what most people expect from a text-editor. The paralellism between its name and Gedit's is also convenient. Anyone who knows what Gedit is should be able to guess what KEdit is and vice versa.

Personally, I think Kubuntu should install both Kate and KEdit by default, labelling the first an "Advance Text Editor" and the second as a "Basic Text Editor" or "Simple Text Editor". I think this solution is ideal, as it allows new users to avoid Kate's complexity while still allowing them to discover its full power once they've become more confident with KDE/Kubuntu/Linux.

Well, I guess that was a bit long and off topic. I guess I'll have to file a bug.

---

### Post by anirban.sam on 2006-02-10
[QUOTE=fabirulo]sorry but:

nosotros@ubuntu:~$ sudo kedit /etc/apt/sources.list
sudo: kedit: command not found

...I'm begginer yes.[/QUOTE]
You need to install kedit. To do that: sudo apt-get install kedit

or 

you can simply replace kedit by vi in the command string

---

### Post by capacman on 2006-02-10
well when kde 3.5.0 was out i upgraded to it. So am i also have to add this new repository to upgrade 3.5.1  or is it just enough to have 
deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main 
line in my /etc/apt/sources.list file

---

### Post by dresnu on 2006-02-10
You should replace the 3.5 repository with the new one

---

### Post by Bachstelze on 2006-02-10
(hmmm never mind :D)

---

### Post by kaydot@kubuntu on 2006-02-10
```
kaydot@kubuntu:~$ sudo apt-key add kubuntu-packages-jriddell-key.gpg
gpg: no ultimately trusted keys found
OK
```

Is this what I'm supposed to be getting? It says 'OK', obviously enough, but, in my experience, it's rare that computers do actually mean that.

---

### Post by Jucato on 2006-02-10
I think that should work now. I also had that before.

---

### Post by kaydot@kubuntu on 2006-02-10
```
kaydot@ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  akregator ark artsbuilder kaddressbook kamera kappfinder karm kate
  kaudiocreator kcontrol kcron kdeadmin-kfile-plugins kdebase-bin
  kdebase-kio-plugins kdegraphics-kfile-plugins kdelibs-bin kdelibs4c2
  kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing
  kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-wizards
  kdeprint kdesktop kdm kfind kghostview khelpcenter kicker klaptopdaemon
  klipper kmenuedit kmilo kmix knetworkconf knotes konq-plugins konqueror
  konqueror-nsplugins konsole kontact kooka kopete korganizer kpdf kpf kppp
  krdc krfb kscd kscreensaver ksmserver ksnapshot ksplash ksvg kuser
  kwalletmanager kwifimanager kwin libkcddb1 libkonq4 libkpimexchange1
  libkpimidentities1 libkscan1 libksieve0 libktnef1
0 upgraded, 0 newly installed, 0 to remove and 68 not upgraded.
```

If I'm not mistaken, that's nearly everything that was installed in the first place. On top of that, I'm still getting this when I go to 'Help > About KDE' in any menu bar.

What's up? :(

---

### Post by Jucato on 2006-02-10
did you do sudo apt-get update first? try to double check if you have the proper repositories enabled.

---

### Post by kaydot@kubuntu on 2006-02-10
[QUOTE=Fenyx]did you do sudo apt-get update first? try to double check if you have the proper repositories enabled.[/QUOTE]
Yeah, I did 'sudo apt-get update'. However, I'm not sure how to check about the repositories. If you're asking whether or not they're in sources.list, then, yeah, they're there. My sources.list currently looks like this:

```
deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu breezy universe
# deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://kubuntu.org/packages/kde351 breezy main
deb ftp://bolugftp.uni-bonn.de/pub/kde/stable/3.5.1/kubuntu breezy main
deb http://www.mirrorservice.org/sites/ftp.kde.org/pub/kde/stable/3.5.1/kubuntu breezy main
deb http://mirror.cc.columbia.edu/pub/software/kde/stable/3.5.1/kubuntu breezy main
```

---

### Post by dresnu on 2006-02-10
As Kosmonaut pointed out to me try using only one mirror for 3.5.1 and comment out the other 3

---

### Post by Jucato on 2006-02-10
Not only that, but another very important thing. comment out the cdrom repository. It's not going to be of any use anymore. It will also cause some conflicts between versions

---

### Post by endernet on 2006-02-10
I just installed Kubuntu today, replacing Ubuntu, and when I wanted to upgrade to KDE 3.5.1 I was looking in here at the procedure.  I'm getting the same thing as kaydot so far.  Even the same 68 packages not upgraded.

My sources file looks the same, I've commented out the CD, and have only one mirror.

Any help will be greatly appreciated.

Thanks

---

### Post by wiseguy on 2006-02-11
Since upgrading, drive partitions are no longer visable under storage media. How can I make these visable again. :-k

---

### Post by ryanakca on 2006-02-11
> ryan@ubuntu:~$ sudo apt-get update
Ign cdrom://Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy Release.gpg
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports Release.gpg [189B]
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release.gpg
Ign [http://people.debian.org](http://people.debian.org) php5.1 Release.gpg
Ign [http://pkg-boinc.alioth.debian.org](http://pkg-boinc.alioth.debian.org) breezy Release.gpg
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy Release
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates Release [30.9kB]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Ign [http://people.debian.org](http://people.debian.org) php5.1 Release
Ign [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg
Ign [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg
Hit [http://pkg-boinc.alioth.debian.org](http://pkg-boinc.alioth.debian.org) breezy Release
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Release.gpg
Get:6 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports Release [19.6kB]
Ign [http://people.debian.org](http://people.debian.org) php5.1/breezy Packages
Ign [http://pkg-boinc.alioth.debian.org](http://pkg-boinc.alioth.debian.org) breezy/universe Packages
Ign [http://kubuntu.org](http://kubuntu.org) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Ign [http://people.debian.org](http://people.debian.org) php5.1/breezy Sources
Ign [http://pkg-boinc.alioth.debian.org](http://pkg-boinc.alioth.debian.org) breezy/universe Sources
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release
Ign [http://kubuntu.org](http://kubuntu.org) breezy Release
Hit [http://people.debian.org](http://people.debian.org) php5.1/breezy Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/main Packages
Hit [http://pkg-boinc.alioth.debian.org](http://pkg-boinc.alioth.debian.org) breezy/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/universe Sources
Ign [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
Hit [http://people.debian.org](http://people.debian.org) php5.1/breezy Sources
Hit [http://pkg-boinc.alioth.debian.org](http://pkg-boinc.alioth.debian.org) breezy/universe Sources
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Release
Ign [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
Ign [http://kubuntu.org](http://kubuntu.org) breezy/main Sources
Err [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
  404 Not Found
Err [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
  404 Not Found
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Err [http://kubuntu.org](http://kubuntu.org) breezy/main Sources
  404 Not Found
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Sources
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/multiverse Sources
Fetched 51.1kB in 3s (16.2kB/s)
Failed to fetch [http://kubuntu.org/packages/kde35/dists/breezy/main/binary-i386/Packages.gz](http://kubuntu.org/packages/kde35/dists/breezy/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://kubuntu.org/packages/kde351/dists/breezy/main/binary-i386/Packages.gz](http://kubuntu.org/packages/kde351/dists/breezy/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://kubuntu.org/packages/kde351/dists/breezy/main/source/Sources.gz](http://kubuntu.org/packages/kde351/dists/breezy/main/source/Sources.gz)  404 Not Found
Reading package lists... Done
W: Couldn't stat source package list [http://kubuntu.org](http://kubuntu.org) breezy/main Packages (/var/lib/apt/lists/kubuntu.org_packages_kde35_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://kubuntu.org](http://kubuntu.org) breezy/main Packages (/var/lib/apt/lists/kubuntu.org_packages_kde351_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://kubuntu.org](http://kubuntu.org) breezy/main Packages (/var/lib/apt/lists/kubuntu.org_packages_kde35_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://kubuntu.org](http://kubuntu.org) breezy/main Packages (/var/lib/apt/lists/kubuntu.org_packages_kde351_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

Any idea what the error is about... it sais that the mirror is down... but, the question is, why? Any ideas on what I could do?

---

### Post by seakiwi on 2006-02-11
[QUOTE=kaydot@kubuntu]```
kaydot@kubuntu:~$ sudo apt-key add kubuntu-packages-jriddell-key.gpg
gpg: no ultimately trusted keys found
OK
```

Is this what I'm supposed to be getting? It says 'OK', obviously enough, but, in my experience, it's rare that computers do actually mean that.[/QUOTE]

Yes, that just means that you don't have his PGP Keys on your keyring - therefore you can't afford them a level of trust.

---

### Post by dresnu on 2006-02-11
@ryanakca: you 've probably already done so but just check again that the addresses in the sources.list are correct. It might be a temporary problem with the mirrors you 're trying to contact. Maybe use some other mirror where you can. If you don't solve it, try doing this: I read it somewhere on this board because I had a similar problem. Comment out all lines in your sources.list and save it. Then run "sudo apt-get update"(which obviously does nothing) and then open up again the sources.list and uncomment the mirrors you need. Then just "sudo apt-get update" and "sudo apt-get upgrade". If it works don't ask me why, but that did just the trick for me.

---

### Post by kaydot@kubuntu on 2006-02-12
Hey, if I use

```

deb http://kubuntu.org/packages/kde-latest breezy main
deb-src http://kubuntu.org/packages/kde-latest breezy main

```,

will it have the same sort of effect? I would assume that it would, given that [http://kubuntu.org/packages/kde-latest/dists/breezy/apt.conf](http://kubuntu.org/packages/kde-latest/dists/breezy/apt.conf) states the description as Kubuntu Breezy KDE 3.5.1, but we all know what assumptions do. Just making sure. >_>


**Update:** Yeah, it appears to work just fine. Yay life.

---

### Post by klett on 2006-02-12
Hi,

I'm newbie...I've followed all the steps explained here and then I have rebooted my machine. The only thing I've noticed is that things happens quite fast, but I haven't found anything different apart from that. How can I see I have successfully updated it?
Thanks!

---

### Post by klett on 2006-02-12
Ok, I found the command on the web:
kde-config --version

but it reports 3.4.3!! I have followed the steps and apt has downloaded around 70MB. Have I  updated kde 3.4.3 instead of upgrading to 3.5?? I'm a bit confused...

Thanks

---

### Post by kaydot@kubuntu on 2006-02-12
klett: Open up Konsole, and send the following, line by line:

```

wget http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg #This retrieves J. Riddel's GPG Key. A GPG is a GNU Privacy Guard. Wiki it if you want.
sudo apt-key add kubuntu-packages-jriddell-key.gpg #This adds the key to your current list.
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup #This copies the file, and writes the copy as a backup.
sudo kwrite /etc/apt/sources.list #This opens the file with superuser privileges.

```

Select all of the file, and replace the entirety of it with the following:

```

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  
## You may replace "us" with your country code to get the closest mirror.

deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## MAJOR BUG FIX UPDATES produced after the final release
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

## UNIVERSE AND MULTIVERSE REPOSITORY (Unsupported by Ubuntu.  Use at own risk.) I have it enabled, personally.
## deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.) I have it enabled, personally.
## deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.) I have it enabled, personally.
## deb http://packages.freecontrib.org/ubuntu/plf breezy free non-free
## deb-src http://packages.freecontrib.org/ubuntu/plf breezy free non-free 

## LATEST KDE VERSION FROM kubuntu.org
deb http://kubuntu.org/packages/kde-latest breezy main
deb-src http://kubuntu.org/packages/kde-latest breezy main

```

Save the file, and in Konsole send the following:

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

and reboot. Hopefully, this'll work. It worked for me on a clean install, doing so before I had done anything else.

---

### Post by klett on 2006-02-13
Thanks for your patience kaydot@kubuntu! I've done exactly what you have told me to do, but when I ran apt-get upgrade I got the following: 
```
 root@ubuntu:~# apt-get upgrade 
Leyendo lista de paquetes... Hecho 
Creando árbol de dependencias... Hecho 
Los siguientes paquetes se han retenido: (The following packages has been kept:)
 ark artsbuilder kamera kappfinder kate kaudiocreator kcontrol kcron
kdeadmin-kfile-plugins kdebase-bin kdebase-kio-plugins
kdegraphics-kfile-plugins kdelibs-bin kdelibs4c2 kdemultimedia-kfile-plugins
kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins
kdepasswd kdeprint kdesktop kdm kfind kghostview khelpcenter kicker
klaptopdaemon klipper kmenuedit kmilo kmix knetworkconf konqueror
konqueror-nsplugins konsole kooka kopete kpdf kpf kppp krdc krfb kscd
kscreensaver ksmserver ksnapshot ksplash ksvg kuser kwalletmanager
kwifimanager kwin libkcddb1 libkonq4 libkscan1 libksieve0 libktnef1 
0 actualizados, 0 se instalarán, 0 para eliminar y 57 no actualizados. 
(0 updated, 0 will be installed, 0 will be removed and 57 won't be updated) 
```
 Why does it keep those packages?:confused:  I'm having problems with my current version of kde, I think it isn't installed properly since it does weird things, specially when something requires root privileges: kde sudo doesn't work as it should. I enter my password and it does nothing. That's why I want to upgrade!

---

### Post by kaydot@kubuntu on 2006-02-13
I really have no idea what to tell you, man. Just be sure that you've run 'sudo apt-get dist-upgrade'. For now, I'm not very good at helping others, since I solve most of my problems by reformatting and trying again, and will probably continue to do so until I become confident in undoing what I've done. I got the same error that you got at first, down to it rejecting my input of the root password, and I don't know what I did differently to fix it, because I thought I did the same exact thing. =/

---

### Post by NeoChaosX on 2006-02-13
[QUOTE=klett]Thanks for your patience kaydot@kubuntu! I've done exactly what you have told me to do, but when I ran apt-get upgrade I got the following: 
 Why does it keep those packages?:confused:  I'm having problems with my current version of kde, I think it isn't installed properly since it does weird things, specially when something requires root privileges: kde sudo doesn't work as it should. I enter my password and it does nothing. That's why I want to upgrade![/QUOTE]
Have you tried **sudo apt-get dist-upgrade**?

---

### Post by ozorba on 2006-02-13
You need to run

sudo apt-get update
sudo apt-get dist-upgrade 

to avoid any " (The following packages has been kept:)" messages...

Enjoy Kubuntu...

---

### Post by klett on 2006-02-13
Hi,

I've tried 
sudo apt-get update
sudo apt-get dist-upgrade
and keep receiving the same output.:cry: 

Any suggestions?

---

### Post by Jucato on 2006-02-13
could you post your sources.list? Maybe we could see something there.

---

### Post by socket on 2006-02-14
Hi,

I have tried what 'kaydot@kubuntu' said but kde doesnt upgrade.
In my first try, the system downloads a lot of things, but KDE version is the same 3.4.3.
How can i solve this problem?
I have typed all the commands in the correct order... :(

---

### Post by Jucato on 2006-02-14
it's still the same, even after you restarted? Now that IS wierd.
Maybe there were some packages that weren't updated or were kept back? Try doing upgrade or dist-upgrade again to make sure that there is nothing left out.

---

### Post by klett on 2006-02-14
my sources.list is the one that kaybot@ubuntu gave me:
```

deb http://es.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://es.archive.ubuntu.com/ubuntu breezy main restricted

## MAJOR BUG FIX UPDATES produced after the final release
deb http://es.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://es.archive.ubuntu.com/ubuntu breezy-updates main restricted

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

## UNIVERSE AND MULTIVERSE REPOSITORY (Unsupported by Ubuntu.  Use at own risk.)
## deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## deb http://packages.freecontrib.org/ubuntu/plf breezy free non-free
## deb-src http://packages.freecontrib.org/ubuntu/plf breezy free non-free 

## LATEST KDE VERSION FROM kubuntu.org
deb http://kubuntu.org/packages/kde-latest breezy main
deb-src http://kubuntu.org/packages/kde-latest breezy main

```

---

### Post by Jucato on 2006-02-14
um... you're trying to upgrade to KDE 3.5.1 right? But I don't see any repository for KDE 3.5.1. Follow this [link]("http://kubuntu.org/announcements/kde-351.php") for the Kubuntu instructions.

---

### Post by klett on 2006-02-14
Thanks Fenyx, but it still doesn't work and I can't figure out why. I have restored my original sources.list and I have added the repositories mentioned in the link. This is my current sources.list: 
```
 
#deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted deb http://es.archive.ubuntu.com/ubuntu breezy main restricted deb-src http://es.archive.ubuntu.com/ubuntu breezy main restricted deb http://kubuntu.org/packages/kde351 breezy main deb ftp://bolugftp.uni-bonn.de/pub/kde/stable/3.5.1/kubuntu breezy main deb http://www.mirrorservice.org/sites/ftp.kde.org/pub/kde/stable/3.5.1/kubuntu breezy main deb http://mirror.cc.columbia.edu/pub/software/kde/stable/3.5.1/kubuntu breezy main 
## Major bug fix updates produced after the final release of the 
## distribution. 
deb http://es.archive.ubuntu.com/ubuntu breezy-updates main restricted deb-src http://es.archive.ubuntu.com/ubuntu breezy-updates main restricted 
## Uncomment the following two lines to add software from the 'universe' 
## repository. 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by theUbuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## universe WILL NOT receive any review or updates from the Ubuntu security ## team. 
# deb http://es.archive.ubuntu.com/ubuntu breezy universe 
# deb-src http://es.archive.ubuntu.com/ubuntu breezy universe 
## Uncomment the following two lines to add software from the 'backports' 
## repository. 
## N.B. software from this repository may not have been tested as 
## extensively as that contained in the main release, although it includes 
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review ## or updates from the Ubuntu security team. 
# deb http://es.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 
# deb-src http://es.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 
deb http://security.ubuntu.com/ubuntu breezy-security main restricted deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted 
# deb http://security.ubuntu.com/ubuntu breezy-security universe 
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe 

``` 
After that I have run sudo -s to log in as root and then: 
```
 
root@ubuntu:/etc/apt# wget http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg
--23:35:56--  http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg
           => `kubuntu-packages-jriddell-key.gpg.1'
Resolviendo people.ubuntu.com... 82.211.81.132
Connecting to people.ubuntu.com|82.211.81.132|:80... conectado.
Petición HTTP enviada, esperando respuesta... 200 OK
Longitud: 26,430 (26K) [text/plain]

100%[===============================================================================>] 26,430        42.03K/s

23:35:57 (41.94 KB/s) - `kubuntu-packages-jriddell-key.gpg.1' saved [26430/26430]


``` 
```

root@ubuntu:/etc/apt# sudo apt-key add kubuntu-packages-jriddell-key.gpg OK 
``` 
```
 
root@ubuntu:/etc/apt# sudo apt-get update
 Des:1 http://security.ubuntu.com breezy-security Release.gpg [189B] 
Des:2 http://kubuntu.org breezy Release.gpg [189B] 
Des:3 http://www.mirrorservice.org breezy Release.gpg [189B] 
Des:4 http://es.archive.ubuntu.com breezy Release.gpg [189B] 
Des:5 http://es.archive.ubuntu.com breezy-updates Release.gpg [189B] 
Des:6 http://security.ubuntu.com breezy-security Release [19,6kB] 
Obj http://kubuntu.org breezy Release 
Obj http://www.mirrorservice.org breezy Release 
Obj http://es.archive.ubuntu.com breezy Release 
Obj http://es.archive.ubuntu.com breezy-updates Release 
Obj http://kubuntu.org breezy/main Packages 
Obj http://www.mirrorservice.org breezy/main Packages 
Obj http://es.archive.ubuntu.com breezy/main Packages 
Des:7 http://mirror.cc.columbia.edu breezy Release.gpg [189B] 
Obj http://es.archive.ubuntu.com breezy/restricted Packages 
Obj http://es.archive.ubuntu.com breezy/main Sources
 Obj http://es.archive.ubuntu.com breezy/restricted Sources 
Obj http://es.archive.ubuntu.com breezy-updates/main Packages 
Obj http://es.archive.ubuntu.com breezy-updates/restricted Packages 
Obj http://es.archive.ubuntu.com breezy-updates/main Sources 
Obj http://es.archive.ubuntu.com breezy-updates/restricted Sources 
Obj ftp://bolugftp.uni-bonn.de breezy Release.gpg 
Obj http://mirror.cc.columbia.edu breezy Release 
Des:8 ftp://bolugftp.uni-bonn.de breezy Release [1793B] 
Des:9 http://security.ubuntu.com breezy-security/main Packages [34,2kB] 
Obj http://mirror.cc.columbia.edu breezy/main Packages 
Obj ftp://bolugftp.uni-bonn.de breezy/main Packages
 Des:10 http://security.ubuntu.com breezy-security/restricted Packages [4458B] Des:11 http://security.ubuntu.com breezy-security/main Sources [10,4kB] Des:12 http://security.ubuntu.com breezy-security/restricted Sources [960B] Descargados 71,8kB en 3s (18,3kB/s) Leyendo lista de paquetes... Hecho (Done)
 
``` 
```
 
root@ubuntu:/etc/apt# sudo apt-get upgrade 
Leyendo lista de paquetes... Hecho 
Creando árbol de dependencias... Hecho 
Los siguientes paquetes se han retenido: (The following packages have been kept) 
ark artsbuilder kamera kappfinder kate kaudiocreator kcontrol kcron kdeadmin-kfile-plugins kdebase-bin kdebase-kio-plugins kdegraphics-kfile-plugins kdelibs-bin kdelibs4c2 kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdeprint kdesktop kdm kfind kghostview khelpcenter kicker klaptopdaemon klipper kmenuedit kmilo kmix knetworkconf konqueror konqueror-nsplugins konsole kooka kopete kpdf kpf kppp krdc krfb kscd kscreensaver ksmserver ksnapshot ksplash ksvg kuser kwalletmanager kwifimanager kwin libkcddb1 libkonq4 libkscan1 libksieve0 libktnef1 
0 actualizados, 0 se instalarán, 0 para eliminar y 57 no actualizados. 
(0 updated, 0 will be installed, 0 will be removed and 57 not updated)
 
```
If I run sudo apt-get dist-upgrade I receive the same output. I can't understand why it keeps those packages. Is there any way to tell apt not to keep a package?:confused:

---

### Post by Jucato on 2006-02-14
(for some reason, all your CODEs appear only on one line)
I'm not entirely sure why packages are being kept. It might be because of some dependency problems? I'm not really sure.

One more solution, but I'm not entirely certain what the consequences might be, but this is how I did it. I didn't actually upgrade my KDE from the command line. I did it through Adept. Run Adept, then Fetch Updates, the Full Upgrade. Just might work.

---

### Post by klett on 2006-02-14
May this have something to do with my current kde being in Spanish? Do I have to remove  my current kde before installing the new one?

---

### Post by klett on 2006-02-14
I haven't time to run adept right now. I'll try it later and let you know Fenyx. Thanks again!

---

### Post by Jucato on 2006-02-14
Btw, you don't have to include all 4 of the repositories given in the Kubuntu site I linked to. You can just enable one at a time They are just mirrors.

---

### Post by ahti on 2006-02-14
I have exactly the same problem - I have double-checked the repository, did apt-get update and upgrade. Even dist-upgrade but no success: all the KDE stuff is kept back. Even worse: dist-upgrade now attempts to remove kmail :(

---

### Post by ahti on 2006-02-14
okey guys, nobody ever mentioned that you need universe sources uncommented in apt sources to get it working.

!!!

---

### Post by klett on 2006-02-14
Hi,

I've tried using Adept but it hasn't worked. I've googled a bit and found a way to find out why apt is keeping back those packages. I won't post the whole output of this command because it's too long and it just repeats the same messages with different kde packages. The package kdelibs4c2 seems to be the source of the problem, since it appears in all the messages. However, I've no idea of what to do next.:-k 
```

root@ubuntu:~# apt-get -o Debug::pkgProblemResolver=yes dist-upgrade
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
Calculando la actualización... Starting
Starting 2
Investigating kdelibs4c2
Package kdelibs4c2 has broken dep on libavahi-client1
Investigating kdelibs-bin
Package kdelibs-bin has broken dep on kdelibs4c2
  Considering kdelibs4c2 123 as a solution to kdelibs-bin 83
  Holding Back kdelibs-bin rather than change kdelibs4c2
Investigating libkonq4
Package libkonq4 has broken dep on kdelibs4c2
  Considering kdelibs4c2 123 as a solution to libkonq4 9
  Holding Back libkonq4 rather than change kdelibs4c2
Investigating kdebase-bin
Package kdebase-bin has broken dep on kdelibs4c2
  Considering kdelibs4c2 123 as a solution to kdebase-bin 5
  Holding Back kdebase-bin rather than change kdelibs4c2

```

Any suggestions?

---

### Post by klett on 2006-02-14
I have uncommented the universe repository and I'm still getting the same message.

---

### Post by socket on 2006-02-14
Oh yeah! Now i'm running KDE 3.5.1 :)
I have got a sources.list at [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic) and open synaptic and update all!
:)

---

### Post by dresnu on 2006-02-14
@klett: try running this: "sudo apt-get install -f" and then using the link suggested by socket

---

### Post by kaydot@kubuntu on 2006-02-14
[QUOTE=Fenyx]um... you're trying to upgrade to KDE 3.5.1 right? But I don't see any repository for KDE 3.5.1. Follow this [link]("http://kubuntu.org/announcements/kde-351.php") for the Kubuntu instructions.[/QUOTE]

```

## LATEST KDE VERSION FROM kubuntu.org
deb http://kubuntu.org/packages/kde-latest breezy main
deb-src http://kubuntu.org/packages/kde-latest breezy main

```

Using that, you don't need to update your sources.list every time KDE releases a new version.

---

### Post by klett on 2006-02-15
Hi all, 

I've tried it and it hasn't worked. Uncommenting the backports repositories I've upgraded 12 packages but there are still 60 being kept back. However, I don't think this repository is the most appropriate to download packages from. I've found some tips on dealing with broken packages and I'll try them when I have time. For the moment being, I give up. 

Thanks everybody for helping me.

---

### Post by knubbe on 2006-02-17
I get an error:
```

Errors were encountered while processing: /var/cache/apt/archives/kdevelop3-dev_4%3a3.3.1-0ubuntu0breezy1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Full output after doing an apt-get upgrade
```

knubbe@laptop:/etc/apt$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  kde-i18n-sv kdegraphics-kfile-plugins kdelibs-bin kdelibs4-dev kdelibs4c2
  kmail
The following packages will be upgraded:
  akregator ark arts artsbuilder cervisia kaddressbook kamera kappfinder karm
  kate kaudiocreator kcontrol kcron kdeadmin-kfile-plugins kdebase-bin
  kdebase-data kdebase-kio-plugins kdelibs-data kdemultimedia-kappfinder-data
  kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing
  kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources
  kdepim-wizards kdeprint kdesktop kdessh kdevelop3 kdevelop3-data
  kdevelop3-dev kdevelop3-doc kdevelop3-plugins kdm kfilereplace kfind
  kghostview khelpcenter kicker kimagemapeditor klaptopdaemon klinkstatus
  klipper kmenuedit kmilo kmix knetworkconf knotes kommander kompare
  konq-plugins konqueror konqueror-nsplugins konsole kontact kooka kopete
  korganizer kpdf kpf kppp krdc krfb kscd kscreensaver ksmserver ksnapshot
  ksplash ksvg ksysguard ksysguardd kuser kwalletmanager kwifimanager kwin
  kxsldbg libarts1-dev libarts1c2 libartsc0 libartsc0-dev libcvsservice0
  libkcal2b libkcddb1 libkdepim1a libkleopatra1 libkmime2 libkonq4
  libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 quanta
  quanta-data
96 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Need to get 91,1MB of archives.
After unpacking 49,2kB disk space will be freed.
Do you want to continue [Y/n]?
Get:1 http://kubuntu.org breezy/main libktnef1 4:3.5.1-0ubuntu0breezy1 [49,6kB]
Get:2 http://kubuntu.org breezy/main libkcal2b 4:3.5.1-0ubuntu0breezy1 [599kB]
Get:3 http://kubuntu.org breezy/main libkdepim1a 4:3.5.1-0ubuntu0breezy1 [520kB]
Get:4 http://kubuntu.org breezy/main akregator 4:3.5.1-0ubuntu0breezy1 [670kB]
Get:5 http://kubuntu.org breezy/main ark 4:3.5.1-0ubuntu0breezy1 [287kB]
Get:6 http://kubuntu.org breezy/main libarts1-dev 1.5.1-0ubuntu0breezy1 [1507kB]
Get:7 http://kubuntu.org breezy/main libarts1c2 1.5.1-0ubuntu0breezy1 [1190kB]
Get:8 http://kubuntu.org breezy/main libartsc0-dev 1.5.1-0ubuntu0breezy1 [21,3kB
]
Get:9 http://kubuntu.org breezy/main libartsc0 1.5.1-0ubuntu0breezy1 [15,0kB]
Get:10 http://kubuntu.org breezy/main arts 1.5.1-0ubuntu0breezy1 [5950B]
Get:11 http://kubuntu.org breezy/main artsbuilder 4:3.5.1-0ubuntu0breezy1 [2212k
B]
Get:12 http://kubuntu.org breezy/main libcvsservice0 4:3.5.1-0ubuntu0breezy1 [10
1kB]
Get:13 http://kubuntu.org breezy/main cervisia 4:3.5.1-0ubuntu0breezy1 [737kB]
Get:14 http://kubuntu.org breezy/main libkleopatra1 4:3.5.1-0ubuntu0breezy1 [440
kB]
Get:15 http://kubuntu.org breezy/main kaddressbook 4:3.5.1-0ubuntu0breezy1 [1364
kB]
Get:16 http://kubuntu.org breezy/main kamera 4:3.5.1-0ubuntu0breezy2 [87,9kB]
Get:17 http://kubuntu.org breezy/main kappfinder 4:3.5.1-0ubuntu0breezy1 [278kB]
Get:18 http://kubuntu.org breezy/main karm 4:3.5.1-0ubuntu0breezy1 [450kB]
Get:19 http://kubuntu.org breezy/main kate 4:3.5.1-0ubuntu0breezy1 [775kB]
Get:20 http://kubuntu.org breezy/main libkcddb1 4:3.5.1-0ubuntu0breezy1 [139kB]
Get:21 http://kubuntu.org breezy/main kaudiocreator 4:3.5.1-0ubuntu0breezy1 [154
kB]
Get:22 http://kubuntu.org breezy/main kdemultimedia-kio-plugins 4:3.5.1-0ubuntu0
breezy1 [180kB]
Get:23 http://kubuntu.org breezy/main libkonq4 4:3.5.1-0ubuntu0breezy1 [261kB]
Get:24 http://kubuntu.org breezy/main konqueror 4:3.5.1-0ubuntu0breezy1 [1984kB]
Get:25 http://kubuntu.org breezy/main kdebase-kio-plugins 4:3.5.1-0ubuntu0breezy
1 [1002kB]
Get:26 http://kubuntu.org breezy/main kdebase-data 4:3.5.1-0ubuntu0breezy1 [5767
kB]
Get:27 http://kubuntu.org breezy/main kdm 4:3.5.1-0ubuntu0breezy1 [620kB]
Get:28 http://kubuntu.org breezy/main kdesktop 4:3.5.1-0ubuntu0breezy1 [758kB]
Get:29 http://kubuntu.org breezy/main kdebase-bin 4:3.5.1-0ubuntu0breezy1 [1045k
B]
Get:30 http://kubuntu.org breezy/main kfind 4:3.5.1-0ubuntu0breezy1 [197kB]
Get:31 http://kubuntu.org breezy/main kicker 4:3.5.1-0ubuntu0breezy1 [1935kB]
Get:32 http://kubuntu.org breezy/main kcontrol 4:3.5.1-0ubuntu0breezy1 [8010kB]
Get:33 http://kubuntu.org breezy/main kcron 4:3.5.1-0ubuntu0breezy1 [205kB]
Get:34 http://kubuntu.org breezy/main kdeadmin-kfile-plugins 4:3.5.1-0ubuntu0bre
ezy1 [32,7kB]
Get:35 http://kubuntu.org breezy/main kdelibs-data 4:3.5.1-0ubuntu0breezy1 [7081
kB]
Get:36 http://kubuntu.org breezy/main kdemultimedia-kappfinder-data 4:3.5.1-0ubu
ntu0breezy1 [29,9kB]
Get:37 http://kubuntu.org breezy/main kdemultimedia-kfile-plugins 4:3.5.1-0ubunt
u0breezy1 [127kB]
Get:38 http://kubuntu.org breezy/main kdenetwork-filesharing 4:3.5.1-0ubuntu0bre
ezy1 [605kB]
Get:39 http://kubuntu.org breezy/main kdenetwork-kfile-plugins 4:3.5.1-0ubuntu0b
reezy1 [46,2kB]
Get:40 http://kubuntu.org breezy/main kdepasswd 4:3.5.1-0ubuntu0breezy1 [239kB]
Get:41 http://kubuntu.org breezy/main libkmime2 4:3.5.1-0ubuntu0breezy1 [114kB]
Get:42 http://kubuntu.org breezy/main kdepim-kio-plugins 4:3.5.1-0ubuntu0breezy1
 [768kB]
Get:43 http://kubuntu.org breezy/main kdepim-kresources 4:3.5.1-0ubuntu0breezy1
[2113kB]
Get:44 http://kubuntu.org breezy/main libkpimidentities1 4:3.5.1-0ubuntu0breezy1
 [72,7kB]
Get:45 http://kubuntu.org breezy/main kdepim-wizards 4:3.5.1-0ubuntu0breezy1 [15
5kB]
Get:46 http://kubuntu.org breezy/main kdeprint 4:3.5.1-0ubuntu0breezy1 [1287kB]
Get:47 http://kubuntu.org breezy/main kdessh 4:3.5.1-0ubuntu0breezy1 [31,7kB]
Get:48 http://kubuntu.org breezy/main kdevelop3-dev 4:3.3.1-0ubuntu0breezy1 [161
kB]
Get:49 http://kubuntu.org breezy/main kdevelop3-data 4:3.3.1-0ubuntu0breezy1 [25
30kB]
Get:50 http://kubuntu.org breezy/main kdevelop3 4:3.3.1-0ubuntu0breezy1 [1264kB]
Get:51 http://kubuntu.org breezy/main kdevelop3-plugins 4:3.3.1-0ubuntu0breezy1
[6808kB]
Get:52 http://kubuntu.org breezy/main kdevelop3-doc 4:3.3.1-0ubuntu0breezy1 [246
7kB]
Get:53 http://kubuntu.org breezy/main quanta 4:3.5.1-0ubuntu0breezy1 [2390kB]
Get:54 http://kubuntu.org breezy/main klinkstatus 4:3.5.1-0ubuntu0breezy1 [291kB
]
Get:55 http://kubuntu.org breezy/main kommander 4:3.5.1-0ubuntu0breezy1 [1491kB]
Get:56 http://kubuntu.org breezy/main quanta-data 4:3.5.1-0ubuntu0breezy1 [972kB
]
Get:57 http://kubuntu.org breezy/main kfilereplace 4:3.5.1-0ubuntu0breezy1 [633k
B]
Get:58 http://kubuntu.org breezy/main kghostview 4:3.5.1-0ubuntu0breezy2 [231kB]
Get:59 http://kubuntu.org breezy/main khelpcenter 4:3.5.1-0ubuntu0breezy1 [1994k
B]
Get:60 http://kubuntu.org breezy/main kimagemapeditor 4:3.5.1-0ubuntu0breezy1 [3
12kB]
Get:61 http://kubuntu.org breezy/main klaptopdaemon 4:3.5.1-0ubuntu0breezy1 [245
kB]
Get:62 http://kubuntu.org breezy/main klipper 4:3.5.1-0ubuntu0breezy1 [253kB]
Get:63 http://kubuntu.org breezy/main kmenuedit 4:3.5.1-0ubuntu0breezy1 [372kB]
Get:64 http://kubuntu.org breezy/main kmilo 4:3.5.1-0ubuntu0breezy1 [142kB]
Get:65 http://kubuntu.org breezy/main kmix 4:3.5.1-0ubuntu0breezy1 [371kB]
Get:66 http://kubuntu.org breezy/main knetworkconf 4:3.5.1-0ubuntu0breezy1 [593k
B]
Get:67 http://kubuntu.org breezy/main knotes 4:3.5.1-0ubuntu0breezy1 [243kB]
Get:68 http://kubuntu.org breezy/main kompare 4:3.5.1-0ubuntu0breezy1 [321kB]
Get:69 http://kubuntu.org breezy/main konq-plugins 4:3.5.1-0ubuntu0breezy1 [1109
kB]
Get:70 http://kubuntu.org breezy/main konqueror-nsplugins 4:3.5.1-0ubuntu0breezy
1 [139kB]
Get:71 http://kubuntu.org breezy/main konsole 4:3.5.1-0ubuntu0breezy1 [694kB]
Get:72 http://kubuntu.org breezy/main kontact 4:3.5.1-0ubuntu0breezy1 [1589kB]
Get:73 http://kubuntu.org breezy/main libkscan1 4:3.5.1-0ubuntu0breezy2 [131kB]
Get:74 http://kubuntu.org breezy/main kooka 4:3.5.1-0ubuntu0breezy2 [754kB]
Get:75 http://kubuntu.org breezy/main kopete 4:3.5.1-0ubuntu0breezy1 [5252kB]
Get:76 http://kubuntu.org breezy/main libkpimexchange1 4:3.5.1-0ubuntu0breezy1 [
107kB]
Get:77 http://kubuntu.org breezy/main korganizer 4:3.5.1-0ubuntu0breezy1 [1543kB
]
Get:78 http://kubuntu.org breezy/main kpdf 4:3.5.1-0ubuntu0breezy2 [718kB]
Get:79 http://kubuntu.org breezy/main kpf 4:3.5.1-0ubuntu0breezy1 [193kB]
Get:80 http://kubuntu.org breezy/main kppp 4:3.5.1-0ubuntu0breezy1 [678kB]
Get:81 http://kubuntu.org breezy/main krdc 4:3.5.1-0ubuntu0breezy1 [504kB]
Get:82 http://kubuntu.org breezy/main krfb 4:3.5.1-0ubuntu0breezy1 [936kB]
Get:83 http://kubuntu.org breezy/main kscd 4:3.5.1-0ubuntu0breezy1 [421kB]
Get:84 http://kubuntu.org breezy/main kscreensaver 4:3.5.1-0ubuntu0breezy1 [815k
B]
Get:85 http://kubuntu.org breezy/main ksmserver 4:3.5.1-0ubuntu0breezy1 [154kB]
Get:86 http://kubuntu.org breezy/main kwin 4:3.5.1-0ubuntu0breezy1 [982kB]
Get:87 http://kubuntu.org breezy/main ksnapshot 4:3.5.1-0ubuntu0breezy2 [151kB]
Get:88 http://kubuntu.org breezy/main ksplash 4:3.5.1-0ubuntu0breezy1 [705kB]
Get:89 http://kubuntu.org breezy/main ksvg 4:3.5.1-0ubuntu0breezy2 [1205kB]
Get:90 http://kubuntu.org breezy/main ksysguard 4:3.5.1-0ubuntu0breezy1 [481kB]
Get:91 http://kubuntu.org breezy/main ksysguardd 4:3.5.1-0ubuntu0breezy1 [64,9kB
]
Get:92 http://kubuntu.org breezy/main kuser 4:3.5.1-0ubuntu0breezy1 [236kB]
Get:93 http://kubuntu.org breezy/main kwalletmanager 4:3.5.1-0ubuntu0breezy1 [34
4kB]
Get:94 http://kubuntu.org breezy/main kwifimanager 4:3.5.1-0ubuntu0breezy1 [226k
B]
Get:95 http://kubuntu.org breezy/main kxsldbg 4:3.5.1-0ubuntu0breezy1 [594kB]
Get:96 http://kubuntu.org breezy/main libksieve0 4:3.5.1-0ubuntu0breezy1 [38,5kB
]
Fetched 91,1MB in 2m22s (639kB/s)
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 147560 files and directories currently installed.)
Preparing to replace libktnef1 4:3.5.0-0ubuntu0breezy2 (using .../libktnef1_4%3a
3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement libktnef1 ...
Preparing to replace libkcal2b 4:3.5.0-0ubuntu0breezy2 (using .../libkcal2b_4%3a
3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement libkcal2b ...
Preparing to replace libkdepim1a 4:3.5.0-0ubuntu0breezy2 (using .../libkdepim1a_
4%3a3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement libkdepim1a ...
Preparing to replace akregator 4:3.5.0-0ubuntu0breezy2 (using .../akregator_4%3a
3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement akregator ...
Replacing files in old package kontact ...
Preparing to replace ark 4:3.5.0-0ubuntu0breezy1 (using .../ark_4%3a3.5.1-0ubunt
u0breezy1_i386.deb) ...
Unpacking replacement ark ...
Preparing to replace libarts1-dev 1.5.0-0ubuntu0breezy1 (using .../libarts1-dev_
1.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement libarts1-dev ...
Preparing to replace libarts1c2 1.5.0-0ubuntu0breezy1 (using .../libarts1c2_1.5.
1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement libarts1c2 ...
Preparing to replace libartsc0-dev 1.5.0-0ubuntu0breezy1 (using .../libartsc0-de
v_1.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement libartsc0-dev ...
Preparing to replace libartsc0 1.5.0-0ubuntu0breezy1 (using .../libartsc0_1.5.1-
0ubuntu0breezy1_i386.deb) ...
Unpacking replacement libartsc0 ...
Preparing to replace arts 1.5.0-0ubuntu0breezy1 (using .../arts_1.5.1-0ubuntu0br
eezy1_all.deb) ...
Unpacking replacement arts ...
Preparing to replace artsbuilder 4:3.5.0-0ubuntu0breezy1 (using .../artsbuilder_
4%3a3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement artsbuilder ...
Preparing to replace libcvsservice0 4:3.5.0-0ubuntu0breezy1 (using .../libcvsser
vice0_4%3a3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement libcvsservice0 ...
Preparing to replace cervisia 4:3.5.0-0ubuntu0breezy1 (using .../cervisia_4%3a3.
5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement cervisia ...
Preparing to replace libkleopatra1 4:3.5.0-0ubuntu0breezy2 (using .../libkleopat
ra1_4%3a3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement libkleopatra1 ...
Preparing to replace kaddressbook 4:3.5.0-0ubuntu0breezy2 (using .../kaddressboo
k_4%3a3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement kaddressbook ...
Replacing files in old package kontact ...
Preparing to replace kamera 4:3.5.0-0ubuntu0breezy1.4 (using .../kamera_4%3a3.5.
1-0ubuntu0breezy2_i386.deb) ...
Unpacking replacement kamera ...
Preparing to replace kappfinder 4:3.5.0-0ubuntu0breezy1 (using .../kappfinder_4%
3a3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement kappfinder ...
Preparing to replace karm 4:3.5.0-0ubuntu0breezy2 (using .../karm_4%3a3.5.1-0ubu
ntu0breezy1_i386.deb) ...
Unpacking replacement karm ...
Replacing files in old package kontact ...
Preparing to replace kate 4:3.5.0-0ubuntu0breezy1 (using .../kate_4%3a3.5.1-0ubu
ntu0breezy1_i386.deb) ...
Unpacking replacement kate ...
Preparing to replace libkcddb1 4:3.5.0-0ubuntu0breezy1 (using .../libkcddb1_4%3a
3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement libkcddb1 ...
Preparing to replace kaudiocreator 4:3.5.0-0ubuntu0breezy1 (using .../kaudiocrea
tor_4%3a3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement kaudiocreator ...
Preparing to replace kdemultimedia-kio-plugins 4:3.5.0-0ubuntu0breezy1 (using ..
./kdemultimedia-kio-plugins_4%3a3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement kdemultimedia-kio-plugins ...
Preparing to replace libkonq4 4:3.5.0-0ubuntu0breezy1 (using .../libkonq4_4%3a3.
5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement libkonq4 ...
Preparing to replace konqueror 4:3.5.0-0ubuntu0breezy1 (using .../konqueror_4%3a
3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement konqueror ...
Preparing to replace kdebase-kio-plugins 4:3.5.0-0ubuntu0breezy1 (using .../kdeb
ase-kio-plugins_4%3a3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement kdebase-kio-plugins ...
Preparing to replace kdebase-data 4:3.5.0-0ubuntu0breezy1 (using .../kdebase-dat
a_4%3a3.5.1-0ubuntu0breezy1_all.deb) ...
Unpacking replacement kdebase-data ...
Preparing to replace kdm 4:3.5.0-0ubuntu0breezy1 (using .../kdm_4%3a3.5.1-0ubunt
u0breezy1_i386.deb) ...
Unpacking replacement kdm ...
Preparing to replace kdesktop 4:3.5.0-0ubuntu0breezy1 (using .../kdesktop_4%3a3.
5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement kdesktop ...
Preparing to replace kdebase-bin 4:3.5.0-0ubuntu0breezy1 (using .../kdebase-bin_
4%3a3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement kdebase-bin ...
Preparing to replace kfind 4:3.5.0-0ubuntu0breezy1 (using .../kfind_4%3a3.5.1-0u
buntu0breezy1_i386.deb) ...
Unpacking replacement kfind ...
Preparing to replace kicker 4:3.5.0-0ubuntu0breezy1 (using .../kicker_4%3a3.5.1-
0ubuntu0breezy1_i386.deb) ...
Unpacking replacement kicker ...
Preparing to replace kcontrol 4:3.5.0-0ubuntu0breezy1 (using .../kcontrol_4%3a3.
5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement kcontrol ...
Preparing to replace kcron 4:3.5.0-0ubuntu0breezy2 (using .../kcron_4%3a3.5.1-0u
buntu0breezy1_i386.deb) ...
Unpacking replacement kcron ...
Preparing to replace kdeadmin-kfile-plugins 4:3.5.0-0ubuntu0breezy2 (using .../k
deadmin-kfile-plugins_4%3a3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement kdeadmin-kfile-plugins ...
Preparing to replace kdelibs-data 4:3.5.0-0ubuntu0breezy2 (using .../kdelibs-dat
a_4%3a3.5.1-0ubuntu0breezy1_all.deb) ...
Unpacking replacement kdelibs-data ...
Preparing to replace kdemultimedia-kappfinder-data 4:3.5.0-0ubuntu0breezy1 (usin
g .../kdemultimedia-kappfinder-data_4%3a3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement kdemultimedia-kappfinder-data ...
Preparing to replace kdemultimedia-kfile-plugins 4:3.5.0-0ubuntu0breezy1 (using
.../kdemultimedia-kfile-plugins_4%3a3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement kdemultimedia-kfile-plugins ...
Preparing to replace kdenetwork-filesharing 4:3.5.0-0ubuntu0breezy1 (using .../k
denetwork-filesharing_4%3a3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement kdenetwork-filesharing ...
Preparing to replace kdenetwork-kfile-plugins 4:3.5.0-0ubuntu0breezy1 (using ...
/kdenetwork-kfile-plugins_4%3a3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement kdenetwork-kfile-plugins ...
Preparing to replace kdepasswd 4:3.5.0-0ubuntu0breezy1 (using .../kdepasswd_4%3a
3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement kdepasswd ...
Preparing to replace libkmime2 4:3.5.0-0ubuntu0breezy2 (using .../libkmime2_4%3a
3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement libkmime2 ...
Preparing to replace kdepim-kio-plugins 4:3.5.0-0ubuntu0breezy2 (using .../kdepi
m-kio-plugins_4%3a3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement kdepim-kio-plugins ...
Preparing to replace kdepim-kresources 4:3.5.0-0ubuntu0breezy2 (using .../kdepim
-kresources_4%3a3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement kdepim-kresources ...
Preparing to replace libkpimidentities1 4:3.5.0-0ubuntu0breezy2 (using .../libkp
imidentities1_4%3a3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement libkpimidentities1 ...
Preparing to replace kdepim-wizards 4:3.5.0-0ubuntu0breezy2 (using .../kdepim-wi
zards_4%3a3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement kdepim-wizards ...
Preparing to replace kdeprint 4:3.5.0-0ubuntu0breezy1 (using .../kdeprint_4%3a3.
5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement kdeprint ...
Preparing to replace kdessh 4:3.5.0-0ubuntu0breezy1 (using .../kdessh_4%3a3.5.1-
0ubuntu0breezy1_i386.deb) ...
Unpacking replacement kdessh ...
Preparing to replace kdevelop3-dev 4:3.3.0-0ubuntu0breezy1 (using .../kdevelop3-
dev_4%3a3.3.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement kdevelop3-dev ...
dpkg: error processing /var/cache/apt/archives/kdevelop3-dev_4%3a3.3.1-0ubuntu0b
reezy1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libkinterfacedesigner.la', which is also in packa
ge kdevelop3
Preparing to replace kdevelop3-data 4:3.3.0-0ubuntu0breezy1 (using .../kdevelop3
-data_4%3a3.3.1-0ubuntu0breezy1_all.deb) ...
Unpacking replacement kdevelop3-data ...
Preparing to replace kdevelop3 4:3.3.0-0ubuntu0breezy1 (using .../kdevelop3_4%3a
3.3.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement kdevelop3 ...
Preparing to replace kdevelop3-plugins 4:3.3.0-0ubuntu0breezy1 (using .../kdevel
op3-plugins_4%3a3.3.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement kdevelop3-plugins ...
Preparing to replace kdevelop3-doc 4:3.3.0-0ubuntu0breezy1 (using .../kdevelop3-
doc_4%3a3.3.1-0ubuntu0breezy1_all.deb) ...
Unpacking replacement kdevelop3-doc ...
Preparing to replace quanta 4:3.5.0-0ubuntu0breezy1 (using .../quanta_4%3a3.5.1-
0ubuntu0breezy1_i386.deb) ...
Unpacking replacement quanta ...
Preparing to replace klinkstatus 4:3.5.0-0ubuntu0breezy1 (using .../klinkstatus_
4%3a3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement klinkstatus ...
Preparing to replace kommander 4:3.5.0-0ubuntu0breezy1 (using .../kommander_4%3a
3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement kommander ...
Preparing to replace quanta-data 4:3.5.0-0ubuntu0breezy1 (using .../quanta-data_
4%3a3.5.1-0ubuntu0breezy1_all.deb) ...
Unpacking replacement quanta-data ...
Preparing to replace kfilereplace 4:3.5.0-0ubuntu0breezy1 (using .../kfilereplac
e_4%3a3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement kfilereplace ...
Preparing to replace kghostview 4:3.5.0-0ubuntu0breezy1.4 (using .../kghostview_
4%3a3.5.1-0ubuntu0breezy2_i386.deb) ...
Unpacking replacement kghostview ...
Preparing to replace khelpcenter 4:3.5.0-0ubuntu0breezy1 (using .../khelpcenter_
4%3a3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement khelpcenter ...
Preparing to replace kimagemapeditor 4:3.5.0-0ubuntu0breezy1 (using .../kimagema
peditor_4%3a3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement kimagemapeditor ...
Preparing to replace klaptopdaemon 4:3.5.0-0ubuntu0breezy1 (using .../klaptopdae
mon_4%3a3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement klaptopdaemon ...
Preparing to replace klipper 4:3.5.0-0ubuntu0breezy1 (using .../klipper_4%3a3.5.
1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement klipper ...
Preparing to replace kmenuedit 4:3.5.0-0ubuntu0breezy1 (using .../kmenuedit_4%3a
3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement kmenuedit ...
Preparing to replace kmilo 4:3.5.0-0ubuntu0breezy1 (using .../kmilo_4%3a3.5.1-0u
buntu0breezy1_i386.deb) ...
Unpacking replacement kmilo ...
Preparing to replace kmix 4:3.5.0-0ubuntu0breezy1 (using .../kmix_4%3a3.5.1-0ubu
ntu0breezy1_i386.deb) ...
Unpacking replacement kmix ...
Preparing to replace knetworkconf 4:3.5.0-0ubuntu0breezy2 (using .../knetworkcon
f_4%3a3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement knetworkconf ...
Preparing to replace knotes 4:3.5.0-0ubuntu0breezy2 (using .../knotes_4%3a3.5.1-
0ubuntu0breezy1_i386.deb) ...
Unpacking replacement knotes ...
Replacing files in old package kontact ...
Preparing to replace kompare 4:3.5.0-0ubuntu0breezy1 (using .../kompare_4%3a3.5.
1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement kompare ...
Preparing to replace konq-plugins 4:3.5.0-0ubuntu0breezy1 (using .../konq-plugin
s_4%3a3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement konq-plugins ...
Preparing to replace konqueror-nsplugins 4:3.5.0-0ubuntu0breezy1 (using .../konq
ueror-nsplugins_4%3a3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement konqueror-nsplugins ...
Preparing to replace konsole 4:3.5.0-0ubuntu0breezy1 (using .../konsole_4%3a3.5.
1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement konsole ...
Preparing to replace kontact 4:3.5.0-0ubuntu0breezy2 (using .../kontact_4%3a3.5.
1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement kontact ...
Preparing to replace libkscan1 4:3.5.0-0ubuntu0breezy1.4 (using .../libkscan1_4%
3a3.5.1-0ubuntu0breezy2_i386.deb) ...
Unpacking replacement libkscan1 ...
Preparing to replace kooka 4:3.5.0-0ubuntu0breezy1.4 (using .../kooka_4%3a3.5.1-
0ubuntu0breezy2_i386.deb) ...
Unpacking replacement kooka ...
Preparing to replace kopete 4:3.5.0-0ubuntu0breezy1 (using .../kopete_4%3a3.5.1-
0ubuntu0breezy1_i386.deb) ...
Unpacking replacement kopete ...
Preparing to replace libkpimexchange1 4:3.5.0-0ubuntu0breezy2 (using .../libkpim
exchange1_4%3a3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement libkpimexchange1 ...
Preparing to replace korganizer 4:3.5.0-0ubuntu0breezy2 (using .../korganizer_4%
3a3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement korganizer ...
Preparing to replace kpdf 4:3.5.0-0ubuntu0breezy1.4 (using .../kpdf_4%3a3.5.1-0u
buntu0breezy2_i386.deb) ...
Unpacking replacement kpdf ...
Preparing to replace kpf 4:3.5.0-0ubuntu0breezy1 (using .../kpf_4%3a3.5.1-0ubunt
u0breezy1_i386.deb) ...
Unpacking replacement kpf ...
Preparing to replace kppp 4:3.5.0-0ubuntu0breezy1 (using .../kppp_4%3a3.5.1-0ubu
ntu0breezy1_i386.deb) ...
Unpacking replacement kppp ...
Preparing to replace krdc 4:3.5.0-0ubuntu0breezy1 (using .../krdc_4%3a3.5.1-0ubu
ntu0breezy1_i386.deb) ...
Unpacking replacement krdc ...
Preparing to replace krfb 4:3.5.0-0ubuntu0breezy1 (using .../krfb_4%3a3.5.1-0ubu
ntu0breezy1_i386.deb) ...
Unpacking replacement krfb ...
Preparing to replace kscd 4:3.5.0-0ubuntu0breezy1 (using .../kscd_4%3a3.5.1-0ubu
ntu0breezy1_i386.deb) ...
Unpacking replacement kscd ...
Preparing to replace kscreensaver 4:3.5.0-0ubuntu0breezy1 (using .../kscreensave
r_4%3a3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement kscreensaver ...
Preparing to replace ksmserver 4:3.5.0-0ubuntu0breezy1 (using .../ksmserver_4%3a
3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement ksmserver ...
Preparing to replace kwin 4:3.5.0-0ubuntu0breezy1 (using .../kwin_4%3a3.5.1-0ubu
ntu0breezy1_i386.deb) ...
Unpacking replacement kwin ...
Preparing to replace ksnapshot 4:3.5.0-0ubuntu0breezy1.4 (using .../ksnapshot_4%
3a3.5.1-0ubuntu0breezy2_i386.deb) ...
Unpacking replacement ksnapshot ...
Preparing to replace ksplash 4:3.5.0-0ubuntu0breezy1 (using .../ksplash_4%3a3.5.
1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement ksplash ...
Preparing to replace ksvg 4:3.5.0-0ubuntu0breezy1.4 (using .../ksvg_4%3a3.5.1-0u
buntu0breezy2_i386.deb) ...
Unpacking replacement ksvg ...
Preparing to replace ksysguard 4:3.5.0-0ubuntu0breezy1 (using .../ksysguard_4%3a
3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement ksysguard ...
Preparing to replace ksysguardd 4:3.5.0-0ubuntu0breezy1 (using .../ksysguardd_4%                                                                                                                                                            3a3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement ksysguardd ...
Preparing to replace kuser 4:3.5.0-0ubuntu0breezy2 (using .../kuser_4%3a3.5.1-0u                                                                                                                                                            buntu0breezy1_i386.deb) ...
Unpacking replacement kuser ...
Preparing to replace kwalletmanager 4:3.5.0-0ubuntu0breezy1 (using .../kwalletma                                                                                                                                                            nager_4%3a3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement kwalletmanager ...
Preparing to replace kwifimanager 4:3.5.0-0ubuntu0breezy1 (using .../kwifimanage                                                                                                                                                            r_4%3a3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement kwifimanager ...
Preparing to replace kxsldbg 4:3.5.0-0ubuntu0breezy1 (using .../kxsldbg_4%3a3.5.                                                                                                                                                            1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement kxsldbg ...
Preparing to replace libksieve0 4:3.5.0-0ubuntu0breezy2 (using .../libksieve0_4%                                                                                                                                                            3a3.5.1-0ubuntu0breezy1_i386.deb) ...
Unpacking replacement libksieve0 ...
Errors were encountered while processing:
 /var/cache/apt/archives/kdevelop3-dev_4%3a3.3.1-0ubuntu0breezy1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Im trying to upgrade from KDE 3.5.0.

---

### Post by zojas on 2006-02-17
kdevelop3-dev and kdevelop3 are conflicting. my guess: try apt-get remove kdevelop3 kdevelop3-dev, then apt-get dist-upgrade, then apt-get install kdevelop3 kdevelop3-dev

---

### Post by cocozz on 2006-02-17
[QUOTE=fabirulo]sorry but:

nosotros@ubuntu:~$ sudo kedit /etc/apt/sources.list
sudo: kedit: command not found

...I'm begginer yes.[/QUOTE]


Just use another KDE's text editor, kate

nosotros@ubuntu:~$ sudo kate /etc/apt/sources.list

---

### Post by Adrian on 2006-02-17
[QUOTE=cocozz]Just use another KDE's text editor, kate

nosotros@ubuntu:~$ sudo kate /etc/apt/sources.list[/QUOTE]

If that does not work, use **kdesu** instead of **sudo**.

(or use kwrite instead of kate)

---

### Post by Feldon on 2006-02-19
I was running pretty much a clean install of Kubuntu Breezy 5.10.  I followed the instructions on the website to upgrade to kde 3.5.1.  When I went into Adept and did the "Fetch Updates" it found 68 upgradeable packages.  However, when I hit "Full Upgrade" nothing happened!  It held back all 68.

So then I renamed the "deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main" to "deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main" and did the "Fetch Updates", "Full Upgrade", "Commit Changes".  This time it upgraded a whole bunch of packages, leaving me with a handful held back.

So then I renamed the source back to "deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main" and did the "Fetch Updates", "Full Uprade", "Commit Changes".  This time, it again upgraded a whole bunch of pacakges, but instead of having the 68 held back, I only have 3 pacakges held back; specifically: kdelibs-bin, kdelibs4c2 and kdegraphics-kfile-plugins.

I've since renamed the source "deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main" to "deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) breezy main" and added the source "deb-src [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) breezy main", but its still sitting with those 3 packages held back.

I should add that the only changes I've made to my default sources.list have been to remove the CD-rom src, and add the above sources.  i.e. I haven't enabled the universe or back-port reposotories.

Any suggestions?

---

### Post by tadashi on 2006-02-19
okay dumb question.  How do I get KDE to run?  I followed all the instructions and downloaded the packages (in the 2nd post).  When I use kde-config --version it says 3.5.1.  I rebooted and my desktop still looks like the old gnome.  I thought I was using KDE but not so sure now.

---

### Post by Adrian on 2006-02-19
[QUOTE=tadashi]okay dumb question.  How do I get KDE to run?  I followed all the instructions and downloaded the packages (in the 2nd post).  When I use kde-config --version it says 3.5.1.  I rebooted and my desktop still looks like the old gnome.  I thought I was using KDE but not so sure now.[/QUOTE]

You should be able to select KDE from the "Session" menu on the login screen (i.e. where you type your name and password).

---

### Post by Jucato on 2006-02-19
@Feldon: try enabling the the unvirse and/or restricted repositories.

Just a theory that I have on why some packages might be held back or broken in upgrading to KDE 3.5.1. The updated KDE (kdebase) is found in a breezy main component. but there might be some dependencies found in other components that may be causing the conflict. I think this is especially true for broken packages when you try to install kde-devel after upgrading kdebase. But again, this is just my theory.

---

### Post by tadashi on 2006-02-19
Okay I session only gives me the choice of last, system default, GNOME, and two other GNOME type selections.  Is there a menu file I need to edit?

nm, since it was a fresh Ubuntu load I just switch and loaded up Kubuntu. :p  I did not realize KDE and Gnome were seperated in seperate distros.  Usually it is a menu option.

---

### Post by zazery on 2006-02-20
I followed the sources in the first post and ended up installing KDE 3.5.0. After that I installed multiple things that were for KDE 3.5.1. I'd like to upgrade to kde 3.5.1 but I get the following errors:

```
apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  kdelibs-bin kdelibs4c2

```

Here is my sources.list. It was copied from a post in this thread and I added a few that were suggested from kubuntu.org's page on upgrading to kde 3.5.1.
```
deb http://es.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://es.archive.ubuntu.com/ubuntu breezy main restricted

## MAJOR BUG FIX UPDATES produced after the final release
deb http://es.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://es.archive.ubuntu.com/ubuntu breezy-updates main restricted

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

## UNIVERSE AND MULTIVERSE REPOSITORY (Unsupported by Ubuntu.  Use at own risk.)
## deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## deb http://packages.freecontrib.org/ubuntu/plf breezy free non-free
## deb-src http://packages.freecontrib.org/ubuntu/plf breezy free non-free 

## LATEST KDE VERSION FROM kubuntu.org
deb http://kubuntu.org/packages/kde-latest breezy main

## This was appended from kubuntu.orgs recommended sources for kde 3.5.1
deb http://kubuntu.org/packages/kde351 breezy main
deb ftp://bolugftp.uni-bonn.de/pub/kde/stable/3.5.1/kubuntu breezy main
deb http://www.mirrorservice.org/sites/ftp.kde.org/pub/kde/stable/3.5.1/kubuntu breezy main
deb http://mirror.cc.columbia.edu/pub/software/kde/stable/3.5.1/kubuntu breezy main

```

Any ideas?

---

### Post by Jucato on 2006-02-20
Just some guess work: 
1. Try doing it in adept rather than through apt-get. If I'm not mistaken, I bypassed that problem before that way. But I'm not 100% sure. If that doesn't work:

2.Try disabling the other repositories for 351 because you only need one. Also try to choose which repository you'll use: the kde-latest or the 351 ones. I think they're basically the same, though. But still, it might be good to avoid repository duplications.

---

### Post by zazery on 2006-02-20
That's a good idea, I changed my sources list to only the KDE mirrors that  were suggested by Kubuntu.org to upgrade to KDE. Using Adept there are only 2 packages that have the status upgradable: kdelibs-bin and kdelibs4c2, neither of them will update since they claim they will break the packages.

I'm starting to think maybe the best idea is either to reinstall Kubuntu or if anyone knows how to downgrade to the KDE that comes with Breezy. Could anyone tell me how to downgrade KDE? I'm used to installing from source or tgz binaries.

---

### Post by Jucato on 2006-02-20
I personally don't recommend downgrading because you might end up messing your system and actually reinstalling everything. If your system is a bit new, I'd say you're better off reinstalling. I just hope that your /home is on a different partition. That way, your data and your user settings will be intact.

If you don't mind my asking again, regarding kdelibs-bin and kdelibs4c2, what version is installed and what version is available? You can see them in the short summaries provided by Adept when you click the green ">" symbol beside each package.

Last suggestion: if this still doesn't work... well... just try. Have you installed the package kdebase?

---

### Post by zazery on 2006-02-20
Installing kdebase fixed the problem, it updated those 2 packages I couldn't update before. Those packages were for kde 3.5.0, and the upgrade was for 3.5.1 so it made sense that Adept was holding them back from being updated. I updated the 'kde' package as well since I was still experiencing problems with my 'Systems Settings' program. Now all my kde related issues have been resolved, though with a lot more software installed than before. Not an issue since I like most of them.

Thanks for your help Fenyx.

---

### Post by Jucato on 2006-02-20
No problem! Glad I could help! :D

---

### Post by Feldon on 2006-02-21
kdebase was uninstalled.

It allowed me to install it but it didn't make a difference.

---

### Post by Jucato on 2006-02-21
ok, please check if kdelibs is also installed. It might help. Good luck!

---

### Post by Proleter on 2006-02-22
[QUOTE=dresnu]@ryanakca: you 've probably already done so but just check again that the addresses in the sources.list are correct. It might be a temporary problem with the mirrors your trying to contact. Maybe use some other mirror where you can. If you don't solve it, try doing this: I read it somewhere on this board because I had a similar problem.** Comment out all lines in your sources.list and save it. Then run "sudo apt-get update"(which obviously does nothing) and then open up again the sources.list and uncomment the mirrors you need. Then just "sudo apt-get update" and "sudo apt-get upgrade"**. If it works don't ask me why, but that did just the trick for me.[/QUOTE]

Bolded text helped me installing the kde.
I have to say that I was very sceptic about this one, since I tried everithing that Google came up with.
Thanks.

---

### Post by j2fraser on 2006-03-03
[QUOTE=zazery]Installing kdebase fixed the problem, it updated those 2 packages I couldn't update before.[/QUOTE]
I am having the same problem many people here have been experiencing and I have a bad feeling that my KDE is irretrievably broken! I obtained the key successfully, added "deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main" to sources.list, did an *apt-get update* and then *apt-get upgrade*. I then see...

> The following packages have been kept back:
  akregator ark artsbuilder kaddressbook kamera kappfinder karm kate
  kaudiocreator kcontrol kcron kdeadmin-kfile-plugins kdebase-bin
  kdebase-kio-plugins kdegraphics-kfile-plugins kdelibs-bin kdelibs4c2
  kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing
  kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-wizards
  kdeprint kdesktop kdm kfind kghostview kgoldrunner khelpcenter kicker
  klaptopdaemon klipper kmail kmenuedit kmilo kmix knetworkconf knotes
  konq-plugins konqueror konqueror-nsplugins konsole kontact kooka kopete
  korganizer kpdf kpf kppp krdc krfb kscd kscreensaver ksmserver ksnapshot
  ksplash ksvg ksysguard ksysguardd kuser kwalletmanager kwifimanager kwin
  libkcddb1 libkdegames1 libkonq4 libkpimexchange1 libkpimidentities1
  libkscan1 libksieve0 libktnef1
0 upgraded, 0 newly installed, 0 to remove and 73 not upgraded. 
If I then do an *apt-get dist-upgrade*, I see...

> The following packages will be REMOVED:
  kmail ksysguard kubuntu-desktop
The following NEW packages will be installed:
  libpoppler0c2-qt perl-suid
The following packages have been kept back:
  akregator ark artsbuilder kaddressbook kamera kappfinder karm kate
  kaudiocreator kcontrol kcron kdeadmin-kfile-plugins kdebase-bin
  kdebase-kio-plugins kdegraphics-kfile-plugins kdelibs-bin kdelibs4c2
  kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing
  kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-wizards
  kdeprint kdesktop kdm kfind kghostview kgoldrunner khelpcenter kicker
  klaptopdaemon klipper kmenuedit kmilo kmix knetworkconf knotes konq-plugins
  konqueror konqueror-nsplugins konsole kontact kooka kopete korganizer kpdf
  kpf kppp krdc krfb kscd kscreensaver ksmserver ksnapshot ksplash ksvg kuser
  kwalletmanager kwifimanager kwin libkcddb1 libkdegames1 libkonq4
  libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1
The following packages will be upgraded:
  ksysguardd
1 upgraded, 2 newly installed, 3 to remove and 70 not upgraded.
Need to get 132kB of archives.
After unpacking 9048kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
I tried *apt-get install kdebase* and then got the following mess!

> Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kdebase: Depends: kappfinder (>= 4:3.5.1-0ubuntu0breezy1) but 4:3.4.3-0ubuntu6 is to be installed
           Depends: kate (>= 4:3.5.1-0ubuntu0breezy1) but 4:3.4.3-0ubuntu6 is to be installed
           Depends: kcontrol (>= 4:3.5.1-0ubuntu0breezy1) but 4:3.4.3-0ubuntu6 is to be installed
           Depends: kdebase-bin (>= 4:3.5.1-0ubuntu0breezy1) but 4:3.4.3-0ubuntu6 is to be installed
           Depends: kdebase-kio-plugins (>= 4:3.5.1-0ubuntu0breezy1) but 4:3.4.3-0ubuntu6 is to be installed
           Depends: kdepasswd (>= 4:3.5.1-0ubuntu0breezy1) but 4:3.4.3-0ubuntu6 is to be installed
           Depends: kdeprint (>= 4:3.5.1-0ubuntu0breezy1) but 4:3.4.3-0ubuntu6 is to be installed
           Depends: kdesktop (>= 4:3.5.1-0ubuntu0breezy1) but 4:3.4.3-0ubuntu6 is to be installed
           Depends: kfind (>= 4:3.5.1-0ubuntu0breezy1) but 4:3.4.3-0ubuntu6 is to be installed
           Depends: khelpcenter (>= 4:3.5.1-0ubuntu0breezy1) but 4:3.4.3-0ubuntu6 is to be installed
           Depends: kicker (>= 4:3.5.1-0ubuntu0breezy1) but 4:3.4.3-0ubuntu6 is to be installed
           Depends: klipper (>= 4:3.5.1-0ubuntu0breezy1) but 4:3.4.3-0ubuntu6 is to be installed
           Depends: kmenuedit (>= 4:3.5.1-0ubuntu0breezy1) but 4:3.4.3-0ubuntu6 is to be installed
           Depends: konqueror-nsplugins (>= 4:3.5.1-0ubuntu0breezy1) but 4:3.4.3-0ubuntu6 is to be installed
           Depends: konqueror (>= 4:3.5.1-0ubuntu0breezy1) but 4:3.4.3-0ubuntu6 is to be installed
           Depends: konsole (>= 4:3.5.1-0ubuntu0breezy1) but 4:3.4.3-0ubuntu6 is to be installed
           Depends: kpager (>= 4:3.5.1-0ubuntu0breezy1) but it is not going to be installed
           Depends: kpersonalizer (>= 4:3.5.1-0ubuntu0breezy1) but it is not going to be installed
           Depends: ksmserver (>= 4:3.5.1-0ubuntu0breezy1) but 4:3.4.3-0ubuntu6 is to be installed
           Depends: ksplash (>= 4:3.5.1-0ubuntu0breezy1) but 4:3.4.3-0ubuntu6 is to be installed
           Depends: ksysguard (>= 4:3.5.1-0ubuntu0breezy1) but it is not going to be installed
           Depends: ktip (>= 4:3.5.1-0ubuntu0breezy1) but it is not going to be installed
           Depends: kwin (>= 4:3.5.1-0ubuntu0breezy1) but 4:3.4.3-0ubuntu6 is to be installed
           Depends: libkonq4 (>= 4:3.5.1-0ubuntu0breezy1) but 4:3.4.3-0ubuntu6 is to be installed
E: Broken packages


I even tried commenting out all the lines in my sources.list, running *apt-get update* and then changing it back and running through *apt-get upgrade* and *apt-get dist-upgrade* again -- but I got the same results.

I'd be very appreciative of any help!

Thanks!:)

---

### Post by Jucato on 2006-03-04
Hi, could you post your sources.list? I'd like to get a look at it. I don't think anything is broken yet, since you haven't proceeded with any actual upgrading just yet. I presume you are working with KDE 3.4.x?

---

### Post by j2fraser on 2006-03-04
[QUOTE=Fenyx]Hi, could you post your sources.list? I'd like to get a look at it. I don't think anything is broken yet, since you haven't proceeded with any actual upgrading just yet. I presume you are working with KDE 3.4.x?[/QUOTE]

Correct. *kde-config --version* shows KDE 3.4.3

My sources.list is as follows:


# deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main

--

Thanks!

---

### Post by Jucato on 2006-03-04
Some suggestions (not 100% sure if they will work)
1. You could try enabling the universe repos (not the one with multiverse, just the plain universe)
2. can you check if the kdelibs package is installed?

Broken packages usually happen (I think) when there conflicting versions between repositories or sections.

---

### Post by j2fraser on 2006-03-04
I checked Adept and it shows kdelibs not installed. When I select install, it shows **BREAK (install)** under action -- which frankly scares me a little, so I'll pass on it unless I hear otherwise.

Also, isn't it a little hazardous to enable universe repos?

BTW, thanks for helping me!

---

### Post by fkamp on 2006-03-04
I'm in the same boat as klett. Wanted to upgrade to kde 3.5.1 to get rid of the "I can't log in as root in kde" problem. I can't run adept without being able to do it as root. ( I selected a root password on the install as I HATE sudo ) anyway I couldn't run adept so I used apt-get to upgrade kde. This is what I have done so far:

Edited sources.list to enable:
 deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) breezy main
commented out cdrom repository
ran apt-get update
then apt-get upgrade. This took awhile as alot of stuff was upgraded. everything but kde!
checked kde version still says 3.4.3 and I still can't run Adept. 
reran apt-get update 
and apt-get upgrade and got "72 packages were held back" 

This is really frustrating Does anyone have any ideas


Currently trying apt-get dist-upgrade will report back with results:

Well it worked! I am at 3.5.1 now but my root password still will not work in kde su. It works in a console though. Any ideas?

---

### Post by j2fraser on 2006-03-17
I had this same problem (upgrading from KDE 3.4.3) and here is how I dealt with it (you should search [www.kubuntuforums.net]("http://www.kubuntuforums.net") for "3.5.1" to see other approaches that people have successfully used). 

I did a console login and then:

[I]apt-get remove kubuntu-desktop
apt-get remove kde*[/I]

Then I enabled universe repositories in my /etc/apt/sources.list (there are a bunch of good sources.list file samples on Ubuntuforums.org and Kubuntuforums.net). Then I ran:

[I]apt-get install kubuntu-desktop
apt-get install kde[/I]

I couldn't get one package -- k3develop I think it was -- but 3.5.1 booted and appears to be running no problem.

In retrospect, and based on the anxiety I underwent as I ripped the entirety of KDE from my system (as the above approach does), I think I would have just tried enabling universe repositories and tried: 1) apt-get update, 2) apt-get upgrade, 3) apt-get dist-upgrade.

Cheers.

---

### Post by ModusOperandi on 2006-05-06
I found this thread while searching for my problem, so i guess I'll just ask here: I'm trying to upgrade from KDE 3.4.3 to 3.5.2. I'm having the problem where everything is being kept back. I have J. Riddel's key, and not even a dist-upgrade will upgrade the packages that are being held back. What's worse is that when I click upgrade in Adept, it does nothing and trying to upgrade one of the packages says BREAK as the action. My sources.list is:

```
#deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu breezy universe
# deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe
deb http://kubuntu.org/packages/kde352 breezy main
```

---

### Post by Rog131 on 2006-05-07
To ModusOperandi.

gingermark writes in "how to get new KDE?" ([http://ubuntuforums.org/showthread.php?t=169192](http://ubuntuforums.org/showthread.php?t=169192))

> 
I would also add the 3.5 & 3.51 repositories - don't ask me why, it just seems to help avoid problems other people have had.


I can't confirm this but i have upgraded from 3.43 -> 3.5 -> 3.5.1 -> 3.5.2 and haven't had problems.

---

### Post by ModusOperandi on 2006-05-07
Same exact result using just the kde-35 source and all three (35, 351, 352). All 68 packages held back. in konsole, and nothing will upgrade in adept (clicking upgrade changes action to BREAK (upgrade))

---

### Post by Rog131 on 2006-05-07
**From APT HOWTO**
([http://www.debian.org/doc/manuals/apt-howto/index.en.html](http://www.debian.org/doc/manuals/apt-howto/index.en.html))

**About** apt-get -u upgrade
([http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-upgrade](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-upgrade))
> 
The process is very simple. Note that in the first few lines, apt-get says that some packages were kept back. This means that there are new versions of these packages which will not be installed for some reason. Possible reasons are broken dependencies (a package on which it depends doesn't have a version available for download) or new dependencies (the package has come to depend on new packages since the last version).

There's no clean solution for this first case. For the second case, it's sufficient to run apt-get install for the specific package in question, as this will download the dependencies. An even cleaner solution is to use dist-upgrade.


**So try** apt-get -u dist-upgrade
([http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-dist-upgrade](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-dist-upgrade))

---

### Post by ModusOperandi on 2006-05-07
Still no change. I guess I'll just have to wait for Dapper.

---

### Post by Rog131 on 2006-05-07
Did you try ?:

sudo apt-get -u install kate
or kcron,kcontrol, ... (1/68 )

To get a better reason why they're being held back. Dependencies or what ?

---

### Post by TranceVictim24 on 2006-05-13
Okay, I have been trying like hell to upgrade from KDE 3.4 to 3.5.   I have read every single post on this thread and here are my problems.

# kate /etc/apt/sources.list
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-15408' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kate: cannot connect to X server :0.0
kate: ERROR: KUniqueApplication: Registering failed!
kate: ERROR: Communication problem with kate, it probably crashed.


<or if i try to open kedit>
# kedit /etc/apt/sources.list
bash: kedit: command not found


<so I try to install kedit>
apt-get install kedit
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kedit: Depends: kdelibs4c2 (>= 4:3.5.2) but 4:3.4.3-0ubuntu2 is to be installed
E: Broken packages


<or if I try to use kwrite>
kwrite /etc/apt/sources.list
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kwrite: cannot connect to X server :0.0


<taking advice from a post>
# apt-get install -f [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package http:


<taking advice from another post>
# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  akregator ark artsbuilder kaddressbook kamera kappfinder karm kate
  kaudiocreator kcontrol kcron kdeadmin-kfile-plugins kdebase-bin
  kdebase-kio-plugins kdegraphics-kfile-plugins kdelibs-bin kdelibs4c2
  kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing
  kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-wizards
  kdeprint kdesktop kdm kfind kghostview khelpcenter kicker klaptopdaemon
  klipper kmenuedit kmilo kmix knetworkconf knotes konq-plugins konqueror
  konqueror-nsplugins konsole kontact kooka kopete korganizer kpdf kpf kppp
  krdc krfb kscd kscreensaver ksmserver ksnapshot ksplash ksvg kuser
  kwalletmanager kwifimanager kwin libkcddb1 libkonq4 libkpimexchange1
  libkpimidentities1 libkscan1 libksieve0 libktnef1
0 upgraded, 0 newly installed, 0 to remove and 68 not upgraded.


Oddly enough, I had an easier time installing 18 rpms in suse 10.0 to get this working.  I just switched to KUbuntu yesterday and, voila! Here I am.
If anyone could hold my hand and walk me through this, I would really appreciate it.  thanks.

---

