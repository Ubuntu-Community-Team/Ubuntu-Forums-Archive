---
title: "Make a GUI for terminal commands"
date: 2010-02-27
forum: General Help
---

### Post by HomoGleek on 2010-02-27
Is there any easy way to Make a GUI for terminal commands?

---

### Post by malikjunaid on 2010-02-27
For what commands, are you looking a GUI?

---

### Post by HomoGleek on 2010-02-27
```
 gi (whatever I'm searching for) 
```

```
get_iplayer --type=tv --get (a shows ID)  --modes=flashstd --force
```

---

### Post by pop.horea on 2013-04-10
Tentativ&#259; de grafic&#259;:


#!/bin/sh
(
echo "# Actualizare sistem de operare"; sleep 2
echo "4" ; apt-get update; apt-get upgrade


echo "# &#536;tergere log-uri"; sleep 2
echo "5" ; cd /var/log; rm -rf ./*


echo "# Defragmentare par&#539;ial&#259; a sistemului de fi&#537;iere"; sleep 2
echo "52" ; e4defrag /root; e4defrag /usr


echo "# Verificare &#537;i marcare BAD-uri pe HDD"; sleep 2
echo "75" ; badblocks -v /dev/sda1; badblocks /dev/sda > /home/bad-blocks; fsck -l bad-blocks /dev/sda


echo "# Schimbare parolei user-ului"; sleep 2
echo "76" ; cd /etc; passwd


echo "# Instalare &#537;i lansare Universal Firewall"; sleep 2
echo "79" ; apt-get install gufw; gufw


echo "# Actualizare distribu&#539;ie sistem"; sleep 2
echo "92" ; apt-get dist-upgrade


) |
zenity --progress \
  --title="Utilit&#259;&#539;i de sistem" \
  --text="Progress:" \
  --percentage=0


if [ "$?" = -1 ] ; then
        zenity --error \
          --text="Rularea utilit&#259;&#539;ilor anulat&#259;."
fi

---

### Post by pop.horea on 2013-04-10
Zenity and scripting. Make text file with permision of running as a program. Then make deb package:
usr/bin/file
usr/DEBIAN/control -- find on net what about control 

then in terminal:
dpkg -b usr filename.deb

instal package
run in terminal sudo filename

---

### Post by oldos2er on 2013-04-10
Closed, please don't bump old threads.

---

