---
title: "GRUB problems after Windows XP reinstall"
date: 2009-10-01
forum: General Help
---

### Post by lodborg on 2009-10-01
Hi guys,

I have some problems with restoring my GRUB after reinstalling Windows XP Professional which wiped away my Kubuntu 9.04 GRUB. Although I did everything by the book and by every recommendaditon and tutorial I found on the net I still have no luck with this. Here's what i do:

I boot from my Kubuntu live cd and run the following commands as root

```
grub
find /boot/grub/stage1 -------> the result is (hd0,5)
root (hd0,5)
setup (hd0)
```The last command gives me the error 22: No such partition. But the partition is obviously there. I've also tried 

```
grub-install --root-directory=/media/root /dev/sda5
```after mounting the /dev/sda to /media/root but this results in another error - "the file /media/root/boot/grub/stage1 can't be read correctly". I've tried it from the live Kubuntu cd and from a Mint live cd but with the same results.

Do you have any ideas? I will really appreciate any help.

Thanks in advance

---

### Post by pawhtiobo on 2009-10-01
Hi :)
 
I recommend downloading supergrub disk: [COLOR=#008000][www.**supergrubdisk**.org]("http://www.supergrubdisk.org") [/COLOR][COLOR=black]to trying to fix your problem...[/COLOR]
 
See ya...

---

### Post by oldfred on 2009-10-02
If supergrub does not work, it usually will solve most problems. then we need to see your exact configuration. This also helps you understand where things are installed if you are interested.

Download and run this script:

Boot Info Script 0.32 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions
[http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3)
cd to directory saved to:
chmod 755 boot_info_script032.sh
sudo ./boot_info_script032.sh
or  as example if on desktop
sudo bash ~/Desktop/boot_info_script*.sh
creates results.txt in the same directory, post with code tags as it will be long.

---

### Post by lodborg on 2009-10-02
Thanks a lot for the answers. The Super Grub Disk solved my problem perfectly.

Thanks once again.

---

### Post by pawhtiobo on 2009-10-02
Nice :guitar:

---

