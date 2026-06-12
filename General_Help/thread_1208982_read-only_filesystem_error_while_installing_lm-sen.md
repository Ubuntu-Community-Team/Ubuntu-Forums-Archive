---
title: "read-only filesystem error while installing lm-sensors"
date: 2009-07-09
forum: General Help
---

### Post by Unkraut on 2009-07-09
Hi!
My hard drive crashed recently so I had to get a new one and reinstall.
Now I just installed lm-sensors and got this strange output:
```

trollkotze@schrotthaufen-mobil:~$ sudo apt-get install lm-sensors
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Lese Status-Informationen ein... Fertig
Die folgenden zusätzlichen Pakete werden installiert:
  libsensors4
Vorgeschlagene Pakete:
  sensord read-edid i2c-tools
Die folgenden NEUEN Pakete werden installiert:
  libsensors4 lm-sensors
0 aktualisiert, 2 neu installiert, 0 zu entfernen und 301 nicht aktualisiert.
Es müssen 187kB an Archiven heruntergeladen werden.
Nach dieser Operation werden 786kB Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren [J/n]? j
Hole:1 http://de.archive.ubuntu.com intrepid/main libsensors4 1:3.0.2-1ubuntu2 [62,2kB]
Hole:2 http://de.archive.ubuntu.com intrepid/main lm-sensors 1:3.0.2-1ubuntu2 [125kB]
Es wurden 187kB in 0s geholt (512kB/s)
Wähle vormals abgewähltes Paket libsensors4.
(Lese Datenbank ... 104325 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacke libsensors4 (aus .../libsensors4_1%3a3.0.2-1ubuntu2_i386.deb) ...
Wähle vormals abgewähltes Paket lm-sensors.
Entpacke lm-sensors (aus .../lm-sensors_1%3a3.0.2-1ubuntu2_i386.deb) ...
Verarbeite Trigger für man-db ...
Richte libsensors4 ein (1:3.0.2-1ubuntu2) ...
udev active, devices will be created in /dev/.static/dev/
rm: Entfernen von „i2c-0-“ nicht möglich: Read-only file system
mknod: „i2c-0-“: Read-only file system
makedev i2c-0 c 89 0 root root 0600: failed
rm: Entfernen von „i2c-0-“ nicht möglich: Read-only file system
rm: Entfernen von „i2c-1-“ nicht möglich: Read-only file system
mknod: „i2c-1-“: Read-only file system
makedev i2c-1 c 89 1 root root 0600: failed
rm: Entfernen von „i2c-1-“ nicht möglich: Read-only file system
rm: Entfernen von „i2c-2-“ nicht möglich: Read-only file system
mknod: „i2c-2-“: Read-only file system
makedev i2c-2 c 89 2 root root 0600: failed
rm: Entfernen von „i2c-2-“ nicht möglich: Read-only file system
rm: Entfernen von „i2c-3-“ nicht möglich: Read-only file system
mknod: „i2c-3-“: Read-only file system
makedev i2c-3 c 89 3 root root 0600: failed
rm: Entfernen von „i2c-3-“ nicht möglich: Read-only file system
rm: Entfernen von „i2c-4-“ nicht möglich: Read-only file system
mknod: „i2c-4-“: Read-only file system
makedev i2c-4 c 89 4 root root 0600: failed
rm: Entfernen von „i2c-4-“ nicht möglich: Read-only file system
rm: Entfernen von „i2c-5-“ nicht möglich: Read-only file system
mknod: „i2c-5-“: Read-only file system
makedev i2c-5 c 89 5 root root 0600: failed
rm: Entfernen von „i2c-5-“ nicht möglich: Read-only file system
rm: Entfernen von „i2c-6-“ nicht möglich: Read-only file system
mknod: „i2c-6-“: Read-only file system
makedev i2c-6 c 89 6 root root 0600: failed
rm: Entfernen von „i2c-6-“ nicht möglich: Read-only file system
rm: Entfernen von „i2c-7-“ nicht möglich: Read-only file system
mknod: „i2c-7-“: Read-only file system
makedev i2c-7 c 89 7 root root 0600: failed
rm: Entfernen von „i2c-7-“ nicht möglich: Read-only file system

Creating config file /etc/sensors3.conf with new version

Richte lm-sensors ein (1:3.0.2-1ubuntu2) ...

Verarbeite Trigger für libc6 ...
ldconfig deferred processing now taking place

```

The strange thing is not that the output is in German :), but that these lines 
```
rm: Entfernen von „i2c-3-“ nicht möglich: Read-only file system
```
translate to
```
rm: Removal of package „i2c-3-“ not possible: Read-only file system
```.
I don't know what's going on here. What is it that is supposed to be removed and can't be removed? And why read-only filesystem?

Sensors works fine, though. But I'm curious. I don't remember these error messages from my previous installation.

---

### Post by miklcct on 2009-07-13
Have you mounted something read-only?

---

