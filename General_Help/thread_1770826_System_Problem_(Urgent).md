---
title: "System Problem (Urgent)"
date: 2011-05-29
forum: General Help
---

### Post by Riku Reed on 2011-05-29
So I need some help on to fixing my system. Gparted doesn't work. It crashes on startup. When I boot up my system "Fedora 15 LXDE" this is what shows up on boot.

> systemd-fsck[678]: dev/mapper/Volgroup-1v_home: One or more block group descripter checksums are invalid. Fixed
systemd-fsck[678]: dev/mapper/Volgroup-1v_home: Group descripter 1152 checksums is invalid.
systemd-fsck[678]: dev/mapper/Volgroup-1v_home: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
systemd-fsck[678]: (i. e., without -a or -p options)
Welcome to emergency mode. Use "systemctl default" or ^D to activate default mode
Give root password for maintenance
(or type Control-D to continue):

After pressing "D" it displays that same text again. But.. When I enter my password to go to maintenance I type "startx" and it shows my desktop. I think once it showed the Fedora login screen to enter my password but nontheless my wireless doesn't work. That same when it just displays the desktop. I checked the user of course and I' logged in as root, not my username.
So now I'm either stuck with trying to save my system or just whatever. Mainly I'd like to save my system but of course right now I don't know.

So I had a spare USB drive with Kubuntu 10.10 on it. This is how I'm on Ubuntu Forums of course. I saw this command to see if it'd work on my system. Saying it was a way of course to fix. I tried and it showed me this:
> ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck from util-linux-ng 2.17.2
dosfsck 3.0.9, 31 Jan 2010, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  3:53/4d, 4:59/53, 5:53/44, 6:4c/4f, 7:49/53, 8:4e/35, 9:55/2e, 10:58/30
  , 90:fa/33, 91:fc/c9, 92:31/8e, 93:c9/d1, 94:8e/bc, 95:d1/f4, 96:bc/7b
  , 97:76/8e, 98:7b/c1, 99:52/8e, 100:06/d9, 101:57/bd, 102:8e/00, 103:c1/7c
  , 104:b1/88, 105:26/4e, 106:bf/02, 107:78/8a, 108:7b/56, 109:f3/40
  , 110:a5/b4, 111:8e/41, 112:d9/bb, 113:bb/aa, 114:78/55, 115:00/cd
  , 116:0f/13, 117:b4/72, 118:37/10, 119:0f/81, 120:a0/fb, 121:56/55
  , 122:20/aa, 123:d2/75, 124:78/0a, 125:1b/f6, 126:31/c1, 127:c0/01
  , 128:b1/74, 129:06/05, 130:89/fe, 131:3f/46, 132:89/02, 133:47/eb
  , 134:02/2d, 135:f3/8a, 136:64/56, 137:a5/40, 138:8a/b4, 139:0e/08
  , 140:18/cd, 141:7c/13, 142:88/73, 143:4d/05, 144:bc/b9, 145:50/ff
  , 146:50/ff, 147:50/8a, 148:50/f1, 149:cd/66, 150:13/0f, 151:eb/b6
  , 152:4b/c6, 153:f6/40, 154:45/66, 155:b4/0f, 156:7f/b6, 157:75/d1
  , 158:25/80, 159:38/e2, 160:4d/3f, 161:b8/f7, 162:74/e2, 163:20/86
  , 164:66/cd, 165:3d/c0, 166:21/ed, 167:47/06, 168:50/41, 169:54/66
  , 170:75/0f, 171:10/b7, 172:80/c9, 173:7d/66, 174:b8/f7, 175:ed/e1
  , 176:75/66, 177:0a/89, 178:66/46, 179:ff/f8, 180:75/83, 181:ec/7e
  , 182:66/16, 183:ff/00, 185:e8/38, 186:eb/83, 187:0f/7e, 188:51/2a
  , 189:51/00, 190:66/77, 191:ff/32, 192:75/66, 193:bc/8b, 194:eb/46
  , 195:07/1c, 196:51/66, 197:51/83, 198:66/c0, 199:ff/0c, 200:36/bb
  , 201:1c/00, 202:7c/80, 203:b4/b9, 204:08/01, 205:cd/00, 206:13/e8
  , 207:72/2b, 208:13/00, 209:20/e9, 210:e4/2c, 211:75/03, 212:0f/a0
  , 213:c1/fa, 214:ea/7d, 215:08/b4, 216:42/7d, 217:89/8b, 218:16/f0
  , 219:1a/ac, 220:7c/84, 221:83/c0, 222:e1/74, 223:3f/17, 224:89/3c
  , 225:0e/ff, 226:18/74, 227:7c/09, 228:fb/b4, 229:bb/0e, 230:aa/bb
  , 231:55/07, 232:b4/00, 233:41/cd, 234:8a/10, 235:16/eb, 236:74/ee
  , 237:7b/a0, 238:cd/fb, 239:13/7d, 240:72/eb, 241:10/e5, 242:81/a0
  , 243:fb/f9, 244:55/7d, 245:aa/eb, 246:75/e0, 247:0a/98, 248:f6/cd
  , 249:c1/16, 250:01/cd, 251:74/19, 252:05/66, 253:c6/60, 254:06/80
  , 255:32/7e, 256:7d/02, 258:66/0f, 259:b8/84, 260:b8/20, 261:fc/00
  , 262:15/66, 263:00/6a, 264:66/00, 265:ba/66, 266:00/50, 267:00/06
  , 268:00/53, 269:00/66, 270:bb/68, 271:00/10, 272:7e/00, 273:e8/01
  , 274:10/00, 275:00/b4, 276:66/42, 277:81/8a, 278:3e/56, 279:24/40
  , 280:7e/8b, 281:34/f4, 282:be/cd, 283:f5/13, 284:72/66, 285:75/58
  , 286:76/66, 287:ea/58, 288:38/66, 289:7e/58, 290:00/66, 291:00/58
  , 292:66/eb, 293:03/33, 294:06/66, 295:64/3b, 296:7b/46, 297:66/f8
  , 298:13/72, 299:16/03, 300:68/f9, 301:7b/eb, 302:b9/2a, 303:10/66
  , 304:00/33, 305:eb/d2, 306:2b/66, 307:66/0f, 308:52/b7, 309:66/4e
  , 310:50/18, 311:06/66, 312:53/f7, 313:6a/f1, 314:01/fe, 315:6a/c2
  , 316:10/8a, 317:89/ca, 318:e6/66, 319:66/8b, 320:60/d0, 321:b4/66
  , 322:42/c1, 323:e8/ea, 324:7f/10, 325:00/f7, 326:66/76, 327:61/1a
  , 328:8d/86, 329:64/d6, 330:10/8a, 331:72/56, 332:01/40, 333:c3/8a
  , 334:66/e8, 335:60/c0, 336:31/e4, 337:c0/06, 338:e8/0a, 339:70/cc
  , 340:00/b8, 341:66/01, 342:61/02, 343:e2/cd, 344:da/13, 345:c6/66
  , 346:06/61, 347:32/0f, 348:7d/82, 349:2b/75, 350:66/ff, 351:60/81
  , 352:66/c3, 353:0f/00, 354:b7/02, 355:36/66, 356:18/40, 357:7c/49
  , 358:66/75, 359:0f/94, 360:b7/c3, 361:3e/42, 362:1a/4f, 363:7c/4f
  , 364:66/54, 365:f7/4d, 366:f6/47, 367:31/52, 368:c9/20, 369:87/20
  , 370:ca/20, 371:66/20, 372:f7/00, 373:f7/00, 374:66/00, 375:3d/00
  , 376:ff/00, 377:03/00, 380:77/00, 381:17/00, 382:c0/00, 383:e4/00
  , 384:06/00, 385:41/00, 386:08/00, 387:e1/00, 388:88/00, 389:c5/00
  , 390:88/00, 391:d6/00, 392:b8/00, 393:01/00, 394:02/00, 395:e8/00
  , 396:37/00, 398:66/00, 399:61/00, 400:72/00, 401:01/00, 402:c3/00
  , 403:e2/00, 404:c9/00, 405:31/00, 406:f6/00, 407:8e/00, 408:d6/00
  , 409:bc/00, 410:6c/00, 411:7b/00, 412:8e/00, 413:de/00, 414:66/00
  , 415:8f/00, 416:06/00, 417:78/00, 419:be/00, 420:cc/00, 421:7d/00
  , 422:e8/00, 423:09/00, 425:31/00, 426:c0/00, 427:cd/00, 428:16/0d
  , 429:cd/0a, 430:19/52, 431:f4/65, 432:eb/6d, 433:fd/6f, 434:66/76
  , 435:60/65, 436:ac/20, 437:20/64, 438:c0/69, 439:74/73, 440:09/6b
  , 441:b4/73, 442:0e/20, 443:bb/6f, 444:07/72, 445:00/20, 446:cd/6f
  , 447:10/74, 448:eb/68, 449:f2/65, 450:66/72, 451:61/20, 452:c3/6d
  , 453:8a/65, 454:16/64, 455:74/69, 456:7b/61, 457:cd/2e, 458:13/ff
  , 459:c3/0d, 460:42/0a, 461:6f/44, 462:6f/69, 463:74/73, 464:20/6b
  , 465:65/20, 466:72/65, 468:6f/72, 469:72/6f, 470:0d/72, 471:0a/ff
  , 472:00/0d, 473:00/0a, 474:00/50, 475:00/72, 476:00/65, 477:00/73
  , 478:00/73, 479:00/20, 480:00/61, 481:00/6e, 482:00/79, 483:00/20
  , 484:00/6b, 485:00/65, 486:00/79, 487:00/20, 488:00/74, 489:00/6f
  , 490:00/20, 491:00/72, 492:00/65, 493:00/73, 494:00/74, 495:00/61
  , 496:00/72, 497:00/74, 498:00/0d, 499:00/0a, 505:00/ac, 506:00/cb
  , 507:00/d8
