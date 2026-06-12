---
title: "Installing Windows XP along side Ubuntu"
date: 2011-06-03
forum: General Help
---

### Post by Jeremywilms on 2011-06-03
I still need my Ubuntu partition & still want to boot via grub however I also need a copy of windows XP installed. The distribution of windows I need is the one on the acer restore partition as I have tried netbooting numerous others with little success.

Alright, so my Acer Aspire One has a partition that I haven't touched (but can boot through via grub) that allows me to restore my system to factory defaults. I have used it once about two months ago, and it did work prior to installing Ubuntu. The "Acer eRecovery Management" utility basically reinstalls the windows Operating system on my netbook into "drive C:\" -- or the first NTFS partition it finds labeled "ACER" So these are the steps I took to get it installed though they do render a single error which I need help solving.

So I netbooted via linux's live cd and 'installed' until I got to the partition configuration utility and freed up some space on my linux partition(So effectively I didn't install anything, I already have linux installed; I just needed a way of freeing some space on what would've been an active partition if I hadn't booted via the livecd and I did through my linux partition instead.) Then I logged into to linux and used gparted to format the new space to NTFS & gave it the label "ACER". Finally I booted via the recovery parition, which initiates a setup that does claim the newly allocated space to be "C:\" and thus the target for restoration. The problem now is before the setup actually begins restoring anything, I get the error message "One of the services DiskPart usses returned a failure. ErrorCode=0, the operation complete successfully." Following the error message, the computer reboots with no apparent effect.

---

### Post by oldfred on 2011-06-04
I thought the drive images only restored to the full drive.

But it says it worked. Maybe it installed enough to be fixable.

Run this to see where you are at:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by lisati on 2011-06-04
It can be a bit tricky, depending on how the recovery partition does its stuff. A couple of recovery routines I've seen have had an option to use an existing partition for Windows that's smaller than the full disk. 

One thing to be aware of is that conventional wisdom holds that it's often easier to install Windows before Ubuntu, because Ubuntu's installer handles partitions belonging to another OS better than the Windows installer. It's often necessary to reinstall grub after reinstalling Windows.

It's also a good idea to make a backup of what you want to keep, just in case something gets seriously broken and you end up having to do a full installation of both Windows and Ubuntu.

---

### Post by Jeremywilms on 2011-06-04
Hey, thanks for you reply.

I too thought that the recovery only restored the entire drive but when I run the recovery setup, it says its going to restore partition ACER of 76 GBs(The correct size of the partition.) I'm 100% positive nothing has been done, the error literally popped up immediately after telling me where it was going to restore; and because it was an error inside one of the services used by DiskPart(probably a partitioning module used by the installer) it likely failed because it couldn't recognize some of the linux partitions or they weren't expected and so it likely didn't even begin restoring anything on the partition. I'm hoping maybe there is a way to fix it though.

I'm afraid I may need to delete all the linux partitions, but if I do, will I need to format the free space as ntfs in order for the restore to work? Because AFAIK I can't actually format it to nfts via the live-cd - I don't have access to "boot as live cd" option, just "install".

I don't mind removing linux, installing windows, then linux; I just want to make sure I follow the correct steps xd.

---

### Post by Jeremywilms on 2011-06-04
Just to confirm, if I remove all the partitions but the recovery, thus leaving the recovery parition the only allocated parition, the rest being free space, the recovery process should succeed, correct?

---

### Post by linuxinstalledfromhdd on 2011-06-04
> **Jeremywilms said:**
> Just to confirm, if I remove all the partitions but the recovery, thus leaving the recovery parition the only allocated parition, the rest being free space, the recovery process should succeed, correct?

That sound correct. You would be better of contacting your tech support, company that made your system, make/mod system. Start a quick trouble ticket to find out 100% since each company does it differently.

---

### Post by Mark Phelps on 2011-06-04
There might be another partition on your drive ahead of the ACER partition -- a boot partition put there by ACER when they configured the PC.  IF there is, do NOT remove that -- only remove the Linux partitions.

After that, your restore SHOULD work.  

We're all saying SHOULD because each OEM does restore differently and there is always the chance that it will NOT work.

If it doesn't work, contact ACER and see what they will do to provide you a full-recovery DVD.

---

