---
title: "Dual boot Vista &amp; U9.10, to add U10.10 and tri-boot?"
date: 2010-10-08
forum: General Help
---

### Post by deadmanschest on 2010-10-08
Hi all - would ask some advice before committing myself to problems.

Before today, a 4GB RAM 64 bit laptop with single 320GB HDD, Vista x64 primary NTFS partition of 60GB for C Drive, then Ubuntu 9.10 64bit on primary ext3 partition of 25GB, no swap partition but swap file I added, then what was an extended NTFS partition that contained the Vista D drive with all my app data, documents and media on 4 or 5 logical partitions.

I boot into GRUB and choose Vista or U9.10, U9.10 by default, and access the NTFS D:drive to share media, documents,config profiles for Firefox and ThunderBird, etc.

The Ubuntu install came from my first try at 8.04, and has been upgraded to 9.10, so it's okay but not great. For example, suspend and hibernate are screwed up because there's no swap partition, I believe, and I would like a more optimal fresh installation of U10.04 without again upgrading it over top of 
9.10/9.04/8.10/8.04...

Today, I repartitioned the D Drive Data extended and logical partitions into one smaller 100GB NTFS primary partition, so its Vista C Drive, U9.10, then D Drive and then unallocated space. I attach an image of GParted to show it.

The partitions aren't optimal but it works for now.

Proposed idea I need help with...

Install U10.04 or U10.10 clean into a new partition on the unallocated space. I thought if I used an Extended partition 
can only have one?) with Logical partitions for the OS, my personal data, a swap partition, etc. that I could get a fresh install of the new Ubuntu and still have a working dual boot until I was happy and then either do a tripleboot and keep Vista and the 2 linux, wipe out the U9.10 partition and merge it 
into the Vista D Drive for data and shared data with the remaining Ubuntu 10.x.
Questions:

Q1 - Should I create a ext4 extended partition in unallocated space and set up logical partitions for /root, /home, /swap and any other recommended?

Q2- Will the U10.x installer do that for me?

Q3 - Can I keep my working GRUB 1.5 with working Vista and Ubuntu 9.10, just add in the new U10.10 install until I get it set up right, and then move the GRUB or whatever boot loader to the new U10.10 intall as default?


These may not be the right questions to ask, but sometimes you need to knowthings to know how to ask the right questions! Thanks, any help appreciated...

Cheers

DMC

---

### Post by deadmanschest on 2010-10-08
Hi all - just an update that avoids editing the first post. I have learned that one can format logical partitions within one extended partition to different file systems - who knew? I spent a time this a.m.searching for such an answer, and finally seem to have found it here:

[https://help.ubuntu.com/community/HowtoPartition/ExtendedPartition](https://help.ubuntu.com/community/HowtoPartition/ExtendedPartition)

Can anyone confirm that is correct?

Thanks

DMC

---

### Post by sikander3786 on 2010-10-08
> **deadmanschest said:**
> Hi all - just an update that avoids editing the first post. I have learned that one can format logical partitions within one extended partition to different file systems - who knew? I spent a time this a.m.searching for such an answer, and finally seem to have found it here:

[https://help.ubuntu.com/community/HowtoPartition/ExtendedPartition](https://help.ubuntu.com/community/HowtoPartition/ExtendedPartition)

Can anyone confirm that is correct?

Thanks

DMC
Yes you surely can.

Have you found answers to questions in your 1st post or they still need to be addressed?

---

### Post by deadmanschest on 2010-10-08
> **sikander3786 said:**
> Yes you surely can.

Have you found answers to questions in your 1st post or they still need to be addressed?

Hi sikander - thanks for the note. I still would like some help with those questions, especially with regard to GRUB 1.5 (my existing).

Learning that I can make logical partitions in different file formats means that I can have some flexibility as, I currently have three (3) primary partitions, but I can now relocate my Windows Data partition onto a [future] Extended partition and free up one primary, and that makes me happy :)

I'd like some advice on setting up /root, /home, /swap and any other suggested within a new Extended partition to hold a new install of U10.04.1 and any advice on how to avoid screwing up my existing GRUB...

Thanks

DMC

---

### Post by deadmanschest on 2010-10-08
> **sikander3786 said:**
> Yes you surely can.

Have you found answers to questions in your 1st post or they still need to be addressed?

Hi sikander - thanks for the note. I still would like some help with those questions, especially with regard to GRUB 1.5 (my existing).

Learning that I can make logical partitions in different file formats means that I can have some flexibility as, I currently have three (3) primary partitions, but I can now relocate my Windows Data partition onto a [future] Extended partition and free up one primary, and that makes me happy :)

I'd like some advice on setting up /root, /home, /swap and any other suggested within a new Extended partition to hold a new install of U10.04.1 and any advice on how to avoid screwing up my existing GRUB...

Thanks

DMC

---

### Post by deadmanschest on 2010-10-08
Sorry - double post - couldn't figure how to edit it away...

sikander - I thought for a minute, please let me put this on 'hold' and consider it Solved for now. I need to sit back and consider how best to optimize the exisitng partitions, now that I know I can relocate my Data drive.

I won't install a new linux distro until I figure out the end game...hehe.

Thanks!

DMC

---

