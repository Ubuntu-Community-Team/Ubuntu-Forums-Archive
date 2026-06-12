---
title: "problem with partitions understanding"
date: 2010-12-31
forum: General Help
---

### Post by Learning0 on 2010-12-31
[SIZE=2]Hi ,[/SIZE]

[SIZE=2]i was reading about linux many times just to understand the partition system in linux but that doesn't make any sense for me which expected actully because i was working on windows since i was 9 years old ![/SIZE]

[SIZE=2]so i have variety of questions i hope if you could help me understand[/SIZE]

[SIZE=2]now in WINDOWS i know that the hardisk separated for example into C:\ and D:\ and E:\[/SIZE]

[SIZE=2]so when i installl ubuntu or any linux system , shall i remove one of the partitions to give a free space for linux or i can just format one of the partiotions and install it on ?[/SIZE]

[SIZE=2]because i want to have 2 main systems in my laptop which are W7 and ubuntu[/SIZE]

[SIZE=2]the second question is[/SIZE]
[SIZE=2]can some one explain for me the linux partition system ? [/SIZE]
[SIZE=2]for example partitions like C D E , how it would be on linux ?[/SIZE]
[SIZE=2]dev1 , dev2 , dev3 ?[/SIZE]


[SIZE=2]Thanks for caring[/SIZE]

---

### Post by Quackers on 2010-12-31
Welcome to UF.
You don't mention which version of Windows you are running.
The first thing to check is how many primary partitions Windows is using on your hard drive. This must not exceed 4, as that is the MBR limit for any one disc.
If you have a look in the disk management console (in Vista or Windows 7) it will tell you.
Windows partitions will always have one called C:, but others can be named more or less any letter. Sometimes they will have a name though, like "System Reserved"
In Linux partitions are named /dev/sda1, /dev/sda2 etc, etc.

---

### Post by Nytram on 2010-12-31
> **Learning0 said:**
> [SIZE=2]Hi ,[/SIZE]

[SIZE=2]so when i installl ubuntu or any linux system , shall i remove one of the partitions to give a free space for linux or i can just format one of the partiotions and install it on ?[/SIZE]

[SIZE=2]because i want to have 2 main systems in my laptop which are W7 and ubuntu[/SIZE]

[SIZE=2]the second question is[/SIZE]
[SIZE=2]can some one explain for me the linux partition system ? [/SIZE]
[SIZE=2]for example partitions like C D E , how it would be on linux ?[/SIZE]
[SIZE=2]dev1 , dev2 , dev3 ?[/SIZE]


[SIZE=2]Thanks for caring[/SIZE]

Hi Learning, welcome to these forums,

It's possible to use your existing partitions for Linux if you have some free, it needs at least 2. Or you can create some new ones using a partition editor.

In Windows as you know the hard drive partitions go thru the alphabet beginning with C:

In Linux each physical hard drive has a letter and each partition on that hard drive has a number. So the first partition on the first hard drive would be sda0, and the 3rd partition on a 2nd hard drive would be sdb2.

It's different to the way Windows works, but not really more complicated.

---

### Post by Learning0 on 2011-01-01
> **Quackers said:**
> Welcome to UF.
You don't mention which version of Windows you are running.
The first thing to check is how many primary partitions Windows is using on your hard drive. This must not exceed 4, as that is the MBR limit for any one disc.
If you have a look in the disk management console (in Vista or Windows 7) it will tell you.
Windows partitions will always have one called C:, but others can be named more or less any letter. Sometimes they will have a name though, like "System Reserved"
In Linux partitions are named /dev/sda1, /dev/sda2 etc, etc.
 
> **Nytram said:**
> Hi Learning, welcome to these forums,
 
It's possible to use your existing partitions for Linux if you have some free, it needs at least 2. Or you can create some new ones using a partition editor.
 
In Windows as you know the hard drive partitions go thru the alphabet beginning with C:
 
In Linux each physical hard drive has a letter and each partition on that hard drive has a number. So the first partition on the first hard drive would be sda0, and the 3rd partition on a 2nd hard drive would be sdb2.
 
It's different to the way Windows works, but not really more complicated.
 
