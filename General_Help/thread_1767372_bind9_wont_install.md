---
title: "bind9 wont install"
date: 2011-05-25
forum: General Help
---

### Post by post15951 on 2011-05-25
Ubuntu Server 11.04

When I
```
apt-get install bind9
```I get
```

root@server1:/home/administrator# apt-get install bind9
Czytanie list pakietÃ³w... Gotowe
Budowanie drzewa zaleÅ¼noÅ&#8250;ci
Odczyt informacji o stanie... Gotowe
Sugerowane pakiety:
  bind9-doc resolvconf
ZostanÄ&#8230; zainstalowane nastÄ&#8482;pujÄ&#8230;ce NOWE pakiety:
  bind9
0 aktualizowanych, 1 nowo instalowanych, 0 usuwanych i 3 nieaktualizowanych.
Konieczne pobranie 0 B/315 kB archiwÃ³w.
Po tej operacji zostanie dodatkowo uÅ¼yte 1061 kB miejsca na dysku.
Prekonfiguracja pakietÃ³w ...
Zaznaczenie poprzednio niezaznaczonego pakietu bind9.
(Odczytywanie bazy danych ... 178462 files and directories currently installed.)
Rozpakowanie bind9 (z .../bind9_1%3a9.7.3.dfsg-1ubuntu2_i386.deb) ...
Przetwarzanie wyzwalaczy dla ufw...
Przetwarzanie wyzwalaczy dla ureadahead...
Przetwarzanie wyzwalaczy dla man-db...
Konfigurowanie bind9 (1:9.7.3.dfsg-1ubuntu2) ...
_** * Starting domain name service... bind9                                 [fail]**_
invoke-rc.d: initscript bind9, action "start" failed.
dpkg: bÅ&#8218;Ä&#8230;d przetwarzania bind9 (--configure):
 podproces zainstalowany skrypt post-installation zwrÃ³ciÅ&#8218; kod bÅ&#8218;Ä&#8482;du 1
WystÄ&#8230;piÅ&#8218;y bÅ&#8218;Ä&#8482;dy podczas przetwarzania:
 bind9
_** E: Sub-process /usr/bin/dpkg returned an error code (1)**_

```
How do I fix it?

---

