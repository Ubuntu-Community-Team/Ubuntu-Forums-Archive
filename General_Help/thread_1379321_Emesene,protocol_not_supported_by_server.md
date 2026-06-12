---
title: "Emesene,protocol not supported by server"
date: 2010-01-12
forum: General Help
---

### Post by ThrashInvasion on 2010-01-12
[IMG]http://i45.tinypic.com/9pmfky.png[/IMG]

What should i do?I can't sign in...

---

### Post by sxmaxchine on 2010-01-12
i have the same problem im trying to work it out and il let u no if i fix the problem

---

### Post by ThrashInvasion on 2010-01-12
i appreciate it :)

---

### Post by sxmaxchine on 2010-01-12
i looked it up and tried a few things and it appears microsoft has a new protocol now so u wil have to upgrade emesene.
to do this first uninstal emesene 
sudo apt-get remove emesene
now download a new version from here
[http://mirror.pacific.net.au/linux/ubuntu/pool/universe/e/emesene/emesene_1.5-1ubuntu1_all.deb]("http://mirror.pacific.net.au/linux/ubuntu/pool/universe/e/emesene/emesene_1.5-1ubuntu1_all.deb")
and if it says that u fail to meet dependencies then download the file for the dependency it says you dont have from here 
[http://packages.ubuntu.com/karmic/emesene]("http://packages.ubuntu.com/karmic/emesene")
hope this helps it worked for me if u need help just ask

---

### Post by ThrashInvasion on 2010-01-12
It worked for me too!!
Thank you very much!!

---

### Post by gmolleda on 2010-01-15
In my Ubuntu 9.04 Jaunty the last version for python-support is 0.8, and the new emesene deb package need the python-support (>= 0.9)

The solution is install first the python-support, you can download it from:
[http://packages.ubuntu.com/karmic/all/python-support/download](http://packages.ubuntu.com/karmic/all/python-support/download)
(information source: [http://forum.emesene.org/index.php/topic,2256.0.html](http://forum.emesene.org/index.php/topic,2256.0.html))

And later you can install the emesene deb package.

&#284;is la revido!

---

### Post by yannis on 2010-01-31
&#947;&#949;&#953;&#945; &#963;&#959;&#965; &#960;&#945;&#964;&#961;&#953;&#974;&#964;&#951;, &#954;&#945;&#953; &#947;&#969; &#949;&#943;&#967;&#945; &#964;&#959; &#943;&#948;&#953;&#959; &#960;&#961;&#972;&#946;&#955;&#951;&#956;&#945; &#945;&#955;&#955;&#940; &#964;&#959; &#941;&#955;&#965;&#963;&#945; &#945;&#955;&#955;&#953;&#974;&#962;!

I went to the [www.emesene.org](www.emesene.org) at the download section and i downloaded the source, i extracted and i run 'emesene'! here you are! if you have any problem it will say it to you. i.e. you can't have spell plugin if you don't have python-gnome2-extras so you type 'sudo apt-get install python-gnome2-extras' and you are ready!

what i did exactly

```
$ wget http://downloads.sourceforge.net/project/emesene/emesene-1.6/emesene-1.6.tar.gz?use_mirror=sunet
$ tar -zxvf emesene-1.6.tar.gz
$ sudo mv emesene-1.6 /usr/local
$ sudo touch /usr/bin/emesene
$ gksudo /usr/bin/emesene
```

in there you write

```
#!/bin/sh
exec python /usr/local/emesene-1.6/Controller.py
```

and continue
```
$ sudo chmod +x /usr/bin/emesene
$ sudo touch /usr/share/applications/emesene.desktop
$ gksudo /usrshare/applications/emesene.desktop
```

and in there write
```
[Desktop Entry]
Name=Emesene
GenericName=Emesene
Comment=MSN Messenger client
Exec=emesene
Icon=/usr/local/emesene-1.6/emesene-logo.png
Terminal=false
Type=Application
Categories=Network;InstantMessaging;


```

the next time you login your menu will be ok!

if you want to start from terminal type 'emesene'!

---

