---
title: "Restoring Windows 7 bootloader with WUBI"
date: 2010-10-14
forum: General Help
---

### Post by spintriae on 2010-10-14
I have a netbook dual-booting Windows 7 and Ubuntu Netbook Edition via Wubi. Ubuntu crashed on me while I was recording a screencast and I rebooted to find the Windows bootloader no longer works. It simply gives me an error ("cannot load bootfont") for a split second and restarts immediately. I'm able to access the grub menu with a bootable USB drive and access the Wubi partition, but I can't boot Windows, including the Windows recovery partition. I can still boot Ubunutu.

My question is: is there a way to restore the Windows bootloader in Ubuntu? If not, how can I replace it with a grub bootloader and keep my Wubi boot options intact?

---

### Post by bcbc on 2010-10-14
Post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net").

Or at least run it and check whether it finds "Windows" in the MBR. This sounds pretty strange that it would be damaged by wubi - it's more likely that the windows partition is affected.

But... if you find that the bootloader is damaged, you can install lilo to work the same as the windows bootloader (ignore warnings that refer to using lilo to boot linux):
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

---

### Post by spintriae on 2010-10-14
Attaching RESULST.txt. It says "No errors found in the Boot Parameter Block." Hmm. 

If I install lilo, will I need to reinstall Wubi or will that stay intact?

Thanks,
Casey

---

### Post by bcbc on 2010-10-14
You should not have grub4dos in the MBR. Wubi uses the windows boot manager to boot, and that is loaded via the windows bootloader (or equivalent). So reinstall windows bootloader or lilo as above.

But there are a few weird things - apart from the mystery of how you got grub4dos in the MBR. For example, fdisk believes you have a 3rd partition of type 83 (linux) but blkid doesn't even see this.

---

### Post by spintriae on 2010-10-14
I can't explain what Grub4Dos is doing there. The third partition is encrypted.

I went ahead and installed lilo which got my back into Windows, but bypassed Ubuntu. I used a Windows util called EasyBCD to restore the Windows bootloader with the Ubuntu boot option, but that option doesn't seem to work for me. It just displays "try (hd0,0): NTFS5" (IIRC) for a split second and restarts. Not quite sure what to make of that.

---

### Post by bcbc on 2010-10-14
> **spintriae said:**
> I can't explain what Grub4Dos is doing there. The third partition is encrypted.

I went ahead and installed lilo which got my back into Windows, but bypassed Ubuntu. I used a Windows util called EasyBCD to restore the Windows bootloader with the Ubuntu boot option, but that option doesn't seem to work for me. It just displays "root hda(0,0)" (IIRC) for a split second and restarts. Not quite sure what to make of that.

you should have an entry for wubildr.mbr in the windows boot manager. 

That try hd(0,0) thing is likely wubildr.mbr trying to find wubildr. The rebooting could be a problem with wubildr opening the root.disk or parsing grub.cfg off the root.disk. 

You said before you could boot Ubuntu - did you install something to get it to boot using grub4dos or anything else that might explain how grub4dos got in the bootloader, because reversing this might be the key to get ubuntu booting using the conventional method

---

### Post by spintriae on 2010-10-15
> **bcbc said:**
> you should have an entry for wubildr.mbr in the windows boot manager. 

I do. I have one for C:\ubuntu\winboot\wubildr.mbr and another for C:\wubildr.mbr; neither of which are working.[/QUOTE]

> **bcbc said:**
> You said before you could boot Ubuntu - did you install something to get it to boot using grub4dos or anything else that might explain how grub4dos got in the bootloader, because reversing this might be the key to get ubuntu booting using the conventional method

Yeah, I think I might have accidentally installed it when I initially started troubleshooting the problem about a week ago. I remember running grub shell but I can't remember what I did in it. I also vaguely recall running `sudo grub-install /dev/sda` which I'm pretty sure gave me an error and didn't fix the problem. I was still able to boot Ubuntu though.