1) Copy original to backup
2) Copy backup to original
3) No action
?

So basically now I'm stuck. I'd like to save my system or format if necessary. But when I tried to pull up Gparted it wouldn't display for some reason "sudo Gparted" it'd pop up than disappear.
Here's what it displayed when it just disappeared:
> ubuntu@ubuntu:~$ sudo gparted
======================
libparted : 2.3
======================
Backtrace has 16 calls on stack:
  16: /lib/libparted.so.0(ped_assert+0x2a) [0xf0d87a]
  15: /lib/libparted.so.0(+0x41257) [0xf45257]
  14: /lib/libparted.so.0(+0x42077) [0xf46077]
  13: /lib/libparted.so.0(+0x4336c) [0xf4736c]
  12: /lib/libparted.so.0(+0xe161) [0xf12161]
  11: /lib/libparted.so.0(ped_disk_add_partition+0x262) [0xf159f2]
  10: /lib/libparted.so.0(+0x44dc5) [0xf48dc5]
  9: /lib/libparted.so.0(+0x44fcf) [0xf48fcf]
  8: /lib/libparted.so.0(ped_disk_new+0x75) [0xf167d5]
  7: /usr/sbin/gpartedbin() [0x8090126]
  6: /usr/sbin/gpartedbin() [0x80a06b5]
  5: /usr/sbin/gpartedbin() [0x80c1f42]
  4: /usr/lib/libglibmm-2.4.so.1(+0x31e42) [0x1b3e42]
  3: /lib/libglib-2.0.so.0(+0x6848f) [0x9ad48f]
  2: /lib/libpthread.so.0(+0x5cc9) [0xb2acc9]
  1: /lib/libc.so.6(clone+0x5e) [0x10926ae]
