---
title: "Harddrive spins down then up"
date: 2009-08-05
forum: General Help
---

### Post by reesje on 2009-08-05
Hi guys,

I am having a problem with my laptop running Ubuntu 9.04. The harddrive spins down, then after 2-120 seconds it spins up again. It does so very often, and also if I don't use the PC at all. It does it with my old 100GB harddrive and it does so with my new 320GB harddrive.

In both Windows 7 and Windows XP it does not do this, and as far as I remember it didn't do it in any of the previous Ubuntu versions I have had installed.

What can I do about it? All this spinning down and up is bound to wear the disk out quite soon. I can se the load_cycle_count in SMART goes up fast. The counter is already at 1500 after 5 days of occasional use.

Thanks in advance.
BR,
René

---

### Post by mikewhatever on 2009-08-05
Can you post some info about your drives:

sudo fdisk -l
sudo hdparm -I /dev/sda | grep 'Advanced power management level'

---

### Post by reesje on 2009-08-06
sudo fdisk -l:
```
Disk /dev/sda: 320.0 Gb, 320072933376 byte
255 heads, 63 sectors/track, 38913 cylinders
Units = cylindre of 16065 * 512 = 8225280 bytes
Disk identifier: 0x21ab21ab

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/sda1   *        6376        9434    24571417+  83  Linux
/dev/sda2            9435        9564     1044225   82  Linux swap / Solaris
/dev/sda3            9565       38913   235745842+   7  HPFS/NTFS

```
sudo hdparm -I /dev/sda | grep 'Advanced power management level':
```
	Advanced power management level: 128

```
I have three other partitions that are hidden from Ubuntu, Bootitng, Windows 7 and Windows XP, all prior to the Ubuntu partition.

I use Ext4 if that matters in any way.

BR,
René

---

### Post by megamania on 2009-08-06
I had the same problem and I read somewhere that it is a bug in the version of hdparm shipped with Jaunty.

Apparently it is fixed in the new version, which is not in the repositories. However, you can download it from the web and install it.

---

### Post by reesje on 2009-08-06
This is strange. It seems to have fixed itself overnight. The harddrive does not stop anymore, like it has done ever since I installed 9.04 both on this drive and on my old drive. As you can see on the output of a small script I've made:
```
rej@HV213-Laptop:~$ ./hdcheck 
tor aug  6 10:47:04 CEST 2009
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       1486
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       224
 12 Power_Cycle_Count       0x0032   100   037   020    Old_age   Always       -       78
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       71
-----------------------------------
rej@HV213-Laptop:~$ ./hdcheck 
tor aug  6 10:48:40 CEST 2009
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       1489
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       224
 12 Power_Cycle_Count       0x0032   100   037   020    Old_age   Always       -       78
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       71
-----------------------------------
rej@HV213-Laptop:~$ ./hdcheck 
tor aug  6 10:54:46 CEST 2009
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       1489
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       224
 12 Power_Cycle_Count       0x0032   100   037   020    Old_age   Always       -       78
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       71
-----------------------------------
rej@HV213-Laptop:~$ ./hdcheck 
tor aug  6 11:26:33 CEST 2009
[sudo] password for rej: 
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       1489
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       224
 12 Power_Cycle_Count       0x0032   100   037   020    Old_age   Always       -       78
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       72
-----------------------------------

```
Before today, the start_stop count incremented rapidly, now it seems not to do so. Very strange.

I will post again if there is any change in the situation.

Thanks for getting back to me.

BR,
René

---

