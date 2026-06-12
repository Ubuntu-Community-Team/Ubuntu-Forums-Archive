---
title: "Help with boot-repair"
date: 2012-07-12
forum: General Help
---

### Post by thatguy93 on 2012-07-12
Hey guys,
I've bee having problems with shutting my laptop down with Ubuntu 12.04LTS, and have tried to use boot-repair to help. It did work, but I forgot to change something,so I had to run the program again.

The thing I forgot to change before, was this:
> Please do not forget to make your EFI-BIOS boot on sda1/EFI/ubuntu/grubx64.efi file!

Can someone please explain how I do this?

Thank you!

---

### Post by YannBuntu on 2012-07-12
Hello
This message means that Boot-Repair has detected that your computer has an EFI partition (sda1), and installed grub-efi. This created a boot file (/EFI/ubuntu/grubx64.efi) on the sda1 partition. You now need to tell your BIOS to boot on this file.

When you reboot your PC, you will first see a screen which generally shows the PC manufacturer logo. 
It generally also displays instructions to open your BIOS menu (eg "Press ESC key to enter BIOS", or something similar). The key is generally Escape or F2, F10...
Press the key to open your BIOS menu, then setup the boot order to make your BIOS boot on the sda1/EFI/ubuntu/grubx64.efi file.

If any problem, please indicate the URL (something like **http//paste.ubuntu/com/XXXXX/** ) you saw at the final window of Boot-Repair, and show pictures of your BIOS.

---

### Post by thatguy93 on 2012-07-12
> **YannBuntu said:**
> Hello
This message means that Boot-Repair has detected that your computer has an EFI partition (sda1), and installed grub-efi. This created a boot file (/EFI/ubuntu/grubx64.efi) on the sda1 partition. You now need to tell your BIOS to boot on this file.

When you reboot your PC, you will first see a screen which generally shows the PC manufacturer logo. 
It generally also displays instructions to open your BIOS menu (eg "Press ESC key to enter BIOS", or something similar). The key is generally Escape or F2, F10...
Press the key to open your BIOS menu, then setup the boot order to make your BIOS boot on the sda1/EFI/ubuntu/grubx64.efi file.

If any problem, please indicate the URL (something like **http//paste.ubuntu/com/XXXXX/** ) you saw at the final window of Boot-Repair, and show pictures of your BIOS.

No luck, here's my BIOS
[IMG]http://i536.photobucket.com/albums/ff321/AdrianRocky719/8d6e835a.jpg[/IMG]

And here's the URL:
[paste.ubuntu.com/1088118/]("http://ubuntuforums.org/paste.ubuntu.com/1088118/")

Also, downloaded Gparted, and took a look, it shows that /dev/sda1 is flagged as boot.

---

### Post by thatguy93 on 2012-07-12
Decided to go back to Fedora for the time being.
Thanks for the help Yann!

---

### Post by YannBuntu on 2012-07-12
You have a Phoenix SecureCore Tiano BIOS. There are other threads about it, eg: [http://ubuntuforums.org/showthread.php?p=12096077#post12096077](http://ubuntuforums.org/showthread.php?p=12096077#post12096077)

Anyway, if your Fedora is working, please indicate your [BootInfo]("https://help.ubuntu.com/community/Boot-Info") URL. It will give us clues on how to boot on Ubuntu too.

---

### Post by marksch on 2013-01-09
Hi,

I have a similar problem, posted here:
[http://ubuntuforums.org/showthread.php?t=2103182](http://ubuntuforums.org/showthread.php?t=2103182)

Kind regards,

Mark

---

### Post by audiocat on 2013-03-31
Good Day YannBuntu,
I have been trying to get Ubuntu 12.04 installed on a MacBook 3,1 as the only operating system.
I followed the procedures here on Rods Books, ([http://www.rodsbooks.com/ubuntu-efi/](http://www.rodsbooks.com/ubuntu-efi/)), but without having Mac installed, I used a LiveCD of Partiton Magic to perform the mentioned procedures using  gdisk, and everything installed correctly, but the Mac will not boot on it's own...even when I press the "options" key to select the partition to boot. When I press the "options" key, it shows an efi boot partition on the hard drive, but just drops to a grub prompt.
The only way I can get into the Ubuntu installation is by starting the Mac with a disk in the super drive and pressing the disk eject button, the disk will pop out and then the screen turns purple with Ubuntu colors and it comes up to my login. Hmmm...very strange.
So...I got into my Ubuntu installation and installed and ran boot-repair. I created a boot info file before I ran boot-repair, listed here, ([http://paste.ubuntu.com/5664336/](http://paste.ubuntu.com/5664336/)), and then the program created a boot info file after repair, ([http://paste.ubuntu.com/5664414/](http://paste.ubuntu.com/5664414/)).
At the end of the boot-repair, it gives me this message, Please do not forget to make your EFI-BIOS boot on sda1/EFI/ubuntu/grubx64.efi file! but Mac's don't use BIOS, so I'm not sure what I need to do with it.
I feel I am getting very close to making efi boot on a Mac, but I think I am overlooking something.
Any suggestions?
Thanks,
Douglas

---

### Post by oldfred on 2013-03-31
I know nothing about Macs. Your post really should be in the Apple sub-forum.

 Post #6 booting Kubuntu 12.10 in EFI mode on my Mac, by  trogdor1138
[http://ubuntuforums.org/showthread.php?t=2091257](http://ubuntuforums.org/showthread.php?t=2091257)
Bit older, Mac & PC UEFI, note issues on some systems
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[http://refit.sourceforge.net/](http://refit.sourceforge.net/)
[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
[http://lifehacker.com/5934942/how-to-dual-boot-linux-on-your-mac-and-take-back-your-powerhouse-apple-hardware](http://lifehacker.com/5934942/how-to-dual-boot-linux-on-your-mac-and-take-back-your-powerhouse-apple-hardware)
Caution on UEFI boot Mac
[http://ubuntuforums.org/showthread.php?t=2012588](http://ubuntuforums.org/showthread.php?t=2012588)

---

### Post by emarkay on 2013-03-31
Quick off topic Q - is there a "liveCD" of Boot-repair I can burn, then just pop into a damaged machine and boot/and run from CD; without having to boot into the live Ubuntu CD and then D/L Boot-repair and all that?
Thanks!

---

### Post by oldfred on 2013-03-31
There is this version.
 [https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)
Correction It was renamed, but above currently takes you here:
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

