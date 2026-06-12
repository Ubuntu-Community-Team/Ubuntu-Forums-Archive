---
title: "Is there a command to locate where grub2 is installed"
date: 2010-05-14
forum: General Help
---

### Post by Kir_B on 2010-05-14
Hi all.

I'm trying to find out which partition grub2 is installed in. Is there a command for this, as I suspect that I may have told it to install to the wrong partition during the upgrade from Karmic to Lucid, and now, I suspect that I've crippled the boot sector for my vista installation.

Thanks a lot. Kirby

---

### Post by Kir_B on 2010-05-14
Thanks to everyone that looked into it, but apparently, there must not be one.

I did finally get my answer as to where grub2 is installed. I downloaded the [boot info script]("http://bootinfoscript.sourceforge.net/") and then ran it with the following code (must be located on/in your desktop for this code to work):

```
sudo bash ~/Desktop/boot_info_script*.sh

```Once it was done running, it saved to my desktop, I opened it with gedit , and the pertinent info was right near the top of the document.

I hope that helps someone. Now I'm back to finding out how get my vista running again, since the upgrade to Lucid, has left it un-bootable ](*,) .

Thanks again everyone. Kirby

---

### Post by dcstar on 2010-05-14
> **Kir_B said:**
> Hi all.

I'm trying to find out which partition grub2 is installed in. Is there a command for this, as I suspect that I may have told it to install to the wrong partition during the upgrade from Karmic to Lucid, and now, I suspect that I've crippled the boot sector for my vista installation.

Thanks a lot. Kirby

A "boot sector" is only used to boot the PC, not a particular OS.

---

### Post by joebu23 on 2010-05-14
You might want to try to boot from a windows install disk and see if the restore option will work.  I'm not sure if it will, but if I remember correctly, the restore process will find the original Windows install and perhaps restore the boot loader.

Also found this:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

That should help you setup the boot loader for dual booting.

---

### Post by Kir_B on 2010-05-14
Thanks joebu23, I'm going to take the plunge tomorrow.

Kirby

---

### Post by gacb on 2010-06-23
Install Startup-Manager on the partition you think Grub is on. Change the default boot partition and see if it made any difference. If not, it's on the other partition.

I have multiple partitions and installed Start-up-Manager sequentially on each until I found the right one.

I bit clunky, but useful for non-scripters.

---

### Post by Kir_B on 2010-06-23
> **gacb said:**
> Install Startup-Manager on the partition you think Grub is on. Change the default boot partition and see if it made any difference. If not, it's on the other partition.

I have multiple partitions and installed Start-up-Manager sequentially on each until I found the right one.

I bit clunky, but useful for non-scripters.

Thanks for the response gacb, but the [boot info script]("http://sourceforge.net/projects/bootinfoscript/") did the job quite nicely. See above.

Kirby

---

