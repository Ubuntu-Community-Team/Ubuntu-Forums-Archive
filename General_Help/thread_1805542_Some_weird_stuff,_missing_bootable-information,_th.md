---
title: "Some weird stuff, missing bootable-information, thx to Avira &quot;repair&quot; boot sectors"
date: 2011-07-16
forum: General Help
---

### Post by Nergatus on 2011-07-16
So yesterday while working under windows Avira told me, that i had bootsector-viruses and wanted to repair all my Partitions. I thought that it couldnt hurt, its a professional program after all... Well i rebootet today and it said, that the bootsector is newly made and i require to run a Bootdisk (term for floppy used) and use sys to make it bootable (freely translated from my memory and from german) ... and after that there is just the grub rescue console. Well, i dont have a win XP boot-floppy, so i booted from my ubuntu live cd and searched my drives:
http://ubuntuforums.org/```

ubuntu@ubuntu:~$ cd /media
ubuntu@ubuntu:/media$ ls
apt  disk
ubuntu@ubuntu:/media$ cd disk
ubuntu@ubuntu:/media/disk$ ls
ls: Zugriff auf ½w &#8730;·3z.wà&#8359; nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf öµ&#9608;&#9474;&#9619;x&#9577;.&#8801;ÿ&#9572; nicht möglich: Eingabe-/Ausgabefehler
.¢»* nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf ^G&#9492;¿&#915;8v¡.&#9500;¥É nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf äç9&#8992;ie.b6&#9558; nicht möglich: Eingabe-/Ausgabefehler
è&#9618;cuè&#964;.yë nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf &#9570;&#920;f&#9562;é<.&#9553;D5 nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf d &#9618;&#963;°&#9600;°.@ºù nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf &#9579;\&#9532;h&#9600;:    &#9559;.&#9500;&#9574; nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf ±&#9557;FS    ºy.²&#9524;&#9562; nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf ;'úb&#9556;.&#9632;&#9580;&#9570; nicht möglich: Eingabe-/Ausgabefehler
33çµ.&#9558;÷&#9575; nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf 8à&#9564;!\&#966;&#945;.&#8801;q&#8993; nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf &#9575;
                  «    BªÇ.9P&#945; nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf &&#9612;&#966;<d&#9579;&#9561;<.3&ç nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf ±/&#9570;Hù.5¡&#9472; nicht möglich: Datei oder Verzeichnis nicht gefunden
ls: Zugriff auf l&#9484;7ó°ß.p&#9617;ü nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf  ,
                   6&#9562;&#8801;.&#9560;&#9567;q nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf ö¥&#8734;[à.±d nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf é÷w&#9553;
_1&#9552;.&#9575;&#9564;&#966; nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf n&#9612;.¼r&#9617; nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf j#¬ë&#963;ú./ nicht möglich: Datei oder Verzeichnis nicht gefunden
ls: Zugriff auf 'µp£a&#9563;8.&#9619;µ&#9484; nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf &#966;&#9562;æ&#9572;½ƒ&#948;.v&#8745;j nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf ê&#9472;}Æ9E1.&#9561;;e nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf OÉ&#8359;I&#9552;î.=µª nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf ¢¿5@ÿuïg.0(f nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf n¬vjqäq.¥db nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf *¿Æ'&#9608;&#9573;&#9575;.'?ä nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf &#9574;µ«p(t&#937;.
                         5 nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf &#9612;ëê1/a
                      &#8801;.{m&#9579; nicht möglich: Datei oder Verzeichnis nicht gefunden
ls: Zugriff auf &#9484;Ö^÷ÿéû.&#9472;0& nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf xb&#9579;&#9560;ù&ô&#9579;.&#9566; nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf Ks_t&#920;[åJ.ày» nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf (&#9618;{o@&#9600;&#9604;.ù,G nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf &#9579;_&#9575; ñ&#9474;&#945;.5&#8776; nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf ~ílo&#9484;&#8734;8e.z&#9561;  nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf &#9567;n
                  dGGâ.d8 nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf |&#8319;'&#937;&#9555;&#9560;ü.ª¿ä nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf d"¬&#964;éñb.°i nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf ;&#9617;u&#8734;&#9580;&#9567;¢.d&#9558;8 nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf &#920;¼¡áv!&#931;T.&#9564;&#8992;&#9555; nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf ,e "&#8804;&#963;&#9556;.&#9608;'&#9563; nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf o&#9474;}3&#9608;pl.S&#9580; nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf  )á&#9561;¢â-¿..v&#9572; nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf &#920;neüj&#9474;è.&#8801;&#9492; nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf  l&#9574;&#9554;mö&#8745;&#8745;.óV&#934; nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf ß&#9559;±&#9568;ñ&#9574;&#9618;..&#9619;8± nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf &#9516;
ô¼^wt.&#9488; nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf 4&#8976;    åIäj.p/ nicht möglich: Datei oder Verzeichnis nicht gefunden
ls: Zugriff auf ª<&#8730;&#9472;&#9554;j&#966;.&#9484;&#9562;£ nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf µ,`Ñ&âéè.
&#937; nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf én    &#9563;.«/% nicht möglich: Datei oder Verzeichnis nicht gefunden
ls: Zugriff auf /z»&#8992;
                     &#8729;ö.
