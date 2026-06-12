---
title: "I need help adding an option to the Grub boot screen"
date: 2009-09-24
forum: General Help
---

### Post by lindhaj on 2009-09-24
Hi,

On a clean hard disk I installed/partitioned as follows:

/dev/hda1        ntfs        Windows 7 RC    flagged as 'boot'
/dev/hda2        ntfs        Windows XP Pro
/dev/hda3        extended
    /dev/hda5    ext3        Ubuntu
    /dev/hda6    linux-swap    Swap space

First I created all the partitions with the Gparted Live CD, then I installed Windows 7, Windows XP and Ubuntu in that order.

Now when I start the computer and the Grub boot screen appears, it only lets me choose between Ubuntu and Windows XP. This is what the menu.lst file says for the XP option:

title        Windows XP
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

How do I add an option that boots Windows 7? I thought the (hd0,0) meant it boots what's on hda1 but apparently it doesn't since that option boots XP and not Win 7. I experimented (yes, I'm a _newbie_!) with copying and pasting the text above so it looked like the text below, but when I restarted the computer and picked my newly created Windows 7 option I only got a blank screen and a few lines that said something about BOOTMNGR (or something) missing.

title        Windows XP
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

title        Windows 7
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1

I hope someone understands my question and can give a fairly detailed step-by-step answer! I'm grateful for any help!

---

### Post by sedawk on 2009-09-24
From my experience:

(hd0,0)=/dev/hda1 (or /dev/sda1)
(hd0,1)=/dev/hda2 (or /dev/sda2)

So what I do not understand is that
(hd0,0) boots XP (from /dev/hda2).

Are you sure you didn't overwrite W7 somehow
when installing XP?

You can mount /dev/hda[12] and check the content
of the file systems.
E.g boot XP, create a file "winxp.txt" on C:\ and
then check if Ubuntu sees that file on /dev/hda1
or /dev/hda2.

---

### Post by lindhaj on 2009-09-26
Thanks sedawk. As you suspected, I had somehow managed to overwrite Windows 7 .... So I reinstalled everything and now have a Grub boot screen where I can choose either Ubuntu or "Windows Vista (loader)". The latter option leads me to the Windows Boot Manager where I can choose between "Windows 7" and "Earlier Version of Windows" (= XP). So now I can at least start everything, but I'd still like to cut the Windows Boot Manager out and just be able to choose between Ubuntu, W7 or XP right there in Grub. Is there a way to do this?

The Windows option in menu.lst now looks like this:

title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

This time I installed XP before W7 so hda1 = XP and hda2 = W7.

Thanks!

---

### Post by oldfred on 2009-09-27
Did you put in the stanza you had before for (hd0,1)?
title        Windows XP
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1

If that does not work it may be because Win7 takes over the dual booting and changes the XP boot. I do not know Win7 but for most windows you can edit the boot.ini for booting. If the grub  XP boot works then look for a boot.ini to eliminate the XP entry.

---

