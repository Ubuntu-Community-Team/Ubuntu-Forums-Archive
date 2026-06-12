---
title: "I made a /home partition... now a question..."
date: 2010-02-11
forum: General Help
---

### Post by jblaven on 2010-02-11
Noob here...  I've messed around with Linux on and off for 10 years or so.  Wow has it come along way.  I just installed ubuntu yesterday on an Emachine.  Everything worked right out of the box!  :p Even my wireless card. I was so pumped, I decided to remove Mepis and install ubuntu on my computer (Emachine is for the kids).

Guess I was shocked at how easy it was after the trouble I had getting the wireless to work with osx86.

Anyway, back to my question.

I saw that it is recommended to make the following partitions, just in case you want to do a reinstall, you will not have to mess with your data files:

/ 29GB
/home 69GB
swap 2GB

I also have windows on the same physical drive on another partition.  My intent was to save my data files to the /home partition, but when I loaded my pictures from a CD-ROM it went straight to / and not to /home.  This automatically gave me a warning that my HD was almost full.  

Is there an OS wide setting that allows all files that are not part of the applications or OS, to be saved to the /home folder automatically?  My / folder is only 29GB, but my /home is 69GB.

I did go into F-Spot and change to where the pictures are automatically imported.  I guess I should have been more alert and watched where I was putting the files.

Joe

---

### Post by Ahadiel on 2010-02-11
When you installed Ubuntu, did you set your 69GB partition to be mounted as /home?

---

### Post by jblaven on 2010-02-11
> **Ahadiel said:**
> When you installed Ubuntu, did you set your 69GB partition to be mounted as /home?

You know, I am not really sure.  I just finished the install.  Sorry about that.  I've gone through it quite a few times, and its all running together! :P

---

### Post by Ahadiel on 2010-02-11
So, you got it working?

---

### Post by jblaven on 2010-02-11
When I rebooted after install, I see the three HD icons on my desktop...

/home 62.9GB
/         26.9GB
swap   3.8GB

---

### Post by Ahadiel on 2010-02-11
> **jblaven said:**
> When I rebooted after install, I see the three HD icons on my desktop...

/home 62.9GB
/         26.9GB
swap   3.8GB

Paste the contents of your /etc/fstab please.

---

### Post by jblaven on 2010-02-11
> **Ahadiel said:**
> So, you got it working?

Well, not really, you know, I guess I should get some rest and try and tackle it in the morning, cause I feel like I'm not thinking straight :lolflag:

---

### Post by jblaven on 2010-02-11
> **Ahadiel said:**
> Paste the contents of your /etc/fstab please.

OK, I'll give it a shot before I sign off...

---

### Post by jblaven on 2010-02-11
Here ya go...

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=b327899c-10df-4116-8e96-a69365ae7328 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=cff79687-ef0f-4ec5-a2f4-8fe177b28d0b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by Ahadiel on 2010-02-11
> **jblaven said:**
> Here ya go...

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=b327899c-10df-4116-8e96-a69365ae7328 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=cff79687-ef0f-4ec5-a2f4-8fe177b28d0b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Yeah, it was what I had thought initially. You did not specify during the installation that you had a separate partition for /home.

So you have 2 options:
1) Modify /etc/fstab to reflect the separate /home partition and copy over your data.
2) Reinstall and specify the separate /home partition during setup. (Probably the simplest out of the two) [http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by jblaven on 2010-02-12
> **Ahadiel said:**
> Yeah, it was what I had thought initially. You did not specify during the installation that you had a separate partition for /home.

So you have 2 options:
1) Modify /etc/fstab to reflect the separate /home partition and copy over your data.
2) Reinstall and specify the separate /home partition during setup. (Probably the simplest out of the two) [http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

=D>

Alright!  That looks like it will work.  I will jump on it in the morning.... as soon as I reinstall, I'll update you guys.

Thanks again for the quick response.

Joe

---

### Post by jblaven on 2010-02-12
> **jblaven said:**
> =D>

Alright!  That looks like it will work.  I will jump on it in the morning.... as soon as I reinstall, I'll update you guys.

Thanks again for the quick response.

Joe

Update.  I think we are in good shape!

---

### Post by Ahadiel on 2010-02-12
> **jblaven said:**
> Update.  I think we are in good shape!

Paste the contents of /etc/fstab just to be sure. :)

---

### Post by jblaven on 2010-02-12
> **Ahadiel said:**
> Paste the contents of /etc/fstab just to be sure. :)

