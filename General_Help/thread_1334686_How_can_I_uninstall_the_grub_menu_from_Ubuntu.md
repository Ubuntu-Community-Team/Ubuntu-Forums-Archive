---
title: "How can I uninstall the grub menu from Ubuntu?"
date: 2009-11-22
forum: General Help
---

### Post by Eagles18 on 2009-11-22
I want to uninstall the grub menu from my cousin's laptop but I can't access Windows.Is there a way to do it from Ubuntu?

---

### Post by blazemore on 2009-11-23
The Grub menu is an integral part of the system.
You can change the timeout to 0, what version of Ubuntu are you using?

---

### Post by Eagles18 on 2009-11-23
> **blazemore said:**
> The Grub menu is an integral part of the system.
You can change the timeout to 0, what version of Ubuntu are you using?
I'm using 9.10
Can't I just delete the Ubuntu partition to get rid of it?

---

### Post by blazemore on 2009-11-23
> **Eagles18 said:**
> I'm using 9.10
Can't I just delete the Ubuntu partition to get rid of it?
Yes you can.
Sorry I thought you wanted to keep Ubuntu as well.

---

### Post by Cheesemill on 2009-11-23
Deleting the Ubuntu partition wont get rid of grub as it's not stored there, it's saved to the MBR (Master Boot Record) of your hard drive.

If you say what you're actually trying to achieve then we can be more help. What OS's do you have currently and what do you want to end up with?

---

### Post by wilee-nilee on 2009-11-23
> **Cheesemill said:**
> Deleting the Ubuntu partition wont get rid of grub as it's not stored there, it's saved to the MBR (Master Boot Record) of your hard drive.

If you say what you're actually trying to achieve then we can be more help. What OS's do you have currently and what do you want to end up with?
 
+1 the removal of the Ubuntu partition will make the other OS system un-bootable with out modifying or rewriting the master boot record.

---

### Post by Eagles18 on 2009-11-23
> **Cheesemill said:**
> Deleting the Ubuntu partition wont get rid of grub as it's not stored there, it's saved to the MBR (Master Boot Record) of your hard drive.

If you say what you're actually trying to achieve then we can be more help. What OS's do you have currently and what do you want to end up with?
I want to end up with Windows XP.

---

### Post by wilee-nilee on 2009-11-23
> **Eagles18 said:**
> I want to end up with Windows XP.

There is a fixmbr for restoring the XP to the MBR. There are many threads on this forum and information on the web. So what we all need to know is do you have a XP install disc or a backup disc and or do you have a recovery partition on the HD. Somebody will help you with this, you can restore the windows bootloader without the disc I believe but I personally just do fresh imstalls in this sort of situation.

---

### Post by Eagles18 on 2009-11-24
> **wilee-nilee said:**
> There is a fixmbr for restoring the XP to the MBR. There are many threads on this forum and information on the web. So what we all need to know is do you have a XP install disc or a backup disc and or do you have a recovery partition on the HD. Somebody will help you with this, you can restore the windows bootloader without the disc I believe but I personally just do fresh imstalls in this sort of situation.
I used the recovery partition to format the whole thing, but, for some reason, the grub menu is still there.

---

### Post by earfer on 2009-12-04
Yeh i have the same problem..beens 3 days now and i cant find a way to fix this...

I have a vista and i formatted every other partition but for some reason i cant get grub to go away~

Summary:

- I Have a vista. dont have ubuntu anymore.
- I dont have any vista installation disk. but i do have a recovery disk from acer. but that doesnt help at all. all it does it format the C: and restore to defult factory.
- Right now my grub menu says: "Error: No such partition"
- The way i get to my vista is by using "G-Parted" to go to my 2rd drive. aka C:

hope some one can help out with this problem.

---

### Post by sakisds on 2009-12-04
Download a windows vista recovery disk(google it, there are available), burn it(using x4 speed), boot from it and run startup repair. I think this will fix your problem.

---

### Post by hardfire_avk on 2009-12-04
hmm.. if your windows is up and running, then you can install easybcd, it is a tool that will help you to take care of your boot-loader. if not, then you can also use windows recovery tool, to override the windows bootloader on the grub. yeah, that works !

---

### Post by StuartN on 2009-12-04
> **earfer said:**
> - I dont have any vista installation disk. but i do have a recovery disk from acer. but that doesnt help at all.

There is a Windows Vista Recovery CD available at [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/) that will rewrite the Windows boot code (without reinstalling or reformatting).

I recently used it for a Vista that would not boot with Grub and found I had to recreate the BCD boot list using BCDEDIT.EXE in command-line mode, because of changes in partition numbering.

---

