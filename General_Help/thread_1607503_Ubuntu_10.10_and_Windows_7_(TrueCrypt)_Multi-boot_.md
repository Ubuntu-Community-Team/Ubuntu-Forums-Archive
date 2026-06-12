---
title: "Ubuntu 10.10 and Windows 7 (TrueCrypt) Multi-boot Problems"
date: 2010-10-27
forum: General Help
---

### Post by samtay on 2010-10-27
Hey everyone,

I have now been searching days for a solution but have found nothing.

I have Ubuntu 10.10 and Windows 7 with TrueCrypt as a multi-boot. It was working fine for a few weeks until I needed to reinstall Ubuntu. If I have the boot flag on the partition where Windows 7 is install (This is where the boot flags was when working before.), it boots fine in to Windows 7 but when pressing Esc it can't find grub2. If I have the boot flag on the partition where Ubuntu is install, it boots fine in to Ubuntu (by pressing Esc or typing the password) but unable to access Windows.

I have tried reinstalling TrueCrypt Boot loader and repairing the header but it have no affect.

My Partitions:
[LIST]
[*]sda1 - Windows 7 Recovery (GRUB2)
[*]sda2 - Windows 7 (TrueCrypt Boot Loader)
[*]sda3 - Ubuntu 10.10 (/)
[*]sda4 - Extended
[*]sda5 - Swap
[*]sda6 - Ubuntu (/home)
[/LIST]

Does anyone have any ideas?

Thanks
Sam

---

### Post by shells on 2010-11-01
Hi samtay,

I'm running in similar problems everytime I'm reinstalling a unix on my business laptop.
It's Win7 x64 w/ TrueCrypt + Fedora + Ubuntu x64.

Did you heard of "easyBCD" ([http://neosmart.net/)?]("http://neosmart.net/%29?") It's a free Windows bootloader editor.
I'm always using the Windows 7 bootloader - because I like it more.
If you don't, stop reading, ha-ha.

That's what's working for me:

-> decrypting the whole drive (because otherwise the images I'm creating would be as big as the whole drive's capacity)
-> create image with acronis bootdisk (or any other imaging software for sure)
-> install new linux
-> store the bootloader where Windows bootloader is -- including Windows in the Ubuntu / Fedora grub never worked 'out-of-the-box' for me, besides I wouldn't use it anyway.
-> booting from Windows DVD - into command prompt (somewhere after you select to recover the system)
-> type: 'bootrec /fixmbr' followed by 'bootrec /fixboot'
-> restart the system -> now your Win7 loader is back there - but you aren't able to boot into the freshly installed *nix anymore
-> back in Windows 7 use easyBCD to add a new entry for grub2 to the Windows bootloader -> save it to MBR
-> now, during boot your Windows 7 loader should show the option to load into unix (it's presented, how you named it) -> selecting the option will load grub2 like you've set it up - or the installer did.
-> after all, reencrypt the Windows systems (I don't use TrueCrypt for the Unix partitions).

If all of that works without decrypting the system... possibly, but I've never tried it, since I don't re-install my business laptop without having a image created.

I hope this helps.

Cheers,
shells

---

### Post by Arvoredo Is. on 2011-02-22
I've just installed "easyBCD" in an windows 7 with Truecrypt full partition encryption in one partition and Ubuntu 10.10 into another partition created later.

I've just installed "easyBCD" and created an automatic new entry. It was like 30 seconds. Then restarted. :)

It worked, and it just confirms that a new entry can be added to the boot list of an encrypted Windows 7 partition. The problem now is that the only way I have to access the Ubuntu 10.10 partition is after typing the WINDOWS password, because "easyBCD" saves the the Ubuntu MBR inside the windows partition at C:\NST\AutoNeoGrub0.mbr. :(

Any clue on how to solve that? maybe if a new partition is created just to hold this C:\NST\AutoNeoGrub0.mbr file?

---

### Post by Arvoredo Is. on 2011-02-23
After many many hours wondering, searching and googling why Ubuntu wouldn't start without Windows Truecrypt password, I've found that I could put the Ubuntu-Linux boot files in the Windows 7 hidden partition. And then voila, it worked! :popcorn:

0. Create the EasyBCD boot menu, as in the post above

Now to the tricky part, because the bootloader won't guess where the files ended up:

1. Create a drive letter to the very Windows hidden partition, say S: using the system Disk Manager
2. Modify the EasyBCD entry in the Windows bootloader for the drive letter of the former hidden partition S: drive letter using the Windows 7 command line bcdedit (since boot.ini is no more) there's a tutorial just for that somewhere, but the command line is something like BCDEDIT /set <identifier> device "partition=S:"
3. copy c:\NST directory and c:\ANG0 file (in the root directory) from C:\ to S:\ (the former hidden partition)
4. If everything went right then the drive letter may be removed, and the system restarted
5. Press esc at the Truecrypt loader and select the Linux entry, no Truecrypt password needed

This worked for me and now I can boot into Ubuntu without having to type the Truecrypt password. It doesn't mean it'll work for you, and a good knowledge of windows command line (cmd.exe) is required not to disappear with boot settings.

---

