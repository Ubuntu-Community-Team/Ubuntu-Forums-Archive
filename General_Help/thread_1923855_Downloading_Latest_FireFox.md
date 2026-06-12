---
title: "Downloading Latest FireFox"
date: 2012-02-11
forum: General Help
---

### Post by SAltonS on 2012-02-11
I am having problems downloading the newest version of FireFox.  I am running Ubuntu 10.10.

When I go to the FireFox page and click on the download tab, I am asked if I want open the file or save the file.  I have clicked both and the same thing happens, a file is downloaded, but FireFox is not updated.

Any ideas?

---

### Post by raja.genupula on 2012-02-11
you wanna update your firefox to latest version ? 
open your terminal and do this . 

```
sudo add-apt-repository ppa:ubuntu-mozilla-security/ppa 
sudo apt-get update 
sudo apt-get install firefox
```

hope that helps . all the best .

---

### Post by winh8r on 2012-02-11
Please follow this guide as it will probably be easier.


[http://ubuntuforums.org/showthread.php?t=1712247&highlight=firefox+mega+thread]("http://ubuntuforums.org/showthread.php?t=1712247&highlight=firefox+mega+thread")



Also remember to run the update manager and ensure all the repositories are enabled.


Any other issues you have can be resolved by a simple search of the forums using the search box in the top right of the page. Most of the issues you will encounter have been experienced before by other people, and there is usually a thread marked [SOLVED] which will give you an instant answer and solution rather than waiting for someone to help you.


Hope this helps you.

---

### Post by SAltonS on 2012-02-11
What are the different channels / versions (beta, aurara)  and PPA's??

Just too confusing.  I am running Ubuntu 10.10 32 Bit Desktop.

---

### Post by MrMeen on 2012-02-11
Im having kinda the same issue. im using 9.10 live and i cant download ANYTHING.

---

### Post by SAltonS on 2012-02-11
We do not need help.  We need somebody who knows what they are doing to TELL us which version to download!

---

### Post by josephmills on 2012-02-11
after you  download the new fire fox open your terminal and change directions to where you have downloaded it 
exsample 
```
cd ~/Downloads
```
then cd into the firefox folder. you will see two different firefox files one is called firefox other is something like firefox-bin. these are the important files. 
In your terminal now do a ```
pwd
``` this will print the working directory. write it down. 

Next in terminal ```
cd /usr/share/applications 
``` then 
```
gksudo gedit firefox.desktop 
```
you should get something that looks like this 
```

[Desktop Entry]
Version=1.0
Name=Firefox Web Browser
Name[ar]=&#1605;&#1578;&#1589;&#1601;&#1581; &#1575;&#1604;&#1608;&#1616;&#1576; &#1601;&#1614;&#1610;&#1614;&#1585;&#1601;&#1615;&#1603;&#1618;&#1587;
Name[ast]=Restolador web Firefox
Name[bn]=&#2475;&#2494;&#2479;&#2492;&#2494;&#2480;&#2475;&#2453;&#2509;&#2488; &#2451;&#2479;&#2492;&#2503;&#2476; &#2476;&#2509;&#2480;&#2494;&#2441;&#2460;&#2494;&#2480;
Name[ca]=Navegador web Firefox
Name[cs]=Firefox Webový prohlíže&#269;
Name[da]=Firefox - internetbrowser
Name[es]=Navegador web Firefox
Name[et]=Firefoxi veebibrauser
Name[fa]=&#1605;&#1585;&#1608;&#1585;&#1711;&#1585; &#1575;&#1740;&#1606;&#1578;&#1585;&#1606;&#1578;&#1740; Firefox
Name[fi]=Firefox-selain
Name[fr]=Navigateur Web Firefox
Name[gl]=Navegador web Firefox
Name[he]=&#1491;&#1508;&#1491;&#1508;&#1503; &#1492;&#1488;&#1497;&#1504;&#1496;&#1512;&#1504;&#1496; Firefox
Name[hr]=Firefox web preglednik
Name[hu]=Firefox webböngész&#337;
Name[it]=Firefox Browser Web
Name[ja]=Firefox &#12454;&#12455;&#12502;&#12539;&#12502;&#12521;&#12454;&#12470;
Name[ko]=Firefox &#50937; &#48652;&#46972;&#50864;&#51200;
Name[ku]=Geroka torê Firefox
Name[lt]=Firefox interneto naršykl&#279;
Name[nb]=Firefox Nettleser
Name[nl]=Firefox webbrowser
Name[nn]=Firefox Nettlesar
Name[no]=Firefox Nettleser
Name[pl]=Przegl&#261;darka WWW Firefox
Name[pt]=Firefox Navegador Web
Name[pt_BR]=Navegador Web Firefox
Name[ro]=Firefox – Navigator Internet
Name[ru]=&#1042;&#1077;&#1073;-&#1073;&#1088;&#1072;&#1091;&#1079;&#1077;&#1088; Firefox
Name[sk]=Firefox - internetový prehliada&#269;
Name[sl]=Firefox spletni brskalnik
Name[sv]=Webbläsaren Firefox
Name[ug]=Firefox &#1578;&#1608;&#1585;&#1603;&#1734;&#1585;&#1711;&#1736;
Name[uk]=&#1042;&#1077;&#1073;-&#1073;&#1088;&#1072;&#1091;&#1079;&#1077;&#1088; Firefox
Name[vi]=Trình duy&#7879;t web Firefox
Name[zh_CN]=Firefox &#32593;&#32476;&#27983;&#35272;&#22120;
Name[zh_TW]=Firefox &#32178;&#36335;&#28687;&#35261;&#22120;
Comment=Browse the World Wide Web
Comment[ar]=&#1578;&#1589;&#1601;&#1581; &#1575;&#1604;&#1588;&#1576;&#1603;&#1577; &#1575;&#1604;&#1593;&#1606;&#1603;&#1576;&#1608;&#1578;&#1610;&#1577; &#1575;&#1604;&#1593;&#1575;&#1604;&#1605;&#1610;&#1577;
Comment[ast]=Restola pela Rede
Comment[bn]=&#2439;&#2472;&#2509;&#2463;&#2494;&#2480;&#2472;&#2503;&#2463; &#2476;&#2509;&#2480;&#2494;&#2441;&#2460; &#2453;&#2480;&#2497;&#2472;
Comment[ca]=Navegueu per la web
Comment[cs]=Prohlížení stránek World Wide Webu
Comment[da]=Surf på internettet
Comment[de]=Im Internet surfen
Comment[es]=Navegue por la web
Comment[et]=Lehitse veebi
Comment[fa]=&#1589;&#1601;&#1581;&#1575;&#1578; &#1588;&#1576;&#1705;&#1607; &#1580;&#1607;&#1575;&#1606;&#1740; &#1575;&#1740;&#1606;&#1578;&#1585;&#1606;&#1578; &#1585;&#1575; &#1605;&#1585;&#1608;&#1585; &#1606;&#1605;&#1575;&#1740;&#1740;&#1583;
Comment[fi]=Selaa Internetin WWW-sivuja
Comment[fr]=Naviguer sur le Web
Comment[gl]=Navegar pola rede
Comment[he]=&#1490;&#1500;&#1497;&#1513;&#1492; &#1489;&#1512;&#1495;&#1489;&#1497; &#1492;&#1488;&#1497;&#1504;&#1496;&#1512;&#1504;&#1496;
Comment[hr]=Pretražite web
Comment[hu]=A világháló böngészése
Comment[it]=Esplora il web
Comment[ja]=&#12454;&#12455;&#12502;&#12434;&#38322;&#35239;&#12375;&#12414;&#12377;
Comment[ko]=&#50937;&#51012; &#46028;&#50500; &#45796;&#45785;&#45768;&#45796;
Comment[ku]=Li torê bigere
Comment[lt]=Naršykite internete
Comment[nb]=Surf på nettet
Comment[nl]=Verken het internet
Comment[nn]=Surf på nettet
Comment[no]=Surf på nettet
Comment[pl]=Przegl&#261;danie stron WWW 
Comment[pt]=Navegue na Internet
Comment[pt_BR]=Navegue na Internet
Comment[ro]=Naviga&#539;i pe Internet
Comment[ru]=&#1044;&#1086;&#1089;&#1090;&#1091;&#1087; &#1074; &#1048;&#1085;&#1090;&#1077;&#1088;&#1085;&#1077;&#1090;
Comment[sk]=Prehliadanie internetu
Comment[sl]=Brskajte po spletu
Comment[sv]=Surfa på webben
Comment[ug]=&#1583;&#1735;&#1606;&#1610;&#1575;&#1583;&#1609;&#1603;&#1609; &#1578;&#1608;&#1585;&#1576;&#1749;&#1578;&#1604;&#1749;&#1585;&#1606;&#1609; &#1603;&#1734;&#1585;&#1711;&#1609;&#1604;&#1609; &#1576;&#1608;&#1604;&#1609;&#1583;&#1735;
Comment[uk]=&#1055;&#1077;&#1088;&#1077;&#1075;&#1083;&#1103;&#1076; &#1089;&#1090;&#1086;&#1088;&#1110;&#1085;&#1086;&#1082; &#1030;&#1085;&#1090;&#1077;&#1088;&#1085;&#1077;&#1090;&#1091;
Comment[vi]=&#272;&#7875; duy&#7879;t các trang web
Comment[zh_CN]=&#27983;&#35272;&#20114;&#32852;&#32593;
Comment[zh_TW]=&#28687;&#35261;&#32178;&#38555;&#32178;&#36335;
GenericName=Web Browser
GenericName[ar]=&#1605;&#1578;&#1589;&#1601;&#1581; &#1608;&#1576;
GenericName[ast]=Restolador Web
GenericName[bn]=&#2451;&#2479;&#2492;&#2503;&#2476; &#2476;&#2509;&#2480;&#2494;&#2441;&#2460;&#2494;&#2480;
GenericName[ca]=Navegador web
GenericName[cs]=Webový prohlíže&#269;
GenericName[da]=Webbrowser
GenericName[es]=Navegador web
GenericName[et]=Veebibrauser
GenericName[fa]=&#1605;&#1585;&#1608;&#1585;&#1711;&#1585; &#1575;&#1740;&#1606;&#1578;&#1585;&#1606;&#1578;&#1740;
GenericName[fi]=WWW-selain
GenericName[fr]=Navigateur Web
GenericName[gl]=Navegador Web
GenericName[he]=&#1491;&#1508;&#1491;&#1508;&#1503; &#1488;&#1497;&#1504;&#1496;&#1512;&#1504;&#1496;
GenericName[hr]=Web preglednik
GenericName[hu]=Webböngész&#337;
GenericName[it]=Browser web
GenericName[ja]=&#12454;&#12455;&#12502;&#12539;&#12502;&#12521;&#12454;&#12470;
GenericName[ko]=&#50937; &#48652;&#46972;&#50864;&#51200;
GenericName[ku]=Geroka torê
GenericName[lt]=Interneto naršykl&#279;
GenericName[nb]=Nettleser
GenericName[nl]=Webbrowser
GenericName[nn]=Nettlesar
GenericName[no]=Nettleser
GenericName[pl]=Przegl&#261;darka WWW
GenericName[pt]=Navegador Web
GenericName[pt_BR]=Navegador Web
GenericName[ro]=Navigator Internet
GenericName[ru]=&#1042;&#1077;&#1073;-&#1073;&#1088;&#1072;&#1091;&#1079;&#1077;&#1088;
GenericName[sk]=Internetový prehliada&#269;
GenericName[sl]=Spletni brskalnik
GenericName[sv]=Webbläsare
GenericName[ug]=&#1578;&#1608;&#1585;&#1603;&#1734;&#1585;&#1711;&#1736;
GenericName[uk]=&#1042;&#1077;&#1073;-&#1073;&#1088;&#1072;&#1091;&#1079;&#1077;&#1088;
GenericName[vi]=Trình duy&#7879;t Web
GenericName[zh_CN]=&#32593;&#32476;&#27983;&#35272;&#22120;
GenericName[zh_TW]=&#32178;&#36335;&#28687;&#35261;&#22120;
Exec=firefox %u
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=firefox
Categories=GNOME;GTK;Network;WebBrowser;
MimeType=text/html;text/xml;application/xhtml+xml;application/xml;application/vnd.mozilla.xul+xml;application/rss+xml;application/rdf+xml;image/gif;image/jpeg;image/png;x-scheme-handler/http;x-scheme-handler/https;x-scheme-handler/ftp;x-scheme-handler/chrome;video/webm;
StartupWMClass=Firefox
StartupNotify=true
X-Ayatana-Desktop-Shortcuts=NewWindow;

[NewWindow Shortcut Group]
Name=Open a New Window
Name[ast]=Abrir una ventana nueva
Name[bn]=Abrir una ventana nueva
Name[ca]=Obre una finestra nova
Name[da]=Åbn et nyt vindue
Name[de]=Ein neues Fenster öffnen
Name[es]=Abrir una ventana nueva
Name[fi]=Avaa uusi ikkuna
Name[fr]=Ouvrir une nouvelle fenêtre
Name[gl]=Abrir unha nova xanela
Name[he]=&#1508;&#1514;&#1497;&#1495;&#1514; &#1495;&#1500;&#1493;&#1503; &#1495;&#1491;&#1513;
Name[hr]=Otvori novi prozor
Name[hu]=Új ablak nyitása
Name[it]=Apri una nuova finestra
Name[ja]=&#26032;&#12375;&#12356;&#12454;&#12451;&#12531;&#12489;&#12454;&#12434;&#38283;&#12367;
Name[ku]=Paceyeke nû veke
Name[lt]=Atverti nauj&#261; lang&#261;
Name[nl]=Nieuw venster openen
Name[ro]=Deschide o fereastr&#259; nou&#259;
Name[ru]=&#1054;&#1090;&#1082;&#1088;&#1099;&#1090;&#1100; &#1085;&#1086;&#1074;&#1086;&#1077; &#1086;&#1082;&#1085;&#1086;
Name[sv]=Öppna ett nytt fönster
Name[ug]=&#1610;&#1744;&#1709;&#1609; &#1603;&#1734;&#1586;&#1606;&#1749;&#1603; &#1574;&#1744;&#1670;&#1609;&#1588;
Name[uk]=&#1042;&#1110;&#1076;&#1082;&#1088;&#1080;&#1090;&#1080; &#1085;&#1086;&#1074;&#1077; &#1074;&#1110;&#1082;&#1085;&#1086;
Name[zh_CN]=&#26032;&#24314;&#31383;&#21475;
Name[zh_TW]=&#38283;&#21855;&#26032;&#35222;&#31383;
Exec=firefox -new-window
TargetEnvironment=Unity




```



these are the important parts 

[COLOR="Red"]Exec=firefox %u[/COLOR]


Please change that to to the dir that I told you to write down so if my new firefox is under my downloads I change it to this  

[COLOR="red"]Exec=/home/$USER/Downloads/firefox10.0/firefox [/COLOR]
save it and there you go should be all good now.  let us know how it all works out. 

p.s you could make a new /usr/share/applications/firefox.desktop 
file for the new one also

---

### Post by oldos2er on 2012-02-11
A PPA is a "Personal Package Archive", and "unofficial" repository.
 
[https://help.ubuntu.com/community/Repositories/Ubuntu#Adding_PPAs](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding_PPAs)

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by oldos2er on 2012-02-11
> **MrMeen said:**
> Im having kinda the same issue. im using 9.10 live and i cant download ANYTHING.

9.10 is no longer supported, so its repositories are offline. If you would like help installing a newer (supported) version of Ubuntu, please start your own thread.

---

### Post by pqwoerituytrueiwoq on 2012-02-11
assuming all [dependencies]("http://www.mozilla.org/en-US/firefox/system-requirements.html") are met
use this **sh** script
run it in a terminal and NOT as root
it will install mozilla's verion to your home folder and will update the same was as it would on windows
@**MrMeen**
it will work on 9.10

---

### Post by SAltonS on 2012-02-11
Sorry, but how do you do that, running it NOT as root?

---

### Post by pqwoerituytrueiwoq on 2012-02-12
just do not use [FONT=Courier New]sudo[/FONT] when you run it
use 
```
me@ubuntu-desktop:~$ Downloads/firefox.sh
``` or
```
me@ubuntu-desktop:~$ sh Downloads/firefox.sh
```

---

