---
title: "MySQL Client Core 5.1 kaputt"
date: 2010-11-23
forum: General Help
---

### Post by 4thfloorstudios on 2010-11-23
Hi,
ich habe das Problem auf Ubuntu 10.04, daß nach dem Upgrade von 9.10 meine MySQL Pakete defekt sind.

Problem ist das Paket mysql-client-core-5.1, welches nicht installierbar ist.

Ich bekomme immer diese Fehlermeldung:

```
Entpacke mysql-client-core-5.1 (aus .../mysql-client-core-5.1_5.1.41-3ubuntu12.7_i386.deb) ...
dpkg: Fehler beim Bearbeiten von /var/cache/apt/archives/mysql-client-core-5.1_5.1.41-3ubuntu12.7_i386.deb (--unpack):
 Versuche, »/usr/bin/mysql« zu überschreiben, welches auch in Paket mysql-client-5.1 0:5.1.51-0.dotdeb.1 ist
dpkg-deb: Unterprozess einfügen mit Signal (Broken pipe) getötet

```Ich bin jetzt überfragt, wie ich am Besten MySQL deinstalliere, ohne meine Datenbanken und Konfig Files zu verlieren.

Kann mir jemand weiter helfen?

Danke,
Oliver

---

### Post by 4thfloorstudios on 2010-11-23
Örgs, sorry, english, I forgot...

So, my mysql-client-core package is broken with the above error message. How can I  fix that wihtout uninstalling mysql or if I have to uninstall mysql, how do I prevent my databases and config from being deleted?

Thanks,
Oliver

---

