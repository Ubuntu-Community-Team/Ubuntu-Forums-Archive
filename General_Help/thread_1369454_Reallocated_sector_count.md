---
title: "Reallocated sector count"
date: 2010-01-01
forum: General Help
---

### Post by halfstrike on 2010-01-01
So, i booted up my laptop in the vista partition and soon after got a BSOD  and  vista wouldn't boot back up so i booted up ubuntu 9.10 and like a true champion ubuntu came on and  isolated my problem and told me what it was . It was that my hard drive had many bad sectors so i checked it out and it turns out my hard drive has 196611 bad sectors so im going to get a new hardrive. So my question is how can i back up all my files in both my vista and my Ubuntu partition.

---

### Post by Herman on 2010-01-01
:) Here's a link, [Learn the dd Command]("http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/") - LinuxQuestions.org

```
dd if=/dev/sda of=/dev/sdb   conv=notrunc,noerror

```The above command will clone an entire hard disk to another hard disk, (such as an external USB drive for example), of equal size or larger than the one you're copying from.

---

### Post by Herman on 2010-01-01
```
dd if=/dev/sda of=/dev/sdb bs=4096 conv=notrunc,noerror
```
I forgot something, the 'bs=4096' is important because it allows the command to get the work done a lot faster. 

Be careful with the dd command, it would be best if you study the web page I linked you to first, the dd command is powerful and it's a great tool when used properly, but it can also be destructive to your data if you use it the wrong way around.

---

### Post by halfstrike on 2010-01-01
thanks man i will study that page and try it out

---

### Post by Herman on 2010-01-01
I used the dd command for copying Vista to a new hard drive after somebody's laptop hard drive was damaged from the lid being slammed, (by a user losing their temper).
I copied the enitre hard disk to a slightly larger USB external hard drive. When the replacement for the laptop hard drive arrived, which was larger again, I copied it from the USB external to the new drive.

But I had a lot of trouble getting it to boot up.

The reason turned out to be that the damage to the original hard drive turned out to have been physically located somewhere in the middle of the hard disk, and thus near the middle of the operating system partition. Since the dd command makes a perfect copy, it was copying the damage as well as the good parts, (from what I can deduce).

The procedure that eventually worked was to use  with GParted in Ubuntu to resize Vista first, so that it no longer occupied the damaged area. Then I tried again with the dd command. Windows needed a CHKDSK first, but it booted and ran and tidied itself up, and as far as I know has been fine ever since.

The reason I'm telling this story is because I'm impressed with GParted's ability to cope with the damaged hard disk and resize Vista successfully in spite of the damaged sectors. 
It might help somebody someday to be aware that resizing with GParted might help in some circumstances.
Normally I wouldn't want to touch an already damaged file system for fear of mixing things up and making things worse.
EDIT: I just remembered to mention that when resizing Vista or Win7 with GParted, it's important to remove the tick mark from 'align with cylinder boundaries', that saves a lot of time.

I don't think you'll need to do that because in your case the bad sectors are probably random and anyway, they've possibly already been mapped out by the file system.

The command CHKDSK /R, run from a Windows Recovery console does a thorough file system check in a Windows partition and attempts to recover data from bad sectors.
I think that most data recovery experts try to preserve the original hard disk as it is and work on a copy of it as a rule whenever possible.

One more thing anyone might need to know when cloning Vista or Windows 7 to a new hard disk is that their boot loaders are coded to the original hard disk's ID number in the MBR. 
You need to make sure you copy the entire disk every time with the dd command and not just the partition so that you will be copying the MBR too.
If you only copy a partition at a time, you should also make a separate copy of the MBR with another dd command which will include the hard disk's ID. It's within the first 446 bytes, right before the partition table.
You won't need to worry about it since you're dd'ing the entire disk.

---

