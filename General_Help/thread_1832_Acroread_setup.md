---
title: "Acroread setup"
date: 2004-10-23
forum: General Help
---

### Post by vulpes on 2004-10-23
In the ubuntu.com archive, and elsewhere, I found the acrobat .deb files (acroread, acroread-plugin, and acroread-debian-files). When I use 'dpkg -i acroread*" everything installs, but when trying to run 'acroread' I get:

/usr/lib/Acrobat5/bin/acroread: no such file or directory

So, I created a symlink in /usr/lib/Acrobat5/bin/acroread to acroread.sh (ln -s acroread.sh acroread).

I then needed to edit the acroread.sh file, making the following change

install_dir=/usr/lib/Acrobat5/Reader

Now everything is working. If someone knows of a better or simpler way, please tell. :-)

---

### Post by adbak on 2004-10-24
Open Synaptic or terminal and search for acroread, acroread-plugin, and acroread-debian-files.  Download and install each of those.  This should solve your problem.  You will probably need to activate the universe repositories, I can't remember.

---

### Post by shufla on 2004-10-25
Hello,

Exactly you need to manually add `mutliverse', look:

```

shufla@hardin:~ $ apt-cache show acroread | egrep ^Section
Section: multiverse/text

```

Here's my /etc/apt/sources.list multiverse add-on:
```

deb http://archive.ubuntu.com/ubuntu/ warty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ warty multiverse

```

After that run ```
sudo apt-get update
``` or push refresh button in synaptic.

Best regards,
Shufla

---

### Post by broseman on 2004-11-09
I did a fresh install of ubuntu, activated universe and multiverse and tried to install Acrobat Reader.
I ended up with the same problems as vulpes!

My solution was to change

```
/usr/lib/Acrobat5/bin/acroread "$@"
```
to 
```
/usr/lib/Acrobat5/bin/acroread.sh "$@"
```
in /usr/bin/acroread

and

```
install_dir=REPLACE_ME
```
to
```
install_dir=/usr/lib/Acrobat5/Reader
```
in /usr/lib/Acrobat5/bin/acroread.sh

I would like to ask for changing that in the repositorys. Who should I contact for this?

Greetings,

 broseman

---

### Post by WW on 2004-11-09
For what it's worth, someone also added this to the wiki:

     [http://www.ubuntulinux.org/wiki/HowToGetAdobeAcrobatReaderWorking](http://www.ubuntulinux.org/wiki/HowToGetAdobeAcrobatReaderWorking)

---

### Post by easy_target on 2004-11-22
Hey people.

I've just downloaded acrobat reader From Adobe's Website and I think they did some fixes to the installation process. My file was already setup properly as well as the install_dir entry.

Can someone please confirm that?

Cheers

---

### Post by Monika on 2004-11-26
I followed the instructions on the Wiki link and I can now open acroread, but the only reason I wanted acroread rather than xpdf in the first place, was that in Windows I can open pdf files in Acrobat Reader in firefox tabs and I find that very useful. Wheras the firefox plugin for ubuntu is obviously not working for me :( What should I do?

---

### Post by Monika on 2004-11-26
Oooops, forget I posted. I realized I hadn't restarted Firefox and now that I have it's working :) Sorry!

---

### Post by fashions on 2005-01-10
acroread seems to be removed from universe url's sources listed. found acrobat 5.0.10 at adobe's site. it is a tar file. need suggesstions on install method so synaptic will install/see it?

---

### Post by Maniak on 2005-01-11
There is a Acrobat Reader V7 beta out there (linux version as well) - you have to sign up to their pre-release program - I haven't yet.

Has anyone else tried using Version 7?

---

### Post by fashions on 2005-01-11
[QUOTE=Maniak]There is a Acrobat Reader V7 beta out there (linux version as well) - you have to sign up to their pre-release program - I haven't yet.

Has anyone else tried using Version 7?[/QUOTE]
looked like you could sign up and wait to be selected to receive the ver 7. i didn't.
i did get the other source lists added and installed acroread.
Adobe does have 5.0.10 available as tar file for download.
[download](http://ardownload.adobe.com/pub/adobe/acrobatreader/unix/5.x/linux-5010.tar.gz)

---

### Post by wulf on 2005-01-18
[QUOTE=fashions]looked like you could sign up and wait to be selected to receive the ver 7. i didn't.
i did get the other source lists added and installed acroread.
Adobe does have 5.0.10 available as tar file for download.
[download](http://ardownload.adobe.com/pub/adobe/acrobatreader/unix/5.x/linux-5010.tar.gz)[/QUOTE]
 I downloaded the one in the repository. I used the same solution as vulpes to finish off the installation - it would be nice to see that done automatically. Maybe in Hoary...

Wulf

---

### Post by emperor on 2005-04-05
FYI, Adobe Acrobat reader v7 is available here:
=============================
[ftp://ftp.adobe.com/pub/adobe/reader/unix/7x/7.0/enu/](ftp://ftp.adobe.com/pub/adobe/reader/unix/7x/7.0/enu/)

---

### Post by eixt on 2005-04-06
[QUOTE=broseman]I did a fresh install of ubuntu, activated universe and multiverse and tried to install Acrobat Reader.
I ended up with the same problems as vulpes!

My solution was to change

```
/usr/lib/Acrobat5/bin/acroread "$@"
```
to 
```
/usr/lib/Acrobat5/bin/acroread.sh "$@"
```
in /usr/bin/acroread

and

```
install_dir=REPLACE_ME
```
to
```
install_dir=/usr/lib/Acrobat5/Reader
```
in /usr/lib/Acrobat5/bin/acroread.sh

I would like to ask for changing that in the repositorys. Who should I contact for this?

Greetings,

 broseman[/QUOTE]

I LOVE YOU, I F##KING LOVE YOU.
I have been f##king around with this shit all day. finaly got it going totaly thanks to you. 

 =D>  =D>  =D>  =D>  =D>

---

