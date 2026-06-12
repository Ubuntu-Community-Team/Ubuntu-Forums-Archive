---
title: "Error Mounting External Hard Drive"
date: 2012-04-22
forum: General Help
---

### Post by NubNubNublet on 2012-04-22
Guys please help me out here i am completely new to linux and i don't know a thing

I'm getting this error everytime i plug in my external hard drive and trying to mount it:
Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

Could someone please help out here because im really confused of what to do now
the only reason I installed Ubuntu on my Pc was because I had windows 7 as my main Os but then after a while i wanted to install windows xp on another partition on the same hard drive but when i did i could not boot into either XP or 7. Normally there should be a screen that should show you what os you want to boot it in and that dosent even show. Now it is showing because ever since i installed linux it created a new purple boot screen but when i choose windows 7 it would not boot into it, it would just show a black screen.

So what i am trying to do now is backup my data on my hard drive onto my external hard drive and then reinstall windows 7 on the first partition

btw i forgot admins pass for win7 and the disc won't work because i scratched it hard

1 last thing it would be kool if someone could tell me how to make games on windows work for ubuntu

THANK YOU SOOOOOOOOO MUCHHHHHHHHHHHHHHHHHHHH!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by dandnsmith on 2012-04-22
That post shows that you are rather confused.
Could you start by saying what you actually installed, and in which order.
An additional comment about what you were able to boot at each stage would help.

Other than that, the quick solution would be to get another external HDD and backup to that - but do you think you could do a useful data backup if you got the new external drive?

---

### Post by Silent Sam on 2012-04-22
Try to burn a copy of UBCD and boot from it. There should be a program in there to fix your grub menu entries. Theres also a app called Kon-Boot. You can use it to bypass the login screen for Windows (if you can get it to boot again). If that doesn't work you can try to use the "reset pass" or "blank pass" function to reset your admin pass. As for the scratched CD, you could take it to Game Stop and ask them nicely if you could use their "Skip Doctor" or whatever they use to fix scratched CDs.  If you don't want to keep Ubuntu and just want XP and 7, install grub4dos (also in UBCD).

UBCD is basically the "Swiss Army Knife" of recovery and diagnostics disks. A must have for any PC repair kit.
If you cant fix your computer with this thing, you shouldn't be allowed to touch a computer.

Just check out the list of tools listed here.
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

Let me know if any of these ideas work.

---

### Post by NubNubNublet on 2012-04-23
well my problem is that i primarily use windows 7 on my pc as my main partition but i tried to install windows xp on a second partition on my hard drive so that when my computer turns on i could choose wether to boot into xp or 7 but then when i tried to install windows xp on my pc i wasnt able to boot into anything, like  when i turn on my pc all the stuff loads and the screen where it starts booting in with the logo and stuff does not show up it would just be a black screen for eternity with a blinking bar in the top left corner.

So what i decided to do was install ubuntu and mount my hard drive and backup everything onto my external hard drive. well the first time i ever plugged my external drive into my pc onlinux it would work but after that it wouldnt work it would give me an error.

So now i do not know how to get my external hard drive working again

---

### Post by NubNubNublet on 2012-04-23
i do have ubcd but im rather not sure of using it because i have important data on both my pc and external drive and im scared of data loss

---

### Post by dandnsmith on 2012-04-23
Your problem started with trying to install XP after Win7.
XP, like all the M'soft OS is remarkably intolerant as regards installation, and installing an earlier version of Windows after a later will result in loss of the later, unless you take special precautions.

My advice would be to repair the Win7 installation - then you should have a working system which can address the external drive problem.

I have not had to do the repair for Win7, but the advice seems to parallel that for earlier Windows versions, and will, if possible start with the Win7 installation CD or DVD.

If in doubt google for the solution to fixing boot on a Windows7 system.

---

### Post by NubNubNublet on 2012-04-23
Oh yes i know that though everytime  put my windows 7 cd in it says that it is corrupt something like that i think it is because of the scratches on it, ill try borrow a friends

---

