---
title: "Open Office Documents losing data problem."
date: 2011-04-11
forum: General Help
---

### Post by imtiaz.ahmad on 2011-04-11
Hi to All!

I am facing a severe problem on many Desktop PC's, whenever an employee is working in Gnome-Open-Office.org document (i.e. Wordprocessor, SpreadSheet, or any other Gnome-office application) and due to power outage after restarting, the previously open document either does not open or it shows a recovery dialogue after clicking on recovery button or clicking on cancel in either case document contain nothing (empty). The file size of the document is either 0kb or within few Kbs range.

Any one have any idea about it ? what to do ?? or any other alternative which is already tested in such environment (i.e. electricity failure )? or any options to be turned on/changed? 

Any help will be welcomed....

Thanks

---

### Post by Thewhistlingwind on 2011-04-11
Are the documents being lost already saved to the disk, happen to be open, then are lost on reboot? Or are they unsaved, then lost because they weren't saved?

---

### Post by imtiaz.ahmad on 2011-04-11
Most of the time we are working in properly saved documents but after rebooting that previously opened documents at the time of electricity failure they are not opening after that... or some documents which are opened after that they are giving us incorrect results (i.e. empty file, or unreadable characters )

---

### Post by grahammechanical on 2011-04-11
I am thankful that I live in a part of the world where the electricity supply is consistent and stable. Although that my change in the future. So, I cannot say much about the electricity supply problems that you have but it the cause of the problems, is it not?  You should think about investing in an Uninterruptible Power Supply. See this link.

[http://en.wikipedia.org/wiki/Uninterruptible_power_supply](http://en.wikipedia.org/wiki/Uninterruptible_power_supply)

I have found that the OpenOffice Database program does not save new data records to the hard disc until you close the program. You may click the save icon on the record form but it is not actually saved to hard disc and data can be lost if the computer is shutdown before the program is closed or the program crashes. I now use the database for a little while and close it and open it again just to make sure my data is safe.

I do not think that any operating system or program will handle sudden power lost without causing corruption to data files or program files. This is why I think that as you are in a business environment you should think about UPS. It will give your people time to save the document to disc and shutdown the programs and OS in the correct manner.

Regards.

---

### Post by imtiaz.ahmad on 2011-04-12
We have invest so much in IT area but some of the UPS's are giving us backup that is why we are facing such problems, i think not many of the applications are causing such type of problems especially Microsoft have very stable environment which is not in case of Ubuntu, i am looking for free alternative of Microsoft Office in Ubuntu which is 99% stable in problems like (electricity failure) we are facing.

---

### Post by Vaphell on 2011-04-12
have you enabled the autobackup feature in open office options? supposedly it will create copies of documents in open office config folder (not enabled by default).

I find the threads about data loss in open office quite disturbing, i see them slightly too often for my taste.
I can't comprehend why file being worked should be opened physically all the time with its content present in RAM only - and in case of crash it irreversibly evaporates .Though when you work with a file, modify and save it, it 'appears' to be changing size and such. This may indicate that filesystem virtually changes the data, but loss happens when it hasn't flushed it to disk yet.
I remember reading about ext4 issues some time ago when it was brand new. It buffered writes for up to 2 or 3 minutes for huge throughput gains vs ext3 and people were losing their whole kde configuration in case of crash (all config files were left in opened-but-not-written-yet state or something like that which is awfully similar to the problem at hand). Supposedly the issue was fixed (at least is not as apparent at it was then). I don't know if it's the filesystem that doesn't make it in time or open office that is to blame here though.
If you don't mind checking if data is safer on slower ext3 partitions, test it. Create some ext3, crash the test machine few times and see what happens. If the problem persists then OO is squarely to blame.

---

### Post by imtiaz.ahmad on 2011-04-14
I have already checked the auto backup and also enabled the auto saving after each minute but still i am facing file crashed problems, may be it could be problem with file system ext4, i will try this one, if it works a very big issue will be solved cause data is most important thing for every one.
i will post if it works.
thanks buddy...

---

### Post by qchem on 2011-08-02
Imtiaz:
I am wondering if you have reached any solution for your problem. Sadly, I had the same troubles since yesterday morning. I am loosing my draft which I have been working on for two months. my computer went frozen and I had to restart it forcefully. unfortunately, I my real document was not there, while a zero size one exists.
any help is highly appreciated.

---

### Post by Hagar Delest on 2011-08-04
Sadly, nothing to do: [22 page term paper replaced with pound signs](http://user.services.openoffice.org/en/forum/viewtopic.php?f=6&t=17677). The power supply failure seems to be the most frequent cause.

In such case, try to check the temporary folder of the system (see in OOo Tools>Options>OOo>Paths). If there are folders like sgmlf.tmp with a file having the same name inside, make a copy of that file, rename it in .odt and cross your fingers.

The problem is that you've to make sure that the temporary folder is not cleaned up at startup when the machine reboots! A live CD may help to test once if it can help.

Else, nothing to do I fear.

---

### Post by The Cog on 2011-08-04
It may be worth trying another filesystem instead of ext4. I have vowed never to use ext4 again after seeing horrible filesystem corruption. ext3 is the "old reliable" that Linux used to use, but personally I tend to use jfs which has survived a number of power cuts and forcible reboots for me. That doesn't help recover your files already lost of course, but it might prevent future problems.

---

