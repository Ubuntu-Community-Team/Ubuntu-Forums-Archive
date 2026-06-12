---
title: "I can not boot into window(if i select windows from option &quot;invalid pa"
date: 2011-03-08
forum: General Help
---

### Post by connect2jan on 2011-03-08
I can not boot into window(if i select windows from option "invalid partition table" msg appearing)

i  have internet working.
I have a dual boot system(windows xp +ubuntu 10.10 )
i Recovered Windows MBR using Ubuntu LIVE CD

i folowed below link
[http://ubuntuforums.org/showthread.php?t=622828&highlight=recover+windows+mbr](http://ubuntuforums.org/showthread.php?t=622828&highlight=recover+windows+mbr)

or

(I  enable the 'universe' repository (System->Administration->Software Sources) before I could install the ms-sys package. I also needed to put "sudo" in front of the ms-sys command (e.g. "sudo ms-sys --mbr /dev/sda") otherwise I got permission denied.)

1) Boot with Ubuntu 10.10 Live CD or Linux Mint Live CD

2) i downloaded ms-sys2.2.deb file
i installed through terminal  dpkg --install ms-sys2.2.deb
 
3)sudo ms-sys --mbr /dev/sda1  (windows xp was installed on sda1)

message:Windows XP master boot record successfully written to /dev/sda1
then i restarted message "invalid partition table"
then i inserted wxp cd ,i selected console(click R for repair)
C:fixmbr ( i typed)
i restarted
from option
-- I can not boot into windows anymore.(if i select windows from option "invalid partition table" msg appearing)
I have a dual boot system (ubuntu/ Windows XP Pro).
I can boot into ubuntu fine and all is well. Just booting into XP is messed up.

When I choose to boot into XP it just sits there with "starting up" in the top left of the screen.

1q)Does anyone know what got messed up and how to fix it.

--------------------------------------------------------------------
2q)fdisk,fixmbr,fixboot are for windows xp or for all windows
these are not working in wxp-msg like"command not found"
-----------------------------------------------------------------------

3q)this commands fdisk,fixmbr,fixboot ,do i need to put up(type)
c:fixmbr or c:\WINDOWS>fixmbr
---------------------------------------------------------------------------
4q)i want remove ubuntu ,i want only windows back(it should work properly)

what to do
any help

---

### Post by howefield on 2011-03-08
Moved to "*General Help*".

You probably get more help for this problem here than in Tutorials and Tips.

---

### Post by kiyop on 2011-03-08
> **connect2jan said:**
> 
3)sudo ms-sys --mbr /dev/sda1  (windows xp was installed on sda1)
The above broke the Partition Boot Record of first partition (/dev/sda1).
/dev/sda1 is Partition Boot Record (PRB) of first partition of the first device (such as HDD).
You should not install code for MBR to /dev/sda1.

I am not sure whether "ms-sys --mbr" write only one sector or more than one sector.

If it write only one sector, you may be able to repair by "fixboot".
Boot with XP install CD and enter into Recovery Console and
```
fixboot
```Or,

You can recover former PBR by copying the backup boot sector.
The backup boot sector is placed at the end of the NTFS partition.

Please boot with Ubuntu LiveCD and open terminal;
"Application" -> "Accessory" -> "Terminal"
```
sudo fdisk -lu
```Post the result by dragging the result and right-click "copy" and open Firefox and open this page and right-click "paste".

---

### Post by connect2jan on 2011-03-09
hi all 
thanks for reply

i done fixmbr,in console windows xp cd

it works greatly
thanku

---

### Post by kiyop on 2011-03-09
fixmbr only?
fixboot?;)

---

