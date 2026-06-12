---
title: "Botched dual boot install Asus UL30 - Grub commands help"
date: 2010-02-10
forum: General Help
---

### Post by ei8htohms on 2010-02-10
Hello All,

I just picked up an Asus UL30VT (sweet machine so far) and wanted to load Ubuntu on it to dual boot with Win 7.  I couldn't figure out how to get it to boot from a live CD of Ubuntu or Gparted, so I decided to try to use Wubi instead.

That seemed to work fine until I wanted to try to migrate the installation from the Windows partition to it's own partition.  I tried to install UNetbootin to partition with but kept getting some kind of error.  Eventually I successfully installed Gparted and used it to create an Ext3 partition and an extended partition with a Swap partition and a storage (Fat32) partition on it.  

All good so far except that on every boot, multiple instances of UNetbootin would show up on the Grub list of boot options and none of them go anywhere (file not found or similar).  I could simply scroll down past these options to boot Windows or Ubuntu so I wasn't worried about it too much (yet).

So eventually I was able to get Ubuntu to migrate to it's own partition (using LVPM) and after more fiddling was able to get it to boot from there (yea!).  So then I want to try to get rid of the UNetbootin business so here's where I made the big mistake: I removed it "completely" using synaptic manager from within the proper Ubuntu installation.

So now when I try to boot into the OS, ALL I get in Grub are the faulty UNetbootin options, with no other operating system boot options available at all!  (ACK!)  

So now I'm pretty well stuck.  Grub can find the /boot folder on (hd0,3), but I'm too much of a noob to know how to issue commands to Grub directly (or edit the faulty commands for UNetbootin) to get it to boot into either Win 7 or Ubuntu.  

I'm happy to pay a consultant to walk me through this or even take it in somewhere to get some expert input (I'm in NYC), so any advice is much appreciated.  

Thanks sincerely!

_john


Nevermind, got it to boot from the live Ubuntu CD and just reinstalled fresh.

---

