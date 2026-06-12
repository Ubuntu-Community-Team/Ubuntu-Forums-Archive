---
title: "Computer won't boot?"
date: 2011-06-10
forum: General Help
---

### Post by cringe dragon on 2011-06-10
I had recently tried to install Ubuntu on my hard drive to make it dual boot with windows 7. The installer crashed in the middle of installing it, &%*$ing up my my bootloader, i guess (I don't know much about this stuff, but I had been reading on some forums). 
Then i had an error when i booted that said this: "error: unknown filesystem grub rescue >". I had to search everywhere online, and i found one that said to try running this command: 
sudo dd if=/dev/zero of=/dev/sda count=1 bs=446 from the terminal. I did so, and i rebooted my computer.
Now nothing will happen, and when i boot it up, there is no error message, and there is just a blinking " _ " on my screen, and I don't know what to do! The only system I can boot now is Ubuntu from my flash drive! Help?!

---

### Post by LowSky on 2011-06-10
simply reinstall the Ubuntu livecd... hopefully all goes well the second time around or reinstall the windows boot loader from the Windows dvd

---

### Post by Quackers on 2011-06-10
If the installer crashed then it is likely that Ubuntu has not been properly installed. It seems though, that grub has been installed to the mbr of the drive, giving you these errors.
If you just want to get Windows booting again, then try installing again, you can fix the Windows bootloader with a Windows repair disc or installation disc.
Boot from that, enter the repair console and from the command prompt run ```
bootrec.exe /fixmbr
``` (note the space between exe and /fixmbr) and if that runs without errors you can reboot when Windows should boot up.

---

