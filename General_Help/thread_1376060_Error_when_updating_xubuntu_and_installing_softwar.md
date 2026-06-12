---
title: "Error when updating xubuntu and installing software"
date: 2010-01-08
forum: General Help
---

### Post by Drojoke on 2010-01-08
When i install software with the install/delete software program or when i update ubuntu, i get an error. I was able to update and install software a few days ago. But now i get this weird error:
```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

Anyone know how to solve this? I haven't been able to find any answers on google or the forums.

---

### Post by Leppie on 2010-01-08
have you tried issuing the suggested command from a terminal?
```
sudo dpkg --configure -a
```

---

### Post by Drojoke on 2010-01-08
> **Leppie said:**
> have you tried issuing the suggested command from a terminal?
```
sudo dpkg --configure -a
```

I did, and i used to get a list of things i didn't quite understood :p. Im pretty new to linux (Been using it for 2 weeks), so i only know a couple of things about the terminal etc.

Now i get this error when trying the command in the terminal:
```
dpkg: vereistenproblemen verhinderen de configuratie van libstdc++6-4.4-dev:
 libstdc++6-4.4-dev is afhankelijk van g++-4.4 (= 4.4.1-4ubuntu8); maar:
  Pakket `g++-4.4' is niet geïnstalleerd.
dpkg: fout bij afhandelen van libstdc++6-4.4-dev (--configure):
 vereistenproblemen - blijft ongeconfigureerd
Fouten gevonden tijdens behandelen van:
 libstdc++6-4.4-dev

```

Translated in dutch:
```
dpkg: Requirement problems are hindering the configuration of libstdc++6-4.4-dev:
 libstdc++6-4.4-dev is independent of g++-4.4 (= 4.4.1-4ubuntu8); but:
  Package `g++-4.4' is not installed.
dpkg: error while settling libstdc++6-4.4-dev (--configure):
 requirement problem - stays unconfigurated
Errors found while treating:
 libstdc++6-4.4-dev

```

---

### Post by Leppie on 2010-01-08
you don't seem to have the g++ compiler installed.
download it here: [http://packages.ubuntu.com/it/karmic/g++-4.4](http://packages.ubuntu.com/it/karmic/g++-4.4)
when download is complete, just double click the file and open with Gdebi to install the package.

1ste x dat ik ubuntu in het nederlands zie :P

---

### Post by Drojoke on 2010-01-09
Thanks alot :). Updates and adding software works now. 

Men xubuntu is eigenlijk half in nederlands :P. Heel veel menu's en applicaties zijn in het engels. Aantal in Nederlands.

---

### Post by Leppie on 2010-01-09
kewl, glad it's working now.
mazzel ;)

---

