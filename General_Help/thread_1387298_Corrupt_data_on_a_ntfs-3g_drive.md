---
title: "Corrupt data on a ntfs-3g drive"
date: 2010-01-21
forum: General Help
---

### Post by joksim on 2010-01-21
hi,

I have a dual boot laptop, Ubuntu 9.10 and Win 7.
a problem occurs when I save a file in ubuntu, after rebooting in Win, they are treated as corrupted, chkdisk is activated and are deleted. If I ignore chkdisk, those files/directories are visible, but are unusable (corrupted).

Maybe its a problem with fuse, or multiple OSes going hibernate or stand by (I have that habbit)

thanks in advance,
Boban,
Macedonia

---

### Post by jamesisin on 2010-01-21
Could you provide a little more information about your current setup?

How many partitions and types ( sudo fdisk -l )?

Where are you trying to save the file (location in file tree and partition)?

---

### Post by joksim on 2010-01-21
> **jamesisin said:**
> Could you provide a little more information about your current setup?

How many partitions and types ( sudo fdisk -l )?

Where are you trying to save the file (location in file tree and partition)?

The output of fdisk is:
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8e0eee9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        8924    71577600    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            8925       27922   152598511+   f  W95 Ext'd (LBA)
Partition 3 does not end on cylinder boundary.
/dev/sda4           27922       38914    88288256    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.
/dev/sda5           14868       27922   104858793+   7  HPFS/NTFS
/dev/sda6            8925       10960    16354107   83  Linux
/dev/sda7           10961       14309    26900811   83  Linux
/dev/sda8           14310       14867     4482103+  82  Linux swap / Solaris

Partition table entries are not in disk order

It happens on regular files (doc, odt, etc) on /dev/sda5.

---

### Post by jamesisin on 2010-01-21
Did you create that NTFS partition using Windows or Ubuntu?  Would it be feasible to simply repartition that space (obviously without effecting the others)?

---

### Post by alpha-buntu on 2010-01-27
> **joksim said:**
> hi,

I have a dual boot laptop, Ubuntu 9.10 and Win 7.
a problem occurs when I save a file in ubuntu, after rebooting in Win, they are treated as corrupted, chkdisk is activated and are deleted. If I ignore chkdisk, those files/directories are visible, but are unusable (corrupted).

Maybe its a problem with fuse, or multiple OSes going hibernate or stand by (I have that habbit)

thanks in advance,
Boban,
Macedonia

Add me.

Setup is Ubuntu 9.10, ntfs-3g. 

I tried using ntfs-3g for one month now but I will stop this. I am having so many MAJOR erros with write-access on NTFS partition that I can not recommend ntfs-3g any more. Its unstable. I have massive amounts of corrupted files, missing files. The last crazy thing was a 4 GB mkv I saved on the ntfs. After  that, ubuntu thought I was some kind of folder ??? 

Some kind of proove? Look at this. I did chkdsk about once a week to fix the missing files and orphaned files. Nicely, it found many errors aside those. 

Some examples:


