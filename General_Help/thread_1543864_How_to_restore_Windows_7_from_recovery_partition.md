---
title: "How to restore Windows 7 from recovery partition?"
date: 2010-08-01
forum: General Help
---

### Post by vickoxy on 2010-08-01
Hi,
i bought asus 1005pe with win 7 installed. I installed also Ubuntu 10.04 ([https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot))

But, now i want to recover windows 7 (the buyer want it so), and at startup i loaded windows vista loader, and it did something, but then it rebooted and i can not do anything. I mean, Ubuntu is still working, but windows 7 starter won´t start and vista loader is repeating the same process. Also, i can not start/boot from USB stick any more.

I have no external DVD and no recovery cds, only recovery partititon. Can anyone help me here?

---

### Post by Nick_Jinn on 2010-08-01
You should have made a recovery disk before installing Ubuntu.


Now, did you make a partition for Ubuntu or did you erase and use the entire disk? If you did the later, your backup partition is long gone.


You may be able to get a recovery DVD from the manufacturer, or you may find a free download for windows 7. I happen to know of a few, but this may or may not be legal in your home country so always check your local laws before downloading windows from an alternative source.

---

### Post by vickoxy on 2010-08-01
> **Nick_Jinn said:**
> You should have made a recovery disk before installing Ubuntu.


Now, did you make a partition for Ubuntu or did you erase and use the entire disk? If you did the later, your backup partition is long gone.


You may be able to get a recovery DVD from the manufacturer, or you may find a free download for windows 7. I happen to know of a few, but this may or may not be legal in your home country so always check your local laws before downloading windows from an alternative source.

I made partition for Ubuntu. I had normal dual-boot with win 7 working. At startup i have listed 5 i think boot devices/partitions. The windows 7 was the 4. and with it i run windows. Windows Vista loader was the last partition, and i never used it until now (i read that this partition is recovery partition for windows 7).

Now if i choose windows 7 to boot i have this message:
> BOOTMGR is missing
Press Ctrl+Alt+Del to restart

---

### Post by Nick_Jinn on 2010-08-01
Did you load Ubuntu first or last?

---

### Post by CharlesA on 2010-08-01
On my eeePC, it tells you to hit F9 for system recovery. That should boot the recovery partition and restore the OS.

---

### Post by vickoxy on 2010-08-02
No, i made it by the book-after Windows 7 i installed Ubuntu. And everything was ok-i had dual-boot working just normal.
If i press F9 it´s the same-i got "loading windows files" screeen, thenb it reboot again, and after that screen with 
> BOOTMGR is missing
Press Ctrl+Alt+Del to restart

And nothing after that-i can not start anything...

---

### Post by Nick_Jinn on 2010-08-02
You could always call Asus customer service and request a recovery DVD.

I got my Win7 from an alternative source only because I lost my recovery DVD. I dont really have much use for it though  outside of a few Bethesda games that I like to use mods for. The few things I need windows for can usually be accomplished via torrents and wine.

---

### Post by vickoxy on 2010-08-02
As said, f9 does nothing-my recovery partition is damaged. I contacted asus and asked them for recovery dvd but they said they havent´t got it, but that they will send a pick-up service and repair that partition.

So, i don´t know what to do...

---

### Post by Nick_Jinn on 2010-08-02
Why is getting a recovery disk not an option?


You should only use torrents if it is legal to do so in your country. You should be entitled to a legal backup of your recovery media, but check with your local laws first. 

