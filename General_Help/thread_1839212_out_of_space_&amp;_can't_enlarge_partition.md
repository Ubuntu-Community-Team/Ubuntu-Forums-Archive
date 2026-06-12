---
title: "out of space &amp; can't enlarge partition"
date: 2011-09-05
forum: General Help
---

### Post by mariannep on 2011-09-05
Hello!

Sorry if this is a silly question but I'm just a very plain vanilla user and just can't find a solution... :/

Everytime I boot I'm greeted with the notice that I have only n Mb free, for values of n between 80 and a 100! :(

I think the problem is that I have a very small sda5 partition (the computer's a bit old) and the linux swap seems small, too. But even though there's space (looking with gparted) I can't move or enlarge that partition. :(
I have tried using a live ubuntu USB, disabled swap and but still it says no free Mb before/after that partition so it won't move :(

Below I'm pasting my partition info. I'd get rid of the Windows one if needed (I only use it for testing once every few months) but I think that's not the real problem.

Any ideas??

Thanks!


Marianne

-----$ sudo fdisk -l

Disco /dev/sda: 160.0 GB, 160000000000 bytes
255 cabezas, 63 sectores/pista, 19452 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0xf8a74311

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1               1           7       56196   de  Utilidad Dell
/dev/sda2   *           8        4343    34826332+   7  HPFS/NTFS
/dev/sda3            4343       10290    47766528   83  Linux
/dev/sda4           17737       19452    13783167    5  Extendida
/dev/sda5           19204       19452     2000061   82  Linux swap / Solaris
/dev/sda6           17737       19135    11235328   83  Linux
/dev/sda7           19135       19203      545792   82  Linux swap / Solaris

Las entradas de la tabla de particiones no están en el orden del disco

Disco /dev/sdb: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x000a59fa

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1       14115   113371178+  83  Linux
/dev/sdb2           14115       19458    42917889    5  Extendida
/dev/sdb5           14115       19233    41113600   83  Linux
/dev/sdb6           19233       19458     1803264   82  Linux swap / Solaris

---

### Post by WorMzy on 2011-09-05
Post the output of the following commands, please:

```
sudo du -hx --max-depth=1 / | sort -h
```
(^give this one a little time to complete)
```
df -h /
```

---

### Post by mariannep on 2011-09-05
Thank you! Here they are!

du: no se puede acceder a «/home/marianne/.gvfs»: Permiso denegado [Access permission denied to that dir]
0	/dev
0	/proc
0	/sys
4,0K	/cdrom
4,0K	/media
4,0K	/mnt
4,0K	/selinux
12K	/.kde
16K	/lost+found
144K	/tmp
200K	/srv
264K	/root
6,7M	/bin
7,5M	/sbin
16M	/etc
123M	/boot
200M	/opt
596M	/var
725M	/lib
3,7G	/usr
4,4G	/home
9,7G	/


S.archivos            Tam.  Usado Disp. % Uso Montado en
/dev/sda6              11G  9,9G  215M  98% /
none                  495M  268K  494M   1% /dev
none                  500M  1,5M  499M   1% /dev/shm
none                  500M  368K  500M   1% /var/run
none                  500M     0  500M   0% /var/lock

Cheers!!

---

### Post by WorMzy on 2011-09-05
Okay, everything looks in order, no out of control logs or anything, you're just running out of space naturally. Looking at your original post, you have three swap partitions. You could get rid of the two on sda (sda5 and sda7), and then extend sda6 so that it take up the space those two partitions were using (approximately 2.5GB). That would be the easiest thing to do for now.

Alternatively, since you have left a sizable gap between sda3 and the extended partition (approximately 55GB), so you could resize the extended partition to fill this space, then resize sda6 to fill the newly acquired space. This approach is far more risky, and I'm not sure whether extended partitions will allow you to resize them to the left or not. You'll definitely need to unmount both swap partitions in the extended partition before gparted will even consider letting you do anything to the extended partition.

Another option depends on what you're using sda3 for. Your current partition (sda6) is a perfectly acceptable size for the OS, as shown by the du output; but your /home folder is sucking up almost half of the available space. If you're not using sda3 for anything in particular (e.g. it just contains a derelict OS), you could convert it into a storage partition. Resize the partition to use up that unused 55GB between it and the extended partition, then (optionally) format it so that it's a clean partition with no trace of whatever was there previously. Once that's done, you can either make it into a dedicated /home partition, or just transfer all your documents, videos, pictures, etc. over to it, and have it be automatically mounted. This option would be the safest of the three, but requires a lot more work to set up.

In any case, make sure you back up any important files before messing with partitions. Things can, and do, occasionally go wrong.

---

### Post by yuri_spb on 2011-09-06
I have a similar issue. / has only a couple of hundreds MB free. Whereas /home has plenty of space.
Using Gparted I have managed to decrease /home and now I have an extra space 4GB near to /. However I cannot merge them into one partition using Gparted. I suspect it is due to the fact that / is on primary partition whereas /home and the new partition are on the ext partition.

Hence I am looking what folders could be moved to a new partition from the / one
Removing /var/cache/apt/archives gives me some space now, but I assume a more long-term solution is necessary.

---

### Post by mariannep on 2011-09-06
Many thanks!!!

As you imagined I can't seem to enlarge the OS partition, so I'm thinking of moving the home directory. I already moved most of my stuff elsewhere long ago so this must be cached files, Picasa stuff maybe...

Does this seem like a sensible way to move /home, using Natty Narwhal?

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Many thanks!

---

### Post by YesWeCan on 2011-09-06
```
Dispositivo Inicio Comienzo Fin Bloques Id Sistema
/dev/sda1       1     7    56196   de Utilidad Dell
/dev/sda2 *     8  4343 34826332+   7 HPFS/NTFS
/dev/sda3    4343 10290 47766528   83 Linux
       [COLOR="Blue"]<< gap of 110GB >>[/COLOR]
/dev/sda4   17737 19452 13783167    5 Extendida
/dev/sda6   17737 19135 11235328   83 Linux
/dev/sda7   19135 19203   545792   82 Linux swap / Solaris
/dev/sda5   19204 19452  2000061   82 Linux swap / Solaris
```
Hi there. Using a live CD and GParted, you should be able to resize sda4 to move its left edge to the end of sda3, and then resize sda6 to move its left edge to fill the gap, thus adding 110GB to sda6.

Messing with partitions is dangerous so make sure you have backed up any vital files before you do it. :)

---

### Post by WorMzy on 2011-09-06
Don't try to enlarge the OS partition first; you'll need to enlarge the extended partition before you can enlarge the OS partition.

So, to clarify, resize sda4 to consume the unutilised space, then resize sda6 (you may need to move or delete sda5 or 7 before you are able to). If you meant that you weren't able to resize sda4, then fair enough.

That tutorial looks sound enough. Just make sure that you read everything through carefully before proceeding, and make sure you don't skip any steps; the last thing you need is to rm -r your /home without checking that everything has copied over to /media/home correctly, and losing half your stuff because of it.

---

### Post by mariannep on 2011-09-13
Thank you both!!! I finally was able to try again last night and it worked like a treat. Moreover, it seems nothing was lost! :)

Of course the problem was I hadn't realized there was an enveloping partition (sda4). Duh to myself!

Anyway.. .I couldn't have it without you! So thanks a lot!!!

---

