---
title: "Best way to image entire laptop HD"
date: 2010-11-01
forum: General Help
---

### Post by skew on 2010-11-01
I have a problem with my one month old Sony Vaio laptop. It's emitting a intermittent high pitched tone from the CPU fans. I work in a quiet environment and it very aggravating and slowly getting louder. Sony service tells me that upon return for service they will wipe the drive and restore it to factory conditions before returning it, standard practice it seems.

    My question is what is the best method to use to make a complete image/copy of the entire drive? The drive includes several partitions besides the usual stuff like the MBR. There is a recovery partition, repair partition, Win7-64bit OS, and (2) Ubuntu partitions. 

 When I get the drive back I would like to restore it to the condition I had it in before sending it in for service. I do have an external eSata drive connected via an eSata port which is plenty large enough to house the image/copy while I wait to get the computer back.  

 Which is the best software to use: dd, gddrescue, Clonezilla, other? I've heard Clonezilla is good and fast, but will it do what I want, making a bitwise copy/image? I also have a live disk of it. However I've also heard that dd is the preferred tool of choice as long as you don't make any mistakes in the command line, otherwise you've toast! I've also heard it's painfully slow. Finally I've read that gddrescue is easier then dd. Is there anything I'm missing? 

Suggestions? Maybe even a command line example (if that type of tool is the best) for a sda to sdb copy would be appreciated.  My greatest concern is getting everything that on the drive now, off and saved so it can be restored perfectly when I finally get the laptop back. 

I have read other posts on the subject, however since this dive has several partitions with assorted file systems, etc. My concern is that it may be more complicated requiring a specific approach. 

Thanks all!

---

### Post by Quackers on 2010-11-01
That does seem to be standard procedure for Sony service. In fact every time I have phoned them for support they just ask you to recover the system back to day 1. Their answer for everything.
I have used Clonezilla and have restored from the backup image as well. All went without a hitch with the actual backup/restore. However you may have to re-install grub after the restore, as Clonezilla doesn't seem to be able to manage that. That's only a 5 minute job though.
By the way, if you haven't made the recovery discs yet, I would hurry :-)

---

### Post by skew on 2010-11-01
> **Quackers said:**
> That does seem to be standard procedure for Sony service. In fact every time I have phoned them for support they just ask you to recover the system back to day 1. Their answer for everything.
I have used Clonezilla and have restored from the backup image as well. All went without a hitch with the actual backup/restore.


From another post I read I understood that it would only preform a file copy not a bitwise copy. Is that correct? BTW, did you backup multiple OS's, all in one go with Clonezilla?

> **Quackers said:**
> 
 However you may have to re-install grub after the restore, as Clonezilla doesn't be able to manage that. That's only a 5 minute job though.


How's that done w/ grub2?

> **Quackers said:**
> 
By the way, if you haven't made the recovery discs yet, I would hurry :-)

That's the first thing I did when I got it home. 8-)

---

### Post by yiannis66 on 2010-11-01
have you read about remastersys ?
[http://www.geekconnection.org/remastersys/]("http://www.geekconnection.org/remastersys/")

---

### Post by EricJonsson on 2010-11-01
dd does what you want, and it's not really slower than anything else if you tell it to read chunks larger than the default 1 byte. Read the manpage carefully, and you ought to be good. :)

---

### Post by Quackers on 2010-11-01
Clonezilla can make bit by bit, partition by partition disk images.
You re-install grub from the Ubuntu Live CD, details here
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by skew on 2010-11-01
> **EricJonsson said:**
> dd does what you want, and it's not really slower than anything else if you tell it to read chunks larger than the default 1 byte. Read the manpage carefully, and you ought to be good. :)

I even printed out the man page. :)

Any suggestion on an appropriate block size?

Is this Correct?
**dd if=/dev/sda bs=1024 of=/dev/sdb **

And...am I right that this operation must be done from a USBkey or live disk?

Finally will the drive I copy be a mirror of the laptops drive or is the information on that drive compressed ,etc in some way?
I ask as I want to know if I'll be able to get specific files off of it if something screws up along the way.

Thanks

---

### Post by skew on 2010-11-01
> **Quackers said:**
> Clonezilla can make bit by bit, partition by partition disk images.
You re-install grub from the Ubuntu Live CD, details here
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Thanks I'll print that out as well.

So far it's Remastersys, dd & Clonezilla. Any reason to choose one over the other, or not? :confused:

---

### Post by Quackers on 2010-11-01
All I can say is that Clonezilla worked ok for me, except the grub thing. The dd command can include compression of the output file. Remastersys I looked at but it seemed like a bit of work to me, but that was a while ago and may be different now.
Good luck with your headache :-)

