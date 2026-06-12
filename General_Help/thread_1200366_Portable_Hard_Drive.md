---
title: "Portable Hard Drive"
date: 2009-06-29
forum: General Help
---

### Post by Nova49 on 2009-06-29
I just recently installed ubuntu onto my portable hard drive. I tried to partition the hard drive so ubuntu would only take up half but that did not work. Although it did work when I said take up the whole drive. Also the hard drive doesn't show up any more in either Vista, Windows 7 or Ubuntu. 
So my first question is how do I make it so the hard drive shows up again.

My second question is the one that is pretty much why I'm here. When my portable hardrive is not connected my computer will not boot. I just get Grub error 15,16,17 or 21. I only have ubuntu on my portable and I have vista and 7 on my computer C: drive. So basically with out the portable nothing works. With the portable everything works. If you need any more information about the topic just ask and thanks for the help.

---

### Post by t4thfavor on 2009-06-29
The bootloaader is installed on the disk inside your pc, while everything else is on the portable. I recommend resizing your wondows partition, and installing to your internal disk. You will not be able to see the Linux partition on the portale due to the fact that it is ext3 file system, and windows cannot read it (another reason to install to the internal)

---

### Post by synapsys on 2009-06-29
First off, the hard drive won't 'show up' in windows 7 or vista because windows os' deny the existence of anything other than windows. Your external won't 'show up' in ubuntu because you used the entire drive for the ubuntu installation. Therefore, there is no more room left to 'store files'.

Secondly, Grub needs to read /boot/grub/menu.lst which is located in your ubuntu installation. This cannot be done if the hard drive that contains /boot/grub/menu.lst is not attached. It seems to me that you should let windows rewrite the mbr with it's own boot loader and plug the external in when you want to use ubuntu. Or leave the external plugged in all the time.

---

### Post by Nova49 on 2009-06-30
For right now the only reason I needed ubuntu on a portable drive was so I could boot my mom's computer with it. Something became corrupted and now it doesn't boot windows. As soon as that is done ill move ubuntu back onto my hard drive.

Also how do you make it boot on other computers. I tried going into the bios and booting it from there but nothing happens. Does it have to do with the same file that only allows to boot on my desktop.

---

### Post by t4thfavor on 2009-06-30
Never tried it that way, but it sounds like the same issue. When you get installed back to your regular hdd, go to system -> Administration and click on USB Startup Disk Creator. This will make a fully bootable usb disk (even out of a 1+GB thumb drive) which is much nicer than lugging around a big fat spinning disk.

Thats the proper way to handle it.

---

### Post by Nova49 on 2009-06-30
So I have to do what you said and reinstall ubuntu. The problem is that I still have the issue were the computer wont boot with out the portable and if I dump the portable my computer wont boot.

---

### Post by Nova49 on 2009-06-30
I'm just wondering is there just a file that I have to move or something I have to download because I want this to be fixed with out to much messing around with files

---

### Post by t4thfavor on 2009-06-30
Your PC will boot if you reinstall ubuntu. It only "wont boot" the way you have it now. No there is no file you can move. It was a bad idea to install a portable drive as your main system, and now you know that, Its how we all learn.

I once lost all my wife's pictures (from her whole digital life including the honeymoon) and nearly died, now I take backups, and have spare copies of everything. You gotta bleed a little before you learn.

(I got them back by putting the hdd in the freezer at work for a few hours)

If you need anything else, we will always be here.
Good luck

---

