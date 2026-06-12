---
title: "Update &amp; Broken Packages"
date: 2012-09-02
forum: General Help
---

### Post by Condor Cluster on 2012-09-02
Hi,

I've just updated my system via Ubuntu Tweak, and the cleaned with Packaged Cleanup.  UT removed a lot of packages, I didn't check properly to see what it removed :(

It has removed Libreoffice and some other stuff I actually wanted to keep, and now when I try and reinstall Libreoffice, it won't let me stating broken packages, and dependencies not going to be installed!

Any idea what's going on?

Thanks.

---

### Post by raja.genupula on 2012-09-02
actually you can fix broken packages by using ```
sudo apt-get install -f
```. open your terminal and type that command . we need to have error report what you're getting.

p.s : Its always better to use Update manager/ apt-get to update your Ubuntu.you can easily watch and manage what they are doing with your PC .

---

### Post by Condor Cluster on 2012-09-02
that command gives:

[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[/I] 
Still can't seem to reinstall Libreoffice :(

Says it depends on other Libre packages that aren't going to be installed?

---

### Post by Condor Cluster on 2012-09-02
when I try to reinstall Libreoffice:

[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  libreoffice: Depends: libreoffice-core (= 1:3.5.4-0ubuntu1~lucid1) but it is not going to be installed
               Depends: libreoffice-writer but it is not going to be installed
               Depends: libreoffice-calc but it is not going to be installed
               Depends: libreoffice-impress but it is not going to be installed
               Depends: libreoffice-draw but it is not going to be installed
               Depends: libreoffice-math but it is not going to be installed
               Depends: libreoffice-base but it is not going to be installed
               Depends: libreoffice-filter-mobiledev but it is not going to be installed
               Depends: libreoffice-java-common (>= 1:3.5.4~) but it is not going to be installed
               Recommends: libreoffice-gnome but it is not going to be installed or
                           libreoffice-kde but it is not going to be installed
E: Broken packages
[/I]

---

### Post by raja.genupula on 2012-09-02
[http://ubuntuforums.org/showthread.php?p=11337815](http://ubuntuforums.org/showthread.php?p=11337815) 

similar link

---

### Post by Condor Cluster on 2012-09-02
Checked the link out, pretty sure its not related to old openoffice stuff.

Was thinking could it be a problem with the libreoffice ppa online?

---

### Post by raja.genupula on 2012-09-02
ok you got installed Open office   ??

---

### Post by Condor Cluster on 2012-09-02
No openoffice installed on my system.

I had libreoffice working fine for ages until a recent update that removed it, now I can't re-install it back!

---

### Post by raja.genupula on 2012-09-02
could you provide me  the log of UT ?

---

### Post by Condor Cluster on 2012-09-02
Could do, not sure where the Ubuntu Tweak stores it's log files though?

EDIT: just saw an older thread [http://ubuntuforums.org/showthread.php?t=1594111&page=3](http://ubuntuforums.org/showthread.php?t=1594111&page=3) 
Think if I wait a few days, the ppa packages 'may sort themselves out'?

---

### Post by captain_rob on 2012-09-03
A libre-office update installed libexttextcat-data and removed the whole libreoffice suite. I removed that package but now can't install libreoffice anymore and get the same messages as above:

[I]
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
libreoffice: Depends: libreoffice-core (= 1:3.5.4-0ubuntu1~lucid1) but it is not going to be installed
Depends: libreoffice-writer but it is not going to be installed
Depends: libreoffice-calc but it is not going to be installed
Depends: libreoffice-impress but it is not going to be installed
Depends: libreoffice-draw but it is not going to be installed
Depends: libreoffice-math but it is not going to be installed
Depends: libreoffice-base but it is not going to be installed
Depends: libreoffice-filter-mobiledev but it is not going to be installed
Depends: libreoffice-java-common (>= 1:3.5.4~) but it is not going to be installed
Recommends: libreoffice-gnome but it is not going to be installed or
libreoffice-kde but it is not going to be installed
E: Broken packages[/I]

I tried a lot of suggestions but nothing helps. I am also beginning to think that there is something wrong with the ppa

---

### Post by Condor Cluster on 2012-09-03
Well, if more people are reading this, and post similar symptoms then it does point towards a messed up libreoffice ppa :-k

---

### Post by ullix on 2012-09-03
same problem here on ubuntu 10.04. Libreoffice was running well, but somehow got removed, and can no longer be installed.

it says unmet dependencies and broken packages. From the terminal:

> ~$ sudo apt-get -f install libreoffice
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Status-Informationen einlesen... Fertig
Einige Pakete konnten nicht installiert werden. Das kann bedeuten, dass
Sie eine unmögliche Situation angefordert haben oder dass, wenn Sie die
Unstable-Distribution verwenden, einige erforderliche Pakete noch nicht
erstellt wurden oder Incoming noch nicht verlassen haben.
Die folgenden Informationen helfen Ihnen vielleicht, die Situation zu lösen:

Die folgenden Pakete haben nicht-erfüllte Abhängigkeiten:
  libreoffice: Hängt ab: libreoffice-core (= 1:3.5.4-0ubuntu1~lucid1) soll aber nicht installiert werden
               Hängt ab: libreoffice-writer soll aber nicht installiert werden
               Hängt ab: libreoffice-calc soll aber nicht installiert werden
               Hängt ab: libreoffice-impress soll aber nicht installiert werden
               Hängt ab: libreoffice-draw soll aber nicht installiert werden
               Hängt ab: libreoffice-math soll aber nicht installiert werden
               Hängt ab: libreoffice-base soll aber nicht installiert werden
               Hängt ab: libreoffice-filter-mobiledev soll aber nicht installiert werden
               Hängt ab: libreoffice-java-common (>= 1:3.5.4~) soll aber nicht installiert werden
E: Kaputte Pakete


Now what? I need the -calc. Like NOW!

---

### Post by Condor Cluster on 2012-09-03
Package Manager History shows:

```
Commit Log for Sun Sep  2 09:35:23 2012


Removed the following packages:
libexttextcat0
libreoffice
libreoffice-base
libreoffice-base-core
libreoffice-calc
libreoffice-common
libreoffice-core
libreoffice-draw
libreoffice-emailmerge
libreoffice-filter-mobiledev
libreoffice-gnome
libreoffice-gtk
libreoffice-help-en-gb
libreoffice-impress
libreoffice-java-common
libreoffice-math
libreoffice-style-human
libreoffice-style-tango
libreoffice-writer
python-uno

Upgraded the following packages:
libexttextcat-data (3.2.0-1ubuntu1~lucid1) to 3.3.1-2~lucid1
libgraphite2-2.0.0 (1.0.3.real-1~lucid1) to 1.1.3-1~lucid1
libvisio-0.0-0 (0.0.17-1~lucid1) to 0.0.19-1~lucid2


Commit Log for Sun Sep  2 12:28:00 2012


Removed the following packages:
libcmis-0.2-0
libexttextcat-data
libgraphite2-2.0.0
libhsqldb-java
libhunspell-1.3-0
libmythes-1.2-0
libservlet2.5-java
libvisio-0.0-0
libwpd-0.9-9
libwpg-0.2-2
libwps-0.2-2
libxerces2-java
ttf-dejavu

Commit Log for Sun Sep  2 17:25:28 2012


Removed the following packages:
uno-libs3
ure

Commit Log for Sun Sep  2 18:20:51 2012


Upgraded the following packages:
ttf-opensymbol (1:3.2.0-7ubuntu4.4) to 2:102.2+LibO3.5.4-0ubuntu1~lucid1

Installed the following packages:
fonts-opensymbol (2:102.2+LibO3.5.4-0ubuntu1~lucid1)

```

---

### Post by ullix on 2012-09-03
note this comment to my bug report [https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1045433](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1045433) 

> Please use the stable ppa for the 3.5 series: ppa:libreoffice/libreoffice-3-5

You can indeed install libreoffice once this ppa is activated in your repositories

---

### Post by Condor Cluster on 2012-09-03
Thanks ullix!

Using the ppa ***ppa:libreoffice/libreoffice-3-5 ***did the trick, managed to reinstall all the packages that the default ppa removed.

:guitar:

---

### Post by henged on 2012-09-04
An alternative solution (which worked for me) is suggested [here ]("http://askubuntu.com/questions/183507/cannot-install-libreoffice")

"Solution is to force version of the package libexttextcat-data to 3.2.0-1ubuntu1 (not to 3.3.1-2~precise1 by default)."

Thanks to original solution finder!
[]("http://askubuntu.com/questions/183507/cannot-install-libreoffice")

---

### Post by Tank Jr on 2012-09-06
I have the same problem, and now I don't have LibreOffice, and cannot install it either.
It seems the change in libexttextcat version (from 0 to 1.0 ?) needs LibreOffice to be built again against the new library. The LibreOffice ppa  [here]("https://launchpad.net/~libreoffice/+archive/ppa?field.series_filter=precise") has the new libexttextcat, but the LibreOffice has not been built yet against this, it seems.

---

### Post by learning_ on 2012-09-26
> **Condor Cluster said:**
> Well, if more people are reading this, and post similar symptoms then it does point towards a messed up libreoffice ppa :-k

This appears to be a common enough issue to point to the ppa being screwed up, however I followed the guide supplied by a fellow [here]("http://nwlinux.com/how-to-remove-open-office-and-install-libre-office-ubuntu/"). He offered two possible install options, one being the ppa route and the other using a WA state mirror (I'm assuming this directs to his own server or something of the sort in his home state). I tried both approaches and neither worked. I continually receive the following message from terminal:
```
****@****-desktop:~$ sudo apt-get install libreoffice-common libreoffice-gnome libreoffice
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libreoffice: Depends: libreoffice-core (= 1:3.5.4-0ubuntu1~lucid1) but it is not going to be installed
               Depends: libreoffice-writer but it is not going to be installed
               Depends: libreoffice-calc but it is not going to be installed
               Depends: libreoffice-impress but it is not going to be installed
               Depends: libreoffice-draw but it is not going to be installed
               Depends: libreoffice-math but it is not going to be installed
               Depends: libreoffice-base but it is not going to be installed
  libreoffice-common: Depends: libreoffice-style-default or
                               libreoffice-style
  libreoffice-gnome: Depends: libreoffice-core (= 1:3.5.4-0ubuntu1~lucid1) but it is not going to be installed
                     Depends: libreoffice-gtk but it is not going to be installed
E: Broken packages

```
Any advice?

EDIT:

Ok so I saw that I missed a couple posts, so I went in and tried ullix's fix. Added the new ppa (libreoffice/libreoffice-3-5), and deslected the previously used ppa (libreoffice/ppa) and tried again: 
```
sudo apt-get update
sudo apt-get install libreoffice-common libreoffice-gnome libreoffice

```
Worked perfectly. 

Attached is my resources list. Make sure the one I highlighted is selected in your list as well or when you try to install, it won't know where to pull the file from.

THANKS for everyone's help and I hope I helped some as well.

---

