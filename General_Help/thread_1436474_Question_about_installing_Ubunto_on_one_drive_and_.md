---
title: "Question about installing Ubunto on one drive and keeping files another drive"
date: 2010-03-22
forum: General Help
---

### Post by monicamaria on 2010-03-22
Hello,

Our computer has two hard drives.  We put programs on C: drive (640GB) and personal files on D: drive (250GB).  So, if we decide to un-install Windows and use only Ubunto on C; drive, will the personal files on D: be affected?  Are there certain things we should do to the personal files first?

I am sure my inexperience is very evident and your patience is appreciated.

Thank you,
Monica

---

### Post by 2hot6ft2 on 2010-03-22
> **monicamaria said:**
> Hello,

Our computer has two hard drives.  We put programs on C: drive (640GB) and personal files on D: drive (250GB).  So, if we decide to un-install Windows and use only Ubunto on C; drive, will the personal files on D: be affected?  Are there certain things we should do to the personal files first?

I am sure my inexperience is very evident and your patience is appreciated.

Thank you,
Monica
Hi Monica,

As long as you don't tell it to do anything with any drive/partition but the one you want it on then no it will not affect them.
I suggest choosing Manual when you get to the partitioner and click Forward to start the manual partitioner and then choosing the drive/partition you want it on.

You will need 2 partitions for ubuntu. You can choose the one where windows is now and select delete then select create new in the space where it was and make one partition where ubuntu will be and file system type ext3 or ext4 mount point "/" check the format box and click Ok. Create another partition in the empty space and file system type "linux swap" 2 GB should be plenty for the swap partition size.

You may want to create the swap partition first at the end of the available space then create the ubuntu partition in the space before it.

Don't let the manual partitioner scare you it just gives you more control of what it's going to do.
No changes are applied until after step 7 of the installer so you can always go back or quit up to that point.

"Are there certain things we should do to the personal files first?" No

---

### Post by monicamaria on 2010-03-22
Thank you for your reply, you make it sound simple so maybe I can handle it.  We are trying Ubunto on our laptop and we found out it won't work with our Lexmark printer.  If we go with Ubunto, we will just have to get a new printer.

Thanks again,
Monica

---

### Post by blueridgedog on 2010-03-22
The concept of a separate drive for user files is pretty common.  You should have few issues making the setup work.  You will need to learn how to access the files and, in the long run, mount the drive where you are happy with it (in your home directory for example).

Come back to this forum for help and you should be able to overcome what roadblocks you find.

---

### Post by 2hot6ft2 on 2010-03-22
> **monicamaria said:**
> Thank you for your reply, you make it sound simple so maybe I can handle it.  We are trying Ubunto on our laptop and we found out it won't work with our Lexmark printer.  If we go with Ubunto, we will just have to get a new printer.

Thanks again,
Monica
It is really simple and you're right Lexmark provides no linux support at all. HP (Hewlet Packard) on the other hand supports linux and work most of the time as plug and play.

There is a How To For Lexmark but considering their lack of cooperation with the linux OS in general I don't purchase their products.

You're welcome and welcome to the community. If you have any other questions just ask.

---

### Post by impert on 2010-03-22
```
we found out it won't work with our Lexmark printer

```

Have you seen [this link?]("http://http://ubuntuforums.org/showthread.php?t=49714")

---

### Post by 2hot6ft2 on 2010-03-22
> **blueridgedog said:**
> The concept of a separate drive for user files is pretty common.  You should have few issues making the setup work.  You will need to learn how to access the files and, in the long run, mount the drive where you are happy with it (in your home directory for example).

Come back to this forum for help and you should be able to overcome what roadblocks you find.
Don't let that sound like a big hassle, it's not, and blueridgedog doesn't mean for it to sound like it would be. I could see how that could be misunderstood. Since the drive is internal the installation of 3 packages and running one setup that only has 4 options to choose from will give you full access to them which I'm assuming are on a NTFS partitions.

---

### Post by theozzlives on 2010-03-22
> **monicamaria said:**
> Are there certain things we should do to the personal files first?