```


Fehler : Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.

C:\Dokumente und Einstellungen\Administrator>chkdsk e: /f
Der Typ des Dateisystems ist NTFS.

CHKDSK kann nicht ausgeführt werden, da das Volume von einem anderen
Prozess verwendet wird.  Die Bereitstellung des Volumes muss zuerst
aufgehoben werden.
ALLE OFFENEN BEZÜGE AUF DIESEM VOLUME SIND DANN UNGÜLTIG.
Möchten Sie die Bereitstellung des Volumes aufheben? (J/N) j
Bereitstellung des Volumes aufgehoben. Alle offenen Bezüge auf dieses
Volume sind ungültig.
Die Volumebezeichnung lautet Seagate 1b.

CHKDSK überprüft Dateien (Phase 1 von 3)…
Beschädigter Attributeintrag (128, “”) wird
vom Datensatzsegment 6052 gelöscht.
Dateiüberprüfung beendet.
CHKDSK überprüft Indizes (Phase 2 von 3)…
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Indexeintrag Ext2Fsd-0.48.exe in Index $I30 der Datei 170211 wird gelöscht.
Indexeintrag EXT2FS~1.EXE in Index $I30 der Datei 170211 wird gelöscht.
Indexeintrag Craig David in Index $I30 der Datei 266956 wird gelöscht.
Indexüberprüfung beendet.
CHKDSK stellt verlorene Dateien wieder her.
CHKDSK überprüft Sicherheitsbeschreibungen (Phase 3 von 3)…
Überprüfung der Sicherheitsbeschreibungen beendet.
Attribut DATA wird in Datei 6052 eingefügt.
CHKDSK überprüft USN-Journal…
Die Überprüfung von USN-Journal ist abgeschlossen.
Fehler im Attribut BITMAP der Masterdateitabelle (MFT) werden berichtigt.
CHKDSK hat freien Speicher gefunden, der in der Volumebitmap als
zugeordnet gekennzeichnet ist.
Windows hat Probleme im Dateisystem behoben.

Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Dokumente und Einstellungen\Administrator>chdsk e: /f
Der Befehl “chdsk” ist entweder falsch geschrieben oder
konnte nicht gefunden werden.

C:\Dokumente und Einstellungen\Administrator>chkdsk e: /f
Der Typ des Dateisystems ist NTFS.
Die Volumebezeichnung lautet Seagate 1b.

CHKDSK überprüft Dateien (Phase 1 von 3)…
Dateiüberprüfung beendet.
CHKDSK überprüft Indizes (Phase 2 von 3)…
Fehler im Index $I30 der Datei 88476 werden berichtigt.
Fehler im Index $I30 der Datei 88479 werden berichtigt.
Indexeintrag ing_126_200804 in Index $I30 der Datei 88479 wird gelöscht.
Indexeintrag ing_127_200804 in Index $I30 der Datei 88479 wird gelöscht.
Indexeintrag ing_128_200804 in Index $I30 der Datei 88479 wird gelöscht.
Indexeintrag ing_129_200804 in Index $I30 der Datei 88479 wird gelöscht.
Indexeintrag ing_130_200804 in Index $I30 der Datei 88479 wird gelöscht.
Indexeintrag ing_131_200805 in Index $I30 der Datei 88479 wird gelöscht.
Indexeintrag ing_132_200805 in Index $I30 der Datei 88479 wird gelöscht.
Indexeintrag ing_133_200805 in Index $I30 der Datei 88479 wird gelöscht.
Indexeintrag ing_134_200805 in Index $I30 der Datei 88479 wird gelöscht.
Indexeintrag ing_135_200805 in Index $I30 der Datei 88479 wird gelöscht.
Indexeintrag moon.mkv in Index $I30 der Datei 170211 wird gelöscht.
Indexüberprüfung beendet.
CHKDSK stellt verlorene Dateien wieder her.
Verwaiste Datei INC732~1 (389001) wird in Verzeichnisdatei 88479 wiederhergestel
lt.
Verwaiste Datei ing_135_200805 (389001) wird in Verzeichnisdatei 88479 wiederher
gestellt.
Verwaiste Datei INC532~1 (389097) wird in Verzeichnisdatei 88479 wiederhergestel
lt.
Verwaiste Datei ing_134_200805 (389097) wird in Verzeichnisdatei 88479 wiederher
gestellt.
Verwaiste Datei INC332~1 (389223) wird in Verzeichnisdatei 88479 wiederhergestel
lt.
Verwaiste Datei ing_133_200805 (389223) wird in Verzeichnisdatei 88479 wiederher
gestellt.
Verwaiste Datei INC132~1 (389296) wird in Verzeichnisdatei 88479 wiederhergestel
lt.
Verwaiste Datei ing_132_200805 (389296) wird in Verzeichnisdatei 88479 wiederher
gestellt.
Verwaiste Datei INCF22~1 (389363) wird in Verzeichnisdatei 88479 wiederhergestel
lt.
Verwaiste Datei ing_131_200805 (389363) wird in Verzeichnisdatei 88479 wiederher
gestellt.
Verwaiste Datei INBD22~1 (389486) wird in Verzeichnisdatei 88479 wiederhergestel
lt.
Verwaiste Datei ing_130_200804 (389486) wird in Verzeichnisdatei 88479 wiederher
gestellt.
Verwaiste Datei ING_12~1 (389613) wird in Verzeichnisdatei 88479 wiederhergestel
lt.
Verwaiste Datei ing_129_200804 (389613) wird in Verzeichnisdatei 88479 wiederher
gestellt.
Verwaiste Datei ING_12~2 (389719) wird in Verzeichnisdatei 88479 wiederhergestel
lt.
Verwaiste Datei ing_128_200804 (389719) wird in Verzeichnisdatei 88479 wiederher
gestellt.
Verwaiste Datei ING_12~3 (389824) wird in Verzeichnisdatei 88479 wiederhergestel
lt.
Verwaiste Datei ing_127_200804 (389824) wird in Verzeichnisdatei 88479 wiederher
gestellt.
Verwaiste Datei ING_12~4 (389910) wird in Verzeichnisdatei 88479 wiederhergestel
lt.
Verwaiste Datei ing_126_200804 (389910) wird in Verzeichnisdatei 88479 wiederher
gestellt.
Verwaiste Datei INB73D~1 (390018) wird in Verzeichnisdatei 88479 wiederhergestel
lt.
Verwaiste Datei ing_125_200804 (390018) wird in Verzeichnisdatei 88479 wiederher
gestellt.
Verwaiste Datei ing_124_200804 (390082) wird in Verzeichnisdatei 88476 wiederher
gestellt.
Verwaiste Datei ing_123_200803 (390191) wird in Verzeichnisdatei 88476 wiederher
gestellt.
Verwaiste Datei ing_122_200803 (390260) wird in Verzeichnisdatei 88476 wiederher
gestellt.
Verwaiste Datei ing_121_200802 (390323) wird in Verzeichnisdatei 88476 wiederher
gestellt.
Verwaiste Datei ing_120_200802 (390445) wird in Verzeichnisdatei 88476 wiederher
gestellt.
Verwaiste Datei ing_119_200802 (390593) wird in Verzeichnisdatei 88476 wiederher
gestellt.
Verwaiste Datei ing_118_200802 (390734) wird in Verzeichnisdatei 88476 wiederher
gestellt.
Verwaiste Datei ing_117_200802 (390849) wird in Verzeichnisdatei 88476 wiederher
gestellt.
Verwaiste Datei ing_116_200801 (390974) wird in Verzeichnisdatei 88476 wiederher
gestellt.
Verwaiste Datei gri_5F25_200803 (391182) wird in Verzeichnisdatei 88476 wiederhe
rgestellt.
Verwaiste Datei GES_17_200811 (392626) wird in Verzeichnisdatei 88476 wiederherg
estellt.
Verwaiste Datei GES_16_200809 (392813) wird in Verzeichnisdatei 88476 wiederherg
estellt.
Verwaiste Datei GES_15_200806 (392953) wird in Verzeichnisdatei 88476 wiederherg
estellt.
Verwaiste Datei GES_14_200803 (393058) wird in Verzeichnisdatei 88476 wiederherg
estellt.
Verwaiste Datei GES_13_200802 (393200) wird in Verzeichnisdatei 88476 wiederherg
estellt.
Verwaiste Datei err_5F254_200812 (393472) wird in Verzeichnisdatei 88476 wiederh
ergestellt.
Verwaiste Datei ERR_5F~4 (393612) wird in Verzeichnisdatei 88476 wiederhergestel
lt.
Verwaiste Datei err_5F253_200812 (393612) wird in Verzeichnisdatei 88476 wiederh
ergestellt.
Verwaiste Datei ERR_5F~3 (393760) wird in Verzeichnisdatei 88476 wiederhergestel
lt.
Verwaiste Datei err_5F252_200812 (393760) wird in Verzeichnisdatei 88476 wiederh
ergestellt.
Verwaiste Datei ERR_5F~2 (393926) wird in Verzeichnisdatei 88476 wiederhergestel
lt.
Verwaiste Datei err_5F251_200811 (393926) wird in Verzeichnisdatei 88476 wiederh
ergestellt.
Verwaiste Datei ERR_5F~1 (394083) wird in Verzeichnisdatei 88476 wiederhergestel
lt.
Verwaiste Datei err_5F250_200811 (394083) wird in Verzeichnisdatei 88476 wiederh
ergestellt.
Verwaiste Datei err_249_200811 (394239) wird in Verzeichnisdatei 88476 wiederher
gestellt.
Verwaiste Datei err_248_200811 (394389) wird in Verzeichnisdatei 88476 wiederher
gestellt.
Verwaiste Datei err_247_200811 (394552) wird in Verzeichnisdatei 88476 wiederher
gestellt.
Verwaiste Datei err_246_200811 (394711) wird in Verzeichnisdatei 88476 wiederher
gestellt.
CHKDSK überprüft Sicherheitsbeschreibungen (Phase 3 von 3)…
Überprüfung der Sicherheitsbeschreibungen beendet.
CHKDSK überprüft USN-Journal…
Die Überprüfung von USN-Journal ist abgeschlossen.
CHKDSK hat freien Speicher gefunden, der in der MFT-Bitmap (Master
File Table) als zugeordnet gekennzeichnet ist.
CHKDSK hat freien Speicher gefunden, der in der Volumebitmap als
zugeordnet gekennzeichnet ist.
Windows hat Probleme im Dateisystem behoben.

1412699840 KB Speicherplatz auf dem Datenträger insgesamt
762270708 KB in 317929 Dateien
160820 KB in 11983 Indizes
0 KB in fehlerhaften Sektoren
600756 KB vom System benutzt
65536 KB von der Protokolldatei belegt
649667556 KB auf dem Datenträger verfügbar

4096 Bytes in jeder Zuordnungseinheit
353174960 Zuordnungseinheiten auf dem Datenträger insgesamt
162416889 Zuordnungseinheiten auf dem Datenträger verfügbar

C:\Dokumente und Einstellungen\Administrator>chkdsk e: /f
Der Typ des Dateisystems ist NTFS.

CHKDSK kann nicht ausgeführt werden, da das Volume von einem anderen
Prozess verwendet wird.  Die Bereitstellung des Volumes muss zuerst
aufgehoben werden.
ALLE OFFENEN BEZÜGE AUF DIESEM VOLUME SIND DANN UNGÜLTIG.
Möchten Sie die Bereitstellung des Volumes aufheben? (J/N) j
Bereitstellung des Volumes aufgehoben. Alle offenen Bezüge auf dieses
Volume sind ungültig.
Die Volumebezeichnung lautet Seagate 1b.

CHKDSK überprüft Dateien (Phase 1 von 3)…
Dateiüberprüfung beendet.
CHKDSK überprüft Indizes (Phase 2 von 3)…
Indexüberprüfung beendet.
CHKDSK überprüft Sicherheitsbeschreibungen (Phase 3 von 3)…
Überprüfung der Sicherheitsbeschreibungen beendet.
CHKDSK überprüft USN-Journal…
Die Überprüfung von USN-Journal ist abgeschlossen.
Das Dateisystem wurde überprüft. Es wurden keine Probleme festgestellt.

1412699840 KB Speicherplatz auf dem Datenträger insgesamt
762270708 KB in 317929 Dateien
160820 KB in 11983 Indizes
0 KB in fehlerhaften Sektoren
600756 KB vom System benutzt
65536 KB von der Protokolldatei belegt
649667556 KB auf dem Datenträger verfügbar

4096 Bytes in jeder Zuordnungseinheit
353174960 Zuordnungseinheiten auf dem Datenträger insgesamt
162416889 Zuordnungseinheiten auf dem Datenträger verfügbar

C:\Dokumente und Einstellungen\Administrator>
20.01.

Dateisystem auf E: wird überprüft.
Der Typ des Dateisystems ist NTFS.

CHKDSK kann nicht ausgeführt werden, da das Volume von einem anderen
Prozess verwendet wird.  Die Bereitstellung des Volumes muss zuerst
aufgehoben werden.
ALLE OFFENEN BEZÜGE AUF DIESEM VOLUME SIND DANN UNGÜLTIG.
Möchten Sie die Bereitstellung des Volumes aufheben? (J/N) Bereitstellung des Volumes aufgehoben. Alle offenen Bezüge auf dieses
Volume sind ungültig.
Die Volumebezeichnung lautet Seagate 1b.
Der Attributeintrag vom Typ 0×80 und mit der Instanzkennung 0×4 ist
von 0×39436ac an für möglicherweise 0×166 Cluster quer verbunden.
Der Attributeintrag vom Typ 0×80 und mit der Instanzkennung 0×4 ist
von 0×39436ac an für möglicherweise 0×166 Cluster quer verbunden.
Einige Cluster, die vom Attribut vom Typ 0×80 und der Instanzkennung 0×4
in der Datei 0×17a4 belegt sind, werden bereits verwendet.
Beschädigter Attributeintrag (128, “”) wird
vom Datensatzsegment 6052 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a41d,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a41e,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a41f,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a420,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a422,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a423,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a424,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a425,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a426,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a427,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a428,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a429,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a42a,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a42b,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a42c,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a42d,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a42e,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a42f,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a430,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a431,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a432,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a434,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a435,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a436,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a437,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a438,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a439,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a43a,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a43b,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a43c,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a43d,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a43e,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a43f,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a440,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a441,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a442,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a433,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a421,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag Ext2Fsd-0.48.exe von Index $I30 in der Datei 0×298e3 verweist auf die nicht verwendete Datei 0×16aa.
Indexeintrag Ext2Fsd-0.48.exe in Index $I30 der Datei 170211 wird gelöscht.
Der Indexeintrag EXT2FS~1.EXE von Index $I30 in der Datei 0×298e3 verweist auf die nicht verwendete Datei 0×16aa.
Indexeintrag EXT2FS~1.EXE in Index $I30 der Datei 170211 wird gelöscht.
Die Dateireferenz 0×510000000016ce von Indexeintrag Craig David von Index $I30 mit dem
übergeordneten Element 0×412cc ist nicht die gleiche wie 0×530000000016ce.
Indexeintrag Craig David in Index $I30 der Datei 266956 wird gelöscht.
Kleinere Inkonsistenzen auf dem Laufwerk werden aufgeräumt.
CHKDSK stellt verlorene Dateien wieder her.
Attribut DATA wird in Datei 6052 eingefügt.
CHKDSK überprüft USN-Journal…
Die Überprüfung von USN-Journal ist abgeschlossen.
Fehler im Attribut BITMAP der Masterdateitabelle (MFT) werden berichtigt.
CHKDSK hat freien Speicher gefunden, der in der Volumebitmap als
zugeordnet gekennzeichnet ist.
Windows hat Probleme im Dateisystem behoben.

1412699840 KB Speicherplatz auf dem Datenträger insgesamt
762854492 KB in 317974 Dateien
160836 KB in 11980 Indizes
0 KB in fehlerhaften Sektoren
600244 KB vom System benutzt
65536 KB von der Protokolldatei belegt
649084268 KB auf dem Datenträger verfügbar

4096 Bytes in jeder Zuordnungseinheit
353174960 Zuordnungseinheiten auf dem Datenträger insgesamt
162271067 Zuordnungseinheiten auf dem Datenträger verfügbar

Weitere Informationen über die Hilfe- und Supportdienste erhalten Sie unter http://go.microsoft.com/fwlink/events.asp.
17.01.

Dateisystem auf E: wird überprüft.
Der Typ des Dateisystems ist NTFS.
Die Volumebezeichnung lautet Seagate 1b.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×21299,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2129b,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2129c,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag Images von Index $I30 in der Datei 0×5 verweist auf die nicht verwendete Datei 0×29afc.
Indexeintrag Images in Index $I30 der Datei 5 wird gelöscht.
Kleinere Inkonsistenzen auf dem Laufwerk werden aufgeräumt.
CHKDSK stellt verlorene Dateien wieder her.
Verwaiste Datei RECYCLER (165729) wird in Verzeichnisdatei 5 wiederhergestellt.
CHKDSK überprüft USN-Journal…
Die Überprüfung von USN-Journal ist abgeschlossen.
CHKDSK hat freien Speicher gefunden, der in der MFT-Bitmap (Master
File Table) als zugeordnet gekennzeichnet ist.
Fehler in Volumebitmap werden berichtigt.
Windows hat Probleme im Dateisystem behoben.

1412699840 KB Speicherplatz auf dem Datenträger insgesamt
734337884 KB in 316327 Dateien
159392 KB in 11838 Indizes
0 KB in fehlerhaften Sektoren
600244 KB vom System benutzt
65536 KB von der Protokolldatei belegt
677602320 KB auf dem Datenträger verfügbar

4096 Bytes in jeder Zuordnungseinheit
353174960 Zuordnungseinheiten auf dem Datenträger insgesamt
169400580 Zuordnungseinheiten auf dem Datenträger verfügbar

Weitere Informationen über die Hilfe- und Supportdienste erhalten Sie unter http://go.microsoft.com/fwlink/events.asp.
29.12.

Dateisystem auf E: wird überprüft.
Der Typ des Dateisystems ist NTFS.

CHKDSK kann nicht ausgeführt werden, da das Volume von einem anderen
Prozess verwendet wird.  Die Bereitstellung des Volumes muss zuerst
aufgehoben werden.
ALLE OFFENEN BEZÜGE AUF DIESEM VOLUME SIND DANN UNGÜLTIG.
Möchten Sie die Bereitstellung des Volumes aufheben? (J/N) Bereitstellung des Volumes aufgehoben. Alle offenen Bezüge auf dieses
Volume sind ungültig.
Die Volumebezeichnung lautet Seagate 1b.
Die Indexbitmap $O in der Datei 0×19 ist nicht korrekt.
Fehler im Index $O der Datei 25 werden berichtigt.
Der erste Indexeintrag der Länge 0×10 ist ein Endknoten, aber der vorhergehende Eintrag ist keiner.
00 00 00 00 00 00 00 00 10 00 00 00 02 00 00 00  …………….
67 ad 4a 61 8a fb da 11 8f 37 00 50 56 c0 00 08  g*JaŠû..7.PV…
Index $O in Datei 25 wird sortiert.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×1d24,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×245c9,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×245cf,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×281e9,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×281ff,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×28200,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2ab5,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2ab1,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a7e,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2a81,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×315b,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×32c3,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×32d0,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2121,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×29ac,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2985,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×7a8b,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×7a85,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×7a82,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×7a83,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×7a84,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×5ec5,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×5ecb,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×5e2f,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×23f9,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×23fa,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×23fb,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×23fc,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×23fd,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×23fe,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2819b,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×221c,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×221d,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×221e,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×221f,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2220,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2221,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2222,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2223,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2224,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2225,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2204,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2205,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2206,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2207,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×242d,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×242e,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×242f,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2430,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2431,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2432,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2433,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2434,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2435,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2436,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2437,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2438,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2439,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×243a,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×243b,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×243c,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×243d,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2f17,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2f18,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2f19,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2f1a,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2f1b,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2f1c,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2f1d,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2c27,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2c28,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2c29,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2c2a,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2c2b,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2c2c,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2c2d,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2c2e,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2c2f,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2c30,
aber diese Datei enthält keine Objektkennung.
Ein Indexeintrag wird aus dem Index $O der Datei 25 gelöscht.
Der Indexeintrag für die Objektkennung in der Datei 0×19 verweist auf Datei 0×2f1e,
aber diese Datei ent

Weitere Informationen über die Hilfe- und Supportdienste erhalten Sie unter http://go.microsoft.com/fwlink/events.asp.




```

---

### Post by zooooz on 2010-05-13
Same story here.
Can confirm the unusable files in xp. chkdsk will delete those on startup.
9.10 32bit and 10.04 both show the same problem.
I too am known to hibernate both OSes and change files on the shared data partition.

---

