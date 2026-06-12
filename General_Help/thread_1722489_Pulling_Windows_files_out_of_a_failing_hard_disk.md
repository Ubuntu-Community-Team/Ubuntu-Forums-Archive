---
title: "Pulling Windows files out of a failing hard disk"
date: 2011-04-05
forum: General Help
---

### Post by Nicholas Escalona on 2011-04-05
I'm running an Acer Aspire 1830T-3721 dual-booting Windows 7 with Ubuntu 10.10 (Desktop).

Background:
So first I dropped my laptop a couple feet while Windows was running. The laptop immediately shut off and then tried to boot. Booting Windows resulted in an unfortunate "Windows has encountered a problem communicating with a device connected to your computer. The error can be caused by ... faulty hardware ... Status: Oxc00000e9 Info: An unexpected I/O error has occurred." But Ubuntu boots fine, and I can access my NTFS files fine, so I was trying to work on the problem from there.

I used testdisk to examine the Windows partition. It told me that the boot sector was okay, but the backup boot sector was bad, and so I followed the prompt to overwrite the backup boot sector. Then I hit "repair MFT", and either the MFT mirror overwrote the (bad) MFT, or the MFT overwrote the (bad) MFT mirror. Testdisk reported that there was a lost NTFS partition, but I ignored it since all my expected partitions were listed fine in the table.

Also, through tinkering with the partition table I was able to get the previously non-booting system recovery partition to boot.

Since then, I've got a different I/O error when I boot Windows. It's more serious sounding, but I don't want to unnecessarily stress the hard disk any by verifying what it said. Also, I stopped seeing the correct contents of my Windows partition - now there's just a 2.8 GB file "hiberfil.sys", and a broken symlink "Documents and Settings". Further, testdisk stopped reporting the lost NTFS partition.

I was running Ubuntu fine for a couple of days. Just today I ran the Windows 7 recovery console and ran a chkdsk on the Windows partition. In pass 2, it spent most of its time slowly spitting these out (for differing number <N>):

```
Correcting error in index $I30 for file <N>
Correcting error in index $I30 for file <N>
Sorting index $I30 for file <N>
```

Then, it seemed to get stuck on a file, and printed another "Correcting error in index $I30" a couple times an hour until I exited the command prompt and booted Ubuntu, intending to run it again later.

So I just did that now and Disk Utility SMART data reads "DISK FAILURE IS IMMINENT". Reallocated sector count says 558, current pending sector count says 25, and so total bad sectors is 583; previous to this boot it had been telling me there were 7 bad sectors.

So now I'm even more in damage control mode; I'm prepared to get another hard drive and reinstall Windows, but I'd really like to save my data if it's still in there somewhere. I don't have an easy way to back up my Windows partition though - it's 300 GB.

Thanks for any suggestions.

Oh yes, and - for the life of the hard drive, is it better that I just leave my laptop running, or that I suspend it, hibernate it, or shut it off until I want to use it to recover files? I do have a SystemRescueCD available to boot from, instead of booting from the hard drive.

---

### Post by 23dornot23d on 2011-04-05
My thoughts on this ... 

When you dropped the computer and it ws running the reading heads on the disk drive probably made ontact with the disk and damaged it so the windows no longer ran.

Ubuntu probably ran ok because the part of the disk that ran on was unaffected ......

You at this stage should have used NTFS tools in Ubuntu to access any data on the windows
partition ....


Why you altered the MFT is difficult to understand here ...... as all the pointers to the correct files etc should not have changed by dropping it ...... 
but now you have changed them both using Linux and Windows ..... 
I think you may have made problems a lot worse .....

but ......

Can you see any files on the NTFS partition or does it no longer exist ...... ?

if you can still get to your data you need a drive capable of holding your data ,,,, a USB drive is often a cheap option here , 300GB or 500GB and 
then try to pull across as much data as possible before and  without doing any more alterations to the bad Disk drive ..........

---

### Post by Habeouscorpus on 2011-04-05
If it was mine, I'd pull what I could right now until it croaked. Then I'd let the professionals handle it... But that's expensive. Leaving it on allows the hard drive to spin up and down, which is what wears it out. But! Since it was caused by damage, a professional would probably be able to pull a lot of the data by putting it in a new enclosure. But that's irrelevant.

It comes down to how important this is. If you absolutely cannot lose this stuff, shut it down quickly and take it to a data recovery service. If you would be ticked if you couldn't, but things would be fine, start backing up all the important stuff with a Live CD of Ubuntu and an external hard drive. 

Sorry to hear it's failing. Hope you recover everything!

---

