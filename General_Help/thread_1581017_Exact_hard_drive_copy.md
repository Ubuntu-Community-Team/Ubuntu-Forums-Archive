---
title: "Exact hard drive copy"
date: 2010-09-24
forum: General Help
---

### Post by wareagle on 2010-09-24
One of the companies I support is being sued (yay!) and I have been asked to make an exact copy of their servers' hard drives, including the ability to recover data.

All of them run Windows Server 2008.  The largest drive is 800GB.  I was thinking of running out and buying 1TB USB hard drives, and using dd to copy them from a live cd.

dd if=/dev/sda of=/dev/sdb bs=4k

Is this the best way to go about doing this?  Also, most servers have multiple hard drives - would I be able to put multiple hard drives on one USB hard drive as separate partitions (if only one of them is bootable)?

---

### Post by stlsaint on 2010-09-24
> Is this the best way to go about doing this? 
There are too many ways to declare one single way "the best way"!
DD works great and can get the job done. As long the drive you are copying TO is equal to or larger than the drive you are coping FROM you will be fine. 

> Also, most servers have multiple hard drives - would I be able to put multiple hard drives on one USB hard drive as separate partitions 

Yes, dd can specify which partition you want to copy to so the same rule applies as above. As long as the partition you are copying TO is larger or equal to the partition you are copying FROM!!

---

### Post by Megaptera on 2010-09-24
Just an aside, if you're doing this for possible legal proceedings you might want to ensure that you comply with 'Chain of Evidence' requirements in your country/jurisdiction so that what you've copied goes unchallenged.

---

### Post by pricetech on 2010-09-24
I'd study up on making forensic copies before I did anything.

---

### Post by john newbuntu on 2010-09-24
If you are using dd, use options like conv=notrunc,noerror to keep going even if there are any hard disk errors.  Also try looking at ddrescue which can handle errors slightly better, retry extracting data from bad sectors and is I believe a tad bit faster than dd.

If this is for a Sarbanes-Oxley kind of audit, you might want to make a disk to disk copy using ddrescue.  This is probably what you want from reading your first line.

---

### Post by QLee on 2010-09-24
[QUOTE=pricetech]I'd study up on making forensic copies before I did anything.[/QUOTE]
Good plan!

Since you work for the defendant, your evidence will be considered biased even if you hold to chain of evidence. If you had to testify, it likely would be the defending attorney's aim to prove that you are totally incompetent and any evidence from you is worthless, unless you are truly an expert with the credentials to prove it, and trump their expert. I'm not telling you how to run your business, only you can decide if what you will charge them will be worth it. 

Standard Disclaimer: I am not a lawyer. 
Get the corporate lawyer to find a third party forensic expert with no previous relationship to the business to hold a copy of the data.

---

