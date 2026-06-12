---
title: "Size of .Private folder"
date: 2011-05-18
forum: General Help
---

### Post by apostolos1975 on 2011-05-18
Hi all,

I have a question regarding the .private folder. In a recently installed 10.10 system in a 20GB partition with the user home folder in the same partition the .private directory takes half of the partition space (10GB). Why is that? I haven't moved any files/dirs in there but there is a bunch of binary files and dirs all with names in the following format:

ECRYPTFS_FNEK_ENCRYPTED.FWaAcQMOu55ZeUThIJHPOprnbLBVNWmpUhfj4tNK032y1Y4iXUGJn2JOXU--

When I was installing the system I selected for home encryption. Is it safe to empty that folder or not?

Thank you in advance for your help

/Apostolos

---

### Post by 3xp10r3r|X13 on 2011-05-18
[FONT=Courier New]Hello there,

1. A partition always takes up space, the only question is how much of the space in your home directory(10 gb partition) you have actually occupied.

e.g. you're having a 10 gb partition and you put a 5 gb video in there so you've occupied 5 of 10 available gb.

2. Those files should be part of the encryption process so I doubt it's a great idea to delete them.

Hope this helped:)[/FONT]

---

### Post by 3xp10r3r|X13 on 2011-05-18
[FONT=Courier New]Sorry got your thread wrong --> Thought it would be 2 different partitions.

It might be just part of the encryption, that you can't see how much space you've occupied --> all files get encrypted and stored in this hidden folder .Private

sry again:D[/FONT]

---

### Post by apostolos1975 on 2011-05-18
> **3xp10r3r|X13 said:**
> [FONT=Courier New]Hello there,

1. A partition always takes up space, the only question is how much of the space in your home directory(10 gb partition) you have actually occupied.

e.g. you're having a 10 gb partition and you put a 5 gb video in there so you've occupied 5 of 10 available gb.

2. Those files should be part of the encryption process so I doubt it's a great idea to delete them.

Hope this helped:)[/FONT]

Hi,

and thanks for quick reply. My initial description was a bit confusing. Inside / (20GB partition) and under /home/user there is this .private folder which takes 10GB with these dirs/files. df -h reports the following:

/dev/sda5              19G   15G  3.2G  82% /
none                  993M  244K  993M   1% /dev
none                 1001M  1.5M 1000M   1% /dev/shm
none                 1001M  172K 1001M   1% /var/run
none                 1001M     0 1001M   0% /var/lock
/home/apostolos/.Private
                       19G   15G  3.2G  82% /home/apostolos

and a file manager I use (GNOME Commander) says that this dir takes up 10GB. But on the other hand I see that the dir is actually a symbolic link:

lrwxrwxrwx  1 apostolos apostolos     34 2011-03-25 09:25 .Private -> /home/.ecryptfs/apostolos/.Private

Could you enlighten me a bit on what is going on here? I am novice to Linux.

Thanks again for help

/Apostolos

---

### Post by 3xp10r3r|X13 on 2011-05-18
[FONT=Courier New]Just check this out, I hope it gives you an answer:

[/FONT]https://help.ubuntu.com/community/EncryptedPrivateDirectory
[FONT=Courier New] 
"After logging back in, all content of any files or folders you write in ~/Private will be encrypted when written to the disk, in the hidden directory ~/.Private." <-- those files are stored in the hidden folder .private

Just by the way, all hidden folders have a "." in front of them. You can even create them by naming them

.name , just by the way

However, click on the link and you will be "enlightened" as you call it :D[/FONT]

---

