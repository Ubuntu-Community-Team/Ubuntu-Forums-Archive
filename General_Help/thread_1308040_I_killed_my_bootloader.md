---
title: "I killed my bootloader"
date: 2009-10-31
forum: General Help
---

### Post by Oblivion_4 on 2009-10-31
Hi Everyone!
I recently upgraded to 9.10 and can no longer start ubuntu or xp on my dual boot. Let me explain. Prior to upgrading to 9.10 I decided that I was going to upgrade to grub2 and change my filesystem to ext4. So I did and that worked successfully. However during my upgrade to 9.10 I was asked if I wanted to upgrade my bootloader, and having upgraded to grub2 I decided not too. BIG MISTAKE! This move inadvertantly stripped grub2 from my system and left me with a non-operational version of grub that can no longer boot into ubuntu or XP.

I would like to know what my options are to solve this problem. I think I may have to reinstall grub2, but I have no idea how to do that from a LiveCD. Can anyone help me?

---

### Post by razorboy5 on 2009-10-31
i think this might help

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

or 

[http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore](http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore)

i did it this way to restore grub back on jaunty however i think it should be similar if not same for karmic...?

---

### Post by Oblivion_4 on 2009-11-01
ok some new developments, neither of the two links posted by the previous user helped at all. When I try to run the command setup in the grub terminal or the grub rescue terminal I recieve the message "command not found" when I install grub with apt-get on the liveCD and try setup (hd0,5) or (hd0) I recieve the message "Error 17: cannot load selected partition"

Also I found a way to load my kernel as well as initrd.img but when I try to boot from there I am given a initramfs terminal and can only run programs that are located in /bin Is there any way to get to gnome from the initramfs shell so that I can use apt-get to do everything for me. 

ALSO, I think the information razorboy gave me is a little outdated because before I install grub on the livecd if I do "grub-install -v" the version is listed as 1.97 but after I install grub using apt-get "grub-install -v" the versin is listed as 0.97 something. Anyway can someone point me to a more recent tutorial or a way to install grub2 from a liveCD?

---

### Post by Oblivion_4 on 2009-11-01
I must apologize to you razorboy5. The first link that you posted here [http://ubuntuforums.org/member.php?u=869127](http://ubuntuforums.org/member.php?u=869127) worked and I can now boot into 9.10 thanks alot

---