Thank you , i get the idea
 
i'm using w7 , and i have one of the partition is empty
 
i will try to install it , and tell you updates
  but before that i have just one question
 
 do i need to delete the partition to make a space for ubntu
or i just need one partition empty and ubntu will be installed inside it ?
 
thanks

---

### Post by coffeecat on 2011-01-01
@Learning0, it is a good idea to be able to understand the difference between primary, extended and logical partitions. That way you can make informed decisions about how to set out your partitions for Windows and Linux to co-exist. It is possible that your one empty partition is a primary one and that you could change this to an extended partition in which you could make two or more logical partitions for Linux, remembering that Linux (usually) uses a separate swap partition. This is my guess, but that needs to be confirmed before you do anything.

Have a look at this Ubuntu documentation page and read through all the links:

[https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics](https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics)

That will give you a much better idea of how it all works and what you might need to do in your particular case. If you have any specific questions, don't hesitate to ask. :)

---

### Post by Quackers on 2011-01-01
Ubuntu will not install inside a NTFS formatted partition. My advice would be to delete that partition and leave the unallocated space for Ubuntu to install into.

Please note!
If you have C:, D: and E: partitions in Windows7 you almost certainly had 4 primary partitions (one for Win 7 boot files). You HAVE to delete one in those circumstances, or you will end up with dynamic disks and Ubuntu will not install!
Did you have a look in Windows disk management console, as I advised?

---

### Post by Learning0 on 2011-01-01
> **coffeecat said:**
> @Learning0, it is a good idea to be able to understand the difference between primary, extended and logical partitions. That way you can make informed decisions about how to set out your partitions for Windows and Linux to co-exist. It is possible that your one empty partition is a primary one and that you could change this to an extended partition in which you could make two or more logical partitions for Linux, remembering that Linux (usually) uses a separate swap partition. This is my guess, but that needs to be confirmed before you do anything.
 
Have a look at this Ubuntu documentation page and read through all the links:
 
[https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics](https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics)
 
That will give you a much better idea of how it all works and what you might need to do in your particular case. If you have any specific questions, don't hesitate to ask. :)
 alright , thank you so much
 
> **Quackers said:**
> Ubuntu will not install inside a NTFS formatted partition. My advice would be to delete that partition and leave the unallocated space for Ubuntu to install into.
 
Please note!
If you have C:, D: and E: partitions in Windows7 you almost certainly had 4 primary partitions (one for Win 7 boot files). You HAVE to delete one in those circumstances, or you will end up with dynamic disks and Ubuntu will not install!
Did you have a look in Windows disk management console, as I advised?
oh , i get it now
so you mean that i cannot make more than 4 primary partitions in one hardisk
and what you said is true 
i have C:  and D:  and E: ( this one is empty i made it for ubuntu )
now all what i have to do , is remove E: and leave it as a free space for ubuntu , am I right ?

---

### Post by QLee on 2011-01-01
[QUOTE=Learning0]alright , thank you so much
 

oh , i get it now
so you mean that i cannot make more than 4 primary partitions in one hardisk
and what you said is true 
i have C:  and D:  and E: ( this one is empty i made it for ubuntu )
now all what i have to do , is remove E: and leave it as a free space for ubuntu , am I right ?[/QUOTE]

In my opinion, a very good thing for you to do at this point, Learning0, would be to boot up the live CD of Ubntu and run the program GParted, from the menu, System-->Administration--GParted, then post a screenshot of what it shows. That could help the people trying to help you know more about the partitions currently on your system.

---

### Post by Quackers on 2011-01-01
> **Learning0 said:**
> alright , thank you so much
 

oh , i get it now
so you mean that i cannot make more than 4 primary partitions in one hardisk
and what you said is true 
i have C:  and D:  and E: ( this one is empty i made it for ubuntu )
now all what i have to do , is remove E: and leave it as a free space for ubuntu , am I right ?

It would seem that way, but Qlee's suggestion is a very good one.
It will help to clear up any questions :wink:

---

### Post by Learning0 on 2011-01-03
i installed it sucessefully
 
Thanks all for your help , especially Quackers

---

