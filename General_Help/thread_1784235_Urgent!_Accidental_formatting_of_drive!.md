---
title: "Urgent! Accidental formatting of drive!"
date: 2011-06-16
forum: General Help
---

### Post by MasterZii on 2011-06-16
I just installed Ubuntu because Windows 7 haven't been booting up at all for the past 2 weeks. Now I saw my C: drive as a shortcut on the Ubuntu desktop and I right clicked it and chose "format" or whatever. **NOW ALL MY FILES ARE GONE FROM THAT DRIVE!!! I HAD OVER 600GB OF IMPORTANT DOCUMENTS!**Is there **ANY** way I can unformat the drive? I only have one and I don't know what i'll do if the files are all gone forever!

---

### Post by crispy_420 on 2011-06-16
First tip I can give is not to use the drive at all if possible. Nothing must be messed with because the further you mess around the more more likely the data will be unrecoverable.

Then there are tools like testdisk to recover to the partition but I have not done this type of recovery before so be patient until you have a valid method before attempting any sort of recovery.

---

### Post by MasterZii on 2011-06-16
Okay, I will not turn my computer on until I can find a legit method to recover the data. But you're saying it is indeed possible?

---

### Post by rbc on 2011-06-16
Is it possible?…..yes. Is it guaranteed?…..no. Sometimes tools like testdisk work, sometimes they don’t. crispy_420 has already given you some very wise advice, but please let me go a step or two farther. You should clone (make an exact copy) of the original drive, albeit a hosed up one at the moment, then make your data recovery attempts on the clone, not the original. That way you can screw up as many times as you need before you get the hang of testdisk, or whatever recovery tool you use, without further damaging the original. 
1.	Get yourself a hard drive of equal capacity to make the clone
2.	Read up on the dd command
3.	Be patient
4.	When, or if, you’re successful with the recovery, use the extra drive to make frequent backups

---

### Post by dFlyer on 2011-06-16
You might want to try photorec. I've never used it but have heard good things about it.

---

### Post by zcacogp on 2011-06-16
I think the message is 'don't despair'. I know that, if the worst comes to the worst, there are some very capable data recovery companies who will almost certainly be able to recover your data (and, yes, they will take your money as well :( .) 

The advice of making an exact copy of the drive and doing your recovery attempts on that is the most sound to date. 

Fingers crossed for you.


Oli.

---

### Post by MasterZii on 2011-06-16
Ahh, I see what you mean. But how can I make a copy of the drive? I can't just drag the empty space to an external? How am I supposed to copy an empty drive?

---

### Post by rbc on 2011-06-16
You said you formatted the drive/partition. Formatted does not necessarily mean files were erased. At best, the files are simply inaccessible at the moment. As I stated earlier, do some reading about dd.

---

### Post by Quackers on 2011-06-16
Testdisk is definitely worth looking into. I have used it to successfully recover whole partitions before.
The second link, written by forum user Herman, is probably the better guide to use.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)

---

### Post by apesa on 2011-06-16
You won't be dragging and dropping anything. Your safest bet is to boot into Ubuntu Live after disconnecting the HDD you accidentally formatted. Then your going to need to mount that and another target HDD of the same or larger size.

Then with that start reading [here]("https://help.ubuntu.com/community/DataRecovery") You will be copying by block only to get all the blocks reassembled on the target drive. Your data is still there, you just can't see it so it will need to be moved at the block level. TestDisk and the other tools read what they can and try to reassemble it back into your files.

If this is all Greek you should make sure you understand how to correctly copy your HDD prior to mounting it.

---

### Post by lisati on 2011-06-16
> **MasterZii said:**
> Ahh, I see what you mean. But how can I make a copy of the drive? I can't just drag the empty space to an external? How am I supposed to copy an empty drive?

The idea behind some of the suggestions made so far is that you don't make a file-by-file copy, but copy the data that is actually recorded on the disk, even if it's not listed in the disk's directory as being part of a file. The "DD" command is one suggestion that has been made.

Deleting files and formatting drives doesn't always overwrite the data on the disk. What often happens is the information that lets the OS find files on the disk is changed to show that it's free space and available for reuse. As long as you haven't written anything else to the disk, there might be enough of the data from the original files left in the "free" space for the specialised programs already mentioned recover the file.

---

### Post by MasterZii on 2011-06-16
Hmm. I would try that but Ubuntu **IS** on the formatted drive. Only the Windows 7 part of the drive was formated, since I had dual boot.

I will take it to geek squad, hopefully they could help fix it?


Oh man... I can't believe I made such a mistake.
I just can't afford losing years of work and files...

---

### Post by Rasa1111 on 2011-06-16
lol, that is exactly what "format" will do to a drive. 

Nothing personal..
But if you didnt know what "format" was going to do, but clicked it anyway..
You might have a difficult time recovering your data. 

Good luck, I think you'll need it.

O_o

---