> **bcbc said:**
> That try hd(0,0) thing is likely wubildr.mbr trying to find wubildr. The rebooting could be a problem with wubildr opening the root.disk or parsing grub.cfg off the root.disk. 

Yeah, I Googled "try hd(0,0): NTFS5:" and there are a lot of threads on the issue so I'll try plowing through those for now and report back with the results. Thanks again.

---

### Post by spintriae on 2010-10-15
Well I looked through the threads and they seem to be unrelated to my problem. They all seem to be related to an issue where the screen displays "try (hd0,0): NTFS5: no wubildr" while the bootloader scans the harddrive for wubildr and eventually boots upon locating. My problem is a little different.

This is what I'm getting:

> try (hd0,0): NTFS5: _

Then:

> error: unknown command "loadfont".
error: file not found.

Both of these screens are displayed for a split second before the computer immediately restarts. I don't think the problem is with wubildr.mbr since I have two of them and they both have the same problem. So it's either wubildr or root.disk. Any ideas how to fix it?

Edit: it's also worth mentioning that I tried hitting insert to open the grub shell and had no luck.

Also, I updated to the latest kernel a while ago and it never appeared in grub. I opted to look into it later but it slipped my mind. Could there have been some error while installing the kernel that caused all this to happen?

---

### Post by bcbc on 2010-10-15
I haven't seen that specific error: bootfont. Are you sure it wasn't 'loadfont'?

If it's loadfont it points to an incompatibility with the grub.cfg and the wubildr. This symptom of displaying an error and rebooting seems to be the latest grub2/wubi feature. What others have done is to boot a live CD, edit their grub.cfg and remove everything apart from the actual menu entries (delete everything above the first 'menuentry'). Save and reboot. This fixes it as the incompatible commands are above the menuentry paragraphs.

so if you want to try this:
1. boot live CD
2. loop mount wubi root.disk
3. backup grub.cfg
```
sudo cp /mountpoint/boot/grub/grub.cfg /mountpoint/boot/grub/grub.cfg.backup 

```4. edit grub.cfg
```
sudo chmod +w /mountpoint/boot/grub/grub.cfg 
gksu gedit /mountpoint/boot/grub/grub.cfg 
#delete lines above first menuentry.
```
5. save and reboot.

If it doesn't work, you don't lose anything. And if it does work, it doesn't seem like you lose anything because - at least on my computer - deleting all those lines from grub.cfg doesn't make any noticeable difference.

---

### Post by spintriae on 2010-10-15
You're right. It was loadfont.

I did what you said and it worked like a charm. Everything is perfect now. Thank you so much!

---

### Post by bcbc on 2010-10-15
> **spintriae said:**
> You're right. It was loadfont.

I did what you said and it worked like a charm. Everything is perfect now. Thank you so much!

Well it's a workaround :) and if you update a kernel or run update-grub it will regenerate the grub.cfg and you'll have the same problem.

EDIT: you are not obliged to do the following - if you can live with the workaround. 

You are running 10.04.1 and your wubi install is on the same partition as windows, so... you are able to regenerate the wubildr file manually. But... this is an undocumented feature and grub2 is very flaky when it comes to wubi. So we'll take some precautions and back up the wubildr file first.

```
sudo cp /host/wubildr /host/wubildr.backup
sudo grub-install /dev/sda1
sudo update-grub

```
Reboot

Explanation of the commands:
1. backup the wubildr. If this doesn't work you might have to go back to the original (although you see it as /host/wubildr when you boot wubi ubuntu, from windows it's c:\wubildr)
2. use the wubi specific override of grub-install (that only works if wubi is installed to the same partition as windows) to regenerate wubildr.
3. regenerate the grub.cfg you just edited. Note if this fails then you will probably get the same loadfont issue and have to reapply the workaround.

PS avoid the upgrade to 10.10 - it has its own problem that I believe has to do with it creating a bad wubildr.

---

