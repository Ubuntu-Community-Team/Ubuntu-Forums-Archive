---
title: "Uninstalling Ubuntu, retaining Win. XP"
date: 2010-04-26
forum: General Help
---

### Post by d2bunt on 2010-04-26
Hello forum. Sorry I don't have any posts on this forum already, but I'm almost pulling my hair out due to my laptops shortcomings.

**What I need to happen, and why:** originally, the laptop came with Windows XP installed. I then created a dual boot by installing Ubuntu 9.04, which I 'updated' to 9.10. In any case, I have now realised that the partition containing Ubuntu is too small (bad advice I received from another Linux forum), at 5GB. It's now struggling to run and the 'space' is almost full. Since my Windows partition (~50GB) is also almost full, I would like to remove Ubuntu and claim that space back (a total of just <60GB). I have no intentions of installing Linux again until I can scrape together enough money to buy a good computer - I'm stuck with what I've got at the moment - so although I appreciate all the advice I can get, please do not suggest replacing my current installation with a smaller flavour of Linux.

**Details:** As mentioned above, the computer has an overall hard disk size of just <60GB. I would like to remove the Ubuntu partitions (around 7GB including swap space), and return them to Windows. I know how to sort out the partitions once the boot loader has been restored, but I'm struggling to find the information I need in order to safely restore the boot loader to the Windows default. I read [this tutorial]("http://ubuntuforums.org/showthread.php?t=508927"), which mentioned MbrFix, but it does not explain how to find out what your boot device is numbered (so I'm not chancing it).

Again, I'm really grateful of any advice given. I'm not a total newbie so feel free to use technical terms in any replies you may have. Thanks! :)

- Danny

---

### Post by ubunterooster on 2010-04-26
Start up the live CD. Go to Gparted in it. Delete the Ubuntu patition then resize the MS one.
Use a copy of [sysrescCD]("http://www.sysresccd.org/Download") to re-put on grub. Sure, you won't be using linux but grub works fine for MS OSs too

Hope to see you back here someday :)

---

### Post by d2bunt on 2010-04-26
So you would advise removing the partitions first and then replacing the boot loader? And I do have the Live CD but it's for the 9.04 version and not the current 9.10 version - does this make a difference? And is there any way to totally remove grub so that the computer automatically boots straight into Windows? **[edit]** Just a thought - can I restore the MBR using the Windows CD first and then resize the partitions?

So many questions. :p

---

### Post by ubunterooster on 2010-04-26
> **d2bunt said:**
> So you would advise removing the partitions first, then replacing the boot loader Yes. > And I do have the Live CD but it's for the 9.04 version and not the current 9.10 version - does this make a difference?no difference> And is there any way to totally remove grub so that the computer automatically boots straight into Windows? When there is only one option, it goes to it without grub ever coming onscreen> Just a thought - can I restore the MBR using the Windows CD first and then resize the partitions? Not sure how to do _anything_ with windows CDs (that was 6 months ago and my mind flushed all that info) but am sure that resizing would mess up MBR. There is a program for reseting the MBR afterwards but forget what it is...
EDIT: [easybcd]("http://neosmart.net/dl.php?id=1"). Also MS has its own [Multiple workspaces]("find.pcworld.com/60931") that is worth a look

---

### Post by d2bunt on 2010-04-26
I will take the steps given to me in your original message - I don't have much of a choice now as I just discovered that all that the Windows CD I got does is format the hard disk and install Windows again. :(

Thanks again. :)

- Danny

---

### Post by pricetech on 2010-04-26
> **d2bunt said:**
>  I don't have much of a choice now as I just discovered that all that the Windows CD I got does is format the hard disk and install Windows again. :(

I hate restore disks.

---

### Post by d2bunt on 2010-04-26
> **pricetech said:**
> I hate restore disks.

So do I now that I've realised it's 100% useless. They market it as a "recovery" disk, despite the fact that it wipes your hard drive and in the process remove all your data. Pathetic.

Anyway, I've just realised that to use Super Boot CD you need to use commands - and I don't have a printer. Is there any easier option that doesn't require memorisation of commands?

---

### Post by v1ad on 2010-04-26
> **d2bunt said:**
> 
Anyway, I've just realised that to use Super Boot CD you need to use commands - and I don't have a printer. Is there any easier option that doesn't require memorisation of commands?

in the old days we used a pen and paper.

---

### Post by wilee-nilee on 2010-04-26
If you need a ISO of XP home so that you can reinstall the MS bootloader in the mbr here you are.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)
I suspect any XP install disc will work.
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)

---

### Post by d2bunt on 2010-04-26
> **v1ad said:**
> in the old days we used a pen and paper.

Ouch! I just didn't fancy writing down an entire page of commands. Talk about jumping on top of the n00bs.

---

### Post by d2bunt on 2010-04-26
> **wilee-nilee said:**
> If you need a ISO of XP home so that you can reinstall the MS bootloader in the mbr here you are.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)
I suspect any XP install disc will work.
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)

Hmm.... well I do have a copy of XP Pro that came with another computer. Does it really make a difference if I restore the boot with an XP CD first, and then remove the partitions after?

---

### Post by ubunterooster on 2010-04-26
You don't need to write them _all_ down; just the commands relevant to what you are doing
MBR will likely be destroyed by resizing but you could try anyway.

---

### Post by louieb on 2010-04-26
Change the MBR to boot straight to XP 1st.  Lots of way to do it. This guy has a hobby of playing with boot loaders. [IDBS Remove Replace Uninstal Grub]("http://members.iinet.net.au/%7Eherman546/p18.html")

---

### Post by d2bunt on 2010-04-26
> **louieb said:**
> Change the MBR to boot straight to XP 1st.  Lots of way to do it. This guy has a hobby of playing with boot loaders. [IDBS Remove Replace Uninstal Grub]("http://members.iinet.net.au/%7Eherman546/p18.html")

I ended up doing it that way in the end. :)

I used MbrFix to restore the Windows XP boot loader, then I used the System Rescue CD, suggested earlier on, to sort out the partitions - turns out you don't need to use commands as the GUI option has GParted. Overall, I'm happy.

Thanks for all your help guys. :) Hopefully I can return to Linux soon...

- Danny

---

### Post by ubunterooster on 2010-04-26
I will wait. :)

---

