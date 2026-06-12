---
title: "Problem With Boot Menu When Installing New Linux Distro"
date: 2012-07-29
forum: General Help
---

### Post by gdawg on 2012-07-29
Hi,

I'm currently booting Win 7, Mint, PCLinuxOS, openSUSE, and Ubuntu 12.04 from Ubuntu on 2 drives. Whenever I attempt to install a distro that is Grub Legacy the boot menu completely disregards the Grub 2 distros. Any suggestions on how to correct this during the installation will be appreciated. Thanks.

---

### Post by mike555 on 2012-07-29
What I do is during install I install grub to the same partition , then use separate boot manager in mbr ( like Gag ) to relay the start.

---

### Post by oldfred on 2012-07-29
Much better to always install grub legacy to the PBR - partition boot sector as it will work from that. But grub2's os-prober is much improved over the limited search that grub legacy has. I would keep grub2 as my main boot loader and let it search for other installs.

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

[http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Custom_Boot_Entries](http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Custom_Boot_Entries)

Grub2
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition_](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition_)

---

### Post by gdawg on 2012-07-29
Thank you mike555 and oldfred for your replies. I'll try your suggestions and will get back to you.

---

### Post by gdawg on 2012-07-30
> **gdawg said:**
> Thank you mike555 and oldfred for your replies. I'll try your suggestions and will get back to you.
Hi,

I ran 'sudo grub-install /dev/sda' and I'm, once again, booting from Ubuntu 12.04. I had to go into '/boot/grub/menu.lst' in PCLinuxOS to remove the boot info that immediately follows 'initrd' to get the new install of PCLinuxOS to boot from Ubuntu.
Thank for all of your help.

Regards,

Glen

---