BACK THEM UP! And in Ubuntu, drive c: will be sda, drive d: would be sdb so as not to get confused. For example the first partition on c: is sda1.

---

### Post by 2hot6ft2 on 2010-03-22
> **impert said:**
> ```
we found out it won't work with our Lexmark printer

```

Have you seen [this link?]("http://ubuntuforums.org/showthread.php?t=49714")
Fixed your link one to many "http://" in it
[http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714)

That's the Lexmark how to I mentioned. Thanks for linking to it.

---

### Post by 2hot6ft2 on 2010-03-22
> **theozzlives said:**
> BACK THEM UP! And in Ubuntu, drive c: will be sda, drive d: would be sdb so as not to get confused.
+1
I always just take for granted that everyone does backups.

---

### Post by theozzlives on 2010-03-22
> **2hot6ft2 said:**
> +1
I always just take for granted that everyone does backups.

I've preached for 17 years, "backup, backup often", and people still don't.

---

### Post by 2hot6ft2 on 2010-03-22
> **theozzlives said:**
> I've preached for 17 years, "backup, backup often", and people still don't.
And they never will I guess until they find out what they have to lose. Good point.;)

What's the old saying. You can lead a horse to water but you can't make him THINK!
Sorry I took so long I was editing some movie upload info.

---

### Post by monicamaria on 2010-03-22
> **2hot6ft2 said:**
> Fixed your link one to many "http://" in it
[http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714)

That's the Lexmark how to I mentioned. Thanks for linking to it.


Yes, I tried this link but it says there is no model z600.  I think it must be too old.

---

### Post by 2hot6ft2 on 2010-03-22
> **monicamaria said:**
> Yes, I tried this link but it says there is no model z600.  I think it must be too old.
On the [lexmark driver download page here]("http://support.lexmark.com/index?page=answers&startover=y&locale=en&userlocale=EN_US+&productCode=&segment=DOWNLOAD&question=z600#1")

It shows this driver for linux z600
[CJLZ600LE-CUPS-1.0-1.TAR.gz]("http://support.lexmark.com/index?page=answerlink&userlocale=EN_US&segment=DOWNLOAD&locale=en&url=http%3A%2F%2Fsupport.lexmark.com%2Findex%3Fpage%3Dcontent%26id%3DDR15809%26actp%3Dsearch%26viewlocale%3Den_US&productCode=&answerid=16777225&searchid=1269306953692") 

That should be the right one since it's the only one there for linux, much to my surprise that one even existed.

Hope that helps. Just had to figure out how to navigate their maze to find things...;)

Now just download it and follow the how to in order to install it and good luck.

---

### Post by monicamaria on 2010-03-22
Thanks for all the great information.  I will definitely  back up our files before doing anything with the computer.  In fact, we are waiting for the computer to come back from being repaired.  After starting up, the computer would start freezing up and then a long beep would come from the tower and would not stop until we restarted it.  We worked with it some, but decided to take it to Office Depot's computer repair.  We have been researching and have been very impressed with the security and simplicity of Ubunto.

These message boards are very helpful and obviously managed by experienced and intelligent people.

Thanks again,
Monica

---

### Post by 2hot6ft2 on 2010-03-22
> **monicamaria said:**
> Thanks for all the great information.  I will definitely  back up our files before doing anything with the computer.  In fact, we are waiting for the computer to come back from being repaired.  After starting up, the computer would start freezing up and then a long beep would come from the tower and would not stop until we restarted it.  We worked with it some, but decided to take it to Office Depot's computer repair.  We have been researching and have been very impressed with the security and simplicity of Ubunto.

These message boards are very helpful and obviously managed by experienced and intelligent people.

Thanks again,
Monica
I hope they fix it up right for you, and yes the ubuntu forum is top notch, if you haven't already noticed that there are people here running a wide variety of operating systems. Not just ubuntu so this forum has a lot of very knowledgeable people in a wide range of things and operating systems.
You'll find sub forums like Mac, Mint Users, Dell, System 76 and many more. Not to mention the diversity of ubuntu itself. There's so many flavors like ubuntu, kubuntu, xubuntu, Lubuntu etc...

And welcome again..

---

