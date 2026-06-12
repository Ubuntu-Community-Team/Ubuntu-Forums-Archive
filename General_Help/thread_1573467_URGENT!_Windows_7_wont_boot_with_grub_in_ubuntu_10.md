---
title: "URGENT! Windows 7 wont boot with grub in ubuntu 10.04!"
date: 2010-09-12
forum: General Help
---

### Post by compiz addict on 2010-09-12
I installed Ubuntu 10.04 on my friends computer using a side-by-side install with windows. Everything seemed fine at first until he tried to boot to Windows. It just restarted the computer.

How can I get rid of grub and Ubuntu and return the computer back to a lame *** windows system?

or maybe fix the grub problem

---

### Post by wilee-nilee on 2010-09-12
> **compiz addict said:**
> I installed Ubuntu 10.04 on my friends computer using a side-by-side install with windows. Everything seemed fine at first until he tried to boot to Windows. It just restarted the computer.

How can I get rid of grub and Ubuntu and return the computer back to a lame *** windows system?

or maybe fix the grub problem

First have them run the bootscript in my signature, and post in code tags as described. This will tell us everything we need to know generally in one set of text to get this fixed.

Also make sure to run in Ubuntu, first to see if this just loads windows correctly. 
```
sudo update-grub
```
Did Windows do a chkdsk when it was rebooted the first time or just act as described?

---

### Post by Lukas666 on 2010-09-12
> **compiz addict said:**
> I installed Ubuntu 10.04 on my friends computer using a side-by-side install with windows. Everything seemed fine at first until he tried to boot to Windows. It just restarted the computer.

How can I get rid of grub and Ubuntu and return the computer back to a lame *** windows system?

or maybe fix the grub problem

Please read this:

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by compiz addict on 2010-09-12
well, before you posted I tried to remove Linux (by removing the ext file system), and now grub doesn't seem to load. So, the only option at the moment is to forget about Ubuntu, and just get Windows 7's boot loader back.

The thing I don't get is that Windows 7 Pro works fine with my Ubuntu install, and on his computer (Win Ultimate) it doesn't work.

Does Micro$oft TRY to make Linux mess things up?

---

### Post by wilee-nilee on 2010-09-12
Ignore the last 2 posts. Easybcd2 would be a last ditch effort that only adds a third bootloader, does that make sense, NO. Easybcd only takes you to the native bootloaders. 

Post the bootscript.

---

### Post by Jesus_Valdez on 2010-09-12
Since you delete the Ubuntu partition, you don't longer have a boot manager.

Get your windows CD or DVD and do a "fixmbr", in order to restore the master boot record. I don't know the correct steps, but pretty sure you can google the details.

Also if Ubuntu doesn't run correctly in your friends PC is, probably a hardware problem.

---

### Post by Lukas666 on 2010-09-12
> **wilee-nilee said:**
> Ignore the last 2 posts. Easybcd2 would be a last ditch effort that only adds a third bootloader, does that make sense, NO. Easybcd only takes you to the native bootloaders. 

Post the bootscript.

Easybcd is not a third bootloader! It just adds more options to Windows native bootloader. I use it with Win7 and Ubuntu as in my case grub could not handle Win7 well.

---

### Post by JK3mp on 2010-09-12
> **Jesus_Valdez said:**
> Since you delete the Ubuntu partition, you don't longer have a boot manager.

Get your windows CD or DVD and do a "fixmbr", in order to restore the master boot record. I don't know the correct steps, but pretty sure you can google the details.

Also if Ubuntu doesn't run correctly in your friends PC is, probably a hardware problem.

+1 this. And when you did have ubuntu up should have checked for a record of it in grubs config, usually detects appropriate partition for windows but with some setups(varying on how manufacturer installed OEM version windows) they arrange partitions weird. You can try reinstalling again, (when it comes up to partitioning be sure you still have NTFS and try using custom layout, if its there then grub just isn't showing it, either b/c of configuration or some unknown(to me anywho) reason. I would try reinstall and using custom partition method.

---

### Post by wilee-nilee on 2010-09-12
Thread starter if your still out there if you need a recovery disc go here.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Now look at the http below if you need directions to the command line using this downloaded booted recovery. Only run the highlighted command.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Thread starter there is the possibility that the grub bootloader has been put in the W7 boot partition, that is why I suggested the script first it will tell us if there are any problems that this command run from recovery would have.

---

### Post by wilee-nilee on 2010-09-12
> **Lukas666 said:**
> Easybcd is not a third bootloader! It just adds more options to Windows native bootloader. I use it with Win7 and Ubuntu as in my case grub could not handle Win7 well.

I can appreciate that it works for you, but was it necessary, in this thread, under the circumstances the person is in; a good post. A non booting W7 after a Ubuntu side by side and your post a easybcd link, please.

---

### Post by Greycloak on 2010-09-12
Simply booting to the Windows 7 disk should offer you a choice to automatically fix boot problems.

---

### Post by wilee-nilee on 2010-09-12
> **Greycloak said:**
> Simply booting to the Windows 7 disk should offer you a choice to automatically fix boot problems.

Most find that the autorepair function fails to rewrite the MBR to a MS bootloader, when another like grub is in there.

---

### Post by Mark Phelps on 2010-09-13
> **wilee-nilee said:**
> Most find that the autorepair function fails to rewrite the MBR to a MS bootloader, when another like grub is in there.

Unfortunately for MS, what you say is true more often than not.

I support several forums, including the premier Windows 7 forum, and Vista forums, and it's really aggravating to read how often folks have to run Startup Repair three times to fix an MBR problem (Not that it tells you that), but all to often, then have to resort to running the repairs from Command Mode -- because the repair Wizard simply can't do the repairs from inside the GUI!

You'd think with all the programming resources that MS must have at their disposal, they could at least write a repair utility that would work.

---

### Post by compiz addict on 2010-09-19
Well, at the moment my friend is now using Ubuntu as his main OS, so it's not too big an issue now. I do think that this issue should be addressed though. There has to be a way to make GRUB more 7-friendly.

---

### Post by wilee-nilee on 2010-09-19
> **Mark Phelps said:**
> Unfortunately for MS, what you say is true more often than not.

I support several forums, including the premier Windows 7 forum, and Vista forums, and it's really aggravating to read how often folks have to run Startup Repair three times to fix an MBR problem (Not that it tells you that), but all to often, then have to resort to running the repairs from Command Mode -- because the repair Wizard simply can't do the repairs from inside the GUI!

You'd think with all the programming resources that MS must have at their disposal, they could at least write a repair utility that would work.

I tried to help on those forums they begged me to stay, but would never adapt to cli when that was all that was going to work, I gave up. This was during the wonderful install grub everywhere if you don't know time. So it was impossible to get them to identify grub in the ntfs.

I actually wrote a paper on the differences on the MS and open source forums and brand loyalty, in a college class, the teacher got a kick out of it.

---

