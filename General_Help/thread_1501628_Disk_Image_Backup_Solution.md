---
title: "Disk Image Backup Solution"
date: 2010-06-04
forum: General Help
---

### Post by Kieron on 2010-06-04
I need a solution to backup my Ubuntu systems, a mix of desktop and servers. Hopefully, it can run on my Win systems too.

I've tried Clonezilla, but you can't mount the backups (be it on windows or linux) to fish for files manually which is a necessity in my case.

Also tried Acronis but I've heard its got a habit of corrupting itself, plus I believe it doesn't support ext4. Plus, I just tried it on my ext3 system and it's reporting a bad filesystem, despite me checking it within ubuntu.

Can anyone point me in the right direction of a possible solution? One of my servers is down and I am literally at wits end waiting to back up the system so I can reinstall w/ vmware-server.

For reference, the system is Ubuntu Lucid Lynx 10.04.

Thank you,
Kieron

---

### Post by Manyette on 2010-06-04
Hi Kieron,
Not sure this is any help, but my strategy is to use Clonezilla for backups after major system changes, and backup of the home directory using tar in between those backups.  One hitch is that Clonezilla does not at this moment work with ext4 formatted drives.  I've used ext3 on my drives for that reason.  Just a thought.

---

### Post by Kieron on 2010-06-04
> **Manyette said:**
> Hi Kieron,
Not sure this is any help, but my strategy is to use Clonezilla for backups after major system changes, and backup of the home directory using tar in between those backups.  One hitch is that Clonezilla does not at this moment work with ext4 formatted drives.  I've used ext3 on my drives for that reason.  Just a thought.

Thanks for the speedy reply.

Yeah I might have a look at going back to clonezilla for now. The drive is indeed ext3, and I've got an idea that I could theoretically create a virtual machine in vmware workstation on my windows desktop and restore the backup onto that, then ssh-ing to retrieve files.

Thanks again! :)

---

### Post by User Abuser on 2010-07-20
> **Manyette said:**
> Hi Kieron,
Clonezilla does not at this moment work with ext4 formatted drives

Maybe I have got something wrong here, but here is a quote from Clonezilla@Launchpad
> Ext4 is supported by partclone now. Therefore if you want to save ext4 system, remember to enter expert mode and use option -q2 so that partclone will save your ext4 partition. //NOTE// In this release, grub does not support ext4. Therefore if your /boot/grub is in ext4 partition, please try experimental Clonezilla live 20090517-jaunty.
That is more then a year before your message. Just making sure that anyone who will read this thread won't take false information. Backing up ext4 is to everyones concern right now since many users migrating or just want to try Linux.
 Also any of you reading should know that Acronis True Image 2011 has ext4 documented and is up for beta testing right now.

---

### Post by Manyette on 2010-07-20
That is true if you use it's "expert mode", but I'm not comfortable with that.  In fact when I installed Lyric, I formatted it as ext3 just for that reason. I'm sure that an expert could use it that way, but I wouldn't advise it for someone new to Ubuntu.  Just overly cautious I guess.

---

### Post by User Abuser on 2010-07-21
It's hard to judge cause I'm not novice, but most of the time using clonezilla you can just "enter" your way forward =)) Choices "by default" are set so that you'll prolly get what you want. You just need to read the tips carefully. Most time they say "If you don't understand just leave it" =D Anyway the point is that i'm not an expert for sure, but I've already did two restores. Couldn't figure how to save GRUB thou =\ Any help??

---

### Post by Manyette on 2010-07-21
Well, I am DEFINITELY no expert, but I have done many clonezilla backups, and I have done one restore to be sure that it works, and I have not had any problem with GRUB2.  This restore was done after a format of the hard disk.  Again, this is with ext3.  When I was using Karmic, it was an ext4 drive, and the restore did NOT work, and in fact, even the backup behaved "funny".  That's why I set up Lyric with ext3. I'm not sure that this is of any help for you, but this was my experience so far. If I've misinformed anyone, I do apologize.

---

### Post by User Abuser on 2010-07-21
> **Manyette said:**
> I have not had any problem with GRUB2.  This restore was done after a format of the hard disk
Aha. So it does save mbr to your / partion image. Thanks
I guess i'll have to take one of my old bad blocked drives and test stuff myself =)
Recently a lot more users started to install linux so I expect a variety of backup software supporting ext4.

Anyone willing to mingle with this, here's a list of software that drew my attention:
Clonezilla
True Image Home 2011 (1st stage beta)
R-drive image
Paragon Hard Disk Manager 2010
Mondo rescue

---

### Post by aeiah on 2010-07-21
clonezilla just creates a partition image, doesnt it? looks like it can create a duplicated copy of the data also...

if you go down the partition image route or use dd instead, then you can mount the image file elsewhere just like you'd mount any other partition, more or less.

---

### Post by Manyette on 2010-07-21
For what it is worth, I do a clonezilla backup once a week, and in between I use tar to backup home after any significant change.

---

### Post by User Abuser on 2010-07-21
dd includes your intire partion and not only data. That's not the way I wanna go.
And this is from clonezilla.org
> Due to the image format limitation, the image can not be explored or mounted. You can _NOT_ recovery single file from the image
So right now I agree with Manyette: Use zilla for system backups and simple .tar for data.
I don't make any promises, but if I manage to test out the software i've mentioned I'll surely post

---

### Post by Manyette on 2010-07-21
I will stand to be corrected, but so far as I know, DD is used only for the first sector and the 61 sectors following that, so that it will be a bare metal recovery, which is why I like it, even at the expense of staying with ext3.  The remaining data is stored using partclone I believe, but you are correct in that single file recovery is not possible, and that is why I use tar for everything except for the bare metal recovery possible with clonezilla. If partclone now works with ext4, then that would be a major improvement, but last time I tried it, some months back, it did not.

---

### Post by User Abuser on 2010-07-21
Sorry, I meant dd in s-by-s mode for ext4 which i'm using.
Clonezilla uses partclone to image ext4 so it obviously supports it =)
[http://partclone.org/](http://partclone.org/)

---

### Post by Manyette on 2010-07-21
Well, now I'm rather sorry to have loaded ext3, but it has worked well, so perhaps at some time in the future I will go to ext4, but it didn't work for me when I tried it last.  Next time a new LTS comes out, perhaps.

---

### Post by User Abuser on 2010-07-21
Yeah, even better. There will prolly be more features, stability and intel by that time)
 As for speed alone, since I have 7 harddrives at home I gave ubuntu a good spin installing it on different fs and personally didn't notice any perceivable performance differences.

---

### Post by Manyette on 2010-07-21
Well, you do a lot better on your "second" than a lot of folks do on their first!

---

### Post by User Abuser on 2010-07-21
Haha thanks :KS That was just my siggy for them gramma-nazy roaming

---