_&#8776; nicht möglich: Datei oder Verzeichnis nicht gefunden
ls: Zugriff auf É&#9618;g{i&#9554;Æ.(ô nicht möglich: Eingabe-/Ausgabefehler
ls: Zugriff auf ?6&#9567;*@è{[.üe nicht möglich: Eingabe-/Ausgabefehler
_&#8804; &#9484;«)&#8992;&#9573;.]&#8734;&#9557;  &#9575;??«?BªÇ.9P&#945;  G]¡cB.&#9567;&#9567;.&#8729;&#931;&#9604;  o&#9474;}3?&#9608;pl.S?&#9580;  v??&#8729;hµ&ƒ.k&#9474;R
½?&#9472;küö&#9553;°.%3¥  &#9555;+£}?&#9617;?&#8805;.bk?  ^G&#9492;¿&#915;8v¡.&#9500;¥É  ö¥&#8734;?[?à?.±d?  ?vôm?µw&#9604;.Üß_
½w &#8730;·3z?.wà&#8359;  &#9632;B?&#8801;?qú&#8745;.6&#9484;&#9617;  &#9552;g&#915;Ü&#9566;eZ?.¢»*  ?OÉ&#8359;?I&#9552;î.=µª  &#9500;V&#9556;&#9573;&#8805;ò&#9616;&.&#9557;s&#8734;
1?&#960;rL?&#9563;U.&#9566;$|  ?&#8801;b?&#9572;&#963;8[.&#9619;Ñ?  &#9570;?g&#966;u&#9570;ä&#9575;.&#9576;y&#9474;  ?(&#9618;{o@&#9600;&#9604;.ù,G  wb&#9484;w&#8745;[û&#9578;.r&#9565;d
&?33?çµ?.&#9558;÷&#9575;  çâö2?F_?.&#9566;&#9567;&#9524;  &#9579;\&#9532;h&#9600;:?&#9559;.&#9500;?&#9574;  oW&#931;&#9577;&#9500;]µ^.&#9619;&#8359;&#964;  w&#9516;ün&#8993;ô&#9604;?.?`é
4&#8976;??åIäj.p/?  ç&#9632;I??&#937;÷&#9558;. &#9616;&#9579;  ±/?&#9570;H??ù.5¡&#9472;  ô&#9568;µ£&#9568;|x&#9559;.&#9555;?&  £&#9500;Xa&#9552;&#9568;M½.&#9579;~&#9563;
¢¿5@ÿuïg.0(f  ?ç&#9567;k&#9573;4??.{_&#9472;  ?|¢iª?£=.p&#9600;¬  öµ?&#9608;&#9474;&#9619;x&#9577;.&#8801;ÿ&#9572;  xb&#9579;&#9560;ù&ô&#9579;.??&#9566;
&#8804;&#9474;[?60?j.?nî  ~ç&#8359;@?lz&#9553;.y?e  &#8993;ì&#9600;Ç# °â.mµ&#915;  &#9484;?Ö^÷ÿéû.&#9472;0&  &#9568;zbä?&#945;â?.í&#9563;&#8359;
?6&#9567;*@è{[.üe?  '?D2{ÜÆ±.&#8730;&#8805;|  ìkx?&#9474;±~ç.?&#9560;÷  'µp£a&#9563;?8.&#9619;µ&#9484;  Zçê&#8992;¢x?&#964;.&#9573;è&#9516;
 ?,?6?&#9562;&#8801;.&#9560;&#9567;q  D&#9571;\¢&#9500;?&#9562;&#9532;.e?&#9553;  ~ílo&#9484;&#8734;8e.z&#9561;   &#9574;µ?«p(t&#937;.??5  ?/z»&#8992;?&#8729;ö.?_&#8776;
8à&#9564;!\&#966;?&#945;.&#8801;q&#8993;  d &#9618;&#963;°&#9600;?°.@ºù  j#¬?ë&#963;ú?.??/  r6?&#9500;?m&#8359;b.é$2  &#915;$?&#9524;&#8805;ñ+?.&#9573;&#937;&#9571;
9@,?|&#9616;?&#966;.$4&#9567;  d"¬?&#964;éñb.°?i  Ks_t&#920;[åJ.ày»  ß4d&#9576;?&#945;µ&#8776;.ñ?ü  &#920;¼¡áv!&#931;T.&#9564;&#8992;&#9555;
á<¥&#9567;04#7.h$>  ê&#9472;}Æ9E1?.&#9561;;e  l3qfö½s¡.&#8976;&#9553;&#9565;  ß&#9559;±&#9568;ñ&#9574;&#9618;..&#9619;8±  'ƒ&#9604;&#920;c&#8805; ?
a²¢Æ:??&#9472;.ƒx&#9571;  ?è&#9618;cuè&#964;?.yë?  l?&#9484;7ó°ß?.p&#9617;ü  T?&#8359;&#960;µW3².°&#9572;&#8976;  ?&#9570;&#920;f&#9562;é?<.&#9553;D5
äç9&#8992;i??e.b6&#9558;  &#9556;÷?&#8801;[ê&#8804;&#9554;.é??  m57áù&#9600;&#9612;&#9559;.úz@  &#9632;?uÄÑ&#8776;&#9484;&#934;.&#9632;Vc  &#920;neüj?&#9474;è.&#8801;?&#9492;
*¿Æ'?&#9608;&#9573;&#9575;.'?ä  &#9612;ëê1/a?&#8801;.{m&#9579;  &#9571;MÖ &#9573;ì&#9618;n.=&#966;&#966;  ~uäp?&#9508;ê½.r&#9576;º  &#964;âò&#9524;&#9567;|&#920;*.&#966;¡?
a?'í?ú&#9572;?.!?9  É&#9618;?g{i&#9554;Æ.(?ô  n?&#9612;.¼r&#9617;       ;|??'úb&#9556;.&#9632;&#9580;&#9570;  &#966;&#9562;æ?&#9572;½ƒ&#948;.v&#8745;j
ª?<&#8730;&#9472;&#9554;j&#966;.&#9484;&#9562;£  én????&#9563;?.«/%  µ,`Ñ&âéè.?&#937;?  ;&#9617;?u&#8734;&#9580;&#9567;¢.d&#9558;8  &&#9612;&#966;<d&#9579;&#9561;<.3&ç
±&#9516;åô&#8805;m&#9559;\.>?&#9577;  é÷w&#9553;?_1&#9552;.&#9575;&#9564;&#966;  &#9567;n?dG?Gâ.?d8  ü&#9564;&#9608;ê?=ây.t)?  !&#966;.ûâ&#9555;«&#9567;.n²£
&#9516;?A}&#9488;Q{&#9563;.0&#9474;·  ,e "?&#8804;&#963;&#9556;.&#9608;'&#9563;  n&#9575;ñ&#9532;âñ&#9472;&#9600;.Vçh  &#9612;û?^?g¬U.&#9617;l&#9576;  ,&#966;&#9496;W?&#8804;?P.&#9616;&#966;?
\Ä£Uù&#9612;¿i.&#9559;}?  &#9562;&#8730;fe'&#9568;&#8359;».,"&#9559;  ?n¬vjqäq.¥db  &#9500;?ú(ó&#963;âÿ.â7c  |&#8319;?'&#937;&#9555;&#9560;ü.ª¿ä
&#9561;&#9576;?ày:q±.¬[º  *fo¥&#9555;p&#9608;é.&#9577;'²  &#9579;_&#9575;? ñ&#9474;&#945;.5&#8776;?  üßôíåjì?.4&#9572;c   )á&#9561;¢â-¿..v&#9572;
&#8776;???à&#949;ÑG.a&#9492;(  ±&#9557;FS??ºy.²&#9524;&#9562;  &#9516;??ô¼^wt.&#9488;??  >?-?vâår.&#9573;=&#9559;   l&#9574;&#9554;mö&#8745;&#8745;.óV&#934;

```
these "words" are arranged in a nice chart, like ls does it but make no sense to me...

Thats my Problem and i would be glad if anyone could tell me how to get my ubuntu (natty) and my winXP to boot again with all my stuff on my harddrives

sry for my bad english,  I haven't written in english for a while and right now not the patience to correct it.

PS: if this helps: gparted says my hdd are unused drives and fdisk says
ubuntu@ubuntu:~$ sudo fdisk -l

Platte /dev/sda: 250.1 GByte, 250059350016 Byte
255 Köpfe, 63 Sektoren/Spur, 30401 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System

Platte /dev/sdb: 1500.3 GByte, 1500301910016 Byte
255 Köpfe, 63 Sektoren/Spur, 182401 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x79ecd26a

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1               1      170155  1366770006    7  HPFS/NTFS
/dev/sdb2          170156      182401    98365345+   5  Erweiterte
/dev/sdb5          170156      181898    94322688   83  Linux
/dev/sdb6          181898      182402     4043776   82  Linux Swap / Solaris
ubuntu@ubuntu:~$ sudo fdisk -lu

Platte /dev/sda: 250.1 GByte, 250059350016 Byte
255 Köpfe, 63 Sektoren/Spur, 30401 Zylinder, zusammen 488397168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System

Platte /dev/sdb: 1500.3 GByte, 1500301910016 Byte
255 Köpfe, 63 Sektoren/Spur, 182401 Zylinder, zusammen 2930277168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x79ecd26a

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1              63  2733540074  1366770006    7  HPFS/NTFS
/dev/sdb2      2733541374  2930272064    98365345+   5  Erweiterte
/dev/sdb5      2733541376  2922186751    94322688   83  Linux
/dev/sdb6      2922188800  2930276351     4043776   82  Linux Swap / Solaris
(its in german but the words aren't that different)

---

### Post by Rubi1200 on 2011-07-16
Hi and welcome to the forums :-)

To try and confirm what is going on we need to see the boot script results:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Nergatus on 2011-07-19
I am sorry for not replying to your post for some days but i hope that you will still help me out^^
gedit didnt want to open it, so i cated it via terminal... i hope no information was lost

```
--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="8"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root 95b085d5-43dd-46b0-8293-b85ba02a4aab
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=800x600
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root 95b085d5-43dd-46b0-8293-b85ba02a4aab
set locale_dir=($root)/boot/grub/locale
set lang=de_DE
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=6
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root BE1095B51095755D
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 95b085d5-43dd-46b0-8293-b85ba02a4aab
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=95b085d5-43dd-46b0-8293-b85ba02a4aab ro splash vga=771  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 95b085d5-43dd-46b0-8293-b85ba02a4aab
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=95b085d5-43dd-46b0-8293-b85ba02a4aab ro single splash vga=771
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 95b085d5-43dd-46b0-8293-b85ba02a4aab
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=95b085d5-43dd-46b0-8293-b85ba02a4aab ro splash vga=771  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 95b085d5-43dd-46b0-8293-b85ba02a4aab
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=95b085d5-43dd-46b0-8293-b85ba02a4aab ro single splash vga=771
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 95b085d5-43dd-46b0-8293-b85ba02a4aab
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=95b085d5-43dd-46b0-8293-b85ba02a4aab ro splash vga=771  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 95b085d5-43dd-46b0-8293-b85ba02a4aab
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=95b085d5-43dd-46b0-8293-b85ba02a4aab ro single splash vga=771
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 95b085d5-43dd-46b0-8293-b85ba02a4aab
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 95b085d5-43dd-46b0-8293-b85ba02a4aab
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=95b085d5-43dd-46b0-8293-b85ba02a4aab /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=4bda3090-f124-42ca-a7fc-2a543e3e7131 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdc        /media/floppy1  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

1345.581020355 = 1444.806619136 boot/grub/core.img                             1
1329.772457123 = 1427.832303616 boot/grub/grub.cfg                             1
1371.904247284 = 1473.070968832 boot/grub/menu.lst                             1
1305.375976562 = 1401.636782080 boot/initrd.img-2.6.32-28-generic              2
1331.206336975 = 1429.371920384 boot/initrd.img-2.6.35-28-generic              1
1334.888690948 = 1433.325817856 boot/initrd.img-2.6.38-8-generic               2
1345.770366669 = 1445.009928192 boot/vmlinuz-2.6.32-28-generic                 1
1345.774368286 = 1445.014224896 boot/vmlinuz-2.6.35-28-generic                 1
1333.239562988 = 1431.555080192 boot/vmlinuz-2.6.38-8-generic                  2
1334.888690948 = 1433.325817856 initrd.img                                     2
1331.206336975 = 1429.371920384 initrd.img.old                                 1
1333.239562988 = 1431.555080192 vmlinuz                                        2
1345.774368286 = 1445.014224896 vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  eb 2a eb 32 eb 32 eb 32  eb 32 eb 32 cb 2a eb 2a  |.*.2.2.2.2.2.*.*|
00000010  eb 2a 0c 33 0c 3b eb 32  eb 32 eb 32 ca 32 ca 2a  |.*.3.;.2.2.2.2.*|
00000020  ca 2a cb 2a eb 32 eb 32  eb 32 eb 2a eb 32 eb 2a  |.*.*.2.2.2.*.2.*|
00000030  ca 2a eb 2a cb 2a ca 2a  ea 2a ca 2a ea 2a 0b 33  |.*.*.*.*.*.*.*.3|
00000040  2c 3b 2c 3b eb 32 ca 32  eb 32 ca 32 ca 32 aa 2a  |,;,;.2.2.2.2.2.*|
00000050  aa 32 ca 32 cb 32 cb 32  af 53 d7 a5 d6 ad 0b 4b  |.2.2.2.2.S.....K|
00000060  cb 3a ec 3a eb 32 eb 32  ec 3a eb 32 eb 32 cb 32  |.:.:.2.2.:.2.2.2|
00000070  cb 32 ca 32 aa 2a ca 32  aa 2a aa 2a cb 32 eb 32  |.2.2.*.2.*.*.2.2|
00000080  cb 32 ca 2a aa 2a aa 2a  ca 2a ca 2a ca 32 ca 2a  |.2.*.*.*.*.*.2.*|
00000090  aa 2a cb 32 aa 2a 8a 2a  ab 32 aa 32 aa 2a 8a 2a  |.*.2.*.*.2.2.*.*|
000000a0  8a 2a aa 2a aa 2a 8a 2a  6a 2a 6a 2a 8a 2a 8b 32  |.*.*.*.*j*j*.*.2|
000000b0  6a 2a 6a 2a aa 2a cb 32  ca 32 6d 43 ef 5b eb 3a  |j*j*.*.2.2mC.[.:|
000000c0  69 2a 6a 2a 8a 32 cc 3a  8f 53 af 5b 4d 53 ae 5b  |i*j*.2.:.S.[MS.[|
000000d0  8e 5b cf 63 10 6c 8e 5b  6e 5b 6d 5b 6d 5b 4d 53  |.[.c.l.[n[m[m[MS|
000000e0  2d 4b 4e 53 f0 63 11 6c  f0 6b 10 6c 31 74 10 6c  |-KNS.c.l.k.l1t.l|
000000f0  4d 53 eb 42 cb 3a eb 42  0c 43 4d 4b 4d 4b 6e 53  |MS.B.:.B.CMKMKnS|
00000100  cf 5b ef 63 4d 4b cb 32  ab 32 ab 32 ab 32 8a 2a  |.[.cMK.2.2.2.2.*|
00000110  6a 2a 69 22 69 22 6a 22  aa 2a aa 2a 8a 2a aa 2a  |j*i"i"j".*.*.*.*|
00000120  ab 2a cb 32 cb 32 ec 3a  ec 3a ec 3a ec 3a 0c 3b  |.*.2.2.:.:.:.:.;|
00000130  2d 43 0c 3b cb 32 aa 2a  aa 2a cb 2a cb 32 aa 32  |-C.;.2.*.*.*.2.2|
00000140  aa 32 aa 32 cb 32 cb 32  8a 2a ab 2a cc 32 ec 32  |.2.2.2.2.*.*.2.2|
00000150  cb 32 8a 2a aa 2a 8a 2a  aa 2a aa 2a 8a 2a 6a 2a  |.2.*.*.*.*.*.*j*|
00000160  6a 2a 8a 2a ab 32 ab 32  cb 32 eb 32 ec 32 cb 32  |j*.*.2.2.2.2.2.2|
00000170  cb 32 eb 32 cb 32 aa 32  aa 32 eb 32 cb 32 ab 2a  |.2.2.2.2.2.2.2.*|
00000180  eb 32 eb 32 eb 32 eb 32  eb 32 cb 32 cb 32 cb 2a  |.2.2.2.2.2.2.2.*|
00000190  ab 32 cb 32 ec 3a 6d 53  10 64 af 5b 2c 43 eb 3a  |.2.2.:mS.d.[,C.:|
000001a0  cb 32 aa 32 eb 32 eb 32  cb 32 cb 32 eb 32 0c 3b  |.2.2.2.2.2.2.2.;|
000001b0  2c 3b 6d 43 6d 43 8e 4b  8e 4b 8e 53 af 53 00 fe  |,;mCmC.K.K.S.S..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 80 3e 0b 00 fe  |............>...|
000001d0  ff ff 05 fe ff ff 02 80  3e 0b 00 70 7b 00 00 00  |........>..p{...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sda

00000000  eb 48 90 49 42 4d 20 41  56 34 30 00 02 01 01 00  |.H.IBM AV40.....|
00000010  02 e0 00 40 0b f0 09 00  12 00 02 00 00 00 00 00  |...@............|
00000020  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000040  00 00 00 00 00 00 00 00  00 00 8c c8 8e d8 fa 8e  |................|
00000050  d0 bc fe ff fb be 77 7c  fc ac 0a c0 74 0b 56 b4  |......w|....t.V.|
00000060  0e bb 07 00 cd 10 5e eb  f0 32 e4 cd 16 b4 0f cd  |......^..2......|
00000070  10 32 e4 cd 10 cd 19 0d  0a 20 20 20 20 20 20 20  |.2.......       |
00000080  20 20 20 20 20 20 20 20  20 20 20 20 20 20 20 20  |                |
*
000000a0  20 20 20 20 0d 0a 0a 44  65 72 20 42 6f 6f 74 73  |    ...Der Boots|
000000b0  65 6b 74 6f 72 20 64 69  65 73 65 72 20 44 69 73  |ektor dieser Dis|
000000c0  6b 65 74 74 65 20 77 75  72 64 65 20 6e 65 75 20  |kette wurde neu |
000000d0  65 72 73 74 65 6c 6c 74  2e 20 20 20 20 20 20 20  |erstellt.       |
000000e0  20 0d 0a 42 65 6e 75 74  7a 65 6e 20 53 69 65 20  | ..Benutzen Sie |
000000f0  64 65 6e 20 44 4f 53 2d  42 65 66 65 68 6c 20 53  |den DOS-Befehl S|
00000100  59 53 20 75 6d 20 64 69  65 73 65 20 44 69 73 6b  |YS um diese Disk|
00000110  65 74 74 65 20 62 6f 6f  74 66 84 68 69 67 20 7a  |ette bootf.hig z|
00000120  75 20 6d 61 63 68 65 6e  21 0d 0a 42 69 74 74 65  |u machen!..Bitte|
00000130  20 6c 65 67 65 6e 20 53  69 65 20 6e 75 6e 20 65  | legen Sie nun e|
00000140  69 6e 65 20 53 79 73 74  65 6d 64 69 73 6b 65 74  |ine Systemdisket|
00000150  74 65 20 69 6e 73 20 4c  61 75 66 77 65 72 6b 20  |te ins Laufwerk |
00000160  75 6e 64 20 0d 0a 64 72  81 63 6b 65 6e 20 53 69  |und ..dr.cken Si|
00000170  65 20 65 69 6e 65 20 54  61 73 74 65 2e 00 00 00  |e eine Taste....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

hexdump: FD/sda/?$
                  ??&#65533;+.???: Eingabe-/Ausgabefehler
hexdump: FD/sda/?$
                  ??&#65533;+.???: Eingabe-/Ausgabefehler
hexdump: FD/sda/?$
                  ??&#65533;+.???: Eingabe-/Ausgabefehler
hexdump: FD/sda/?&#65533;&#65533;??|?*.?&#65533;: Eingabe-/Ausgabefehler
hexdump: FD/sda/?&#65533;&#65533;??|?*.?&#65533;: Eingabe-/Ausgabefehler
hexdump: FD/sda/?&#65533;&#65533;??|?*.?&#65533;: Eingabe-/Ausgabefehler
: Eingabe-/Ausgabefehler
: Eingabe-/Ausgabefehler
: Eingabe-/Ausgabefehler
hexdump: FD/sda/&#65533;<&#65533;?04#7.h$>: Eingabe-/Ausgabefehler
hexdump: FD/sda/&#65533;<&#65533;?04#7.h$>: Eingabe-/Ausgabefehler
hexdump: FD/sda/&#65533;<&#65533;?04#7.h$>: Eingabe-/Ausgabefehler
hexdump: FD/sda/1?rL?U.?$|: Eingabe-/Ausgabefehler
hexdump: FD/sda/1?rL?U.?$|: Eingabe-/Ausgabefehler
hexdump: FD/sda/1?rL?U.?$|: Eingabe-/Ausgabefehler
hexdump: FD/sda/&#65533;&#65533;&#65533;2F_.???: Eingabe-/Ausgabefehler
hexdump: FD/sda/&#65533;&#65533;&#65533;2F_.???: Eingabe-/Ausgabefehler
hexdump: FD/sda/&#65533;&#65533;&#65533;2F_.???: Eingabe-/Ausgabefehler
hexdump: FD/sda/&#65533;4d?&#65533;?.&#65533;&#65533;: Eingabe-/Ausgabefehler
hexdump: FD/sda/&#65533;4d?&#65533;?.&#65533;&#65533;: Eingabe-/Ausgabefehler
hexdump: FD/sda/&#65533;4d?&#65533;?.&#65533;&#65533;: Eingabe-/Ausgabefehler
hexdump: FD/sda/??[60?jn&#65533;: Eingabe-/Ausgabefehler
hexdump: FD/sda/??[60?jn&#65533;: Eingabe-/Ausgabefehler
hexdump: FD/sda/??[60?jn&#65533;: Eingabe-/Ausgabefehler
hexdump: FD/sda/?&#65533;(&#65533;?&#65533;&#65533;.&#65533;7c: Eingabe-/Ausgabefehler
hexdump: FD/sda/?&#65533;(&#65533;?&#65533;&#65533;.&#65533;7c: Eingabe-/Ausgabefehler
hexdump: FD/sda/?&#65533;(&#65533;?&#65533;&#65533;.&#65533;7c: Eingabe-/Ausgabefehler
hexdump: FD/sda/9@,|?
                      ?.$4?: Eingabe-/Ausgabefehler
hexdump: FD/sda/9@,|?
                      ?.$4?: Eingabe-/Ausgabefehler
hexdump: FD/sda/9@,|?
                      ?.$4?: Eingabe-/Ausgabefehler
hexdump: FD/sda/a'&#65533;&#65533;?.!9: Eingabe-/Ausgabefehler
hexdump: FD/sda/a'&#65533;&#65533;?.!9: Eingabe-/Ausgabefehler
hexdump: FD/sda/a'&#65533;&#65533;?.!9: Eingabe-/Ausgabefehler
hexdump: FD/sda/?A}?Q{?.0?&#65533;: Eingabe-/Ausgabefehler
hexdump: FD/sda/?A}?Q{?.0?&#65533;: Eingabe-/Ausgabefehler
hexdump: FD/sda/?A}?Q{?.0?&#65533;: Eingabe-/Ausgabefehler
hexdump: FD/sda/a&#65533;&#65533;&#65533;:?.?x?: Eingabe-/Ausgabefehler
hexdump: FD/sda/a&#65533;&#65533;&#65533;:?.?x?: Eingabe-/Ausgabefehler
hexdump: FD/sda/a&#65533;&#65533;&#65533;:?.?x?: Eingabe-/Ausgabefehler
hexdump: FD/sda/?b??8[.?&#65533;: Eingabe-/Ausgabefehler
hexdump: FD/sda/?b??8[.?&#65533;: Eingabe-/Ausgabefehler
hexdump: FD/sda/?b??8[.?&#65533;: Eingabe-/Ausgabefehler
hexdump: FD/sda/?+&#65533;}??.bk: Eingabe-/Ausgabefehler
hexdump: FD/sda/?+&#65533;}??.bk: Eingabe-/Ausgabefehler
hexdump: FD/sda/?+&#65533;}??.bk: Eingabe-/Ausgabefehler
hexdump: FD/sda/?B?q&#65533;?.6??: Eingabe-/Ausgabefehler
hexdump: FD/sda/?B?q&#65533;?.6??: Eingabe-/Ausgabefehler
hexdump: FD/sda/?B?q&#65533;?.6??: Eingabe-/Ausgabefehler
hexdump: FD/sda/'???c?&#65533;: Eingabe-/Ausgabefehler
hexdump: FD/sda/'???c?&#65533;: Eingabe-/Ausgabefehler
hexdump: FD/sda/'???c?&#65533;: Eingabe-/Ausgabefehler
hexdump: FD/sda/'D2{&#65533;&#433;.??|: Eingabe-/Ausgabefehler
hexdump: FD/sda/'D2{&#65533;&#433;.??|: Eingabe-/Ausgabefehler
hexdump: FD/sda/'D2{&#65533;&#433;.??|: Eingabe-/Ausgabefehler
hexdump: FD/sda/D?\&#65533;???.e?: Eingabe-/Ausgabefehler
hexdump: FD/sda/D?\&#65533;???.e?: Eingabe-/Ausgabefehler
hexdump: FD/sda/D?\&#65533;???.e?: Eingabe-/Ausgabefehler
hexdump: FD/sda/??fe'??&#65533;.,"?: Eingabe-/Ausgabefehler
hexdump: FD/sda/??fe'??&#65533;.,"?: Eingabe-/Ausgabefehler
hexdump: FD/sda/??fe'??&#65533;.,"?: Eingabe-/Ausgabefehler
hexdump: FD/sda/*fo&#65533;?p?&#65533;.?'&#65533;: Eingabe-/Ausgabefehler
hexdump: FD/sda/*fo&#65533;?p?&#65533;.?'&#65533;: Eingabe-/Ausgabefehler
hexdump: FD/sda/*fo&#65533;?p?&#65533;.?'&#65533;: Eingabe-/Ausgabefehler
hexdump: FD/sda/?
                 ?&#65533;?&#65533;G.a?(: Eingabe-/Ausgabefehler
hexdump: FD/sda/?
                 ?&#65533;?&#65533;G.a?(: Eingabe-/Ausgabefehler
hexdump: FD/sda/?
                 ?&#65533;?&#65533;G.a?(: Eingabe-/Ausgabefehler
hexdump: FD/sda/G]&#65533;cB.??.???: Eingabe-/Ausgabefehler
hexdump: FD/sda/G]&#65533;cB.??.???: Eingabe-/Ausgabefehler
hexdump: FD/sda/G]&#65533;cB.??.???: Eingabe-/Ausgabefehler
hexdump: FD/sda/\&#291;U&#65533;?&#65533;i.?}
                          : Eingabe-/Ausgabefehler
hexdump: FD/sda/\&#291;U&#65533;?&#65533;i.?}
                          : Eingabe-/Ausgabefehler
hexdump: FD/sda/\&#291;U&#65533;?&#65533;i.?}
                          : Eingabe-/Ausgabefehler
hexdump: FD/sda/?g?u?&#65533;?.?y?: Eingabe-/Ausgabefehler
hexdump: FD/sda/?g?u?&#65533;?.?y?: Eingabe-/Ausgabefehler
hexdump: FD/sda/?g?u?&#65533;?.?y?: Eingabe-/Ausgabefehler
hexdump: FD/sda/&#65533;?I?&#65533;?.&#65533;??: Eingabe-/Ausgabefehler
hexdump: FD/sda/&#65533;?I?&#65533;?.&#65533;??: Eingabe-/Ausgabefehler
hexdump: FD/sda/&#65533;?I?&#65533;?.&#65533;??: Eingabe-/Ausgabefehler
hexdump: FD/sda/|&#65533;i&#65533;&#65533;=.p?&#65533;: Eingabe-/Ausgabefehler
hexdump: FD/sda/|&#65533;i&#65533;&#65533;=.p?&#65533;: Eingabe-/Ausgabefehler
hexdump: FD/sda/|&#65533;i&#65533;&#65533;=.p?&#65533;: Eingabe-/Ausgabefehler
hexdump: FD/sda/&#65533;&#65533;&#65533;&#65533;&#65533;j&#65533;.4?c: Eingabe-/Ausgabefehler
hexdump: FD/sda/&#65533;&#65533;&#65533;&#65533;&#65533;j&#65533;.4?c: Eingabe-/Ausgabefehler
hexdump: FD/sda/&#65533;&#65533;&#65533;&#65533;&#65533;j&#65533;.4?c: Eingabe-/Ausgabefehler
hexdump: FD/sda/&#65533;?k&#65533;&#65533;?&#65533;.%3&#65533;: Eingabe-/Ausgabefehler
hexdump: FD/sda/&#65533;?k&#65533;&#65533;?&#65533;.%3&#65533;: Eingabe-/Ausgabefehler
hexdump: FD/sda/&#65533;?k&#65533;&#65533;?&#65533;.%3&#65533;: Eingabe-/Ausgabefehler
hexdump: FD/sda/&#65533;?k?4.{_?: Eingabe-/Ausgabefehler
hexdump: FD/sda/&#65533;?k?4.{_?: Eingabe-/Ausgabefehler
hexdump: FD/sda/&#65533;?k?4.{_?: Eingabe-/Ausgabefehler
hexdump: FD/sda/l3qf&#65533;&#65533;s&#65533;.???: Eingabe-/Ausgabefehler
hexdump: FD/sda/l3qf&#65533;&#65533;s&#65533;.???: Eingabe-/Ausgabefehler
hexdump: FD/sda/l3qf&#65533;&#65533;s&#65533;.???: Eingabe-/Ausgabefehler
hexdump: FD/sda/~&#65533;?lz?.ye: Eingabe-/Ausgabefehler
hexdump: FD/sda/~&#65533;?lz?.ye: Eingabe-/Ausgabefehler
hexdump: FD/sda/~&#65533;?lz?.ye: Eingabe-/Ausgabefehler
hexdump: FD/sda/&#65533;?&#65533;&#65533;?m?\.>?: Eingabe-/Ausgabefehler
hexdump: FD/sda/&#65533;?&#65533;&#65533;?m?\.>?: Eingabe-/Ausgabefehler
hexdump: FD/sda/&#65533;?&#65533;&#65533;?m?\.>?: Eingabe-/Ausgabefehler
hexdump: FD/sda/m57&#65533;&#65533;???.&#65533;z@: Eingabe-/Ausgabefehler
hexdump: FD/sda/m57&#65533;&#65533;???.&#65533;z@: Eingabe-/Ausgabefehler
hexdump: FD/sda/m57&#65533;&#65533;???.&#65533;z@: Eingabe-/Ausgabefehler
hexdump: FD/sda/!?.&#65533;&#65533;?&#65533;?.n&#65533;&#65533;: Eingabe-/Ausgabefehler
hexdump: FD/sda/!?.&#65533;&#65533;?&#65533;?.n&#65533;&#65533;: Eingabe-/Ausgabefehler
hexdump: FD/sda/!?.&#65533;&#65533;?&#65533;?.n&#65533;&#65533;: Eingabe-/Ausgabefehler
hexdump: FD/sda/n?&#65533;?&#65533;&#65533;??.V&#65533;h: Eingabe-/Ausgabefehler
hexdump: FD/sda/n?&#65533;?&#65533;&#65533;??.V&#65533;h: Eingabe-/Ausgabefehler
hexdump: FD/sda/n?&#65533;?&#65533;&#65533;??.V&#65533;h: Eingabe-/Ausgabefehler
hexdump: FD/sda/oW???]&#65533;^.???: Eingabe-/Ausgabefehler
hexdump: FD/sda/oW???]&#65533;^.???: Eingabe-/Ausgabefehler
hexdump: FD/sda/oW???]&#65533;^.???: Eingabe-/Ausgabefehler
hexdump: FD/sda/r6?m?b.&#65533;$2: Eingabe-/Ausgabefehler
hexdump: FD/sda/r6?m?b.&#65533;$2: Eingabe-/Ausgabefehler
hexdump: FD/sda/r6?m?b.&#65533;$2: Eingabe-/Ausgabefehler
hexdump: FD/sda/T??&#65533;W3&#65533;.&#65533;??: Eingabe-/Ausgabefehler
hexdump: FD/sda/T??&#65533;W3&#65533;.&#65533;??: Eingabe-/Ausgabefehler
hexdump: FD/sda/T??&#65533;W3&#65533;.&#65533;??: Eingabe-/Ausgabefehler
hexdump: FD/sda/~u&#65533;p?&#65533;&#65533;.r?&#65533;: Eingabe-/Ausgabefehler
hexdump: FD/sda/~u&#65533;p?&#65533;&#65533;.r?&#65533;: Eingabe-/Ausgabefehler
hexdump: FD/sda/~u&#65533;p?&#65533;&#65533;.r?&#65533;: Eingabe-/Ausgabefehler
hexdump: FD/sda/?u&#65533;&#65533;???.?Vc: Eingabe-/Ausgabefehler
hexdump: FD/sda/?u&#65533;&#65533;???.?Vc: Eingabe-/Ausgabefehler
hexdump: FD/sda/?u&#65533;&#65533;???.?Vc: Eingabe-/Ausgabefehler
hexdump: FD/sda/>-v&#65533;&#65533;r.?=?: Eingabe-/Ausgabefehler
hexdump: FD/sda/>-v&#65533;&#65533;r.?=?: Eingabe-/Ausgabefehler
hexdump: FD/sda/>-v&#65533;&#65533;r.?=?: Eingabe-/Ausgabefehler
hexdump: FD/sda/?V???&#65533;?&.?s?: Eingabe-/Ausgabefehler
hexdump: FD/sda/?V???&#65533;?&.?s?: Eingabe-/Ausgabefehler
hexdump: FD/sda/?V???&#65533;?&.?s?: Eingabe-/Ausgabefehler
hexdump: FD/sda/wb?w?[&#65533;?.r?d: Eingabe-/Ausgabefehler
hexdump: FD/sda/wb?w?[&#65533;?.r?d: Eingabe-/Ausgabefehler
hexdump: FD/sda/wb?w?[&#65533;?.r?d: Eingabe-/Ausgabefehler
.`&#65533;: Eingabe-/Ausgabefehler
.`&#65533;: Eingabe-/Ausgabefehler
.`&#65533;: Eingabe-/Ausgabefehler
hexdump: FD/sda/&#65533;?&#65533;&#65533;?|x?.?
                          &: Eingabe-/Ausgabefehler
hexdump: FD/sda/&#65533;?&#65533;&#65533;?|x?.?
                          &: Eingabe-/Ausgabefehler
hexdump: FD/sda/&#65533;?&#65533;&#65533;?|x?.?
                          &: Eingabe-/Ausgabefehler
hexdump: FD/sda/&#65533;?Xa??M&#65533;.?~?: Eingabe-/Ausgabefehler
hexdump: FD/sda/&#65533;?Xa??M&#65533;.?~?: Eingabe-/Ausgabefehler
hexdump: FD/sda/&#65533;?Xa??M&#65533;.?~?: Eingabe-/Ausgabefehler
hexdump: FD/sda/??&#65533;y:q&#65533;.&#65533;[&#65533;: Eingabe-/Ausgabefehler
hexdump: FD/sda/??&#65533;y:q&#65533;.&#65533;[&#65533;: Eingabe-/Ausgabefehler
hexdump: FD/sda/??&#65533;y:q&#65533;.&#65533;[&#65533;: Eingabe-/Ausgabefehler
hexdump: FD/sda/&#65533;??&#65533;=&#65533;y.t): Eingabe-/Ausgabefehler
hexdump: FD/sda/&#65533;??&#65533;=&#65533;y.t): Eingabe-/Ausgabefehler
hexdump: FD/sda/&#65533;??&#65533;=&#65533;y.t): Eingabe-/Ausgabefehler
hexdump: FD/sda/?zb&#65533;?&#65533;.&#65533;??: Eingabe-/Ausgabefehler
hexdump: FD/sda/?zb&#65533;?&#65533;.&#65533;??: Eingabe-/Ausgabefehler
hexdump: FD/sda/?zb&#65533;?&#65533;.&#65533;??: Eingabe-/Ausgabefehler
?.?&#65533;?: Eingabe-/Ausgabefehler
?.?&#65533;?: Eingabe-/Ausgabefehler
?.?&#65533;?: Eingabe-/Ausgabefehler

ubuntu@ubuntu:~/Desktop$ 
```Eingabe-/Ausgabefehler = Input/Output Error

   ...Der Bootsektor dieser Diskette wurde neuerstellt.       
. ..Benutzen Sie den DOS-Befehl SYS um diese Diskette bootfähig zu machen!..
Bitte  legen Sie nun eine Systemdiskette ins Laufwerk und ..drücken Sie eine Taste....

= The bootsector of this floppy was newly created.
... Use the DOS-command SYS to make this floppy bootable! ...
Please insert a System-floppy (msdosfloppy) to make this floppy bootable ...press any key...

---

### Post by Nergatus on 2011-07-27
mind if i bump? i really dont care if windows would be lost, all that i want is my partitions back after deleting (avira) the boot sectors

---

### Post by Paddy Landau on 2011-07-27
In case Rubi1200 doesn't reply, it looks at first glance that your disk is OK, but Avira has messed up your boot partition.

Have a look at how to reinstall Grub 2 (that's the boot program that lets you start Windows or Linux). Go to the [Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275") thread, and scroll all the way down to point 13, "Reinstalling GRUB 2 from LiveCD ".

---

