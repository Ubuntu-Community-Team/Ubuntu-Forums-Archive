---
title: "Can't start Windows 7 from GRUB"
date: 2010-09-26
forum: General Help
---

### Post by AlabamaRoy on 2010-09-26
My Ubuntu/Windows 7 dual-boot config worked fine until I foolishly allowed Ubuntu to install updates. It replaced Windows 7's boot loader with GRUB, and now I can't start Windows 7. No matter what I do, I wind up on a blank screen with nothing but a mouse cursor. I can't even boot from my Windows 7 recovery CD--it does the same thing! 

Everything was perfect with Windows 7 until Ubuntu changed the boot loader. I hate Ubuntu and I want my Windows 7 back. Any ideas? I'm so tired of this problem!

:confused:

---

### Post by grahammechanical on 2010-09-26
When you install Ubuntu or any Linux distribution it will always put a boot loader in the MBR (Master Boot Record). When you update the Operating System then GRUB will also be updated if the Ubuntu kernel is being updated. This is standard practice.

Did you by any chance install Windows 7 after installing Ubuntu? You mention the windows boot loader. Does Windows allow for a dual boot of different Operating systems? Or, only MS operating systems? Interesting?

I have updated Ubuntu several times. I have more than one OS on the Hard disc, each is in its own partition. They are Ubuntu installations that I use for testing. I have yet to have the update process fail to recognise these other Operating Systems and place them in the boot loader menu. I cannot understand how a Ubuntu kernel update (which would require an change in the GRUB menu) would fail to find a Windows 7 installation on the hard disc and set up the boot loader to do its job correctly.

I think that you have done something that you are not telling us?

Regards

---

