---
title: "Dual boot probleem"
date: 2010-06-11
forum: General Help
---

### Post by fidelfloris on 2010-06-11
Goede middag,

Ik heb Ubuntu geüpgraded naar 10.04. Nu zie ik in de Grub nog wel de Windows entry.
Maar als ik er op klik kom ik terug bij de grub, en kan ik feitelijk alleen Ubuntu kiezen.

Nu heb ik de ultimate boot cd en ik kan naar de recovery gaan van Vista.
Alleen kan ik dan helaas enkel en alleen de standaard instellingen van Vista terugzetten.
Dan zou ik dus de rest kwijt zijn.

Is er een manier om bij mijn Vista omgeving te komen zonder verlies van bestanden?

Kan ik vanuit Ubuntu de grub aanpassen?

sudo os-prober en daarna sudo update-grub

hebben niets uitgehaald.

dit is het resultaat van sudo fdisk -l
sudo fdisk -l

[sudo] password for: 

Schijf /dev/sda: 1000.2 GB, 1000204886016 bytes
255 koppen, 63 sectoren/spoor, 121601 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Schijf-ID: 0x067b51a8

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1               1        1913    15360000   27  [onbekend]
/dev/sda2   *        1913       49791   384579584    7  HPFS/NTFS
/dev/sda3           49791       87372   301873186    7  HPFS/NTFS
/dev/sda4           87373      121601   274944442+   5  Uitgebreid
/dev/sda5           87373      120475   265899816   83  Linux
/dev/sda6          120476      121601     9044563+  82  Linux wisselgeheugen

Schijf /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 koppen, 63 sectoren/spoor, 121601 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Schijf-ID: 0x47a16e32

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdb1               1       61773   496190598+   7  HPFS/NTFS
/dev/sdb2           61774      121601   480568410    5  Uitgebreid
/dev/sdb5           61774      120475   471523783+  83  Linux
/dev/sdb6          120476      121601     9044563+  82  Linux wisselgeheugen

Kan iemand mij helpen?

Groeten Fidel

---

### Post by TeoBigusGeekus on 2010-06-11
&#916;&#949;&#957; &#954;&#945;&#964;&#945;&#955;&#945;&#946;&#945;&#943;&#957;&#969; &#955;&#941;&#958;&#951;! &#924;&#942;&#960;&#969;&#962; &#952;&#945; &#956;&#960;&#959;&#961;&#959;&#973;&#963;&#949;&#962; &#957;&#945; &#956;&#945;&#962; &#964;&#959; &#960;&#949;&#953;&#962; &#963;&#964;&#945; &#945;&#947;&#947;&#955;&#953;&#954;&#940; &#942; &#963;&#964;&#945; &#949;&#955;&#955;&#951;&#957;&#953;&#954;&#940;;

---

