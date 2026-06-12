---
title: "Can't run Teamviewer 7"
date: 2012-04-12
forum: General Help
---

### Post by JCM_Pico on 2012-04-12
Hi there,

I'm not being able to run Teamviewer in Ubuntu. I downloaded and installed Debian, Ubuntu (32-bit) that I have found in their site...

I get this message:

```
$ teamviewer
TeamViewer: 7.0.9348
Profile: /home/jcmteixeira (jcmteixeira)
Desktop: gnome
LSB Version:    core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.4 LTS
Release:    10.04
Codename:    lucid
 
Checking setup...

```

---

### Post by jonobr on 2012-04-12
Looking at the message there doesnt appear to be anything wrong indicated,
Im guessing you installation freezes at that point?

Anyway, from [This walk though/]("http://www.liberiangeek.net/2011/12/quickly-install-teamviewer-in-ubuntu-11-10-oneiric-ocelot/") on Oneiric, it seems pretty straight forward, 

Maybe if you look in /var/log directory there may be some logs you could post, however, double check the installation against the above and reinstall would be my recommendation!

---

### Post by JCM_Pico on 2012-04-12
I've reinstalled it and the problem is the same....
In /var/log/ can't find any error associated with teamviewer neither when running dmesg

---

### Post by jonobr on 2012-04-12
I saw a recommendation to run

sudo apt-get -f install

for any dependency issues there may be.

---

### Post by JCM_Pico on 2012-04-12
> **jonobr said:**
> I saw a recommendation to run

sudo apt-get -f install

for any dependency issues there may be.



I've tried that but the result ia the same... I've searched the web and can't find any thing related to this problem :(

---

### Post by jonobr on 2012-04-12
I would normally suggest you make sure your system is update to date

remove the package 

run

```
sudo apt-get update && sudo apt-get upgrade
```

then reinstall

I have never had an issue running the above command, but you do find people complaining about stuff not working after they update their system.
Usually with wireless, so it up to you if you want to give it a try

Cheers

---

### Post by JCM_Pico on 2012-04-13
I've found teamviewer log files and it seams that there's some problem with the wine configuration... I've crossover installed don't know if its incompatible (it shouldn't) ....

```
TeamViewer: 7.0.9348
Profile: /home/jcmteixeira (jcmteixeira)
Desktop: gnome
LSB Version:    core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch
Distributor ID: Ubuntu
Description:    Ubuntu 10.04.4 LTS
Release:        10.04
Codename:       lucid

ldd: /opt/teamviewer/teamviewer/7/wine/drive_c/Program: No such file or directory
ldd: Files/TeamViewer/Version7/tvwine.dll.so: No such file or directory
** Using fallback library for libXtst.so.6
ldd: /opt/teamviewer/teamviewer/7/wine/drive_c/Program: No such file or directory
ldd: Files/TeamViewer/Version7/tvwine.dll.so: No such file or directory

Error: Failed to substitue missing libXtst.so
```

---

### Post by jonobr on 2012-04-13
Hello

Im a bit confused (maybe because I never used or installed teamspeak) but the instruction I sent earlier showed installing teamspeak on ubuntu using apt-get or through the repos in synaptic.

Im not sure why wine is involved?
It didnt mention using wine.

Im thinking you got the windows exe for teamspeak and installed via wine, but again, the package appears to be availble on the repos already.

---

### Post by JCM_Pico on 2012-04-13
> **jonobr said:**
> Hello

Im a bit confused (maybe because I never used or installed teamspeak) but the instruction I sent earlier showed installing teamspeak on ubuntu using apt-get or through the repos in synaptic.

Im not sure why wine is involved?
It didnt mention using wine.

Im thinking you got the windows exe for teamspeak and installed via wine, but again, the package appears to be availble on the repos already.

I dont know why wine ia envolved but I im shoure that I've install from a *.deb

---

### Post by mErchamion on 2012-04-13
Wine is involved because teamviewer is not linux native, so you need a wine platform to run it. in other words, teamviewer is a windows program, and you need wine to make it run. However, as far as I know, installing through the deb should be enough, as it packs a wine server that launches whenever you launch teamviewer.

---

### Post by blackangelpr on 2012-04-14
> **mErchamion said:**
> Wine is involved because teamviewer is not linux native, so you need a wine platform to run it. in other words, teamviewer is a windows program, and you need wine to make it run. However, as far as I know, installing through the deb should be enough, as it packs a wine server that launches whenever you launch teamviewer.

:confused::confused: why you said wine is involved team viewer have a program .deb  [http://www.teamviewer.com/en/download/index.aspx](http://www.teamviewer.com/en/download/index.aspx)    :confused:

---

### Post by daslinkard on 2012-04-14
I just went to this [site]("http://www.teamviewer.com/en/download/index.aspx?os=linux")....selected the 32 bit download for Ubuntu....the file downloaded and the Ubuntu Software Center opened up with me having the option to install Team Viewer 7....it is then in the Unity.

**The link that I have is the same site that you have previously listed.  I chose to download the file (saved it to my downloads) then went to where I saved it....The file saved as "teamviewer_linux.deb" and at that point in time I double-clicked on the downloaded file....it immediately brought me to the Software Center in which I could download Team Viewer on my system.

After clicking on the install button I was prompted for my password....then once the program was downloaded I hit the Super key....typed in Team and there the program was under my applications.

I hope this helps!

---

### Post by Patric42 on 2012-05-23
I just had the same problem and deleting the ~/.teamviewer directory completely solved my problem instantly.

HTH,

Patric

---

