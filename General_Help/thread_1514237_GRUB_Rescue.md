---
title: "GRUB Rescue"
date: 2010-06-20
forum: General Help
---

### Post by aahernan on 2010-06-20
Hello all,

I have an HP HDX18t Laptop. I bought it a couple years ago and it came with Windows Vista. A few months ago I installed Ubuntu on it. Windows Vista was installed on one of the 500GB hard drives - C:\ - and was listed as sda1 in the Grub menu. The recovery was listed as sda2.

Ubuntu was installed on the secondary 500GB hard drive - D:\ - and was listed as sdb1.

I'm selling the computer so I wanted to remove Ubuntu from the computer, and following a guide I found online I deleted the partition it was on. Sure enough that worked, but now I am getting an error as follows when I turn my computer on:

error: no such device: 32e029a9-2d27-....etc
grub rescue >

Does anyone have any idea on how to get around this? Any help would be appreciated as I was planning on turning the computer over to its new owner tomorrow.

Also, I still haven't backed up my personal files(stupid I know) - so I'd like to get back into Vista to take care of that. Then I will just reset it to factory condition.

Thanks in advance,
Allan

---

### Post by aahernan on 2010-06-20
UPDATE: I tried using super grub disk to install grub but when I tried to but from the USB it says that it is a non system disk or disk error. Replace and press any key when ready. Any other ways to do this?

---

### Post by RJ12 on 2010-06-20
Do you have a Windows Disk?

---

### Post by aahernan on 2010-06-20
No CD. I managed to get Super Grub onto a flash drive, and it ran Windows. After I restarted, without the USB stick it went right back to the grub rescue> screen.

What do I need to click in Super Grub to get it to install? All the smiley faces and sad faces make it confusing.

Thanks for the reply,
Allan

---

### Post by JKyleOKC on 2010-06-20
If you have everything you want to save, already copied off, just activate the system restore partition to put the machine back to factory condition. This should restore the original MBR, which will remove the call to grub that's causing your problem.

If that does not work, Windows versions before Vista had procedures to repair the MBR (Master Boot Record) that could accomplish the same thing. I don't use Vista so don't know whether it still has such a capability, though...

---

### Post by RJ12 on 2010-06-20
You should probably use a Windows Vista disk and fix the mbr. First download the CD that NeoSmart provides [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/"). Then you need to put the image on your flash drive, then boot it and get to the command prompt on there

I think the commands to fix it should be

bootrec.exe /fixboot (you may not need this one)
bootrec.exe /fixmbr

If you need any other help don't hesitate to ask :)

---

### Post by aahernan on 2010-06-20
I actually just realized that I don't want to factory reset as that would force me to reinstall a lot of useful programs (Office, Photoshop, etc).

Just to reiterate, I can currently run Windows out of Super Grub Disk. When I remove the usb stick though it goes back to the GRUB error. When I click "Fix Windows Boot" (the command that is supposed to reinstall the MBR) it says I need to select the previous operating system but only shows one file(syslinux) in the options. Clicking that takes me to a screen to select the HD that it is on, after which it only says:

set out device=hd0 etc. etc. flashing cursor for ten minutes. Anyone have any experience using Super Grub?

---

### Post by aahernan on 2010-06-20
Hello RJ12,

I downloaded the Vista ISO you mentioned and put it on a USB stick. When I select the USB stick though at boot-time and select the Vista image it just goes back to the selection screen. (Clicking Default on the UNEtbootin sends it to a blank screen for a second, then back to the Default screen).

---

