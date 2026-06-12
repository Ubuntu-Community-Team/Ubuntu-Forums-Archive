---
title: "Windows 7 , Ubuntu, and grub2 - booting problems"
date: 2010-03-21
forum: General Help
---

### Post by spaik on 2010-03-21
hi

i really need ur help as soon as possible :(

i have windows7 installed on my toshiba laptop and i have installed ubuntu Karmic yesterday from the live cd on a different partition. however the grub doesn't see my windows7.. i tried everything on the internet to try and fix this problem...
when i type $ sudo update-grub  thats what i get :-
>  Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
“Adding Windows”
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
done


please i need this worked out as soon as possible as i have work to to on windows.

thank you very much :(

---

### Post by prodigy_ on 2010-03-21
Boot into Ubuntu. Press Alt+F2 and type ```
gnome-terminal
``` to open Terminal. In Terminal window type ```
sudo fdisk -l
``` to list partition table. Post the output here.

---

### Post by sunrise-7 on 2010-03-21
I have a similar problem and together someone may have an answer for both which benefits.

My wife specifically purchased a new Dell Inspiron 1545 laptop, with 64-bit Windows 7, 2.20 GHz. 4.00 GB memory with the hope of running a dual boot with Ubuntu 9.10. This is the second attempt to persuade her to use Linux after a complete crap out a few weeks ago with a partition dual boot on a 4-yr-old Acer 3610 that proved to be hardware deficient.

[COLOR=black]Used install option of Ubuntu 9.10 as a Program, no partitioning required.  [/COLOR]
[COLOR=black]ReStarted to complete install  [/COLOR]
[COLOR=black]Used the Update Manager to update with 239 urgent Security Updates!  [/COLOR]
[COLOR=black]ReStarted. selected Ubuntu  [/COLOR]
[COLOR=black]Dual Boot Menu was garbled and the following appeared, for Ubuntu, instead .. 
[/COLOR]
[COLOR=black]
[/COLOR]
[COLOR=black]GNU-GRUB version 1.97~beta4
Minimal BASH-like line editing ....
sh:grub> 
[/COLOR]
[COLOR=black]
[/COLOR]
[COLOR=black]ReStarted and selected Windows7
Uninstalled, as if a Program [/COLOR]Will Ubuntu 9.10 only install with Windows 7 as a dual boot partition option, or is there a bug in it that is showing up here? 

I have to have something that works or there is no use making the effort as I cannot leave the laptop not working or limping along because of Ubuntu, or, there will not be another invitation for a LOONG time to try it.

---

### Post by spaik on 2010-03-21
> Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x07eec164

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       21772   173342720    7  HPFS/NTFS
/dev/sda3           21772       24322    20478976   83  Linux


so as u can see sda1 is the recovery partition for vista that came on the laptop... i dont actually need that any more and will delete it soon. sda2 is the one with windows 7. and sda3 is ubuntu...

---

### Post by prodigy_ on 2010-03-21
Save this script as a text file in your home folder (called, for example, "grub.sh"):```

#!/bin/sh
cat <<EOF > /etc/grub.d/40_custom
#!/bin/sh
exec tail -n +3 \$0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Windows (on /dev/sda2)" {
        insmod ntfs
        set root=(hd0,2)
        chainloader +1
}
EOF
sed -i 's/^GRUB_HIDDEN_TIMEOUT=.*/#&/' /etc/default/grub
update-grub
```
Then in Terminal run the script:```
sudo sh ~/grub.sh
```

Then reboot. One extra line will appear on your grub boot menu: "Windows (on /dev/sda2)" - select it and you should boot into Windows.

---

### Post by spaik on 2010-03-21
did that and still it gives me this error
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
“Adding Windows”
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
done

```

---

### Post by prodigy_ on 2010-03-21
For Windows 7 you shouldn't rely on OS prober. Just ignore its error messages. The purpose of this script is to add a menu entry for Windows manually.

Did you try to reboot? Don't be afraid. :-) If (unlikely) Windows still won't boot, this will only mean that its bootloader is on the first, hidden partition. I'll tell you what to do.

---

### Post by spaik on 2010-03-21
ok i will reboot after the update manager finish and will see. thanks anyway.

---

### Post by garvinrick4 on 2010-03-21
> **spaik said:**
> so as u can see sda1 is the recovery partition for vista that came on the laptop... i dont actually need that any more and will delete it soon. sda2 is the one with windows 7. and sda3 is ubuntu...
Partition that says Vista is Windows 7 recovery partition, it is just read as Vista by Linux.
But it is already to small a partition for 7 recovery image. Takes 12 gig or so. You do not have near that. And should say NTFS not unknown.
Did you upgrade from Vista to 7?

Looks kind of a mess in the sda1 here is mine.

/dev/sda1    *          2,048       409,599       407,552   7 HPFS/NTFS
/dev/sda2             409,600   419,802,095   419,392,496   7 HPFS/NTFS
/dev/sda3         419,810,580   599,706,449   179,895,870   5 Extended
/dev/sda5         515,782,953   596,188,214    80,405,262  83 Linux
/dev/sda6         596,188,278   599,706,449     3,518,172  82 Linux swap / Solaris
/dev/sda7         419,810,706   511,766,639    91,955,934  83 Linux
/dev/sda8         511,766,703   515,782,889     4,016,187  82 Linux swap / Solaris
/dev/sda4         599,719,936   625,139,711    25,419,776   7 HPFS/NTFS

sda1 being boot and only boot.
sda2 being 7
sda4 being recovery
sda5 and 7 being karmic and lucid
sda3 being a primary partition to hold all my two Linux installs.
sda 6 and 8 being swap or virtual memory for Linux (really not needed with 3 or 4 gig of Ram in Machine)

gparted in Ubuntu is a good piece of software let it do its thing.
These were all made by gparted when installed from Ubuntu Burned CD of OS.
Did not use manual but let the software do it since it choose a nice size for each.
Use manual when you know your way around gparted software.

Notice all things NTFS when has Windows involved. All ext4 when Linux involved.

Do believe you have trouble and will be better off taking your Windows 7 install disks
and starting over. Come back to this thread if you need help. I can do that for you.

---

### Post by garvinrick4 on 2010-03-21
> **prodigy_ said:**
> For Windows 7 you shouldn't rely on OS prober. Just ignore its error messages. The purpose of this script is to add a menu entry for Windows manually.

Did you try to reboot? Don't be afraid. :-) If (unlikely) Windows still won't boot, this will only mean that its bootloader is on the first, hidden partition. I'll tell you what to do.
For my own knowledge which companys are still using hidden partitions for recovery? I know Dell did in XP. Under 4 gig now 7 is closer to 12 gig. Would be nice for me to know.

---

### Post by garvinrick4 on 2010-03-21
> **sunrise-7 said:**
> I have a similar problem and together someone may have an answer for both which benefits.

My wife specifically purchased a new Dell Inspiron 1545 laptop, with 64-bit Windows 7, 2.20 GHz. 4.00 GB memory with the hope of running a dual boot with Ubuntu 9.10. This is the second attempt to persuade her to use Linux after a complete crap out a few weeks ago with a partition dual boot on a 4-yr-old Acer 3610 that proved to be hardware deficient.

[COLOR=black]Used install option of Ubuntu 9.10 as a Program, no partitioning required.  [/COLOR]
[COLOR=black]ReStarted to complete install  [/COLOR]
[COLOR=black]Used the Update Manager to update with 239 urgent Security Updates!  [/COLOR]
[COLOR=black]ReStarted. selected Ubuntu  [/COLOR]
[COLOR=black]Dual Boot Menu was garbled and the following appeared, for Ubuntu, instead .. 


[/COLOR]
[COLOR=black]
[/COLOR]
[COLOR=black]GNU-GRUB version 1.97~beta4
Minimal BASH-like line editing ....
sh:grub> 
[/COLOR]
[COLOR=black]
[/COLOR]
[COLOR=black]ReStarted and selected Windows7
Uninstalled, as if a Program [/COLOR]Will Ubuntu 9.10 only install with Windows 7 as a dual boot partition option, or is there a bug in it that is showing up here? 

I have to have something that works or there is no use making the effort as I cannot leave the laptop not working or limping along because of Ubuntu, or, there will not be another invitation for a LOONG time to try it.
[COLOR=black]You installed Wubi version. There are lots of  threads with you symptoms look under Wubi.[/COLOR]

---

### Post by spaik on 2010-03-21
yes its a vista recovery coz the laptop originaly came with vista but i installed windows seven and i forgot that this partition is there...

My problem is solved now and i can boot into windows from grub and everything is super ok :)

thanks prodigy_ .. and thanks everyone... :D :D u r the best community ever :)

---

### Post by sunrise-7 on 2010-03-22
Thanks [garvinrick4]("http://ubuntuforums.org/member.php?u=899097") for the reply.
I did not know anything about WUBI
Found it on THIS site by having to search Google!
Yes, there are over 250 problems with it.
I installed from a CD I received from this site in February, 2010.
The disc has a WUBI (Windows-Ubuntu Boot Installation?) file of Oct, 2009
Last update per the wubi.org site is March 22, 2009!
The short answer is to skip the "Load as a Windows Program" option and either risk the re-partitioning load, which may crap out Windows 7, or wait a few months in hopes of a cleaner load .. if anyone is working on the problems. Appears that WUBI is not ready for Windows 7 yet, or, not on laptops. I'll wait.
Ubuntu is beginning to sound like Windows .. releasing secure versions with major failures!

---

### Post by spaik on 2010-03-23
i dont think there is any problem with ubuntu and windows 7 if u install ubuntu using wubi coz i have done it before.. i found the best way to do that without any problems is to have a different partition for ubuntu away from windows partition and just install ubuntu using wubi in the empty partition and it will work just fine.

---

### Post by Gregorybekkers on 2010-03-23
I had the same problem.
this is because windows 7 uses 2 partitions to startup 1 100 mb partition and your system partition.
the best u can use Bootit-NG

---

