---
title: "Ntldr is missing after erasing windows and installing ubuntu"
date: 2012-04-30
forum: General Help
---

### Post by strem066 on 2012-04-30
I hope I'm in the right forum but here it goes....

Computer/Laptop in question:HP Compaq 6830s

Let me start off and say that I have been having problems with this  computer and decided to install ubuntu because at the time it was the  only known option available. I should also mention that it was the only  known option available because the cd-rom is presently nonoperational so  the only way to boot anything is from a USB stick.

The computer is presently running the newest version of Ubuntu (12.xxx).  When I installed ubuntu I chose the option to erase windows and install  ubuntu only. I now realize that was not the best option. Ubuntu is fine  but I would rather have some sort of windows operating system so I made  a bootable Windows 7 usb key in order to install Windows 7. This  bootable USB key works fine on my other computer which is a HP Pavillion  A1710n and running Windows XP. However, when I put this USB key in my  laptop I get the "NTLDR file is missing press any key to restart". I  can't access the windows setup at all. I verified all my boot options  and everything is set to USB. I have searched all over the internet but  can't find anything for MY particular situation. I am by no means a  computer gooroo but it seems to me that the NTLDR file is in fact  missing and I need to reinstall it but how can I do that with Ubuntu?

Any help would be appreciated, thanks!

---

### Post by dandnsmith on 2012-04-30
I'd say that you are quite right, and it is looking for ntldr (it being the basic boot program). I'd hazard a guess that it works on the other PC because that has a working XP with its own ntldr.

I think that the problem is with the way the usb stick has been set up - but I've no idea how to correct it, as I've no idea how you created it and what you have on it.

Perhaps someone versed in Windows and its ways can shed light (aren't you in the wrong forums for this?)

---

### Post by oldfred on 2012-04-30
I am not sure where you are getting a ntldr missing error. With Windows 7 it is bootmgr. Are you really booting from the Windows installer or do you still have an NTFS partition with boot flag and with XP in the PBR?

I ran Windows 7 repair USB chkdsk on my XP (did work better than XP's chkdsk) but it wrote a Windows 7 PBR - partition boot sector that referred to bootmgr not ntldr.

If you have just installed Ubuntu the entire drive is Linux format and Windows does not see Linux formated partitions correctly.

For Windows to install you need either unallocated space with an available primary partition or a NTFS formated primary partition (sda1 thru sda4) with the boot flag (active partition in Windows).

---

### Post by strem066 on 2012-04-30
> **oldfred said:**
> I am not sure where you are getting a ntldr missing error. With Windows 7 it is bootmgr. Are you really booting from the Windows installer or do you still have an NTFS partition with boot flag and with XP in the PBR?

I ran Windows 7 repair USB chkdsk on my XP (did work better than XP's chkdsk) but it wrote a Windows 7 PBR - partition boot sector that referred to bootmgr not ntldr.

If you have just installed Ubuntu the entire drive is Linux format and Windows does not see Linux formated partitions correctly.

For Windows to install you need either unallocated space with an available primary partition or a NTFS formated primary partition (sda1 thru sda4) with the boot flag (active partition in Windows).


I was trying to install Windows XP previously before I realized I only had an update version and not the full version, Maybe that has something to do with it...

---

### Post by strem066 on 2012-04-30
Here's what I'm gonna do. I'm gonna get a full version of xp and install  it (since that's as close as i came to installing windows). After I'll  upgrade to xp with the other version I have...hopefully this works. I'll  keep you guys posted.

---

### Post by strem066 on 2012-04-30
> **strem066 said:**
> Here's what I'm gonna do. I'm gonna get a full version of xp and install  it (since that's as close as i came to installing windows). After I'll  upgrade to xp with the other version I have...hopefully this works. I'll  keep you guys posted.

Problem fixed. I did what is listed above. Thanks for all the help folks!

---

