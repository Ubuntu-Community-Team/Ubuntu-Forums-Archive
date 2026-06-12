---
title: "How to remove grub"
date: 2010-03-24
forum: General Help
---

### Post by WestsideRiderz15 on 2010-03-24
i have an msi wind, with recovery partitions @ partition 1, os @ partition 2. WIndows recovery cd didnt help because i think it writes to the first partition automatically
Fixmbr/fixboot/bootcfg combo did not work. I formatted the Ubuntu Netbook remix 9.(something) from windows and got a GRUB error. (grub replaces files on your Master boot record)



WOOP. HERE is the solution. (only works if you can still boot to windows  via emergency bootloader) I used:
Novicorps Win to Flash: free ware
A  downloaded copy of windows xp sp3 home (torrent) (dl the version and  service pack you have or need)
MBRFIX.exe: freeware (cnet.com)

first,  use win to flash, goto tasks and click create bootable emergency flash  drive.
A window will open. I used these options: USB-hdd, fat 16 cha,  then point it to the directory of the windows iso you downloaded. then  point it to your flash drive.
This creates a bootable flash drive  with the 3 common files u need to boot (NTDECT, boot.ini ect)

go  into your bios when the pc boots and tell it to load usb harddrive  first.

reboot

Windows should now boot.

Start menu,  run, cmd.exe
a dos window will open
go back to your desktop,  extract mbrfix into its own folder (3 files) (mbrfix64 is for 64 bit  versions, check with your provider to see what you have)
go back to  your dos window
c:\documents and settings\(your name)>cd desktop
...cd  (folder name withmbrfix in it)
if you type DIR, it should show the 3  files (mbrfix, mbrfix64, and an html file)
should look something  like this
c:\documents and settings\(your name)\desktop\temp>

Now,  MY OS partition is my second partition because my first one was a  recovery partition. i have one hard drive
hard drive numbers start at  0, partitions start at 1.

in the dos window type:
mbrfix/drive 0 /partition 2 /fixmbr /yes
this fixes the mbr for 1st hard drive, 2nd partition

rebooted and done!

P.S. Read comments on Cnet on MBRfix and also comments on MBRfix website  to learn more.

P.P.S I believe this can also be done by removing your hard drive from your pc and doing all this on another computer with your hard drive slaved to it.

---

