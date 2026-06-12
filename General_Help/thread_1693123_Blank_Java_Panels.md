---
title: "Blank Java Panels"
date: 2011-02-22
forum: General Help
---

### Post by iRoN_RoCK on 2011-02-22
I attached screenshots of the website. It should show panels similar to second pic. Do you know any solution? I'm running Ubuntu 10.10. I tried in chromium, google chrome and firefox.

[[IMG]http://img255.imageshack.us/img255/8315/screenshotjl.th.png[/IMG]](http://img255.imageshack.us/i/screenshotjl.png/)[[IMG]http://img87.imageshack.us/img87/1778/95417451.th.jpg[/IMG]](http://img87.imageshack.us/i/95417451.jpg/)

---

### Post by runeh76 on 2011-02-22
What java and flash version u have?
Type ```
about:plugins
``` to address bar

---

### Post by iRoN_RoCK on 2011-02-22
Java(TM) Plug-in 1.6.0_22
Shockwave Flash 10.2 r152

---

### Post by runeh76 on 2011-02-22
Yeah correct

I dont know what u mean those panels? "It should show panels similar to second pic"

Maybe the website is corrupt?

---

### Post by iRoN_RoCK on 2011-02-22
Right side and bottom side panels which exists on second pic is supposed to be shown but it is just blank. Website runs ok on windows 7.
First pic was taken in Ubuntu and second was taken in windows.

---

### Post by runeh76 on 2011-02-22
Aah okey :)

hmm it could be just some java setting? Have u tryed to check ur settings in Java plugin control panel? I dont know, just quessing..

---

### Post by iRoN_RoCK on 2011-02-22
I can't find any settings about this

---

### Post by runeh76 on 2011-02-22
System/Preferences menu

---

### Post by runeh76 on 2011-02-22
Oh..do u have 32 or 64bit Ubuntu?
And java.. JRE or JDK?

U should use JRE Java version

Synaptic: 
Remove
openJDK Java6 runtime
icedtea 6 plugin
libaccess bridge java
openJDK java 6 web start

and then install:
sun-java6-jre
sun-java6-bin
sun-java6-plugin 

or terminal (command remove also open-JDK java)
(note this is for maverick 32bit)
```
sudo add-apt-repository 'deb http://archive.canonical.com/ubuntu maverick partner'
sudo apt-get update 
sudo apt-get install sun-java6-plugin
sudo apt-get remove icedtea6-plugin openjdk-6-jre
```

---

### Post by iRoN_RoCK on 2011-02-24
It still doesn't work. Also it doesn't pass java test at [http://www.java.com/en/download/testjava.jsp](http://www.java.com/en/download/testjava.jsp) now.

---

### Post by runeh76 on 2011-02-25
```
sudo add-apt-repository 'deb http://archive.canonical.com/ubuntu maverick partner'
sudo apt-get update 
sudo apt-get install sun-java6-plugin
sudo apt-get remove icedtea6-plugin openjdk-6-jre
```

---

### Post by iRoN_RoCK on 2011-02-25
> **runeh76 said:**
> ```
sudo add-apt-repository 'deb http://archive.canonical.com/ubuntu maverick partner'
sudo apt-get update 
sudo apt-get install sun-java6-plugin
sudo apt-get remove icedtea6-plugin openjdk-6-jre
```

No change.

---

### Post by lykeion on 2011-02-26
If you post the link to the site it would be easier to help...

---

### Post by iRoN_RoCK on 2011-03-01
> **lykeion said:**
> If you post the link to the site it would be easier to help...

Site: [www.gamyun.net]("http://www.gamyun.net")

I will guide you the site as it is Turkish. I created a fake account for you. Login area is on the left side of page. Enter these and click "Giris".
```
User(Rumuzunuz):    test12
Password(Sifreniz): pass12
```

After you log in, select "TAVLA" game for example. It is backgammon game. Then select a saloon under "Gamyun salonlari". Another tab will be opened in your browser and Java applet will be load. That's where problem exists. It shows gray box in my pc since when I did what runeh76 said. Anyway I think it can be solved if I install openjdk back.

Real problem happens when you 'sit' on any table.(There must be "Oyna" button on free tables in saloon you entered.) It is supposed to show right and bottom panels like in pics I posted in post #1.

---

### Post by lykeion on 2011-03-03
Okay I tested the site in Firefox and I didn't have the problems you're describing. Managed to open a "game window" and the right and bottom panels appeared as they should (see attached screenshot).

Are you sure it's a Java problem? A lot of similar game sites is Flash-driven, so it might as well be Flash that's causing the problem. Check the help/FAQ of the game site and see if it requires Flash. If so make sure you have Adobe Flash plugin installed (and restart browser and try again after installation):
```
sudo apt-get install adobe-flashplugin
```

---

### Post by iRoN_RoCK on 2011-03-06
I tried that but it's still same. By the way, my friend has this problem too in her pc.

---

### Post by iRoN_RoCK on 2011-05-24
Problem was gone when I installed Ubuntu Natty 11.04. Icedtea and openjdk are pre-installed.

---

### Post by linuxinstalledfromhdd on 2011-05-24
Whenever you do a new installation of Ubuntu make sure you follow a walkthough. It really helps tremendously to install all of the extra plugins and applications.  Check out:

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

:)

---

