---
title: "Ubuntu bootable USB stick with private partition"
date: 2012-06-17
forum: General Help
---

### Post by IcemanBG on 2012-06-17
Hello there,

In my company we have one development team under Linux, they need a bootable usb stick with 2 partition, one public partition and a private partiton (not visible before call a c program)..when the system boot, syslinux or grup call initrd, then init call a binary file that request a password to user, after this, if the password is correct, mount the private partition, and load the os (i think to use squashfs)...One of our developers made binary files.but can someone explain to me how to all of that??

Tnx in advance

---

### Post by meathdeath on 2012-06-17
pendrivelinux.com

thank me later:)

---

### Post by Cheesemill on 2012-06-17
You can achieve the the same result by doing a full install to the USB stick using the alternate CD and choosing 'LVM with encryption' at the partitioning stage.

---

### Post by IcemanBG on 2012-06-18
> **Cheesemill said:**
> You can achieve the the same result by doing a full install to the USB stick using the alternate CD and choosing 'LVM with encryption' at the partitioning stage.

Ok ..can I encrypt in that way OS partition..we want to encrypte all data actualy not only "home" ..And my team want that system ask for a password on boot process?

---

### Post by Cheesemill on 2012-06-18
> **IcemanBG said:**
> Ok ..can I encrypt in that way OS partition..we want to encrypte all data actualy not only "home" ..And my team want that system ask for a password on boot process?
That's exactly what you get.

The entire drive is encrypted (except a tiny /boot partition containing the GRUB files).
You are asked for a password straight after the GRUB menu.

---

### Post by IcemanBG on 2012-06-18
> **Cheesemill said:**
> That's exactly what you get.

The entire drive is encrypted (except a tiny /boot partition containing the GRUB files).
You are asked for a password straight after the GRUB menu.

Ok tnx I`ll try to do that..I`m w8ing for more informations from my team,why and what they exactley need to do

---

### Post by IcemanBG on 2012-06-18
> **Cheesemill said:**
> That's exactly what you get.

The entire drive is encrypted (except a tiny /boot partition containing the GRUB files).
You are asked for a password straight after the GRUB menu.

I didnt explain to u our problem on right way..Problem is because we want to use hardware based encryption ,we have USB with hw encrypted key..how to solve this?

---

### Post by Cheesemill on 2012-06-18
If it has physical buttons on it to enter in the passcode then you can just use it as a normal USB stick.

Otherwise it probably won't work at all with Linux, all the ones I've tested need to be unlocked using on-board software which only works with Windows.

What make and model number are your USB sticks?

---

### Post by sudodus on 2012-06-18
> **IcemanBG said:**
> I didnt explain to u our problem on right way..Problem is because we want to use hardware based encryption ,we have USB with hw encrypted key..how to solve this?

If you must use the hardware encryption, you are probably stuck with Windows (at least to use that encrypted partition).

Otherwise I would vote for *Cheesemill*'s solution, so maybe you can convince your colleagues about that.

---

### Post by IcemanBG on 2012-06-18
> **sudodus said:**
> If you must use the hardware encryption, you are probably stuck with Windows (at least to use that encrypted partition).

Otherwise I would vote for *Cheesemill*'s solution, so maybe you can convince your colleagues about that.

They will ship me that usb in Friday and then ill let you know..btw one of us developers said to me that he maid an C binary which unlocks the partition

---

### Post by Cheesemill on 2012-06-18
You would need to install GRUB onto the unencrypted part of the drive along with the kernel and a custom initrd that contained your decryption binaries. Then the rest of the files that you would usually find on a Live CD (including the squashfs) could live on the encrypted part.

I have no experience with this but these links may help point you in the right direction:

[http://manpages.ubuntu.com/manpages/dapper/man8/mkinitrd.8.html](http://manpages.ubuntu.com/manpages/dapper/man8/mkinitrd.8.html)
[https://wiki.ubuntu.com/CustomizeLiveInitrd](https://wiki.ubuntu.com/CustomizeLiveInitrd)
[http://www.indiangnu.org/2009/how-to-create-editextract-initrd-in-ubuntudebian-and-redhatfedora-linux/](http://www.indiangnu.org/2009/how-to-create-editextract-initrd-in-ubuntudebian-and-redhatfedora-linux/)
[http://uck.svn.sourceforge.net/viewvc/uck/trunk/uck/docs/html/building-script.html](http://uck.svn.sourceforge.net/viewvc/uck/trunk/uck/docs/html/building-script.html)


I still think it would be **much** easier (and cheaper) to go with a software encrypted full installation on a normal USB stick.
Is there any reason you *have* to use hardware encryption?

---

### Post by IcemanBG on 2012-06-19
> **Cheesemill said:**
> You would need to install GRUB onto the unencrypted part of the drive along with the kernel and a custom initrd that contained your decryption binaries. Then the rest of the files that you would usually find on a Live CD (including the squashfs) could live on the encrypted part.

I have no experience with this but these links may help point you in the right direction:

[http://manpages.ubuntu.com/manpages/dapper/man8/mkinitrd.8.html](http://manpages.ubuntu.com/manpages/dapper/man8/mkinitrd.8.html)
[https://wiki.ubuntu.com/CustomizeLiveInitrd](https://wiki.ubuntu.com/CustomizeLiveInitrd)
[http://www.indiangnu.org/2009/how-to-create-editextract-initrd-in-ubuntudebian-and-redhatfedora-linux/](http://www.indiangnu.org/2009/how-to-create-editextract-initrd-in-ubuntudebian-and-redhatfedora-linux/)
[http://uck.svn.sourceforge.net/viewvc/uck/trunk/uck/docs/html/building-script.html](http://uck.svn.sourceforge.net/viewvc/uck/trunk/uck/docs/html/building-script.html)


I still think it would be **much** easier (and cheaper) to go with a software encrypted full installation on a normal USB stick.
Is there any reason you *have* to use hardware encryption?

Yeah, I think u are absolutely in right..our technician director also said that something like that and he suggest using of squshfs...btw I am not sure because I`m not part of that team I just help to them..As I know they use ermine to run programs to avoid library package depedencies ,they also do reverse engineering on elf obfuscated C files..I`ll ask them for more informations..Also I`ll post their C source for unlocking partitions..

---

