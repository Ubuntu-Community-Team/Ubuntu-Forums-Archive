---
title: "Kernel Panic - not syncing : VFS: Unable to mount root as fs on unknown-block (8,1)"
date: 2010-02-06
forum: General Help
---

### Post by ApocoLypTus on 2010-02-06
I was updating my Ubuntu 9.10 Karmic Koala when i decided that i should reboot my computer. All the downloads were done. When i rebooted it booted in normally but when it got into the kernel loading part, Linux-Bzimage and initrd loaded fine, But then Kernel Panic - not syncing : VFS: Unable to mount root as fs on unknown-block (8,1) came up. This is a wubi install also, and i have never had any troubles before.
 
I need some help because i can't enter into Ubuntu and i need to get on it.

---

### Post by ApocoLypTus on 2010-02-06
please help

---

### Post by Brinstar on 2010-02-06
im having the same problem, just installed karmic with wubi, i can still log in with the previous kernel. 

idk whats wrong with the -19 kernel though.

---

### Post by sandkernel on 2010-02-06
Wonder if its just a Wubi problem. I'm running the -19 kernel on a standalone Ubuntu laptop - no issues even with the reboot.

---

### Post by Brinstar on 2010-02-06
[http://ubuntuforums.org/showpost.php?p=8766173&postcount=4](http://ubuntuforums.org/showpost.php?p=8766173&postcount=4)

---

### Post by ApocoLypTus on 2010-02-06
> **Brinstar said:**
> [http://ubuntuforums.org/showpost.php?p=8766173&postcount=4](http://ubuntuforums.org/showpost.php?p=8766173&postcount=4)

Thank you, i will try it.

e/ i have just tried it, i downloaded the patch. Put it in my c:\Ubuntu\winboot folder, overwrited the old one and rebooted. I then proceeded to edit my grub. i pressed e > Removed insmod ntfs. Pressed crtl+x and booted into my Ubuntu kernel. It came up with the same error and it did not work.

---

### Post by Brinstar on 2010-02-06
just copy the downloaded wubidlr file into C:\

it worked for me 1st time, im on the new kernel now.

---

### Post by ApocoLypTus on 2010-02-06
> **Brinstar said:**
> just copy the downloaded wubidlr file into C:\

it worked for me 1st time, im on the new kernel now.

Okay so i dont have to remove anything like on grub?

Okay so i dont have to remove anything like on grub?

e/ Didn't work. Didn't remove anything and still didn't work. Would it have to do that im on a 64-bit computer?

---

### Post by Brinstar on 2010-02-06
> **ApocoLypTus said:**
> Okay so i dont have to remove anything like on grub?

Okay so i dont have to remove anything like on grub?

e/ Didn't work. Didn't remove anything and still didn't work. Would it have to do that im on a 64-bit computer?

i didnt have to remove anything, and im on 64bit also

literally ALL i did was copy the NEW wubidlr into "C:\" on the main Windows drive and it worked

you might want to try doing a "sudo update-grub2" to see if that helps.

just to make sure, you are doing the copy/move from Windows, right? if not, you should be.

---

### Post by ApocoLypTus on 2010-02-06
> **Brinstar said:**
> i didnt have to remove anything, and im on 64bit also

literally ALL i did was copy the NEW wubidlr into "C:\" on the main Windows drive and it worked

you might want to try doing a "sudo update-grub2" to see if that helps.

just to make sure, you are doing the copy/move from Windows, right? if not, you should be.

It worked! I put it in the wrong folder. I put it in the Ubuntu folder. Not my main c: Drive.

---

### Post by Crews06 on 2010-02-07
I am having the same problem. 

I installed it on my computer and everything works fine.

i installed it on my girlfriends computer and the wireless wouldn't pick up so i had to go to hardware drivers and install the wireless card?! 

i did a bunch of stuff before that in the terminal but not exactly sure what i did!!!

the wireless started working and then i rebooted to make sure it worked and got this same error.

Can you walk me through how you fix it please?!??!?!?

---

### Post by Crews06 on 2010-02-07
I cant even boot into ubuntu.. how do you install something if you cant boot?! i am completely lost.

---

### Post by ApocoLypTus on 2010-02-07
> **Crews06 said:**
> I cant even boot into ubuntu.. how do you install something if you cant boot?! i am completely lost.

Go on Windows Vista. And is your install a Wubi? If not i can't help you there.

---

### Post by Crews06 on 2010-02-07
ubuntu is the only OS on the computer.  I dont have windows vista anymore.

---

### Post by icehole on 2010-02-07
same thing here as well.. System was hashing a torrent & then poof cant boot.. the only OS on this is Ubuntu..

---

### Post by ApocoLypTus on 2010-02-07
> **icehole said:**
> same thing here as well.. System was hashing a torrent & then poof cant boot.. the only OS on this is Ubuntu..

Use a live CD. But i don't know what to do for that. Then probably make a thread so some other people can help. Im just a user, not a techie.

---

