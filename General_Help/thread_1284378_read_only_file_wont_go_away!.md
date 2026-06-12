---
title: "read only file wont go away!"
date: 2009-10-06
forum: General Help
---

### Post by mickmouse13 on 2009-10-06
using ubuntu 9.10 
just when i was getting the hand of things XD i mounted a version of my oblivion disk onto my desktop. i now want to delete it due to hardrive sspace... so i tried delete and unmount. this did not work. i tried (its a foulder) 
sudo rm -rf directoryand neither works its a read only file.  so i tried 

```
mick@mick-desktop:~$ sudo rm -rf /home/mick/Desktop/obl
```and i only get this
```
mick@mick-desktop:~$ sudo rm -rf /home/mick/Desktop/obl
rm: cannot remove `/home/mick/Desktop/obl/autorun.inf': Read-only file system
rm: cannot remove `/home/mick/Desktop/obl/data1.cab': Read-only file system
rm: cannot remove `/home/mick/Desktop/obl/data1.hdr': Read-only file system
rm: cannot remove `/home/mick/Desktop/obl/data2.cab': Read-only file system
rm: cannot remove `/home/mick/Desktop/obl/data3.cab': Read-only file system
rm: cannot remove `/home/mick/Desktop/obl/data4.cab': Read-only file system
rm: cannot remove `/home/mick/Desktop/obl/data5.cab': Read-only file system
rm: cannot remove `/home/mick/Desktop/obl/data6.cab': Read-only file system
rm: cannot remove `/home/mick/Desktop/obl/data7.cab': Read-only file system
rm: cannot remove `/home/mick/Desktop/obl/data8.cab': Read-only file system
rm: cannot remove `/home/mick/Desktop/obl/DXREDIST/Aug2005_d3dx9_27_x64.cab': Read-only file system
rm: cannot remove `/home/mick/Desktop/obl/DXREDIST/Aug2005_d3dx9_27_x86.cab': Read-only file system
rm: cannot remove `/home/mick/Desktop/obl/DXREDIST/Aug2005_MDX_x86.cab': Read-only file system
rm: cannot remove `/home/mick/Desktop/obl/DXREDIST/BDA.cab': Read-only file system
rm: cannot remove `/home/mick/Desktop/obl/DXREDIST/BDANT.cab': Read-only file system
rm: cannot remove `/home/mick/Desktop/obl/DXREDIST/BDAXP.cab': Read-only file system
rm: cannot remove `/home/mick/Desktop/obl/DXREDIST/DirectX.cab': Read-only file system
rm: cannot remove `/home/mick/Desktop/obl/DXREDIST/DSETUP.dll': Read-only file system
rm: cannot remove `/home/mick/Desktop/obl/DXREDIST/dsetup32.dll': Read-only file system
rm: cannot remove `/home/mick/Desktop/obl/DXREDIST/dxdllreg_x86.cab': Read-only file system
rm: cannot remove `/home/mick/Desktop/obl/DXREDIST/dxnt.cab': Read-only file system
rm: cannot remove `/home/mick/Desktop/obl/DXREDIST/DXSETUP.exe': Read-only file system
rm: cannot remove `/home/mick/Desktop/obl/DXREDIST/dxupdate.cab': Read-only file system
rm: cannot remove `/home/mick/Desktop/obl/engine32.cab': Read-only file system
rm: cannot remove `/home/mick/Desktop/obl/layout.bin': Read-only file system
rm: cannot remove `/home/mick/Desktop/obl/Oblivion.ico': Read-only file system
rm: cannot remove `/home/mick/Desktop/obl/OblivionLauncher.exe': Read-only file system
rm: cannot remove `/home/mick/Desktop/obl/Readme.txt': Read-only file system
rm: cannot remove `/home/mick/Desktop/obl/Setup.bmp': Read-only file system
rm: cannot remove `/home/mick/Desktop/obl/setup.exe': Read-only file system
rm: cannot remove `/home/mick/Desktop/obl/setup.ibt': Read-only file system
rm: cannot remove `/home/mick/Desktop/obl/setup.ini': Read-only file system
rm: cannot remove `/home/mick/Desktop/obl/setup.inx': Read-only file system
rm: cannot remove `/home/mick/Desktop/obl/setup.isn': Read-only file system

```i also tried nautilus and got smiler results. any ideas?

---

### Post by j.bell730 on 2009-10-06
Give this a try:
```
sudo shred -ufv /home/mick/Desktop/obl/*
```
If it's unsuccessful, post output.

---

### Post by mickmouse13 on 2009-10-06
trying to change permission only ends the same way, it will just say "you can change this.. its read only"  (Thats on the desktop AND in nautelis)

---

### Post by mickmouse13 on 2009-10-06
mick@mick-desktop:~$ sudo shred -ufv /home/mick/Desktop/obl
shred: /home/mick/Desktop/obl: failed to open for writing: Is a directory


humm

---

### Post by mickmouse13 on 2009-10-06
let me clerify the thing i want gone IS a folder

---

### Post by kanikilu on 2009-10-06
You say you mounted it first, can you unmount it and then delete the mountpoint?
```
sudo umount /home/mick/Desktop/obl
```
If that doesn't work, post the output of ```
mount
```

---

### Post by mickmouse13 on 2009-10-06
```
mick@mick-desktop:~$ sudo shred -ufv /home/mick/Desktop/obl/*
shred: /home/mick/Desktop/obl/autorun.inf: failed to open for writing: Read-only file system
shred: /home/mick/Desktop/obl/data1.cab: failed to open for writing: Read-only file system
shred: /home/mick/Desktop/obl/data1.hdr: failed to open for writing: Read-only file system
shred: /home/mick/Desktop/obl/data2.cab: failed to open for writing: Read-only file system
shred: /home/mick/Desktop/obl/data3.cab: failed to open for writing: Read-only file system
shred: /home/mick/Desktop/obl/data4.cab: failed to open for writing: Read-only file system
shred: /home/mick/Desktop/obl/data5.cab: failed to open for writing: Read-only file system
shred: /home/mick/Desktop/obl/data6.cab: failed to open for writing: Read-only file system
shred: /home/mick/Desktop/obl/data7.cab: failed to open for writing: Read-only file system
shred: /home/mick/Desktop/obl/data8.cab: failed to open for writing: Read-only file system
shred: /home/mick/Desktop/obl/DXREDIST: failed to open for writing: Is a directory
shred: /home/mick/Desktop/obl/engine32.cab: failed to open for writing: Read-only file system
shred: /home/mick/Desktop/obl/layout.bin: failed to open for writing: Read-only file system
shred: /home/mick/Desktop/obl/Oblivion.ico: failed to open for writing: Read-only file system
shred: /home/mick/Desktop/obl/OblivionLauncher.exe: failed to open for writing: Read-only file system
shred: /home/mick/Desktop/obl/Readme.txt: failed to open for writing: Read-only file system
shred: /home/mick/Desktop/obl/Setup.bmp: failed to open for writing: Read-only file system
shred: /home/mick/Desktop/obl/setup.exe: failed to open for writing: Read-only file system
shred: /home/mick/Desktop/obl/setup.ibt: failed to open for writing: Read-only file system
shred: /home/mick/Desktop/obl/setup.ini: failed to open for writing: Read-only file system
shred: /home/mick/Desktop/obl/setup.inx: failed to open for writing: Read-only file system
shred: /home/mick/Desktop/obl/setup.isn: failed to open for writing: Read-only file system
```i missed the astarisk at the end... but the outcome is still almost the same.

---

### Post by mickmouse13 on 2009-10-06
sudo umount worked
thanks alot.

---

