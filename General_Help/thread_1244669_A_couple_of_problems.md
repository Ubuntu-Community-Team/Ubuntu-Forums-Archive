---
title: "A couple of problems"
date: 2009-08-19
forum: General Help
---

### Post by vegetosayajin on 2009-08-19
Hello,I recently installed Ubuntu 9.04 Desktop thanks to wubi.
I have 2 problems.One of them is that all my cyrilic documents are unreadable.That includes the song info in Rhythmbox,subtitle files in bulgarian for movies,and simple text files.
Here are some screenshots if I don't make much sense:
[[IMG]http://www.pic-bg.net/files/5xczbtexnl3k8v72bkcgn4m2v7ef27whf612tbqk_thumb.png[/IMG]](http://www.pic-bg.net/files/5xczbtexnl3k8v72bkcgn4m2v7ef27whf612tbqk.png) [[IMG]http://www.pic-bg.net/files/ag7rqnrxtk1ctcrd56wd65vn3dqjipn8kvkiaed8_thumb.png[/IMG]](http://www.pic-bg.net/files/ag7rqnrxtk1ctcrd56wd65vn3dqjipn8kvkiaed8.png) [[IMG]http://www.pic-bg.net/files/h2nbpcoiqi9bb3xwprwtass058yctlzg2i1itmjv_thumb.png[/IMG]](http://www.pic-bg.net/files/h2nbpcoiqi9bb3xwprwtass058yctlzg2i1itmjv.png)

The other problem is with the flash player in Mozilla Firefox.
When there is a video in youtube(example) first it shows a gray screen with a play button and when I press it then the video becomes visible.
The volume scroll in all the video sites doesn't work.
Maby there are more problems,but these are the two that I can't figure out.

I'm a windows user so don't be too hard on me XD

---

### Post by blazemore on 2009-08-19
The first problem: I suggest installing the package "console-cyrillic"

Do this by going to Applications->Accesories->Terminal, then type
```
sudo apt-get install console-cyrillic
```
Press Enter, type your password, then press Enter again

The second problem I think you installed a Firefox extension that makes this happen? Check your extensions list (Tools -> Addons) for an addon called NoFlash or similar.

---

### Post by matthewbpt on 2009-08-19
In the text editor, if you right click the text, the second to last option in the menu allows you to change input method and you can choose Cyrillic as an input method, hope that helps.

---

### Post by vegetosayajin on 2009-08-19
Both methods don't work.

[FONT="Lucida Console"]My ubuntu automatically installed in bulgarian language,is that of any help?
All the menus and everything else is in bulgarian except these files up.[/FONT]

---

### Post by vegetosayajin on 2009-08-19
please :(

---

### Post by vegetosayajin on 2009-08-20
```
ivo@ubuntu:~$ sudo apt-get install console-cyrillic
&#1063;&#1077;&#1090;&#1077;&#1085;&#1077; &#1085;&#1072; &#1089;&#1087;&#1080;&#1089;&#1098;&#1094;&#1080;&#1090;&#1077; &#1089; &#1087;&#1072;&#1082;&#1077;&#1090;&#1080;... &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
&#1048;&#1079;&#1075;&#1088;&#1072;&#1078;&#1076;&#1072;&#1085;&#1077; &#1085;&#1072; &#1076;&#1098;&#1088;&#1074;&#1086;&#1090;&#1086; &#1089;&#1098;&#1089; &#1079;&#1072;&#1074;&#1080;&#1089;&#1080;&#1084;&#1086;&#1089;&#1090;&#1080;       
&#1063;&#1077;&#1090;&#1077;&#1085;&#1077; &#1085;&#1072; &#1080;&#1085;&#1092;&#1086;&#1088;&#1084;&#1072;&#1094;&#1080;&#1103;&#1090;&#1072; &#1079;&#1072; &#1089;&#1098;&#1089;&#1090;&#1086;&#1103;&#1085;&#1080;&#1077;&#1090;&#1086;... &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
console-cyrillic &#1074;&#1077;&#1095;&#1077; &#1077; &#1085;&#1072;&#1081;-&#1085;&#1086;&#1074;&#1072;&#1090;&#1072; &#1074;&#1077;&#1088;&#1089;&#1080;&#1103;.
&#1057;&#1083;&#1077;&#1076;&#1085;&#1080;&#1090;&#1077; &#1087;&#1072;&#1082;&#1077;&#1090;&#1080; &#1089;&#1072; &#1073;&#1080;&#1083;&#1080; &#1080;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1085;&#1080; &#1072;&#1074;&#1090;&#1086;&#1084;&#1072;&#1090;&#1080;&#1095;&#1085;&#1086; &#1080; &#1074;&#1077;&#1095;&#1077; &#1085;&#1077; &#1089;&#1072; &#1085;&#1077;&#1086;&#1073;&#1093;&#1086;&#1076;&#1080;&#1084;&#1080;:
  kdebase-runtime-data-common libqt4-qt3support libxine1-x librdf0 libqt4-test
  libqt4-script libqt4-designer libqt4-network libqt4-dbus
  libboost-program-options1.35.0 kdelibs5 libxcb-xv0 phonon libexiv2-5
  librasqal1 libqt4-opengl khelpcenter4 libqt4-xmlpatterns libakonadiprivate1
  libsoprano4 kde-icons-oxygen libqt4-help libclucene0ldbl libqtcore4
  python-sip4 kdepimlibs-data qt4-qtconfig libxine1-console soprano-daemon
  libqt4-sql libqt4-svg python-qt4-common libphonon4 libqt4-xml
  libqt4-assistant libplasma3 libxine1-misc-plugins phonon-backend-gstreamer
  kdepimlibs5 kdelibs-bin libqtgui4 redland-utils libpq5 libstreams0
  libqt4-webkit exiv2 kdelibs5-data kdebase-runtime libqt4-sql-mysql
  libxcb-shape0 libaudio2 libxcb-shm0 kdebase-runtime-data
  kdebase-runtime-bin-kde4 libxine1-bin libstreamanalyzer0 libxine1
&#1048;&#1079;&#1087;&#1086;&#1083;&#1079;&#1074;&#1072;&#1081;&#1090;&#1077; „apt-get autoremove“ &#1079;&#1072; &#1076;&#1072; &#1075;&#1080; &#1087;&#1088;&#1077;&#1084;&#1072;&#1093;&#1085;&#1077;&#1090;&#1077;.
0 &#1072;&#1082;&#1090;&#1091;&#1072;&#1083;&#1080;&#1079;&#1080;&#1088;&#1072;&#1085;&#1080;, 0 &#1085;&#1086;&#1074;&#1080; &#1080;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1085;&#1080;, 0 &#1079;&#1072; &#1087;&#1088;&#1077;&#1084;&#1072;&#1093;&#1074;&#1072;&#1085;&#1077; &#1080; 0 &#1073;&#1077;&#1079; &#1087;&#1088;&#1086;&#1084;&#1103;&#1085;&#1072;.
ivo@ubuntu:~$ 

```
It says that the packages have been installed and no longer needed.
But the text files in cyrillic are still unreadable,what do I have to do? >.<

---

