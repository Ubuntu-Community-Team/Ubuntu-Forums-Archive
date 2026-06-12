---
title: "error 18?????"
date: 2006-05-03
forum: General Help
---

### Post by rebelguy on 2006-05-03
when the computer goes to restart to finnish installing  it says

[B]GRUB loading stage 1.5.

GRUB Loading,PleaseWait...
Error 18[/B]

what do i do?

---

### Post by MJN on 2006-05-06
It may be down to your partitions, specifically where that containing /boot is located on your hard disk. Many old(er) BIOSes are unable to boot from the hard disk if the boot code is beyond cylinder 1024.

Anyway, give some details about your hard disk e.g. size, the partitions that you used in the setup and what else is on it and we can take it from there.

Mathew

---

### Post by rebelguy on 2006-05-06
20.8 GB

#1 Primary 20.7 GB    B    F    ext3         /
#5 Logical 131.6 MB        F    swap        swap

only OS is Ubuntu

---

### Post by MJN on 2006-05-07
Okay, that does not seem bad insofar that your root partition is at least at the beginning of the disk...

However, and somebody please feel free to correct me here, there is no guarantee that the 2nd stage of the Grub bootloader is also located near the beginning - sure it will be somewhere in the first 20GB but not necessarilly the first 1024 cylinders (8.5GB?).

So, to make sure it is try repartitioning (and reinstalling I'm afraid but it shouldn't take too long) as per the following:

#1 Primary 50MB (B=Bootable?) F ext3 /boot
#2 Primary 20.2GB F ext3 /
#5 Logical 131.6MB F swap swap

Now your boot code will be right at the beginning and the BIOS should have no problems reaching it. It might be worth, before doing the above, grabbing yourself a copy of the 'Super GRUB Disc' ([http://adrian15.raulete.net/grub/tiki-index.php]("http://adrian15.raulete.net/grub/tiki-index.php")) as, whilst I haven't used it myself (almost had to) I believe it's pretty helpful in these circumstances and might even tell you exactly what's wrong with your current setup.

How old is the machine? Did you choose the swap size? I usually follow the common 2x RAM 'rule'... (You may have also done if your RAM is 64MB and, in which case, I suspect it could be old enough that the 1024 cylinder rule is a relevant and likely cause of your problem)

Mathew

---

### Post by rebelguy on 2006-05-07
what version of the super disk



its an old computer it came with 95 on it

---

### Post by MJN on 2006-05-07
Are you posting from a Windows machine right now? If so, [http://adrian15.raulete.net/grub/tiki-download_file.php?fileId=21]("http://adrian15.raulete.net/grub/tiki-download_file.php?fileId=21") is a bootable floppy creator that'll do the trick. I actually stumbled across the utility having downloaded the 'Ultimate Boot CD' from [http://www.ultimatebootcd.com/]("http://www.ultimatebootcd.com/")

Mathew

---

### Post by rebelguy on 2006-05-07
but this machine isnt the one im installing ubuntu on

---

### Post by MJN on 2006-05-07
Yeah I know - the download at the link I gave will just stick the Super Grub utility onto a floppy then you can put that in your Ubuntu machine, boot from it, and see what it says.

I still think you're going to have to re-partition however - although it would be interesting to see if the SG floppy has anything to say about the situation first.

Mathew

---

### Post by rebelguy on 2006-05-07
can i put it on cd the machine i have dosent have a floppy

---

### Post by adrian15 on 2006-05-08
[QUOTE=rebelguy]can i put it on cd the machine i have dosent have a floppy[/QUOTE]

Yes. Of course. Super Grub Disk comes also as a cdrom version which is multilingual. 

[Downloads of Super Grub Disk Cdrom]("http://adrian15.raulete.net/grub/tiki-list_file_gallery.php?galleryId=1")

Error 18 is about [error 18 explanation]("http://www.gentoo.org/doc/en/grub-error-guide.xml#doc_chap6")

So I think you are going to update your bios (very dangerous) or repartition your hard disk as MJN recommends you.


adrian15

---

### Post by rebelguy on 2006-05-08
which ID number should I use?

---

### Post by rebelguy on 2006-05-08
which ID number do I use -- there is so many choices which one do I use ?

---

### Post by adrian15 on 2006-05-09
[QUOTE=rebelguy]which ID number do I use -- there is so many choices which one do I use ?[/QUOTE]

Do you mean Super Grub Disk version? The biggest one. The most recent one. It will work in your computer even if it is very old.

If I were you I will repartition your hard disk so that you do have an small /boot partition at the beginning of it.

adrian15

---

### Post by rebelguy on 2006-05-11
[QUOTE=MJN]Are you posting from a Windows machine right now? If so, [http://adrian15.raulete.net/grub/tiki-download_file.php?fileId=21]("http://adrian15.raulete.net/grub/tiki-download_file.php?fileId=21") is a bootable floppy creator that'll do the trick. I actually stumbled across the utility having downloaded the 'Ultimate Boot CD' from [http://www.ultimatebootcd.com/]("http://www.ultimatebootcd.com/")

Mathew[/QUOTE]



i saved the file to a thumb drive and extracted it to a floopy on another computer but it dosent work. what do i do?](*,)

---

### Post by MJN on 2006-05-12
<duplicate post removed>

---

### Post by MJN on 2006-05-12
I think your best bet is to reinstall, and this time putting a 50MB partition right at the beginning mounted at /boot as discussed above.
 
I only recommended the grub disc as a quick means to help diagnose the problem - however in the time it's taken to deploy it you could have reinstalled the OS several times over! :)
 
Mathew

---

### Post by rebelguy on 2006-05-12
i did that but it still dosnt work. i wanted to try the floppy on another computer 

see Ubuntu 5.10 instalation problem [http://ubuntuforums.org/showthread.php?t=168606](http://ubuntuforums.org/showthread.php?t=168606)

---

### Post by adrian15 on 2006-05-12
[QUOTE=rebelguy]i saved the file to a thumb drive and extracted it to a floopy on another computer but it dosent work. what do i do?](*,)[/QUOTE]

There are some reasons why SGD should not boot but I think your problem is a different one. You do not have made ok the SGD floppy.

You do have to extract the file to a temporary folder and if I remember well run the .bat file so that a floppy that you will have on a floppy drive will  be "burned" with Super Grub Disk. Nevertheless the zip includes a txt file for you to read!

I've read your conversation about trying to make again an smaller boot partition and it does not work for you. I don't know what can be your problem and I do not have time right now to see the installation problem that you point on a link.

In the last effort we can try a manual installation of grub from a live cd to see if another version grub will do better the job than the one provided by ubuntu. But that will be in another post and another day if you wish to, of course.

adrian15

---

### Post by MJN on 2006-05-12
[quote=rebelguy]i did that but it still dosnt work. i wanted to try the floppy on another computer 

see Ubuntu 5.10 instalation problem [http://ubuntuforums.org/showthread.php?t=168606]("http://ubuntuforums.org/showthread.php?t=168606")[/quote] 
I'm confused - the date of that thread is one week ago yet I only told you to create a /boot partition near the beginning only a matter of days ago... :confused:

Did you, or did you not, try a small partition at the beginning and mounted it at /boot? If so, what was the error? And can you confirm the partition list (as you did in post #3 of this thread)?

Mathew

---