### Post by crispy_420 on 2011-06-16
Make an image of the disk at issue as mentioned by several others. There was mention of dd which is not really user friendly and if you screw up the syntax you may end up wiping the drive further. FTK offers a free imaging tool that creates a bit by bit copy.

Even if the drives appears empty there is data present on it, it may just in bad condition. There is always a chance to recover in most cases and imaging is the best route. Make an image and work with copies, if you screw up just make a new copy. That way you have no risk to try various methods.

---

### Post by apesa on 2011-06-17
> **crispy_420 said:**
> There was mention of dd which is not really user friendly and if you screw up the syntax you may end up wiping the drive further. 

ddrescue is a wrapper around dd that makes it much easier. there is also a well written tutorial on using it in different circumstances.

---

### Post by levidurfee on 2011-06-17
> **crispy_420 said:**
> Make an image of the disk at issue as mentioned by several others. There was mention of dd which is not really user friendly and if you screw up the syntax you may end up wiping the drive further. FTK offers a free imaging tool that creates a bit by bit copy.

Even if the drives appears empty there is data present on it, it may just in bad condition. There is always a chance to recover in most cases and imaging is the best route. Make an image and work with copies, if you screw up just make a new copy. That way you have no risk to try various methods.
I agree, the FTK imager is really good.

[http://accessdata.com/support/adownloads#FTKImager](http://accessdata.com/support/adownloads#FTKImager)

I worked for the Geek Squad a few years ago, and in 2004 when I first got there, they would let us do some data recovery, but before I left the policy changed and required them to send the drives off.

---

### Post by MasterZii on 2011-06-17
Okay, I will try using this.

But first i'll make image copies.

And what do you mean? Geek squad can't fix this now?

---

### Post by MasterZii on 2011-06-21
What are your opinions on this program? [http://www.paretologic.com/lp/datarecovery/pro/trapeze/index.html](http://www.paretologic.com/lp/datarecovery/pro/trapeze/index.html)

---

### Post by Quarkrad on 2011-06-21
I have been here before pre Ubuntu days - I ran winxp and formatted my complete HD!  However, to my amazement I was able to get my data back despite formatting the whole drive!  Assuming your original set up was ntfs - I have had a lot of success with a product called Getdataback. An easy method is to borrow another HD, install winxp on it and load a copy of getdataback for ntfs.  Set that HD as master and connect your original HD to your pc as a slave drive. Fire up getdataback and let it run (analyse your slave drive).  Last time I did this (on my sons laptop HD that was in a complete mess) it took 9 hours to fully analyse!  However, at the end of the process I could see the original files in a folder structure and copied them to the other drive.  If you use getdataback you cannot copy files on to the same drive as the corrupted drive hence you need the second (Master Drive).  This means additions drives, setting up partitions and a degree of effort but if your data is valuable to you it is worth it - the process is not quick but I have experienced some amazing results with it.

---

### Post by MasterZii on 2011-06-22
> **Quarkrad said:**
> I have been here before pre Ubuntu days - I ran winxp and formatted my complete HD!  However, to my amazement I was able to get my data back despite formatting the whole drive!  Assuming your original set up was ntfs - I have had a lot of success with a product called Getdataback. An easy method is to borrow another HD, install winxp on it and load a copy of getdataback for ntfs.  Set that HD as master and connect your original HD to your pc as a slave drive. Fire up getdataback and let it run (analyse your slave drive).  Last time I did this (on my sons laptop HD that was in a complete mess) it took 9 hours to fully analyse!  However, at the end of the process I could see the original files in a folder structure and copied them to the other drive.  If you use getdataback you cannot copy files on to the same drive as the corrupted drive hence you need the second (Master Drive).  This means additions drives, setting up partitions and a degree of effort but if your data is valuable to you it is worth it - the process is not quick but I have experienced some amazing results with it.

Does that program still leave the "data" on the formatted drive? Like does it just copy over the files or does it unformat the data itself and move it? If that makes any sense...

---

### Post by Hermansuco on 2011-07-02
I recently made the same mistake trying to format an ipod. Instead I formatted the windows partition. I created an image for this partition in an external drive using ftk imager. It generated more than 200 files which I assume I can use to retrieve files if necessary. Now, I am going to try Testdisk to try to "write" the partition but I have a question. By "writing" the partition, would this mean that it would overwrite the missing files? This is a 500 Gigs disk and 350 were allocated for this windows partition I am trying to recover. Should I instead use another disk to write it? and if so, would Testdisk give me an option to change the target drive? 

Have you been able to recup your partition yet?

---

### Post by EduardoCR on 2012-09-26
Hello there !

I came to this thread advised by **johnnyboysmithy** on another [thread]("http://ubuntuforums.org/showthread.php?p=12262974#post12262974"), about some problems I experienced with a file system change gone wrong on an external hdd.

I gave TestDisk a go and it really worked, as easy as it could ever get.

Many thanks, people.

---

