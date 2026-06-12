---
title: "Drive Odd Size Question"
date: 2009-09-28
forum: General Help
---

### Post by Whym on 2009-09-28
Hello. I would like to ask for some assistance please.

[http://img42.imageshack.us/img42/1487/drivesizequestion.png](http://img42.imageshack.us/img42/1487/drivesizequestion.png)

I want to format these drives and install 9.04. But I don't want anything deleted, and after moving all the data off these onto an external drive, this (see image) is what I have.
What is going on here?
Is this normal or?
They are internal partitions, with - as you can see nothing on them, yet the usage chart seems strange...
I don't want anything deleted, and yes, Viewing hidden files is enabled.
What should someone do if they want to format these but, don't want *ANYTHING* deleted?

While I have a reasonable knowledge of what I am doing, HD anomalies are not my area - and something I am still trying to learn about.

Thank you very much in advance for any help you may give me.

 - Whym

---

### Post by Lars Noodén on 2009-09-28
'formatting' a drive is deleting not just the files and directories but even the filesystem itself.  There's no way to 're-format' and not delete everything.  

A common work-around is to backup all files and directories elsewhere and then go to work.  Then do a restore when you are done.  

You might want to look at the drives using the program gparted.

---

### Post by Whym on 2009-09-28
Thank you for the reply.

So to have space used up like that with the contents being listed as Nothing is not normal then?
I can not explain what we see in my screenshot from before. How does that happen?
I wondered if that used space was just the Filesystem or something - as I said this not my area.:(

Here is what GParted has to say on the matter...
[http://img16.imageshack.us/img16/2585/screenshotxw.png](http://img16.imageshack.us/img16/2585/screenshotxw.png)
Odd as well.

Again, thanks for the reply Lars Noodén.

---

### Post by ankspo71 on 2009-09-28
Hi,
I'm not an expert but I have seen that Partition information takes up space, even when the drive is empty. I see you have one formatted as ext4 but the other is empty (or maybe a dos partition table???). Being that the drives are different sizes, I suspect/guess that the larger one will have more spaced that is used after formatting. If you are unsure of the health of the drives you could test it and wipe it clean with zeros. I don't know of any disk wiping/testing tools for linux off hand, but the one I use is called Powermax by Maxtor. I just found an iso copy here [http://www.tacktech.com/display.cfm?ttid=287](http://www.tacktech.com/display.cfm?ttid=287) among other tools. It doesn't format a drive though, so I use gparted for the actual formatting, or mkntfs in the terminal if I want a ntfs drive .
hope this helps.
James.

---

### Post by Bucky Ball on 2009-09-28
Yep, normal; if sda is an empty 40Gb physical drive.

This is showing usable space. Small area on first part of partition generally reserved for system (for any info your partitioning puts on the drive). Just remember that to format anything you will need to unmount it. If you boot from a Live CD no partitions will be mounted.

---

### Post by Whym on 2009-09-30
Thank you ever so much for the replies both of you.

> **Bucky Ball said:**
> Yep, normal; if sda is an empty 40Gb physical drive.

This is showing usable space.
Maybe you could elaborate a little please? I don't understand how this is normal.
Specifically...
I don't understand how it can be normal to have the pie chart show space is being used, yet on the same dialogue box say the contents is Nothing.

I also don't understand why GParted presents what we see here in the way that it does.

Though the first of the above two issues is, of course, much more important to me than the second one.
Any further help on explaining either of those two issues would be amazing. I would really, really appreciate it.
Thank you.

> **ankspo71 said:**
> Hi,
I'm not an expert but I have seen that Partition information takes up space, even when the drive is empty.
Do I understand correctly, that that  means you have seen this phenomena before?

---

### Post by ankspo71 on 2009-09-30
Yes, I have seen it before. I have two hard drives on this pc (one is for storage), and we have 2 more pc's here... one is my wife's with windows xp and the other is a 10 year old pc that sits in the closet as a spare. Whenever her windows clonks out I erase the hard drive and start fresh. Also, from time to time I swap out our hard drives thinking one would be better than the other (it's a bad habit of mine). So yeah, I see weird things like this too when I compare my hard drives with different apps. As the other poster said, it's normal to see things like this. I think so too. I suppose not all programs interpret drive space the same way too (eg including/excluding partition information and/or reserved space etc).
James

---

### Post by Whym on 2009-09-30
Thank you for the reply, ankspo71!

So if I understand correctly - you are saying it is safe to wipe the drive as there is nothing on it despite the fact that the pie chart show space is being used, (yet on the same dialogue box it says the contents is Nothing) As there is nothing, no actual information, to wipe?
Sorry for the repetition, I am just trying to get things crystal clear.

Again, thanks for the reply.

---

### Post by ankspo71 on 2009-09-30
Hi Again,

Any hard drive is safe to wipe clean with a wiping app as long as there is no information in there that you need, you have a partition editor (which you do in Ubuntu), and if there is no restore partition on the hard drive to restore an operating system. Most windows users these days have a separate restore partition so I wouldn't recommend wiping the drive to them, because they wont be able to go back to windows unless they had a full restore cd handy. Wiping the drive is completely optional and rarely required...but it can be used to help ensure any previous sensitive data can't be recovered in the future, and to ensure that you will be not installing an OS over corrupted partitions (I have only had that problem in windows so far). If this is a used hard drive (especially if you weren't the one using it) then I recommend it, but otherwise you should be good to go as is. Overwriting (wiping) a hard drive can take a very long time, and much longer if you choose to wipe the drives with random data. For me to wipe a 120gb hard drive with zeros, I need about an hour for a single pass. If you are working with a new hard drive, then wiping isn't necessary. I hope I was able to clarify this a little better than the first time.:P 
James

---

### Post by Whym on 2009-10-02
Hi James. Thank you for your reply.
We seem to have a slight mix up in communication.

> **ankspo71 said:**
> ...as long as there is no information in there that you need...
That is what I am trying to determine. That, right there, is my problem.
I don't want to accidently delete any information.
And since it says that space is being used (the pie chart) I do not want to format the drive.
Unless there is some explanation as to how this kind of thing happens - to have the pie chart and the words in that same dialogue box (that say the contents is Nothing) disagree. Which do I trust?
Maybe this is a normal, well known, bug.

Hopefully I have articulated my problem slightly better this time - very much my fault. Sorry for not making myself clear enough.

Again, thank you for the reply.

---

### Post by Whym on 2009-10-12
Does anybody have any knowledge that could shed some light on this?
It seems like a bug to me, but whoever I ask - here and elsewhere there seems to be very little known about it.

---

### Post by louieb on 2009-10-12
If its ext3/ext4 then its reserved space. Its not used - but its not free to anything but a privileged process.  Can be adjusted with tune2fs
> 
       -m reserved-blocks-percentage
              Set the percentage of the filesystem which may only be allocated
              by privileged processes.   Reserving some number  of  filesystem
              blocks for use by privileged processes is done to avoid filesys&#8208;
              tem fragmentation, and to allow system  daemons,  such  as  sys&#8208;
              logd(8),  to continue to function correctly after non-privileged
              processes are prevented from writing to  the  filesystem.   Nor&#8208;
              mally, the default percentage of reserved blocks is 5%.




---

### Post by Whym on 2009-10-17
Thank you ever so much louieb for the reply!

> **louieb said:**
> If its ext3/ext4 then its reserved space.
It appears to be ext3... I think.
One of the drives (as shown in the image in the first post) says it is. The other one does not appear to have any label in that way.
[http://img42.imageshack.us/img42/1487/drivesizequestion.png](http://img42.imageshack.us/img42/1487/drivesizequestion.png)
Do you have an idea of what is going on with that? What does that mean if there is no label there?

So, from what you are saying if it is Ext3/4 then having space show up like that as used is a normal occurrence?
What if it is not Ext3/4, what would the explanation be in that case?

---

