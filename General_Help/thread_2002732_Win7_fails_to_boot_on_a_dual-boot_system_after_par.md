---
title: "Win7 fails to boot on a dual-boot system after partition move"
date: 2012-06-13
forum: General Help
---

### Post by okok on 2012-06-13
I have both windows 7 and ubuntu 12.04 (dual boot) on the same HD. I moved my windows 7 partition alightly to the "left" using GParted in order to solve a partition misalignment problem.

The operation was completed succesfully, but now when I choose windows7 from the grub menu, I get a a windows message saying "Windows failed to start. A recent hardware or software change might be the cause." It also says "the boot selection failed because a required device is inaccessible". It suggests that I boot from the windows installation DVD and choose "Repair your system".

When I choose Ubuntu from the grub menu it loads normally. I can also access the files on my NTFS (win7) partition. I don't think any information was lost there.

What would be the right way to fix the windows 7 boot problem? If I use the repair option from the windows DVD, is it likely to prevent me from loading ubuntu (and require fixing the grub menu)? Is there a risk it might harm with my linux partitions?

---

### Post by Kalma on 2012-06-13
Likely, grub is pointing to a different partition after moving them.

First, be sure the Windo$ partition is a Primary one, or it won't boot.

Second, try to reset grub, using:

```
sudo dpkg-reconfigure grub
```

If still not working, try this
[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by fantab on 2012-06-13
What do you mean by " I moved my Windows7 partition to the left"? Did your action change the partition number?

Try from Terminal:

```
sudo update-grub
```

And try again to boot into Win7.

---

### Post by Jonny87 on 2012-06-13
Try the following from your Ubuntu;

```
sudo update-grub
```

Then try booting Windows.

---

### Post by okok on 2012-06-13
Thank you all, but it is likely to assume that the problem is with grub if the message presented is a message of the winodws OS? The order of partitions didn't change, and it is the windows loader, not grub, that gives the error message and can't find what it is supposed to find.

What I meant by "moving the windows partition to the left" was this. My first partition is a small fat16 partition containing diagnostics utilities that came pre-installed with my computer. The next primary partition is the NTFS one on which windows is installed. Then I have a linux-swap and a linux partition. What I did was to shrink the fat16 partition from 100mb to 99mb and move the NTFS partition to the point where the fat16 partition ends so that there is no unused space between them. (Then I also expanded the linux swap, the 3rd partition, to fill up the small space created by moving the 2nd partition.)

---

### Post by Kalma on 2012-06-13
Sorry, I made a mistake when copying the command. The complete command is (assuming you have GRUB2):


```
sudo dpkg-reconfigure grub-pc 
```

---

### Post by okok on 2012-06-13
As I suspected, updating/reconfiguring GRUB made no difference. The problem has nothing to do with grub, because the message I get is from the windows boot manager, not from grub, and thus belongs to the internal workings of the windows OS.

From what I read in other places, running "repair" from the windows 7 DVD is supposed to fix this. However, I am still no sure whether this may mess with my non-windows partitions, or with grub, and prevent me from loading ubuntu.

---

### Post by Jonny87 on 2012-06-13
I'd still try updating grub if you haven't already. because yes, if you use the Win 7 recovery you will lose grub and have to reinstall it by booting to a live CD and issuing a series of commands to reinstall it which while it is possible, its just tedious and more time consuming especially if update grub happens to work. 

If fix up the grub boot loader doesn't work then I would have to say use the Win7 Recovery to reinstall the windows boot loader.

---

### Post by Jonny87 on 2012-06-13
> **okok said:**
> As I suspected, updating/reconfiguring GRUB made no difference. The problem has nothing to do with grub, because the message I get is from the windows boot manager, not from grub, and thus belongs to the internal workings of the windows OS.

From what I read in other places, running "repair" from the windows 7 DVD is supposed to fix this. However, I am still no sure whether this may mess with my non-windows partitions, or with grub, and prevent me from loading ubuntu.

Ignore the first part of my last post sorry. Yes, the grub will be replaced. but it can be reinstalled from CD.

---

### Post by Topsiho on 2012-06-13
I think that it is Windows that is confused by the new HD situation that it finds when booting. You changed a partition, and Windows discovers it was changed and complains about it.

Not sure how to solve this, but in the future you can prevent this by applying changes to the partitions that Windows uses in Windows itself.

I read somewhere that possibly you should give Windows time to sort things out when booting Windows (probably it checks the disk, and this takes time).

Topsiho

---

### Post by Kalma on 2012-06-13
I assume you have already run both commands (update and reconfigure), and still not working.

Have you checked if the Windows partition is Primary? Use testdisk to check and eventually repair the status of your partition table... Perhaps the problem is there. I think it is worth before re-installing.

[http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")

---

### Post by okok on 2012-06-13
I followed window's own advice and used the 'repair my computer' tool from the windows DVD. I had prepared myself to having to re-install grub, but this time I was pleasantly surprised by windows: the fix took less than a mintue, and when it finished, my grub menu remained intact, and I am now able to load both windows and linux again as before.

---

### Post by Kalma on 2012-06-13
Good news, Congratulations!!!

You were right, it was not grub, but Windows itself. Likely it was needing something at the very beginning of the partition which was lost after moving it...

---

### Post by Jonny87 on 2012-06-13
> **okok said:**
> I followed window's own advice and used the 'repair my computer' tool from the windows DVD. I had prepared myself to having to re-install grub, but this time I was pleasantly surprised by windows: the fix took less than a mintue, and when it finished, my grub menu remained intact, and I am now able to load both windows and linux again as before.

Well trust Windows to never play by the rules and prove everyone wrong.

Obviously windows was able to fix it with out fully replacing the boot loader. The Windows boot loader will allow you to boot multiple Windows installs, but not Linux. Thus I was expecting that if it replaced grub then you'd have to re-install grub. Been there done that all before to day.

Oh well all good for you then. Be sure to mark your post as Solved.

---

### Post by fantab on 2012-06-13
Good... you solved your problem.

---

### Post by Mark Phelps on 2012-06-13
> **okok said:**
> I followed window's own advice and used the 'repair my computer' tool from the windows DVD. I had prepared myself to having to re-install grub, but this time I was pleasantly surprised by windows: the fix took less than a mintue, and when it finished, my grub menu remained intact, and I am now able to load both windows and linux again as before.

So, you learned a valuable lesson: do NOT use Linux filesystem tools to mess around with Windows filesystems.  Doing so can render your Windows filesystems unbootable.

You could have done all of this safely using Windows filesystem tools -- and not only the ones from Microsoft.  There are FREE, downloadable Windows filesystem partitioning tools -- which would have done this without corrupting the Windows boot.

---

### Post by okok on 2012-06-13
> **Mark Phelps said:**
> You could have done all of this safely using Windows filesystem tools -- and not only the ones from Microsoft.  There are FREE, downloadable Windows filesystem partitioning tools -- which would have done this without corrupting the Windows boot.

Possibly, but as far as I know, at least the built-in tools aren't capable of handling non-microsoft file systems, so they might not be of help where changes to other partitions are necessary too. In this case I could, perhaps, do some of the tasks from within windows and some using linux tools.

---

