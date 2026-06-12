---
title: "Installing Win7 alongside a Ubuntu partition"
date: 2012-01-19
forum: General Help
---

### Post by Rodayo on 2012-01-19
I'm trying to install windows 7 on my laptop which has 11.10. 

I used gparted to create 40GB extended partition.

I made a win7 usb and when I get the step that lets you choose which partition you want to install it on I select the 40GB one and it gives me an error message:
"Setup was unable to create a new system partition or locate an existing system partition"
And to clarify the 40GB one appeared as an "Extended" partition and the 420Gb one appeared as "System".

I also tried creating the 40GB partition as "Primary" but that give me the same error...

Here's a screenshot of what gparted looks like:(this was after the win7 installation failed, and I also formatted it in that setup so that's why it's formatted in ntfs)

[IMG]http://i.imgur.com/DKKka.png[/IMG]


Has anyone else had success installing win7 next to ubuntu? How did you do it?

---

### Post by xyzzyman on 2012-01-19
Windows has to be installed in a primary partition. It doesn't have to be the first, but it can't be in an extended.

---

### Post by oldfred on 2012-01-19
Besides being a primary NTFS partition it must also have boot flag. In Windows the boot flag is the active partition, so if it sees the active partition as Linux formated it does not know what to do. 

Grub does not use boot flag, Lilo does, Windows has to have it to boot or make repairs and a few BIOS want a boot flag on a primary partition to boot anything (assumes Windows?).

---

### Post by Rodayo on 2012-01-19
> **oldfred said:**
> Besides being a primary NTFS partition it must also have boot flag. In Windows the boot flag is the active partition, so if it sees the active partition as Linux formated it does not know what to do. 

Grub does not use boot flag, Lilo does, Windows has to have it to boot or make repairs and a few BIOS want a boot flag on a primary partition to boot anything (assumes Windows?).

Thank you I will try this and get back to you =]

---

### Post by alphacrucis2 on 2012-01-19
Don't forget that installing Windows will also blow away the GRUB MBR so you will have to reinstall grub using a live CD once the Windows is complete.

---

### Post by Rodayo on 2012-01-19
> **oldfred said:**
> Besides being a primary NTFS partition it must also have boot flag. In Windows the boot flag is the active partition, so if it sees the active partition as Linux formated it does not know what to do. 

Grub does not use boot flag, Lilo does, Windows has to have it to boot or make repairs and a few BIOS want a boot flag on a primary partition to boot anything (assumes Windows?).

This didn't work =/

I formatted the 40Gb partition as a primary NTFS partition and set the 'boot' flag. 

Over in the windows installers it showed up as a "System" partition whereas before it was "Primary". But I had the same error message when I tried to continue with the installation.

---

