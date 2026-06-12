---
title: "Problem viewing/repairing RAID0"
date: 2011-09-14
forum: General Help
---

### Post by thefubz on 2011-09-14
Hello,
I am new to ubuntu and need help fixing my windows RAID0 so I can see it.
I found this nifty command dmraid but I am having trouble getting it to work and understanding it

```

love@TUX:~$ sudo dmraid -s
ERROR: isw: wrong number of devices in RAID set "isw_dfcagcibbi_RAIDrive" [1/2] on /dev/sdc
*** Group superset isw_dfcagcibbi
--> Subset
name   : isw_dfcagcibbi_RAIDrive
size   : 488391936
stride : 256
type   : stripe
status : broken
subsets: 0
devs   : 1
spares : 0

```Then I tried dmraid -R (repair)
```

love@TUX:~$ sudo dmraid -dR isw_dfcagcibbi_RAIDrive
DEBUG: isw metadata found at 250059348992 from probe at 250059348992

DEBUG: checking pdc metadata at 250059317760
DEBUG: checking pdc metadata at 250059219456
DEBUG: checking pdc metadata at 250059218944
DEBUG: checking pdc metadata at 250059341824
DEBUG: checking pdc metadata at 250059145728
DEBUG: checking pdc metadata at 250059047424
DEBUG: checking pdc metadata at 250059004416
DEBUG: checking pdc metadata at 250058973696
DEBUG: checking pdc metadata at 250058851328
DEBUG: checking pdc metadata at 250058842624
DEBUG: checking pdc metadata at 250058883584
DEBUG: checking pdc metadata at 250058863104
DEBUG: checking pdc metadata at 137438913024
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at 250058267136
DEBUG: checking pdc metadata at 250059317760
DEBUG: checking pdc metadata at 250059219456
DEBUG: checking pdc metadata at 250059218944
DEBUG: checking pdc metadata at 250059341824
DEBUG: checking pdc metadata at 250059145728
DEBUG: checking pdc metadata at 250059047424
DEBUG: checking pdc metadata at 250059004416
DEBUG: checking pdc metadata at 250058973696
DEBUG: checking pdc metadata at 250058851328
DEBUG: checking pdc metadata at 250058842624
DEBUG: checking pdc metadata at 250058883584
DEBUG: checking pdc metadata at 250058863104
DEBUG: checking pdc metadata at 137438913024
DEBUG: not isw at 203928108032
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at 203927026176
DEBUG: checking pdc metadata at 203928076800
DEBUG: checking pdc metadata at 203927978496
DEBUG: checking pdc metadata at 203927977984
DEBUG: checking pdc metadata at 203928100864
DEBUG: checking pdc metadata at 203927904768
DEBUG: checking pdc metadata at 203927806464
DEBUG: checking pdc metadata at 203927763456
DEBUG: checking pdc metadata at 203927732736
DEBUG: checking pdc metadata at 203927610368
DEBUG: checking pdc metadata at 203927601664
DEBUG: checking pdc metadata at 203927642624
DEBUG: checking pdc metadata at 203927622144
DEBUG: checking pdc metadata at 137438913024
DEBUG: _find_set: searching isw_dfcagcibbi
DEBUG: _find_set: not found isw_dfcagcibbi
DEBUG: _find_set: searching isw_dfcagcibbi_RAIDrive
DEBUG: _find_set: searching isw_dfcagcibbi_RAIDrive
DEBUG: _find_set: not found isw_dfcagcibbi_RAIDrive
DEBUG: _find_set: not found isw_dfcagcibbi_RAIDrive
ERROR: isw: wrong number of devices in RAID set "isw_dfcagcibbi_RAIDrive" [1/2] on /dev/sdc
DEBUG: set status of set "isw_dfcagcibbi_RAIDrive" to 2
DEBUG: _find_set: searching isw_dfcagcibbi_RAIDrive
DEBUG: _find_set: searching isw_dfcagcibbi_RAIDrive
DEBUG: _find_set: found isw_dfcagcibbi_RAIDrive
DEBUG: _find_set: found isw_dfcagcibbi_RAIDrive
Rebuild: raid0 cannot be rebuild

DEBUG: freeing devices of RAID set "isw_dfcagcibbi_RAIDrive"
DEBUG: freeing device "isw_dfcagcibbi_RAIDrive", path "/dev/sdc"
DEBUG: freeing devices of RAID set "isw_dfcagcibbi"
DEBUG: freeing device "isw_dfcagcibbi", path "/dev/sdc"

```What else do I need to do?

