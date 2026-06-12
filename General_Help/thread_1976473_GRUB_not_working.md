---
title: "GRUB not working"
date: 2012-05-08
forum: General Help
---

### Post by TXbirder on 2012-05-08
I have Win7 on one hard drive and Ubuntu 11.10 on a second.  When I start the computer it *always* opens Win7.  To get to Ubuntu I have to jump into BIOS and select the hard drive with Ubuntu on it.
When it opens I see the GRUB screen.  Why does it not open first thing  as GRUB always did when I was using 10.10?

I asked Gigabyte(motherboard manufacturer) for a solution.  Their answer is to go into BIOS Advanced Settings to specify the drive.  I have and it had no effect.  Is there some way to prioritize GRUB or is this strictly a BIOS problem? 

John

---

### Post by drs305 on 2012-05-08
If desired, you can install Grub to both drives so that no matter which one BIOS selects the MBR points to your Ubuntu installation. 

Right now it sounds like Ubuntu controls one drive while Windows controls the other, with BIOS always selecting the Windows drive. If you decide to put Grub into both drives' MBRs, you might want to make sure you have a Windows recovery CD available should you need it to restore Windows. That shouldn't be necessary, but it's a good thing to have in any case.

If you decide to put GRUB on both drives, just boot into Ubuntu, then install it to both drives. Don't select a partition, just the drives. Then update grub just to make sure the menu is current:
```

sudo grub-install /dev/sda 
sudo grub-install /dev/sdb
sudo update-grub
```

---

### Post by TXbirder on 2012-05-08
OK.  Thanks.  I got it working.  I had skipped a step in changing BIOS.  Brain fart.

---

