---
title: "Backup solution for Windows / Ubuntu dual boot all in one shot..."
date: 2011-09-13
forum: General Help
---

### Post by killabee44 on 2011-09-13
Guys,

I set up a couple of machines for friends with dual boot windows/ubuntu and would like to know if there's a backup solution that can handle backing up and restoring both operating systems in one shot.

Usually I stick with Acronis for Windows, but I  tried it and the restore did not work on the Ubuntu side. Windows was fine though.

Im looking to restore a complete hard drive with both operating systems as well as Grub.

So, what do you guys suggest? Thanks.

---

### Post by lmarmisa on 2011-09-13
> **killabee44 said:**
> Guys,

I set up a couple of machines for friends with dual boot windows/ubuntu and would like to know if there's a backup solution that can handle backing up and restoring both operating systems in one shot.

Usually I stick with Acronis for Windows, but I  tried it and the restore did not work on the Ubuntu side. Windows was fine though.

Im looking to restore a complete hard drive with both operating systems as well as Grub.

So, what do you guys suggest? Thanks.

I recommend Clonezilla Live:

[http://www.clonezilla.org/](http://www.clonezilla.org/)

---

### Post by b2zeldafreak on 2011-09-13
I recommend this as well.

---

### Post by killabee44 on 2011-09-13
Thanks guys, I was just reading about clonezilla too.. :)

Do you all know what the ppa for clonezilla is?

Weird that it's not listed on their site.

---

### Post by lmarmisa on 2011-09-15
Clonezilla is not a package integrated in Ubuntu. Clonezilla is a Live CD / USB.

[http://www.clonezilla.org/downloads/stable/iso-zip-files.php](http://www.clonezilla.org/downloads/stable/iso-zip-files.php)

---

### Post by haqking on 2011-09-15
> **killabee44 said:**
> Thanks guys, I was just reading about clonezilla too.. :)

Do you all know what the ppa for clonezilla is?

Weird that it's not listed on their site.


Download and burn the .iso.  You boot to it and clone a part or disk to destination part/disk or image.

Make sure your Filesystems are dismounted cleanly, if you get any errors choose a expert clone and choose the 

fsck-part expert option

and should fix it.

other than that its pretty much like Ghost but better ;-)

you can also setup a clonezilla server if you want to

---

### Post by killabee44 on 2011-09-15
The backup worked great. Thanks for all the help guys, I appreciate it.

---

### Post by killabee44 on 2011-09-15
Ok, guys I have another question.

Some friends I know own two HP laptops. Exact same model numbers and everything. 

If I already reinstalled windows and also installed ubuntu on the first machine (lets call it laptop #1) and did a Clonezilla backup. Can I restore that backup to laptop #2?

Im sure the answer will be no since it will cause network problems, but I thought I'd ask anyway. 

Is there a way around this?

**Not looking forward to doing everything all over again on the 2nd machine. :(

What do you all think?

---

### Post by haqking on 2011-09-16
> **killabee44 said:**
> Ok, guys I have another question.

Some friends I know own two HP laptops. Exact same model numbers and everything. 

If I already reinstalled windows and also installed ubuntu on the first machine (lets call it laptop #1) and did a Clonezilla backup. Can I restore that backup to laptop #2?

Im sure the answer will be no since it will cause network problems, but I thought I'd ask anyway. 

Is there a way around this?

**Not looking forward to doing everything all over again on the 2nd machine. :(

What do you all think?


You can restore an image to any hard drive you like as long as the HDD destination is the same size or larger than the source.

As for issues in this case i suspect they will be minimal as when things boot up they will  just be seen as a hardware change or something, you may need to modiy IP adresses etc if they were set to static and will now be the same as the source but should be ok for the most part

---

### Post by killabee44 on 2011-09-16
> **haqking said:**
> You can restore an image to any hard drive you like as long as the HDD destination is the same size or larger than the source.

As for issues in this case i suspect they will be minimal as when things boot up they will  just be seen as a hardware change or something, you may need to modiy IP adresses etc if they were set to static and will now be the same as the source but should be ok for the most part

Haqking,

The reason I ask is that I remember back in the day with windows we had to use a program called Sysprep when we dropped the same image on multiple machines that had the same hardware.

What it did was (other than reset the windows activation) to reset the computer security identifier (SID). 

I wasn't sure how that would work in Ubuntu.

---

### Post by haqking on 2011-09-16
> **killabee44 said:**
> Haqking,

The reason I ask is that I remember back in the day with windows we had to use a program called Sysprep when we dropped the same image on multiple machines that had the same hardware.

What it did was (other than reset the windows activation) to reset the computer security identifier (SID). 

I wasn't sure how that would work in Ubuntu.


yah im familiar with sysprep and ghost and sysdiff and the SID issue.

Linux handles hardware differently to windows.  I am not saying there wont be any issues, the main one with windows when sysprep it on a network was computer names and such due to netbios broadcasts and the like.

If i was you make the clone as simple as possible and then do it, like i said you may get IP add conflicts is using statics obviously, as for computer name you can change that, Linux does not broadcast a netbios name.

[http://www.linuxjournal.com/article/10884](http://www.linuxjournal.com/article/10884)

There are also others such as clonesys etc.

remember that in Linux you may have ssh keys or services unique to the machine.  As far as a desktop build goes should be failry straight forward, you said the harware is similar so no great shakes i doubt.  

Just have a backup of everything before cloning such as a clone of the machine you are cloning over and of course the personal data.

But for what you need the old windows SID thing wont be an issue and as long as using DHCP shouldnt really have to change much at all if anything.

The windows partition comes back to the old rules though ;-)

And i am saying all this based on not knowing your actual machines or hardware of course.  but i clone builds of other peoples machines into VM environements all the time with no real issues, and have done so to other machines as a full build.  Every situation is unique

---

### Post by killabee44 on 2011-09-16
Thanks haqking...

Good to know Linux is superior in yet another way :D


I appreciate the knowledge.

---