---

### Post by matt_symes on 2010-11-01
Hi

Its personal choice really. They will all do the job you want. Personally i've used clonezilla. dd can be a bit slow and i have never remastersys but i do believe it covers your requirements.

Kind regards

---

### Post by skew on 2010-11-01
Thanks again everyone for bearing with me on this. Just a couple of final questions. 

First, do any of these tools verify the clone/copy? 

Two, and I do know I asked this one earlier.  Will the drive I copy to be a *mirror* of the laptops drive or is the information on that drive scrambled, converted ,etc in some way?  I do appreciate I have the option to compress it if I wanted, An option i don't exptect to use. Basically I'm asking if the copied information will still be in a readable workable format where files could be extracted if desired. I'm referring specifically to dd and Clonezilla (my current coin toss choices) unless I don't like the answers to the above)

And Quackers. Thanks for you kind words on my growing headache ](*,) I do have aspirin at the ready as most of my head pain has come from pulling out what little hair I have left. ;-)

---

### Post by CharlesA on 2010-11-01
> **Quackers said:**
> All I can say is that Clonezilla worked ok for me, except the grub thing. The dd command can include compression of the output file. Remastersys I looked at but it seemed like a bit of work to me, but that was a while ago and may be different now.
Good luck with your headache :-)

With Clonezilla, you can go into "expert mode" and tell it not to reinstall GRUB and it'll leave the MBR alone.

I don't think Clonezilla verifies the cloned image, but you can always restore the image to a VM or to the same machine to test, that's what I do.

Else you can run this:

```
cat /path/to/diskimage/sda* | gzip -tv -
```

Change sda to sdb or whatever the name of the partition is.

---

### Post by Quackers on 2010-11-01
> **CharlesA said:**
> With Clonezilla, you can go into "expert mode" and tell it not to reinstall GRUB and it'll leave the MBR alone.

I don't think Clonezilla verifies the cloned image, but you can always restore the image to a VM or to the same machine to test, that's what I do.

Else you can run this:

```
cat /path/to/diskimage/sda* | gzip -tv -
```

Change sda to sdb or whatever the name of the partition is.

Thanks for that CharlesA, I hadn't tried expert mode :-)

---

### Post by skew on 2010-11-01
This is a stupid question I'm sure, but neither of these tools harm the original drive in the process of imaging/cloning said drive right? Harm meaning erase /delete not destroy.

---

### Post by matt_symes on 2010-11-01
hi

No. The original drives will be fine. 

Kind regards

---

### Post by CharlesA on 2010-11-01
> **skew said:**
> This is a stupid question I'm sure, but neither of these tools harm the original drive in the process of imaging/cloning said drive right? Harm meaning erase /delete not destroy.
Correct.

That's why I usually test the image in a VM to make sure it restores ok.

If it fails, I can just clone the drive again. :)

---

### Post by skew on 2010-11-01
> **matt_symes said:**
> hi

No. The original drives will be fine. 

Kind regards


Okay then, that's it. I'll give it a go. 

Oh and I found the answer to the retrieving of "individual files" question.  Apparently it's **no** with either of these tools although Clonezilla mentions a workaround method using a VM, although I'd imagine the same could apply to dd as well. none the less I'm going with Clonezilla.  

I'll report back when I've got something to report.

Thanks everyone, you've all been most helpful. Wish me success[-o<

---

### Post by skew on 2010-11-03
> **skew said:**
> 

I'll report back when I've got something to report.



Report: Success

  I started with loading into RAM the tools from a Parted Magic CD I had burned from an ISO. 
I had originally planned on using Clonezilla but my external drive was not recognized as it was new 
and without any file system. As I didn't know which was the best FS to format the drive to with 
Clonezilla I opted to go with dd instead. It was dead simple to use. My only complaint was the lack 
of a verbose option to monitor it's progress. The command I used was: 

dd if=/dev/sda of=/dev/sdb bs=1k

I let it run overnight and the next morning it had finished, reporting no errors. I then tried to boot
from the external drive onto the laptop without success even though I had set the boot order in the BIOS 
correctly. All I got was a non-blinking cursor. I didn't want to remove the internal HD and try again so
I rebooted the from the backed up drive onto a separate desktop computer. It booted perfectly and seems to work 
flawlessly, albeit a bit slower since the two systems are quite different. I did not however boot into my 
Win partition as I was not sure how that OS would take to the desktop since it came with the laptop and is 
therefore bound it. I am hoping that since the other Ubuntu partitions worked correctly that it was backed 
correctly as well. 

Now I can send my laptop off to get serviced, assured of restoring the systems when I get it back.

Once again thanks to all who helped!:D

---

