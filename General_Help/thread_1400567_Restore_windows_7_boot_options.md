---
title: "Restore windows 7 boot options"
date: 2010-02-07
forum: General Help
---

### Post by dtech on 2010-02-07
Hi,

by accident I deleted my windows 7 partition yesterday (I was formatting 2 external drives). I immediatly quit the (ubuntu) disk utility.

The partition (/dev/sda2) was still mounted as /windows, also after a reboot. I could access all data

However, I could not boot into windows anymore, I got a error message like "Device [some_serial] not found". When I ran update-grub in ubuntu it didn't add windows 7 (like it normally does usual xx_os_other)

Anyone know how I can restore this?

I use ubuntu 9.10 with grub2.

---

### Post by meierfra. on 2010-02-07
Sounds like you only deleted the Windows 7 system partition, and not the operating system. But before we jump to conclusion lets have a better look at your setup. Follow these [instructions ]("http://bootinfoscript.sourceforge.net/")to run the boot info script and post the RESULTS.txt.

---

### Post by dtech on 2010-02-08
In the meantime I have restored it. It took quite some googling and a few curses (since it didn't work again). But this is the summary of what I had to do (minus all the irrelevant things/things I did in the wrong order).

It should work in about the same way for Vista btw.

[list=1]
[*]Burn an ubuntu live cd / ubuntu usb stick from your working ubuntu installation or another computer. Also find out which device your hd is (usually /dev/sda)
[*]Make sure you have your Windows 7 DVD
[*]Put it in the computer and boot from the Windows 7 DVD (modern computers usually have a key like f9 to summon a boot menu, otherwise edit it in your BIOS which you can usually reach with del or f11)
[*]Select your language
[*]Select "repair your computer"
[*]If your windows installation show up, skip to step 9
[*]start a command prompt (select it or press shift+f10) and do the following commands:
```

diskpart
list disk
select [[your windows 7 disk number]]
list partition
select [[your windows 7 partition number]]
active
exit

del C:\boot\bcd [[Don't mind if it gives a "File not found" error, replace C: with your windows 7 drive]]

bootsect.exe /nt60 all /force
bootrec.exe /fixmbr
bootrec.exe /scanos [[Choose the windows 7 partition to boot from, include multiple if you have multiple windows installations]]
bootrec.exe /rebuildbcd [[You might have to choose again]]
bootrec.exe /fixboot
shutdown -r -t 0 [[reboots your computer]]
[[Remove Windows 7 drive]]

```
[*]Try booting from windows 7, if it works, skip to step 14. Otherwise reinsert the windows 7 dvd and continue with step 9 (select repair your computer again)
[*]Select the windows installation. If you get an error about startup problems, press "do not repair"
[*]Press "repair startup options" (or something like that)
[*]Reboot, remove windows 7 DVD and try to boot to windows 7. If is works, skip to step 14. Otherwise reinsert dvd and continue.
[*]Select your windows 7 installation, start a command prompt and do step 7.
[*]Try to boot, if it doesn't work now I don't know how to solve your problem.
[*]Insert your ubuntu live cd / usb stick
[*]Start a terminal
[*]Insert the following commands:
```

sudo mount /dev/sda2 /mnt [[replace /dev/sda2 with your linux partition]]
[[If you get an error about /mnt not existing enter "sudo mkdir /mnt" first]]
sudo mount --bind /dev /mnt/dev
chroot /mnt
update-grub /dev/sda [[this restores grub, but your windows installation misses, replace /dev/sda with the correct hard drive]]
[[Press Ctrl+D to exit the chroot, then reboot and remove the live cd]]

```
[*]Boot into ubuntu
[*]Start a terminal, and enter:
```

sudo update-grub

```
[*]Your bootload should now be restores into the origional state. If you customized it in the wrong way (manually edit files instead of editing the scripts in /etc/grub.d) you need to do it again.
[/list]

Your computer should now be in the origional state!
Note that this was for grub2, for grub1 step 16-18 differ.

---

### Post by meierfra. on 2010-02-08
Good job. One suggestion though:

As far as I know, you don't need to run  "bootrec.exe /fixmbr". 
And if you don't run "bootrec.exe /fixmbr", you won't have to do steps 14-19.

---

### Post by dtech on 2010-02-08
I had to, but I already had messed up my mbr/boot in previous attempts to fix it.

Then again, it isn't that much of a problem, and this way you're sure it works.

---

