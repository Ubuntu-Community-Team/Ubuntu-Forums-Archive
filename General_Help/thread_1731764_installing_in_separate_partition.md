---
title: "installing in separate partition"
date: 2011-04-17
forum: General Help
---

### Post by jackobi on 2011-04-17
Hello everyone. I am new to Linux and would be very grateful for advice.
I have  Ubuntu  8.10 on a cd rom I got it with Computeractive magazine a few years ago complete with instructions how to install it.
I have been running it as a live disk and have finally decided to install it along alongside Windows on a separate partition. I realise that version 8.10 is a few years old but I am comfortable with it until such times as I am more experienced.
Can anyone tell if there is enough room on my laptop to install Ubuntu in a seperate partition
At present my Laptop is running Windows XP and the specs are ( if I have read it properly )

Processor 1.60 
Hard Drive 149gb
512 RAM 
There are programs on the disk that I won’t need. Can I remove them to make room on my computer once Ubuntu is installed or is that a daft question.
If this is OK can you advise me if I need a Firewall and a Virus Checker installed.I am sorry if you have been asked this before but I am not sure.
I am a silver surfer and still finding my way about computers so I apologise if these are silly questions.
Thank you in advance for any advice given

---

### Post by suduntu on 2011-04-17
It would be great if you could provide how many partitions you have got on your hard disk and their respective free space

---

### Post by jackobi on 2011-04-17
Hi suduntu.
Thanks for your answer.As far as I can understand I only have one partition. Appart from my cd drive I have "C" drive and when I click on properties it says.

Total Space 149gb
Used Space 19.1gb
Free Space 129 gb
Sorry for my lack of Knowledge.
Thanks again

---

### Post by pbpersson on 2011-04-17
> **jackobi said:**
>  I realise that version 8.10 is a few years old but I am comfortable with it until such times as I am more experienced.

Here are some thoughts to consider:

1.  You can get a newer version for free from the web.
2.  If you have problems there is a chance that few people remember the minute details of that version from two years ago 
3.  If you encounter problems they have probably already been fixed in a newer version.

Yes, after you install Ubuntu you can delete a bunch of applications that you don't need to free up room for things you do need.

Your RAM seems sort of low - you might want to try Xubuntu which runs better on machines with lower RAM.  However, you said the CD has been working fine for you so perhaps the slower response time is not a real concern in your case.

A firewall is a good idea if this computer is connected directly to the Internet through a cable modem.  A virus checker....well, you are one hundred thousand times safer on Ubuntu than you are on Windows when it comes to being attacked by a virus. Most people do not use a virus checker on Ubuntu.

---

### Post by Scunnered on 2011-04-17
Welcome to Ubuntu forum

You would be much better loading the 10.04 version as this is supported for 3 years.  Alternatively you could wait until mid May when with any luck the 11.04 (the most up to date) will have settled down.

I am not sure about installing 11.04 but from memory 10.04 will offer to load on the free space on your hard drive. You should be able to nominate the amount of space that you wish to use.  If after adopting this method you feel that there is the need to alter the allocated space this can be done by using a live CD and System > Administration > Gparted.

I hope this will assist you.

---

### Post by suduntu on 2011-04-17
In addition to what others said, it is advisable to have a recovery disk made before you proceed installing Ubuntu. It will come handy in case if anything goes wrong, you will be able to recover XP.

As you have got only one partition using the entire capacity of the hard drive, you may want to shrink or resize it. This can be done using "gparted" tool from the LiveCD.

I would recommend you to go for the newer version of Ubuntu 10.10. you can download it for free!

---

### Post by jackobi on 2011-04-17
Hi Guys.Thanks for your advice regarding different versions of Linux.I can download one from the Net but because there is some sort of system muck up in my Windows XP I can't burn the iso to disk.I downloaded both mint and ubuntu netbook edition and no matter what burner program I use it freezes.That was one of the reasons for using the disk I have 8.10.
I would have to go to my local computer shop and ask  them to download and burn it for me.
Thanks again for your help.

---

### Post by oldfred on 2011-04-17
windows/NTFS needs about 30% free space to work well. You can then shrink windows down but leave space for it to continue to work well. You may want to experiment with some of the other lighter weight versions of Ubuntu.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 1 GB Mountpoint swap logical

The new rule on swap is equal to memory unless you have 1GB or less of RAM then the old rule of 2x is still best. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

Recognize with the old version you will have old grub legacy which is ok. Newer installs use grub2 which is more complex but better.

---

