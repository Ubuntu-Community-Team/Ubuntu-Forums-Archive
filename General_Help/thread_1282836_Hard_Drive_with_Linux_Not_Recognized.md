---
title: "Hard Drive with Linux Not Recognized"
date: 2009-10-04
forum: General Help
---

### Post by LarryXIII on 2009-10-04
I recently installed Xubuntu, since I already burned it for another computer, but it will no longer post. So I just took the hard drive and installed Xubuntu on the hard drive for my computer.Everything ran smoothly when I installed, but when replugged in my Windows hard drive with Xubuntu running, cause I wanted some files, like music, pictures, etc. Xubuntu did not recognize the hard drive. When I restarted, since I installed some updates, I did not have a bootloader. So I thought okay, so I continued and Windows did not recognized the hard drive at all. Does anyone have a fix for this? I don't want to constantly pull and replug my SATA cable just so I can run Linux, especially since I'm thinking of putting the hard drive in the case.

---

### Post by jaxxstorm on 2009-10-04
> **LarryXIII said:**
> I recently installed Xubuntu, since I already burned it for another computer, but it will no longer post. So I just took the hard drive and installed Xubuntu on the hard drive for my computer.Everything ran smoothly when I installed, but when replugged in my Windows hard drive with Xubuntu running, cause I wanted some files, like music, pictures, etc. Xubuntu did not recognize the hard drive. When I restarted, since I installed some updates, I did not have a bootloader. So I thought okay, so I continued and Windows did not recognized the hard drive at all. Does anyone have a fix for this? I don't want to constantly pull and replug my SATA cable just so I can run Linux, especially since I'm thinking of putting the hard drive in the case.

Right ok, I'm a little confused with your post, but I'll attempt to help.

You had a computer, the computer stopped posting and and you removed the hard drive and installed Xubuntu.

Then, once you'd installed xubuntu, you added another hard drive with windows and while the computer was running (can you confirm this is what you did?) and the hard drive wasn't detected?

[I]If this is the case, its because hard drives aren;t hot swappable (unless you have some fancy server, which I'm assuming you don't!) Your motherboard + BIOS will have a hard time detecting a SATA or IDE hard drive while the computer is running
[/I]

then you installed some updates, which you say killed your bootloader?

*This is unlikely, I'm not aware of any updates that would damage GRUB. Chances are, adding the Windows hard drive means the bootloader has been hidden behind the windows partition's bootloader. Window's bootloader doesn't "do" detecting linux. You need to reconfigure your hard drive so that the primary one is Xubuntu's, then the secondary one is Windows. That way, you can then configure GRUB to detect windows*

Then once you booted into windows, your Linux hard drive wasn't detected

*Again, this is a Windows issue. Linux uses a different file system to Windows, and windows refuses to detect it. Fortunately, there are plugins for linux which mean Linux can detect window filesystems.*

What I would suggest is the following.

Check your hard drives and make sure they're jumpered correctly. Ensure the Linux hard drive is primary master, and the windows one is primary slave. This will get you in a situation where you can boot into Linux but not windows. Then edit your grub menu.lst to include Windows, allowing you to dual boot.

I hope I got the jist of your problem, and I hope this helps

---

### Post by LarryXIII on 2009-10-04
Sorry about making it hard to understand. You got most of it correct, but I installed Xubuntu, then I tried to plug in my SATA HDD to get some files and it didn't show it. I think that's the only thing you didn't understand correctly. And thanks, I'll see how to set the IDE HDD to Primary Master on my Mobo.

---

