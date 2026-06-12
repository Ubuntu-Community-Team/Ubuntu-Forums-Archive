---
title: "Problems with grub and no OS"
date: 2009-11-23
forum: General Help
---

### Post by cgalmrott on 2009-11-23
OK a couple of weeks ago my windows decided to BSD on me. I decided that the only way to get my work off of my hard drive was to boot a Linux distribution from a Live CD and backup my files. So this I did and not having my XP installation disk with me I also installed Ubuntu (9.10 - Karmic). All was going well. This was my first time with a Linux dis and after getting over the "oh my god how does this work" I was quite happy. However I have work due in a weeks time and I really need to use my software - Indesign, Solidworks etc. So with my copy of XP back in possession and no longer in storage I followed the following instructions to remove Ubuntu so I could install XP:

[I]load live CD and run gported under system tools. Click on partition with Linux and press delete. Now right click and create new logical drive and select NTFS. You now have a blank hard disk.

[/I]So this I did and instead of booting up my XP disk I got a grub error. No problem I thought I'll put in Karmic disc instead. Bugger Same problem. Good OS, yep that doesn't work as well. No disc. Same deal.

So this is what I am getting:

[B]boot from CD/DVD...
[/B][I]reads disc and decides there is nothing in the drive
[/I][B]grub loading
error: unknown filesystem
grub rescue>
[/B]
Now what do I do? Ideally I'd like to install XP and maybe install Ubuntu later as a dual boot to continue my explorations. Otherwise I will quite happily install any other OS as long as I can get my machine working!

Please help; it's terrible not having a computer.

---

### Post by snowpine on 2009-11-23
If GRUB is attempting to load, your computer is trying to boot from the hard drive. You need to enter your BIOS options (Esc or one of the F keys on most computers) and change the boot order to boot from the CD drive first.

If your Windows Install CD isn't working properly, I'm not sure Ubuntu Forums is the appropriate place for support (but we'll try our best anyway, because we're friendly like that). :)

---

### Post by cgalmrott on 2009-11-23
> **snowpine said:**
> If GRUB is attempting to load, your computer is trying to boot from the hard drive. You need to enter your BIOS options (Esc or one of the F keys on most computers) and change the boot order to boot from the CD drive first.

I have it booting from the CD/DVD's and it tries the disc and then goes to grub. This works with the Ubuntu disc aswell so is not just the windows one not working. The disk was working like 5 minutes before when I used the Live CD to reformat the hard drive.

---

### Post by snowpine on 2009-11-23
I don't understand how Gparted could modify your BIOS in that way... but I suppose anything is possible. :)

If your CD drive is kaput, another option is to create a Live USB thumb drive (using Ubuntu's 'usb-creator' app or Unetbootin) and try booting from that instead of a CD.

---

### Post by cgalmrott on 2009-11-23
> **snowpine said:**
> I don't understand how Gparted could modify your BIOS in that way... but I suppose anything is possible. :)

If your CD drive is kaput, another option is to create a Live USB thumb drive (using Ubuntu's 'usb-creator' app or Unetbootin) and try booting from that instead of a CD.

I'm not sure if it is the drive or not. Either way I don't have an OS to create a live USB from.

Do you have any idea how I could remove grub without the OS, is there a command that I can type in to the prompt do you know?

---

### Post by snowpine on 2009-11-23
I suppose you could try temporarily disconnecting the hard drive cable, see if the CD will boot without the hard drive? (Obviously you won't be able to install if the drive is disconnected, this is just to troubleshoot the problem booting from your CD drive).

I do not know how to remove grub without the ability to boot from Live CD. However, I really do not thing Grub is the problem here... if your computer will not boot from CD, it is a hardware and/or BIOS problem. If Grub is attempting to load, then boot-from-CD has already failed. :(

---

### Post by Dave_gb on 2009-11-23
I had exactly this when I recently removed Mint off my lappy.

I am running Win 7 on another partition and could not boot into it due to it grinding to a halt at the Grub error.

I booted from the installation DVD and chose the 'repair your computer' option.

I then selected command prompt and typed **bootrec /fixmbr**, pressed enter.

Then I typed **bootrec /fixboot**, hit enter.

Restarted machine and bingo, was able to boot back into Windows.

I believe the process is the same for XP.

Hope you get it sorted.

Dave

---

### Post by Dave_gb on 2009-11-23
Just re-read your post and realise you can not boot xp from the cd. RTFP Dave :)

---

### Post by cgalmrott on 2009-11-23
I shall try disconnecting the hard drive and retry booting from DVD's to see where that gets me. At the moment I am a 1/2 mile from my PC so it shall have to wait. Cheers for the advice though

---

### Post by cgalmrott on 2009-11-23
I'll give disconnecting the hard drive ago and see what happens. I'll also try persevering with the live CD's to see if I can get anything up and running. Cheers for the help

---

### Post by gadolinio on 2009-11-23
> **snowpine said:**
> I suppose you could try temporarily disconnecting the hard drive cable, see if the CD will boot without the hard drive? (Obviously you won't be able to install if the drive is disconnected, this is just to troubleshoot the problem booting from your CD drive).

I do not know how to remove grub without the ability to boot from Live CD. However, I really do not thing Grub is the problem here... if your computer will not boot from CD, it is a hardware and/or BIOS problem. If Grub is attempting to load, then boot-from-CD has already failed. :(

+1 to this opinion...
I can't think of any way of modifying GRUB without an OS either, but if phisically removing the hard disk doesn't let you boot from the live cd... the problem might have something to do with the CD drive or BIOS. In the latter case, maybe you could find some solution by searching in the bios' options (make sure CDROM is still before HDD in the boot order, the CDROM unit is recognized by the computer, etc).

---

### Post by McFarley on 2009-11-23
So unplugging your boot drive didn't resolve the inability to boot from the cd drive?

---

