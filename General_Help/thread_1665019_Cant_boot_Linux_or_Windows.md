---
title: "Cant boot Linux or Windows"
date: 2011-01-11
forum: General Help
---

### Post by 1492 on 2011-01-11
I can't boot Ubuntu or Window 7 on my computer. Here is what happens when I try to start my computer, this is what I get:
[P1010028 (COPY).jpg]("http://ubuntuforums.org/attachment.php?attachmentid=180788&stc=1&d=1294790454")

It then restarts and does the same thing.

I tried plugging an ethernet cable into the computer and then my printer. This is what I got:

                      [IMG]http://ubuntuforums.org/images/attach/jpg.gif[/IMG]     [P10]("http://ubuntuforums.org/attachment.php?attachmentid=180786&stc=1&d=1294790454")

Right now I am using a Live CD. How do I fix this? Any advice is really appreciated. I am not sure if there is any other info I need to give, so please let me know if I need to add anything.

The last thing I did was setup my printer on Ubuntu, restart the computer, boot Windows 7, then later when I tried to reboot, this is what happened.

---

### Post by khamil8686 on 2011-01-11
i googled the error that came on screen and got 2 posts on ubuntuforums about the error and it seemed they had bootloader problems, the first post they tried booting from a live cd and running sudo update-grub2 (sudo update grub if lubuntu uses grub1 instead of grub2) and then another post i came across was marked solved and they said they used the windows 7 install cd to repair an installation and that solved the problem (im assuming they had to boot into a live cd and reinstall grub though) hopefully this helps :)

---

### Post by 1492 on 2011-01-11
Thank you, I hadn't even thought of looking it up on google. However, I can't find the Windows 7 install CD (I'm not sure if I even have it). I did find several other CD's including one called "device drivers, diagnostics, and utilites". I also have the CD's for Windows XP, but it's not installed on the computer. Would either of these help? I also put in ```
sudo update-grub2
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
```

---

### Post by 1492 on 2011-01-12
Bump

---

### Post by 1492 on 2011-01-12
There is something called "grub-rescue-pc". Would this fix the problem?

---

### Post by oldfred on 2011-01-12
Your BIOS is not booting from the hard drive and just going to the next device on the list which is boot from Internet.

If you want specific advice, post the details of your system:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

Otherwise you can reinstall a windows boot loader or grub or grub2 which every you need.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

This will boot whatever code is in the partition with the boot flag including windows. Grub does not use boot flag.
Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

---

### Post by 1492 on 2011-01-12
Thank you so much! It's working fine now. I really appreciate it.

---

