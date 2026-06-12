---
title: "Wubi install won't boot"
date: 2011-12-29
forum: General Help
---

### Post by wweeks on 2011-12-29
Hey everyone, I seem to be having a problem booting my Wubi install and wonder if anyone could provide me any guidance. 

**Computer:**
Acer Aspire
AMD Phenom II X4 N970
8GB RAM
500GB HD

**Partition table:**
[unlabled] 15GB Recovery Partition
SYSTEM RESERVED 100MB System, Active,Primary Partition
Acer (C: ) 350.01 GB Boot, Page File, Crash Dump, Primary Partition
Partition (E: ) 100.65 GB Logical Drive

I have Windows 7, Ubuntu (wubi) and Jolicloud (wubi style install) sitting on C: and those all work fine. Windows 8 is sitting on the logical drive, E:, and boots fine. However, I have a wubi install on E: that will not boot at all. Is this because it's a logical drive? Any insights you could provide would be great!

---

### Post by wweeks on 2011-12-29
In case this would help;
> Windows Boot Manager
--------------------
identifier              {9dea862c-5cdd-4e70-acc1-f32b344d4795}
device                  partition=\Device\HarddiskVolume2
description             Windows Boot Manager
locale                  en-US
inherit                 {7ea2e1ac-2e61-4728-aaa3-896d9d0a9f0e}
default                 {6524581b-8d90-11e0-acee-de4ebabeeca5}
resumeobject            {3dcd9284-2ad6-11e1-8b54-806e6f6e6963}
displayorder            {6524581b-8d90-11e0-acee-de4ebabeeca5}
                        {f158c070-2c24-11e1-a6c6-fd14d4a9d561}
                        {65245806-8d90-11e0-acee-de4ebabeeca5}
                        {6524580f-8d90-11e0-acee-de4ebabeeca5}
                        {f158c06f-2c24-11e1-a6c6-fd14d4a9d561}
toolsdisplayorder       {b2721d73-1db4-4c62-bf78-c548a880142d}
timeout                 30
displaybootmenu         Yes
custom:26000025         No

Windows Boot Loader
-------------------
identifier              {6524581b-8d90-11e0-acee-de4ebabeeca5}
device                  partition=C:
path                    \Windows\system32\winload.exe
description             Windows 7
locale                  en-US
osdevice                partition=C:
systemroot              \Windows
resumeobject            {3dcd9284-2ad6-11e1-8b54-806e6f6e6963}

Windows Boot Loader
-------------------
identifier              {f158c070-2c24-11e1-a6c6-fd14d4a9d561}
device                  partition=E:
path                    \Windows\system32\winload.exe
description             Windows 8
locale                  en-US
osdevice                partition=E:
systemroot              \Windows
resumeobject            {75501d93-3074-11e1-adbe-806e6f6e6963}

Real-mode Boot Sector
---------------------
identifier              {65245806-8d90-11e0-acee-de4ebabeeca5}
device                  partition=C:
path                    \ubuntu\winboot\wubildr.mbr
description             Ubuntu

Real-mode Boot Sector
---------------------
identifier              {6524580f-8d90-11e0-acee-de4ebabeeca5}
device                  partition=C:
path                    \jolicloud\winboot\jolildr.mbr
description             Joli OS

Real-mode Boot Sector
---------------------
identifier              {f158c06f-2c24-11e1-a6c6-fd14d4a9d561}
device                  partition=E:
path                    \linuxmint\winboot\wubildr.mbr
description             Linux Mint

---