### Post by Silverdogz on 2011-04-05
First I would probably have pulled the HD just to look at it if just to see if the case for it was fine. If it isn't it is only a matter of time before it fails completely. Also if you have a desktop plug it into that and transfer the entire drive to it get a new HD for laptop transfer back and it will save you a few $$$.

---

### Post by tgalati4 on 2011-04-05
photorec is the tool to use to recover files to an external drive or thumb drive.

man photorec

You need to first recover what you can from the Windows partition while the disk is still spinning.  If you damaged a head with a crash, you may not have much time to do recovery.  Only after you have recovered important documents/files can you then proceed to troubleshoot the partition/boot problem.

By trying to resurrect the partition, you are modifying the disk (which is risky) and you are running out of time to perform recovery should a disk head fail.

---

### Post by Nicholas Escalona on 2011-04-05
Believe me, I know I screwed it up worse than it was, lol. I'm usually pretty lucky with this kind of tinkering so I'm careless.

If I'm going to purchase a replacement hard drive to install, wouldn't it make sense to transfer the stuff to that instead of getting an external drive?

I guess I'll be needing some kind of adapter to do that... would I want SCSI to USB?

Thanks guys. Live and learn! The data isn't critical... I suppose it'd be worth about $60 to me to save it all, if the alternative were to lose it all.

---

### Post by 23dornot23d on 2011-04-05
If you can get a drive and clone it then do so ..... my reason for the external was for laptop 
and the fact you would be able to do it without a shut down - but you probably have a desktop .....  
and have no worries about adding a new drive to it and cloning it .....

But whichever way is best for you to get the data onto another drive .... 
simplicity while its running if you had a USB hard drive or you knew someone with a 
USB hard drive the data could be taken off there and this could be done while its still running .....

My advice is only based on what you had said earlier  ...... and yes if you know how to install
a second drive set it up and get the data across to it do that ...... then do this.



If you cannot easily add a second drive as a slave drive - then continue asking questions and we will see if we can help some more .....

The data that was on the original was probably ok even after running testdisk .....

but after doing that - then the Windows Check disk option probably started moving things around here and trying to correct 
things to the new alterations you had done ......

> 
Just today I ran the Windows 7 recovery console and ran a chkdsk on the  Windows partition. In pass 2, it spent most of its time slowly spitting  these out (for differing number <N>):

     Code:
     Correcting error in index $I30 for file <N> Correcting error in index $I30 for file <N> Sorting index $I30 for file <N> 
Then, it seemed to get stuck on a file, and printed another  "Correcting error in index $I30" a couple times an hour until I exited  the command prompt and booted Ubuntu, intending to run it again later.
1 ... Now the easiest way to get any data off of it is a USB hard drive ..... borrowed or bought
(once you have a new drive installed then you can transfer your DATA back)

or 
2 ... Take it into a repair shop where they have all the right gear to do it .....

or 
3.... Do it yourself if you know how to set up a new drive alongside the one that is messed up.


Is it a desktop machine or a laptop ?
> 
I guess I'll be needing some kind of adapter to do that... would I want SCSI to USB?



I hope that this helps  - as that is what I would do if it was my machine .... 
( but then its easy for me as  I have 4 USB's laying around and they always come in useful - for backups etc )

---

### Post by Nicholas Escalona on 2011-04-06
So I borrowed an external HDD, and booted from my SysRescCD. I ran a [FONT="Courier New"]dd if=/dev/sda3 of=/mnt/ext/disk.img[/FONT], and this was the result after a while:
```

dd: reading `/dev/sda3': Input/output error
10479584+0 records in
10479584+0 records out
5365547008 bytes (5.4 GB) copied, 1119.76 s, 4.8 MB/s

```

Should I try to run the dd again?
Should I use [FONT="Courier New"]conv=noerror[/FONT]?
Perhaps start at the point that failed, to not waste time with the part I already have?
[FONT="Courier New"]dd if=/dev/sda3 of=/mnt/ext/disk2.img bs=4096 skip=1309948[/FONT]
(where 1309948 is 5365547008/4096)
should I use 4096 as block size? Input and output locations are both NTFS. My attempted run was without specifying [FONT="Courier New"]bs[/FONT] at all, which I think means it used 512. Sorry, I don't know a ton about dd.

Or should I run photorec instead? It seems that if my goal is to minimize total disk ops, I should first get the data off the failing drive, and then maybe run photorec on that.

Thanks guys.

---

### Post by Nicholas Escalona on 2011-04-09
After doing some research I came across GNU ddrescue as the most appropriate utility in its class for my purposes here. I'm running it now. So ignore my last post; dd is apparently a pretty bad idea for data rescue.

---

