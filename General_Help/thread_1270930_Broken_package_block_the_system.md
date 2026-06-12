---
title: "Broken package block the system"
date: 2009-09-20
forum: General Help
---

### Post by kedmanee on 2009-09-20
It start when I open a page with flash content in the Firefox. From there I changed to the Adobe site. I choose "*.deb for Ubuntu 8.04+*". 
Since this I can not use the package system anymore.
I try reinstall:
```
abc:~# sudo aptitude install adobe-flashplugin
Die folgenden teilweise installierten Pakete werden konfiguriert:
  adobe-flashplugin 
0 Pakete aktualisiert, 2 zusätzlich installiert, 0 werden entfernt und 5 nicht aktualisiert.
Muss 0B/530kB an Archiven herunterladen. Nach dem Entpacken werden 2925kB zusätzlich belegt sein.
Wollen Sie fortsetzen? [Y/n/?] y
E: Ich konnte keine Datei für Paket adobe-flashplugin finden. Das könnte heißen, dass Sie dieses Paket von Hand korrigieren müssen.
Schreibe erweiterte Statusinformationen... Fertig
E: Ich konnte keine Datei für Paket adobe-flashplugin finden. Das könnte heißen, dass Sie dieses Paket von Hand korrigieren müssen.
E: Interner Fehler: Liste der herunterzuladenden Pakete konnte nicht erzeugt werden
```

I try to remove:
```
abc:~# sudo aptitude purge adobe-flashplugin
Die folgenden Pakete werden ENTFERNT:
  adobe-flashplugin{p} 
0 Pakete aktualisiert, 0 zusätzlich installiert, 1 werden entfernt und 5 nicht aktualisiert.
Muss 0B an Archiven herunterladen. Nach dem Entpacken werden 10,4MB frei werden.
Wollen Sie fortsetzen? [Y/n/?] y
Schreibe erweiterte Statusinformationen... Fertig
dpkg: Fehler beim Bearbeiten von adobe-flashplugin (--purge):
 Paket ist in einem sehr schlechten inkonsistenten Zustand - Sie sollten
 es erneut installieren, bevor Sie es zu entfernen versuchen.
Fehler traten auf beim Bearbeiten von:
 adobe-flashplugin
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
This has the advice to reinstall. 

I try with dpkg:
```
abc:~# sudo dpkg -r adobe-flashplugin
dpkg: Fehler beim Bearbeiten von adobe-flashplugin (--remove):
 Paket ist in einem sehr schlechten inkonsistenten Zustand - Sie sollten
 es erneut installieren, bevor Sie es zu entfernen versuchen.
Fehler traten auf beim Bearbeiten von:
 adobe-flashplugin
```

Anyone a idea to get rid of the "evil" package?

---

### Post by cogier on 2009-09-20
Try the following command in Terminal.

```
sudo apt-get install -f

```

Also try the Web Browser Opera it has Flash already built in and I think it is better browser than Firefox.

Hope that helps

---

### Post by kedmanee on 2009-09-20
> **cogier said:**
> Try the following command in Terminal.

```

abc:~# sudo apt-get install -f
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Lese Status-Informationen ein... Fertig
E: Das Paket adobe-flashplugin muss neu installiert werden, ich kann aber kein Archiv dafür finden.

```
means: have to re-install / can't find a archive

> **cogier said:**
> Also try the Web Browser ...
With respect, your opinion about some browser is offtopic in this thread.

---

### Post by sunchiqua on 2009-09-20
```
sudo rm -r /var/cache/apt/archives/*

```

Try again :)

---

### Post by kedmanee on 2009-09-20
To empty the cached packages did not help.
The problem is still the same.

---

### Post by fliegengewicht on 2009-09-20
Same problem... after i tried to install the .deb package from adobe via >  dpkg -i install_flash_player_10_linux.de i cant use apt or aptitude any longer.

---

### Post by gradinaruvasile on 2009-09-20
Try this:

```
cd /var/lib/dpkg/
```

```
sudo cp status status-backup
```

```
sudo gedit status
```

find the section of ur package and delete it completely
save file

```
sudo apt-get update
```

Should be fixed...

---

### Post by fliegengewicht on 2009-09-20
..  Thank you. This works.

---

### Post by gradinaruvasile on 2009-09-20
You are fast... Sorry about that, i mistakenly pressed the submit button. It is fixed now.

---

### Post by kedmanee on 2009-09-20
The problem is solved 
[http://ubuntuforums.org/showpost.php?p=7980940&postcount=7](http://ubuntuforums.org/showpost.php?p=7980940&postcount=7)

works!

Thanks all for the attention & assistance
Special thank to "gradinaruvasile"
Hardy

---

### Post by fenario on 2009-09-22
> **kedmanee said:**
> The problem is solved 
[http://ubuntuforums.org/showpost.php?p=7980940&postcount=7](http://ubuntuforums.org/showpost.php?p=7980940&postcount=7)

works!

Thanks all for the attention & assistance
Special thank to "gradinaruvasile"
Hardy

Thanks God for this treasure. It saves my screen from getting too much spit cursed at it. I've been looking for a way to intercept apt-get and synaptic but could not find a location. Good stuff.

Fenario

---

### Post by daverave999 on 2009-10-19
> **gradinaruvasile said:**
> Try this:

```
cd /var/lib/dpkg/
```

```
sudo cp status status-backup
```

```
sudo gedit status
```

find the section of ur package and delete it completely
save file

```
sudo apt-get update
```

Should be fixed...
My hero! I've been having difficulty removing (or reinstalling) a package that was broken as my power cut out while installing it. This fixed me problem. Thank you so much!

---

