---
title: "btrfs raid0 disk array dying?"
date: 2010-06-27
forum: General Help
---

### Post by yee379 on 2010-06-27
Hi,

i think my btrfs volume is hosed.... it mounts okay, but iostat shows /dev/sdg on 100% load. dmesg shows lots of 'parent transid verify failed on x wanted y found z'. then after a while i can't read from it (access to the filesystem freezes). subsequently, the machine hangs completely after a few hours.

can anyone provide any guidance in how to proceed? since btrfsck doesn't actually do anything (according to the btrfs mailing list), how do i repair it?

cheers,

Yee.

ubuntu 10.4. tried latest tools from git repo.

$ sudo /usr/local/bin/btrfs-show
failed to read /dev/sr0

Label: none  uuid: ea7ea0b3-bc42-4b0c-9173-346df61d4454
       Total devices 3 FS bytes used 3.56TB
       devid    3 size 1.82TB used 0.00 path /dev/sde
       devid    1 size 1.82TB used 1.82TB path /dev/sdf
       devid    2 size 1.82TB used 1.82TB path /dev/sdg

Btrfs v0.19-16-g075587c


$ sudo /usr/local/bin/btrfsck /dev/sdf
failed to read /dev/sr0
parent transid verify failed on 2703873638400 wanted 9074 found 9016
parent transid verify failed on 2703884750848 wanted 9074 found 9055
parent transid verify failed on 2703884763136 wanted 9074 found 9060
parent transid verify failed on 2703883599872 wanted 9074 found 9034
parent transid verify failed on 2703920717824 wanted 9066 found 7543
parent transid verify failed on 2703912325120 wanted 9066 found 7543
parent transid verify failed on 2703912034304 wanted 9066 found 7543
parent transid verify failed on 2703881900032 wanted 9071 found 9060
parent transid verify failed on 2703881793536 wanted 9069 found 9057
bad block 2703860367360
Extent back ref already exists for 2703873536000 parent 0 root 2
bad block 2703860621312
bad block 2703861547008
Extent back ref already exists for 2703876689920 parent 0 root 2
Extent back ref already exists for 2703881900032 parent 0 root 2
Extent back ref already exists for 2703879290880 parent 0 root 2
Extent back ref already exists for 2703873753088 parent 0 root 2
parent transid verify failed on 2703921885184 wanted 9066 found 7543
parent transid verify failed on 2703921889280 wanted 9066 found 7543
parent transid verify failed on 2703879036928 wanted 9069 found 9061
parent transid verify failed on 2703881867264 wanted 9075 found 9065
parent transid verify failed on 2703873536000 wanted 9074 found 9062
parent transid verify failed on 2703883190272 wanted 9075 found 9061
parent transid verify failed on 2703869997056 wanted 9073 found 9060
parent transid verify failed on 2703922012160 wanted 9066 found 7543
parent transid verify failed on 2703921975296 wanted 9066 found 7543
parent transid verify failed on 2703867707392 wanted 9071 found 9060
parent transid verify failed on 2703922679808 wanted 9066 found 7543
parent transid verify failed on 2703922032640 wanted 9066 found 7543
parent transid verify failed on 2703881891840 wanted 9075 found 9057
parent transid verify failed on 2703882297344 wanted 9075 found 9061
parent transid verify failed on 2703884488704 wanted 9074 found 9057
parent transid verify failed on 2703884353536 wanted 9074 found 9057
parent transid verify failed on 2703884365824 wanted 9074 found 9055
parent transid verify failed on 2703921500160 wanted 9066 found 7543
parent transid verify failed on 2703883177984 wanted 9075 found 9061
parent transid verify failed on 2703921487872 wanted 9066 found 7543
parent transid verify failed on 2703922683904 wanted 9066 found 7543
parent transid verify failed on 2703873753088 wanted 9074 found 9062
parent transid verify failed on 2703874314240 wanted 9074 found 9056
Extent back ref already exists for 2703865823232 parent 0 root 2
Extent back ref already exists for 2703866810368 parent 0 root 2
Extent back ref already exists for 2703866986496 parent 0 root 2
Extent back ref already exists for 2703867031552 parent 0 root 2
Extent back ref already exists for 2703867625472 parent 0 root 2
Extent back ref already exists for 2703867609088 parent 0 root 2
Extent back ref already exists for 2703868829696 parent 0 root 2
Extent back ref already exists for 2703869734912 parent 0 root 2
Extent back ref already exists for 2703870255104 parent 0 root 2
Extent back ref already exists for 2703870562304 parent 0 root 2
Extent back ref already exists for 2703871201280 parent 0 root 2
Extent back ref already exists for 2703871168512 parent 0 root 2
Extent back ref already exists for 2703873040384 parent 0 root 2
Extent back ref already exists for 2703872610304 parent 0 root 2
Extent back ref already exists for 2703874686976 parent 0 root 2
Extent back ref already exists for 2703873318912 parent 0 root 2
Extent back ref already exists for 2703873740800 parent 0 root 2
Extent back ref already exists for 2703874465792 parent 0 root 2
Extent back ref already exists for 2703876370432 parent 0 root 2
Extent back ref already exists for 2703877046272 parent 0 root 2
Extent back ref already exists for 2703877050368 parent 0 root 2
Extent back ref already exists for 2703878647808 parent 0 root 2
Extent back ref already exists for 2703876407296 parent 0 root 2
Extent back ref already exists for 2703872782336 parent 0 root 2
Extent back ref already exists for 2703907266560 parent 0 root 2
Extent back ref already exists for 2703906869248 parent 0 root 2
Extent back ref already exists for 2703907241984 parent 0 root 2
Extent back ref already exists for 2703907553280 parent 0 root 2
Extent back ref already exists for 2703907942400 parent 0 root 2
Extent back ref already exists for 2703910154240 parent 0 root 2
Extent back ref already exists for 2703915515904 parent 0 root 2
Extent back ref already exists for 2703916965888 parent 0 root 2
Extent back ref already exists for 2703875280896 parent 0 root 2
Extent back ref already exists for 2703878635520 parent 0 root 2
Extent back ref already exists for 2221635985408 parent 0 root 2
Extent back ref already exists for 2703883841536 parent 0 root 2
Extent back ref already exists for 2703882489856 parent 0 root 2
Extent back ref already exists for 2703883186176 parent 0 root 2
Extent back ref already exists for 2221711962112 parent 0 root 2
parent transid verify failed on 2703875964928 wanted 9066 found 9064
parent transid verify failed on 2703920701440 wanted 9066 found 7543
parent transid verify failed on 2703921225728 wanted 9066 found 7543
parent transid verify failed on 2703919247360 wanted 9066 found 7543
parent transid verify failed on 2703921467392 wanted 9066 found 7543
parent transid verify failed on 2703919116288 wanted 9066 found 7543
parent transid verify failed on 2703920193536 wanted 9066 found 7543
leaf parent key incorrect 2703862099968
bad block 2703862099968
parent transid verify failed on 2703869194240 wanted 9069 found 9062
parent transid verify failed on 2703872065536 wanted 9075 found 9060
leaf parent key incorrect 2703865634816
bad block 2703865634816
parent transid verify failed on 2703872434176 wanted 9077 found 9059
leaf parent key incorrect 2703868116992
bad block 2703868116992
leaf parent key incorrect 2703869460480
bad block 2703869460480
parent transid verify failed on 2703878242304 wanted 9075 found 9065
leaf parent key incorrect 2703871660032
bad block 2703871660032
leaf parent key incorrect 2703872061440
bad block 2703872061440
bad block 2703873073152
parent transid verify failed on 2703873613824 wanted 9077 found 9025
bad block 2703873536000
bad block 2703876689920
leaf parent key incorrect 2703877709824
bad block 2703877709824
parent transid verify failed on 2703897231360 wanted 9077 found 9061
parent transid verify failed on 2703901822976 wanted 9077 found 9061
parent transid verify failed on 2703879938048 wanted 9075 found 9065
leaf parent key incorrect 2703879299072
bad block 2703879299072
bad block 2703881900032
leaf parent key incorrect 2703882805248
bad block 2703882805248
Extent back ref already exists for 2703885160448 parent 0 root 2
leaf parent key incorrect 2703883829248
bad block 2703883829248
parent transid verify failed on 2703878213632 wanted 9077 found 9061
bad block 2703896338432
Extent back ref already exists for 531120128 parent 0 root 2
Extent back ref already exists for 3624028745728 parent 0 root 2
Extent back ref already exists for 458403840 parent 0 root 2
Extent back ref already exists for 3624039575552 parent 0 root 2
Extent back ref already exists for 2221892575232 parent 0 root 2
Extent back ref already exists for 538480640 parent 0 root 2
Extent back ref already exists for 2221926707200 parent 0 root 2
Extent back ref already exists for 2221926719488 parent 0 root 2
Extent back ref already exists for 746985025536 parent 0 root 2
Extent back ref already exists for 2703867379712 parent 0 root 2
Extent back ref already exists for 2703877795840 parent 0 root 2
Extent back ref already exists for 3624023527424 parent 0 root 2
Extent back ref already exists for 3624023547904 parent 0 root 2
Extent back ref already exists for 3624029978624 parent 0 root 2
Extent back ref already exists for 2221998817280 parent 0 root 2
Extent back ref already exists for 747239817216 parent 0 root 2
Extent back ref already exists for 1497120432128 parent 0 root 2
Extent back ref already exists for 1497285292032 parent 0 root 2
Extent back ref already exists for 1497514807296 parent 0 root 2
Extent back ref already exists for 1497549565952 parent 0 root 2
Extent back ref already exists for 746363998208 parent 0 root 2
Extent back ref already exists for 2703878045696 parent 0 root 2
Extent back ref already exists for 2221998825472 parent 0 root 2
Extent back ref already exists for 3624204349440 parent 0 root 2
Extent back ref already exists for 484401152 parent 0 root 2
Extent back ref already exists for 2221929988096 parent 0 root 2
Extent back ref already exists for 707141632 parent 0 root 2
Extent back ref already exists for 2221930053632 parent 0 root 2
Extent back ref already exists for 2703875485696 parent 0 root 2
Extent back ref already exists for 3624161251328 parent 0 root 2
Extent back ref already exists for 3624024666112 parent 0 root 2
Extent back ref already exists for 165191680 parent 0 root 2
Extent back ref already exists for 3623966523392 parent 0 root 2
Extent back ref already exists for 2221876412416 parent 0 root 2
Extent back ref already exists for 1496842756096 parent 0 root 2
Extent back ref already exists for 2221936676864 parent 0 root 2
Extent back ref already exists for 1497422680064 parent 0 root 2
Extent back ref already exists for 1497454501888 parent 0 root 2
Extent back ref already exists for 2221823078400 parent 0 root 2
Extent back ref already exists for 3624937074688 parent 0 root 2
Extent back ref already exists for 3624953167872 parent 0 root 2
Extent back ref already exists for 3624268865536 parent 0 root 2
Extent back ref already exists for 2221718986752 parent 0 root 2
Extent back ref already exists for 414621696 parent 0 root 2
Extent back ref already exists for 2221929848832 parent 0 root 2
Extent back ref already exists for 3624936488960 parent 0 root 2
Extent back ref already exists for 3623950848000 parent 0 root 2
Extent back ref already exists for 733777920 parent 0 root 2
Extent back ref already exists for 3624953176064 parent 0 root 2
Extent back ref already exists for 2221928071168 parent 0 root 2
Extent back ref already exists for 3624310071296 parent 0 root 2
Extent back ref already exists for 2221906374656 parent 0 root 2
Extent back ref already exists for 2221906382848 parent 0 root 2
Extent back ref already exists for 2703871188992 parent 0 root 2
Extent back ref already exists for 2703879311360 parent 0 root 2
Extent back ref already exists for 761036800 parent 0 root 2
Extent back ref already exists for 751378432 parent 0 root 2
Extent back ref already exists for 2221916528640 parent 0 root 2
parent transid verify failed on 2703899471872 wanted 9077 found 9061
parent transid verify failed on 2703876403200 wanted 9078 found 9055
parent transid verify failed on 2703880609792 wanted 9069 found 9065
parent transid verify failed on 2703904714752 wanted 9066 found 5091
leaf parent key incorrect 2703904018432
bad block 2703904018432
parent transid verify failed on 2703921881088 wanted 9066 found 7543
parent transid verify failed on 2703883845632 wanted 9074 found 9061
parent transid verify failed on 2703887519744 wanted 9076 found 9056
btrfsck: disk-io.c:410: find_and_setup_root: Assertion `!(ret)' failed.
Aborted

---

### Post by Blue Beard on 2010-07-12
There is a looping problem that has been fixed in linux 2.6.35-rc4 (used in 10.10)

---