Here ya go! [-o<

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda9 during installation
UUID=53c94851-0e2e-48ee-878a-452f6010dde9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=8070851e-a07c-4d25-b7ce-be8a75b417d5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by Ahadiel on 2010-02-12
> **jblaven said:**
> Here ya go! [-o<

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda9 during installation
UUID=53c94851-0e2e-48ee-878a-452f6010dde9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=8070851e-a07c-4d25-b7ce-be8a75b417d5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Doesn't look like you setup /home correctly.

---

### Post by jblaven on 2010-02-12
> **Ahadiel said:**
> Doesn't look like you setup /home correctly.

](*,)darn

---

### Post by Ahadiel on 2010-02-12
> **jblaven said:**
> ](*,)darn

You following that guide I posted earlier right?

---

### Post by jblaven on 2010-02-12
> **Ahadiel said:**
> You following that guide I posted earlier right?

I tried.  I am re-reading it now to make sure I didn't move too fast during all the excitment! :p

---

### Post by Ahadiel on 2010-02-12
> **jblaven said:**
> I tried.  I am re-reading it now to make sure I didn't move too fast during all the excitment! :p

Well, the ESSENTIAL part of that guide is the custom partition layout.

---

### Post by bruno9779 on 2010-02-12
There is another way.

Not easier, but didn't involve reinstalling.
Psychocats has an excellent tutorial on moving /home to its own partition here:

[http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/)

---

### Post by jblaven on 2010-02-12
> **bruno9779 said:**
> There is another way.

Not easier, but didn't involve reinstalling.
Psychocats has an excellent tutorial on moving /home to its own partition here:

[http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/)

Thanks Bruno,

I don't have any personal files on the computer that can't be put back on in about 30 seconds.  Plus I already started reinstalling.  I'll keep your link as backup.

---

### Post by jblaven on 2010-02-12
OK, 

I am ready to set up my swap partition.

Do I need to set it up as primary or logical?  Also, do I need to set a mount point for the swap partition?

I'll sit tight till I hear back :popcorn:

---

### Post by jblaven on 2010-02-12
> **jblaven said:**
> OK, 

I am ready to set up my swap partition.

Do I need to set it up as primary or logical?  Also, do I need to set a mount point for the swap partition?

I'll sit tight till I hear back :popcorn:

Think I just answered my question while looking at the options.  The swap will not have a mount point.

---

### Post by jblaven on 2010-02-12
> **Ahadiel said:**
> Yeah, it was what I had thought initially. You did not specify during the installation that you had a separate partition for /home.

So you have 2 options:
1) Modify /etc/fstab to reflect the separate /home partition and copy over your data.
2) Reinstall and specify the separate /home partition during setup. (Probably the simplest out of the two) [http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)


OK,

I followed step 2, and I think I did it right this time...

Problem is now, I am unsure of how to access the /etc/fstab

What's the easiest way for a noob to get to this file?

Thanks

---

### Post by flippo on 2010-02-13
```
gksu gedit /etc/fstab
```

Be very careful modifying fstab, if you screw it up you may end up with an unbootable system, and have to fix it with a live-cd.

---

### Post by jblaven on 2010-02-13
> **flippo said:**
> ```
gksu gedit /etc/fstab
```Be very careful modifying fstab, if you screw it up you may end up with an unbootable system, and have to fix it with a live-cd.

I guess I should be more specific...  I tried to do a search for it, so I can cut and paste it here for you guys to check it.  Need you to tell me if I did it right.  The way Linux organises its files are quite different than what I am used to and I am having difficulty searching for it.

Any ideas on how to pull it up so I can just copy and paste?  I did it earlier, but for some reason, when I search for it, no luck.

---

### Post by flippo on 2010-02-13
that command will open it, then you can view or edit it.  If you want to make sure you don't edit it then just open a terminal and type ```
cat /etc/fstab
```That will display its contents in the terminal, you can copy and paste from there.

---

### Post by jblaven on 2010-02-13
> **flippo said:**
> that command will open it, then you can view or edit it.  If you want to make sure you don't edit it then just open a terminal and type ```
cat /etc/fstab
```That will display its contents in the terminal, you can copy and paste from there.

There we go!

joe@joe-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=cb4ff98d-d908-45af-9cd9-7ec70caa91c7 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=a5aa61ed-72c4-46e5-9ae8-456cf2cebad6 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=a80337bc-5172-49cb-9ef6-52ab08e089ea none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
joe@joe-desktop:~$

---

### Post by flippo on 2010-02-13
looks correct to me.  As you can see by the fstab / is on sda2 and /home is on sda3.  If you type 'df -h' into a terminal you can also see where your partitions are and what their sizes are.  If this is what you tried to set up, it looks like you did it.

---

### Post by jblaven on 2010-02-14
> **flippo said:**
> looks correct to me.  As you can see by the fstab / is on sda2 and /home is on sda3.  If you type 'df -h' into a terminal you can also see where your partitions are and what their sizes are.  If this is what you tried to set up, it looks like you did it.

Sweet!  Thanks for everyone's help!

---