Assertion (head_size <= 63) at ../../../libparted/labels/dos.c:662 in function probe_partition_for_geom() failed.
ubuntu@ubuntu:~$ 

---

### Post by dragonfly41 on 2011-05-29
I have no idea how to decipher the outputs you've just posted ..

I just want to point out that if you want to use a partition editor you can use **[COLOR=Blue]parted[/COLOR]** which is command line version of gparted .. without the gui.

run this command to get details .. [COLOR=Blue]**man parted**[/COLOR]

---

### Post by lemonchicken on 2011-05-29
> 1) Copy original to backup
2) Copy backup to original
3) No actionit seems you are being asked how to fix the problem, in which case I would select '2) Copy backup to original'.

---

### Post by oldfred on 2011-05-29
You are using RAID or LVM. I know enough about them to know you do not use the standard procedures to repair them in many cases.

This may tell those who know more about your system:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
Is able to search LVM partitions if the LVM2 package is install
# ("apt-get install lvm2" in debian based distros)
# Is able to search Linux Software Raid partitions (MD Raids) if
# the "mdadm" package is installed.
[http://grub.enbug.org/LVMandRAID](http://grub.enbug.org/LVMandRAID)

---

### Post by Riku Reed on 2011-05-29
> **lemonchicken said:**
> it seems you are being asked how to fix the problem, in which case I would select '2) Copy backup to original'.

When I selected '2 it does nothing
See?

> 1) Copy original to backup
2) Copy backup to original
3) No action
? 2
Leaving file system unchanged.
/dev/sda1: 259 files, 178089/970899 clusters
ubuntu@ubuntu:~$ 

Unless that question mark has to do with something?

---

### Post by Riku Reed on 2011-05-29
I gave up with trying to save my Fedora. Is their a way to format my hard drive? Gparted still even after re-installing through the live CD won't stay up it quickly disappears after I start it up. Giving me the error from my earlier post.
Basically all I want to for now is format my system as FAT32. Since I'm in the live session I tried to install Kubuntu but it won't move pass "Prepare" it's stuck on "Disk Setup"? Don't know what to do. I tried "parted" didn't do much by the way.

---

### Post by linuxinstalledfromhdd on 2011-05-29
Who originally setup up the raid installation for you?

---

### Post by Riku Reed on 2011-05-29
> **linuxinstalledfromhdd said:**
> Who originally setup up the raid installation for you?

What do you mean?

---

### Post by Thewhistlingwind on 2011-05-29
Run fsck.

Ask for help at the prompt, I won't repeat the documentation.

---

### Post by oldfred on 2011-05-29
FAT is not a Linux file system. Only use FAT for flash drives or where you abolutely have to have compatiblity like with an Xbox. Use NTFS if sharing a partition with windows. Otherwise you have to use Linux partitions for any Linux install.

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by Riku Reed on 2011-06-02
Just went in and formatted my USB flash drive from a different computer. Got that fixed with my 4 Gigabyte flash drive.
Mainly everything else seems covered. =P

---

