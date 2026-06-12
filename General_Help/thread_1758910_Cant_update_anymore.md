---
title: "Cant update anymore"
date: 2011-05-15
forum: General Help
---

### Post by Sethnix on 2011-05-15
Hi
I hope im in the right forum and you can help me with my problem :/

I cant update anymore. Everytime i open the "update manager" i got this message:
> Paketinformationen konnten nicht initialisiert werden

Ein unlösbares Problem ist während der Initialisierung der Paketinformation aufgetreten.

Bitte melden Sie einen Fehler im Paket »update-manager« und fügen Sie die folgende Fehlermeldung an den Fehlerbericht an:

'E:Encountered a section with no Package: header, E: Problem with MergeList /var/lib/apt/lists/de.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E: Die Paketliste oder die Statusdatei konnte nicht eingelesen oder geöffnet werden.' How can I fix the problem?

And sorry for my english Im german ;)

---

### Post by fooman on 2011-05-15
open a terminal,  and type or copy/paste the following commands:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

hope that helps.

---

### Post by Sethnix on 2011-05-16
Thanks for ur help i can start it now but when I check for updates i got this message :/
> W:Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/source/Sources](http://de.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/source/Sources)  416  Requested Range Not Satisfiable [IP: 141.30.13.20 80]
, W:Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/natty-updates/main/source/Sources](http://de.archive.ubuntu.com/ubuntu/dists/natty-updates/main/source/Sources)  416  Requested Range Not Satisfiable [IP: 141.30.13.20 80]
, W:Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/source/Sources](http://de.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/source/Sources)  416  Requested Range Not Satisfiable [IP: 141.30.13.20 80]
, W:Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/source/Sources](http://de.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/source/Sources)  416  Requested Range Not Satisfiable [IP: 141.30.13.20 80]
, W:Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/natty-updates/main/binary-i386/Packages](http://de.archive.ubuntu.com/ubuntu/dists/natty-updates/main/binary-i386/Packages)  416  Requested Range Not Satisfiable [IP: 141.30.13.20 80]
, W:Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/binary-i386/Packages](http://de.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/binary-i386/Packages)  416  Requested Range Not Satisfiable [IP: 141.30.13.20 80]
, W:Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/binary-i386/Packages](http://de.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/binary-i386/Packages)  416  Requested Range Not Satisfiable [IP: 141.30.13.20 80]
, W:Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/binary-i386/Packages](http://de.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/binary-i386/Packages)  416  Requested Range Not Satisfiable [IP: 141.30.13.20 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

