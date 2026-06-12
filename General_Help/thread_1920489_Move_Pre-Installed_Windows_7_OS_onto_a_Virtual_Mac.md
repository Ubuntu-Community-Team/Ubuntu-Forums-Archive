---
title: "Move Pre-Installed Windows 7 OS onto a Virtual Machine"
date: 2012-02-04
forum: General Help
---

### Post by sideffects on 2012-02-04
Is it possible to do this, or am I screwed? I called Microsoft, and the nice lady told me that I could purchase a product key for Windows 7 for $200.

---

### Post by sefs on 2012-02-04
> **sideffects said:**
> Is it possible to do this, or am I screwed? I called Microsoft, and the nice lady told me that I could purchase a product key for Windows 7 for $200.

Sounds like you have an OEM version there, which means that legally you would be out of luck, as I don't believe the OEM licenses are transferable from machine to machine.  I am pretty sure they are only legitimate for the computer they were initially installed on.

p.s.
You could probably read this thread 
[http://www.sevenforums.com/windows-updates-activation/74832-help-need-transfer-oem-win-7-key-new-machine.html](http://www.sevenforums.com/windows-updates-activation/74832-help-need-transfer-oem-win-7-key-new-machine.html) to see why it won't work that way.

---

### Post by sideffects on 2012-02-04
> **sefs said:**
> Sounds like you have an OEM version there, which means that legally you would be out of luck, as I don't believe the OEM licenses are transferable from machine to machine.  I am pretty sure they are only legitimate for the computer they were initially installed on.

p.s.
You could probably read this thread 
[http://www.sevenforums.com/windows-updates-activation/74832-help-need-transfer-oem-win-7-key-new-machine.html](http://www.sevenforums.com/windows-updates-activation/74832-help-need-transfer-oem-win-7-key-new-machine.html) to see why it won't work that way.

Yes, it's OEM. That bites. Thanks for the help!

---

### Post by xyzzyman on 2012-02-05
From MS Windows 7 End-User License:

> "(3.d) Use with Virtualization Technologies. 
Instead of using the software directly on the licensed computer, you may install and use the software within only one virtual (or otherwise emulated) hardware system on the licensed computer. When used in a virtualized environment, content protected by digital rights management technology, BitLocker or any full volume disk drive encryption technology may not be as secure as protected content not in a virtualized environment. You should comply with all domestic and international laws that apply to such protected content."

You can use any Windows 7 install DVD. You may have to skip entering the serial key, and enter & activate it once it's installed and you're in Windows (Using the serial key on the COA on your system.)

Another option (I haven't tried it myself) is to use the free utility VMware vCenter converter. It converts physical installs to virtual installs. [http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/) VirtualBox supports VMWare images so don't worry about that.

---

### Post by sideffects on 2012-02-05
> **xyzzyman said:**
> From MS Windows 7 End-User License:



You can use any Windows 7 install DVD. You may have to skip entering the serial key, and enter & activate it once it's installed and you're in Windows (Using the serial key on the COA on your system.)

Another option (I haven't tried it myself) is to use the free utility VMware vCenter converter. It converts physical installs to virtual installs. [http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/) VirtualBox supports VMWare images so don't worry about that.

I have the VMWare converter installed, but it only converts up to Vista. My issue is, that I don't have an install disk, only what's on my system. I tried to download a digital image, but the Microsoft store won't let me download it for free

---

### Post by xyzzyman on 2012-02-05
[http://lifehacker.com/5832896/download-windows7-isos-to-reinstall-without-restoring-your-system](http://lifehacker.com/5832896/download-windows7-isos-to-reinstall-without-restoring-your-system)

And page 20 of the manual says Windows 7 is supported. [http://www.vmware.com/pdf/convsa_50_guide.pdf](http://www.vmware.com/pdf/convsa_50_guide.pdf)
Are you using the newest version?

---

### Post by sideffects on 2012-02-05
> **xyzzyman said:**
> [http://lifehacker.com/5832896/download-windows7-isos-to-reinstall-without-restoring-your-system](http://lifehacker.com/5832896/download-windows7-isos-to-reinstall-without-restoring-your-system)

And page 20 of the manual says Windows 7 is supported. [http://www.vmware.com/pdf/convsa_50_guide.pdf](http://www.vmware.com/pdf/convsa_50_guide.pdf)
Are you using the newest version?

You are awesome. Thanks for the links!

---

### Post by xyzzyman on 2012-02-05
> **sideffects said:**
> You are awesome. Thanks for the links!

If you do wind up using VMWare converter post back here if it works and what if any quirks you experience.

---

### Post by wildmanne39 on 2012-02-05
Hi, be careful you might end up with a none bootable system and no way to reinstall.

---

### Post by xyzzyman on 2012-02-05
> **wildmanne39 said:**
> Hi, be careful you might end up with  a none bootable system and no way to reinstall.

Why is that? He could just use his recovery disks... Plus I don't believe it wipes out the original, you have to do that yourself.

---

### Post by sefs on 2012-02-05
Will the OEM he has after vmware converter detect the VM as "new" hardware?

I am curious to know if this works.  Keep us in the loop.

Thanks.

---

### Post by Mark Phelps on 2012-02-05
> **sefs said:**
> Will the OEM he has after vmware converter detect the VM as "new" hardware?

YES ... it will detect is as "new" -- which is why when folks have tried to use a VM to point to their existing install, it allways required reactivation.

---

### Post by sefs on 2012-02-05
> **Mark Phelps said:**
> YES ... it will detect is as "new" -- which is why when folks have tried to use a VM to point to their existing install, it allways required reactivation.

If it does he'll never be able to activate it legally in the VM then since it's OEM.  I don't think OEM's are transferable between systems.

---

### Post by xyzzyman on 2012-02-05
> **sefs said:**
> If it does he'll never be able to activate it legally in the VM then since it's OEM.  I don't think OEM's are transferable between systems.

It's legal on the same computer to move it into a VM install. As I previously posted it's right in the EULA.

> "(3.d) Use with Virtualization Technologies. 
Instead of using the software directly on the licensed computer, you may install and use the software within only one virtual (or otherwise emulated) hardware system on the licensed computer. When used in a virtualized environment, content protected by digital rights management technology, BitLocker or any full volume disk drive encryption technology may not be as secure as protected content not in a virtualized environment. You should comply with all domestic and international laws that apply to such protected content."

---

### Post by haqking on 2012-02-05
i clone physical images into VM all the time.

clonezilla

The issues you are likely to encounter are legal, if it was OEM then technically if the VM is on the same machine then its legal

If your do it to a VM on different hardware then thats different.

Legal issues aside, you can clone a physical to virtual machine.

---

### Post by Mark Phelps on 2012-02-06
With an OEM version, activation is generally handled automatically by code buried in the BIOS.  Whether or not that same code will work with a VM installation, I do not know.

If it does work, as long as you only clone the physical install into a VM -- and then ERASE the physical install, you are living withing the terms of the EULA.  

And, with the physical install gone, you shouldn't have to worry about reactivation later.

---

### Post by sideffects on 2012-02-06
> **Mark Phelps said:**
> With an OEM version, activation is generally handled automatically by code buried in the BIOS.  Whether or not that same code will work with a VM installation, I do not know.

If it does work, as long as you only clone the physical install into a VM -- and then ERASE the physical install, you are living withing the terms of the EULA.  

And, with the physical install gone, you shouldn't have to worry about reactivation later.

Will I be able to erase the physical install safely if I am dual booting right now?

---

### Post by xyzzyman on 2012-02-06
> **sideffects said:**
> Will I be able to erase the physical install safely if I am dual booting right now?

If you are using grub then most likely yes. The problem will be if you delete the partition instead of just formatting it, it could change your partition #'s which might be an issue. I would just format it as NTFS if I was getting rid of the install and leave it open as a storage partition.

---

### Post by Mark Phelps on 2012-02-06
> **sideffects said:**
> Will I be able to erase the physical install safely if I am dual booting right now?

You SHOULD be able to do this from inside Ubuntu -- as it does not use the Windows partitions.

But BEFORE you do that, if you even think about ever needing your Win7 install back in the future, you should consider imaging it off to an external drive.  That way, if the VM migration fails down the road, you can still get your working Win7 back.

If you're interested in doing this, read below:

Macrium Reflect (MR) provides a FREE version that can be used to image and restore partitions or entire drives.

To do this, download the FREE version from their website and install it in MS Windows.

Then, use the option to create and burn a Linux Boot CD.  This will provide you a means of booting and restoring MS Windows later.

Then, use MR to image off the Win7 OS partition (and if there is a boot partition, that as well) to an external drive.

NOW, you have the ability to restore Win7 to its current state, and unlike with the Recovery option, you won't have to reinstall any of your apps.

---

### Post by sideffects on 2012-02-06
> **Mark Phelps said:**
> You SHOULD be able to do this from inside Ubuntu -- as it does not use the Windows partitions.

But BEFORE you do that, if you even think about ever needing your Win7 install back in the future, you should consider imaging it off to an external drive.  That way, if the VM migration fails down the road, you can still get your working Win7 back.

If you're interested in doing this, read below:

Macrium Reflect (MR) provides a FREE version that can be used to image and restore partitions or entire drives.

To do this, download the FREE version from their website and install it in MS Windows.

Then, use the option to create and burn a Linux Boot CD.  This will provide you a means of booting and restoring MS Windows later.

Then, use MR to image off the Win7 OS partition (and if there is a boot partition, that as well) to an external drive.

NOW, you have the ability to restore Win7 to its current state, and unlike with the Recovery option, you won't have to reinstall any of your apps.

Okay, that sounds like a great idea. Thanks! Follow up question, is it possible to back up all of my Ubuntu files and settings as well, and then format my system? Lenovo created a TON of random backup/restore partitions which made it very difficult to install Ubuntu in the first place. I would like to clean those up. I would also like to use my entire HDD for Ubuntu; whereas, now I have most of my HDD space allocated to Windows. Is there a way to do this safely?

---

