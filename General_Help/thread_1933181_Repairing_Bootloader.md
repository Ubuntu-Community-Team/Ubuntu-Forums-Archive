---
title: "Repairing Bootloader"
date: 2012-02-28
forum: General Help
---

### Post by mcgrandlej on 2012-02-28
I have worked my way into a situation where it seems that I have numerous different bootloaders and was hoping somebody could help me fix it. I have searched around on here and on google and tried different solutions but it has only made my problem worse. 

Heres what happened:
[LIST=1]
[*]I had an installation of Windows 7
[*]I installed backtrack 5 in a blank partition and dual booted the two
[*]From within Backtrack, I installed BURG and had that working fine
[*]I booted into Windows, and deleted my Backtrack installation (not the best way to do it I know)
[*]I installed Ubuntu in a new partition created by the installer
[*]After restarting my computer, I was greeted with a grub rescue prompt
[*]I re-installed Backtrack into its old partition to try and repair the boot loader
[*]I then attempted to rebuild the MBR hoping that would solve the problem
[/LIST]

At this point I it would allow me to boot into the OSes. However, I had one screen which would allow me to choose between Backtrack and Windows. If I selected Windows, it would give me another screen giving me the choice between Ubuntu and Windows. Choosing Ubuntu would give me a screen with all three options (Backtrack, Ubuntu, Windows).

I attempted to install BURG and now everything is screwed. I'm using Super Grub to boot me into Ubuntu and Windows.

If anyone can give me some help in returning me computer to just one bootloader, preferably BURG, that would be very very appreciated. Thanks

---

### Post by oldfred on 2012-02-29
I think burg is not maintained anymore and I do not know it.

I suggest this as it can either do minor fixes or run the boot info script so we can see what may be wrong:

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.


Sometimes if system is ok, but grub is the issue this will directly boot so you can repair grub from inside system.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

---