Thanks!

---

### Post by mike4ubuntu on 2011-09-22
I'd like to know as well.  I had problems trying to rebuild a RAID 1 drive.  I tried to use the spare /dev/sdb drive to re-mirror the /dev/sda drive

```
mike@lic3:/$ sudo dmraid -s
ERROR: pdc: wrong # of devices in RAID set "pdc_dfifghbjhf" [1/2] on /dev/sda
ERROR: pdc: wrong # of devices in RAID set "pdc_dfifghbjhf" [1/2] on /dev/sda
*** Active Set
name   : pdc_bgajjfhijh
size   : 3906249984
stride : 128
type   : mirror
status : ok
subsets: 0
devs   : 2
spares : 0
*** *Inconsistent* Set
name   : pdc_dfifghbjhf
size   : 976562432
stride : 128
type   : mirror
status : inconsistent
subsets: 0
devs   : 1
spares : 0
mike@lic3:/$
```

```
mike@lic3:/$ sudo dmraid -r
/dev/sdd: pdc, "pdc_bgajjfhijh", mirror, ok, 3906249984 sectors, data@ 0
/dev/sdc: pdc, "pdc_bgajjfhijh", mirror, ok, 3906249984 sectors, data@ 0
/dev/sda: pdc, "pdc_dfifghbjhf", mirror, ok, 976562432 sectors, data@ 0
mike@lic3:/$ ll /dev/sd*
0 brw-rw---- 1 root disk 8,  0 2011-09-16 19:52 /dev/sda
0 brw-rw---- 1 root disk 8,  1 2011-09-16 19:52 /dev/sda1
0 brw-rw---- 1 root disk 8, 16 2011-09-16 19:52 /dev/sdb
0 brw-rw---- 1 root disk 8, 17 2011-09-16 19:52 /dev/sdb1
0 brw-rw---- 1 root disk 8, 32 2011-09-16 19:52 /dev/sdc
0 brw-rw---- 1 root disk 8, 48 2011-09-16 19:52 /dev/sdd
0 brw-rw---- 1 root disk 8, 64 2011-09-21 21:26 /dev/sde
0 brw-rw---- 1 root disk 8, 65 2011-09-22 07:56 /dev/sde1

```

```
mike@lic3:/$ sudo dmraid -dR pdc_dfifghbjhf /dev/sdb
DEBUG: not isw at 2000398932992
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at 2000397851136
DEBUG: not isw at 2000398932992
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at 2000397851136
DEBUG: not isw at 500107860992
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at 500106779136
DEBUG: not isw at 500107860992
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at 500106779136
DEBUG: _find_set: searching pdc_bgajjfhijh
DEBUG: _find_set: not found pdc_bgajjfhijh
DEBUG: _find_set: searching pdc_bgajjfhijh
DEBUG: _find_set: not found pdc_bgajjfhijh
DEBUG: _find_set: searching pdc_bgajjfhijh
DEBUG: _find_set: found pdc_bgajjfhijh
DEBUG: _find_set: searching pdc_bgajjfhijh
DEBUG: _find_set: found pdc_bgajjfhijh
DEBUG: _find_set: searching pdc_dfifghbjhf
DEBUG: _find_set: searching pdc_dfifghbjhf
DEBUG: _find_set: not found pdc_dfifghbjhf
DEBUG: _find_set: not found pdc_dfifghbjhf
DEBUG: _find_set: searching pdc_dfifghbjhf
DEBUG: _find_set: not found pdc_dfifghbjhf
DEBUG: checking pdc device "/dev/sdc"
DEBUG: checking pdc device "/dev/sdd"
DEBUG: set status of set "pdc_bgajjfhijh" to 16
DEBUG: checking pdc device "/dev/sdc"
DEBUG: checking pdc device "/dev/sdd"
DEBUG: set status of set "pdc_bgajjfhijh" to 16
DEBUG: checking pdc device "/dev/sda"
ERROR: pdc: wrong # of devices in RAID set "pdc_dfifghbjhf" [1/2] on /dev/sda
DEBUG: set status of set "pdc_dfifghbjhf" to 4
DEBUG: checking pdc device "/dev/sda"
ERROR: pdc: wrong # of devices in RAID set "pdc_dfifghbjhf" [1/2] on /dev/sda
DEBUG: set status of set "pdc_dfifghbjhf" to 4
DEBUG: _find_set: searching pdc_dfifghbjhf
DEBUG: _find_set: found pdc_dfifghbjhf
Segmentation fault
mike@lic3:/
```

---

