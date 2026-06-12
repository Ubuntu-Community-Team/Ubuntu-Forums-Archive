---
title: "Removing linux and grub on duel boot box"
date: 2010-03-22
forum: General Help
---

### Post by Swatfoot on 2010-03-22
Hello and thanks for any help in advance, I've recently installed Vmware on Vista and I am using that to run Linux. I prefer this method over duel booting as I can quickly switch between the two OSes. So here is what I would like to do. 

1) Remove swap partition (not needed).
2) Remove Linux and format partition to NTFS for windows use.
3) Remove Grub.

What I don't want to do.

1) Reinstall Windows Vista (Lots of programs installed).

---

### Post by xodus1 on 2010-03-22
Format both swap and linux partition to ntsf, Boot into windows or boot into recover from windows disc, command prompt type fixmbr. Done no more duel boot and grub gone.

---

### Post by zarthon on 2010-03-22
I am using VMware Workstation the other way though to run windows in Linux mainly because of Linux software raid and also so i can  I can browse, email, and work while windows reboots. It's stable but still must be rebooted more frequently and each time you will have to shutdown or suspend the VM then shutdown and reboot window then restart the vm.

There are also of course other advantages to doing it the other way around. I think it really depends on where you want to use most of your hardware and if it's compatible with linux. Why did you decided to go with linux in windows?.

Anyway good luck! VMware Workstation, ubuntu ,  and windows 7 ( never adopted vista) all totally rock for me.

---

