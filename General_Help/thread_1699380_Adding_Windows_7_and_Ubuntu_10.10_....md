---
title: "Adding Windows 7 and Ubuntu 10.10 ..."
date: 2011-03-03
forum: General Help
---

### Post by matamoscas on 2011-03-03
I have a working 10.04 Ubuntu, that I have been using for the past year or so. I have been very happy with it.

But, I just picked up a new HDD as I want to install Windows 7 (merely for testing purposes), and the latest Ubuntu 10.10, also for testing purposes.

I know I should install the Windows before the Ubuntu (that has always been easier).  

I also know, I could simply disconnect the HDD (old one) and have no problems. =)

My question is:

If I throw in the other HDD, install Windows, and then install Ubuntu...

How will my original bootloader, on my main hard drive recognize the two new systems? Will it somehow do this automatically?  

What do I need to do to coordinate this efficiently?

I like to try to think one step ahead =)

Thanks, have a great week!

---

### Post by YesWeCan on 2011-03-03
On your original Ubuntu you just do 'sudo update-grub' and it should scan the new HDD and add its OSes to your boot menu.

---

### Post by matamoscas on 2011-03-03
Ah cool Thanks a bunch!

---

### Post by BHEJU on 2011-03-03
If you want to install win-7 just for testing.. I suggest you use Virtual set-up (either VirtualBox or VMWare or ....).
So that even if you crash it, it's easy to fix.
However, if you know you want to dual-boot then, If its no big issue, I would suggest you wipe the HD and install win7 first (unless you are exp in UBUNTU) as you will need to tweak bootloader manually.

Cheers

---

### Post by 3Miro on 2011-03-03
Check with your BIOS. Every HDD has a separate boot-loader and a newer BIOS would have a way to select "boot priority for HDD". I used to have a "dual-boot" setup, where I would select between Linux and Windows by picking a different HDD at boot form the BIOS.

In your case:
- disconnect the old HDD
- install Windows 7
- install Ubuntu 10.10
- connect the old HDD and this should get you to either the old Ubuntu 10.04 or the new 10.10
- in either case, you can just run:
```
sudo update-grub
```
and on the next reboot all entries for 10.04, 10.10 and Windows 7 should appear.

Keep in mind which HDD boots after you reconnect both. You will be using either Grub from 10.10 or 10.04, if you later erase that version of Ubuntu, you may run into some trouble.

---

### Post by matamoscas on 2011-03-05
> **3Miro said:**
> Check with your BIOS. Every HDD has a separate boot-loader and a newer BIOS would have a way to select "boot priority for HDD". I used to have a "dual-boot" setup, where I would select between Linux and Windows by picking a different HDD at boot form the BIOS.

In your case:
- disconnect the old HDD
- install Windows 7
- install Ubuntu 10.10
- connect the old HDD and this should get you to either the old Ubuntu 10.04 or the new 10.10
- in either case, you can just run:
```
sudo update-grub
```
and on the next reboot all entries for 10.04, 10.10 and Windows 7 should appear.

Keep in mind which HDD boots after you reconnect both. You will be using either Grub from 10.10 or 10.04, if you later erase that version of Ubuntu, you may run into some trouble.

Yeah this is what I did, and it worked like a charm!

I also had to go into the BIOS to change the boot order of the two drivers, as the newer one had priority =)  But, otherwise, it was a lot less painful than it could have been. I guess I have already walked a lot of those painful paths before =) So, I knew what to be aware of.

thanks again.

---

### Post by Mark Phelps on 2011-03-05
> **BHEJU said:**
> If you want to install win-7 just for testing.. I suggest you use Virtual set-up (either VirtualBox or VMWare or ....)

Disagree ... If you really want to test something, not just experiment with it, you need to be using it in its native environment.

If something fails, or if something fails to work properly or efficiently, how will you know if it's really a Win7 problem, or a complication due to using Virtualization?

You probably won't.

Plus, virtualization, unless you have LOTS of memory, is going to be slower than using it in native mode.  So, you won't get a feel for real-time performance.

---