[http://www.picktorrent.com/download/99/3973635/windows-7-professional-lite-%D0%B4%D0%BB%D1%8F-eee-pc:-%D0%BE%D0%B1%D1%80%D0%B0%D0%B7-.tib/](http://www.picktorrent.com/download/99/3973635/windows-7-professional-lite-%D0%B4%D0%BB%D1%8F-eee-pc:-%D0%BE%D0%B1%D1%80%D0%B0%D0%B7-.tib/)


This is in Russian. You will have to download your preferred languages....however, the disk may REPAIR your system and bring back your languages. So it might not have to be a totally new install 

Any Win7 disk might work though. If you have the key on your PC then it shouldnt be a problem.

---

### Post by vickoxy on 2010-08-02
well, i removed windows 7 and its partition-i left only recovery partition, and have no idea what for is that partition. Is that a full win 7 installation file, or only some tool to repair existing win 7?

Asus Support said to me that they are not delivering cds any more...

---

### Post by Mark Phelps on 2010-08-02
You said the partition you left was the boot partition.  IF that was indeed the case, it was NOT the recovery partition and you have thus, removed the recovery partition.

Despite what other folks have told you, the vendor is NOT required to provide you a recovery CD/DVD; they are only required to provide you a WAY of recovering your Windows setup -- and if they do that by allowing you to press a function key, which will then start WinPE and begin a restore from a recovery partition, they have met their requirement.

I find it disgusting, though, that they claim they can NOT provide you a full restore DVD, even if they have to charge you for it!

Without the recover capability, you are NOT going to be able to restore the machine to its original condition.  Even if you DO reinstall Win7, it will probably NOT have the proper drivers, and will certainly NOT have the additional SW and utilities that ASUS installed in the original.

If the "buyer" really wants this in original condition, your only choice may be to have ASUS restore it for you.

---

### Post by vickoxy on 2010-08-02
Frankly, i don´t even know any more what do i have. I had Win 7 loader and when i boot it it was win 7. The second boot option was windows vista loader, and i presumed that this was recovery partition. I started it, it loaded windows files, asked me if i want to recover windows 7. I choose yes, and system rebooted but gave me that error message above. And windows was dead. 

Ok, in the meanwhile i tried one windows 7 version from my friend-i installed it from usb stick without problems. But, as i have no key for this version, only for delivered asus win 7 starter, i removed it. And i decided to sell on ebay the computer without windows-only with ubuntu.

Well, i am not very upset because all of this windows thing because i don´t use it (only in rare occasions), but it is a shame if i can not restore it back to its industrial condition. With linux is that much, much easier...

---

### Post by CharlesA on 2010-08-02
I suppose that is why I always image any machine I get before messing with it. I've had to go back to the factory image before and after you install a different OS, the recovery partition sometimes won't boot at all.

Glad you were able to sorta get it resolved.

---

### Post by vickoxy on 2010-08-02
> **CharlesA said:**
> I suppose that is why I always image any machine I get before messing with it. I've had to go back to the factory image before and after you install a different OS, the recovery partition sometimes won't boot at all.

Glad you were able to sorta get it resolved.

Well, i didn´resolve anything :???:-i can not restore factory image but at least i know that windows can be installed...

---

### Post by CharlesA on 2010-08-02
> **vickoxy said:**
> Well, i didn´resolve anything :???:-i can not restore factory image but at least i know that windows can be installed...

I suppose that is what matters, if you are just going to throw it on ebay.

If the buyer wants Windows, they can install Windows.

As a sidenote: My 1005HA came with a "recovery DVD" but the recovery partition definitely takes less time.

---

### Post by Cavsfan on 2010-08-02
I bought my daughter an ASUS laptop recently and I had to make the recovery DVDs about 4 of them if I remember. 

If you did not make those, you will probably have to send it back to ASUS or buy another copy of Windows...

---

### Post by vickoxy on 2010-08-02
> **Cavsfan said:**
> I bought my daughter an ASUS laptop recently and I had to make the recovery DVDs about 4 of them if I remember. 

If you did not make those, you will probably have to send it back to ASUS or buy another copy of Windows...

Thanks for advice, but it is too late now... still, it goes to sell without windows-but anyone who has any copy of windows at home can install it with usb stick (there is one cool tool on windows.com to make bootable usb stick from Win DVD or .iso picture)

---

