---
title: "How to uninstall Ubuntu from a netbook"
date: 2009-11-12
forum: General Help
---

### Post by Puzzled Guy on 2009-11-12
Hello,
I installed UNR onto my HDD by mistake instead of my external one. I googled for a solution and found this: [http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/](http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/)

It seems to be a good way but the problem is, I have an MSi Wind U100 and that has NO CD drive but I have the CD mentioned in the above article. What I want to know is: Is it possible to burn the file on the Windows CD to a USB stick (kingston datatraveler 8gb)?

Another thing, I will only be using that method to uninstall IF I get confirmation from someone who has tried it him/herself and if it is possible to somehow burn the CD file to a USB stick.

So, anyone who has done this before, please let me know if it will work or not.

PS: I need to uninstall it because the install process went wacko and now there is not even enough space to install updates or anything else("Not enough disk space" error message or something like that)

---

### Post by mikewhatever on 2009-11-12
Uninstalling Ubuntu is easy, first, restore the Windows bootloader, then, just boot from the USB stick and delete the Ubuntu partitions with Gparted. However, it seems like you are also looking at reinstalling Windows, which has nothing to do with Ubuntu. Why don't you elaborate on that.

---

### Post by Puzzled Guy on 2009-11-12
I don't want to remove Windows (not yet anyway). I know how to remove the Ubuntu partitions but then I also have to restore the master boot record.

That is the only thing I really need to know, how to restore the MBR without ruining anything else :P

And, like I said, my computer doesn't have a CD drive (we can't get an external one either) but I read that you need that dumb CD to be able to restore/repair the MBR. I have the CD already, I just need to make a bootable USB from it...](*,)

I hope that Ubuntu is worth all the trouble it caused (cause I'm gonna reinstall it to an external hd this time)

---

### Post by paf.goncalves on 2009-11-12
You can try VirtualBox.

On other PC make a iso of the windows CD and copy it to a usb.
Boot from a live ubuntu usb.
Install VirtualBox in the usb.
Run VirtualBox and create a rawdisk (search in the documentation) that points to your netbook disk.
Use the iso as a virtual CDROM.
Now you can boot the virtual machine and recover windows, or do a fresh install (if your internal disk is IDE choose the PIIX3 controller).

If you do a fresh install, remember that the hardware is virtualized, and the first time you boot the real machine it will detect new hardware.

I used something like this, but the other way around, to restore ubuntu from windows.

---

### Post by mikewhatever on 2009-11-14
I think, Puzzled Guy, that you are going the wrong path. Windows is not Ubuntu, so it can't boot from usb, it's simply not designed for that. There are many other ways to restore the MBR, thanks for clarifying that's what you want, for example:

[http://members.iinet.net.au/~herman546/p18.html#MbrFix.ex](http://members.iinet.net.au/~herman546/p18.html#MbrFix.ex)

[http://members.iinet.net.au/~herman546/p18.html#Replace_GRUB_in_MBR_with_ms-sys](http://members.iinet.net.au/~herman546/p18.html#Replace_GRUB_in_MBR_with_ms-sys)

---

### Post by Monotoko on 2009-11-14
It is possible to put Windows onto a USB flashdrive using BartPE, i have done it before, i believe i followed this artical: 
[http://wiki.eeeuser.com/windowsxpusb](http://wiki.eeeuser.com/windowsxpusb)

---

### Post by Puzzled Guy on 2009-11-14
Thanks mikewhatever! That site seems to be what I'm looking for. Just another question: If I use the my-sys program, then will I be able to delete the Ubuntu partitions too? So that Ubuntu will be completely gone and so I can then reinstall ubuntu?

---

### Post by Puzzled Guy on 2009-11-14
Whoops! Sorry! Didn't read the end of the page "step 2: deleting the linux partition"

Anyway, I'm not marking this thread as solved until I test it...

---

### Post by Puzzled Guy on 2009-11-15
Thanks a million mikewhatever! I went to the link you posted. To anyone who reads this, for Windows, I say that MbrFix.exe is the easiest to use.

I, as the owner of this thread, officially end this thread.:KS

---

