---
title: "My Computer won't Dual-Boot"
date: 2011-05-30
forum: General Help
---

### Post by DaYiM on 2011-05-30
Hello.
i have installed Ubuntu on a partition on my secondary HDD, sense then i have never used windows ( one week ), 
then i have formatted my windows  which is in the primary HDD.
Now when my computer restart it doesn't show my about wanting to start Ubuntu or windows it starts windows immediately.
PS: in my secondary HDD the partition which Ubuntu is installed on, i still see that it filled with data;it's not empty.

* one more question please; before i have installed Ubuntu i have created a partition ( 50GB ),
which i choose the HardDisk manager to make as "Linux Ext4"; then i have installed Ubuntu on!
is what i did right or wrong or it doesn't matter? Please Help in these two matters!

---

### Post by hal8000 on 2011-05-30
> **DaYiM said:**
> Hello.
i have installed Ubuntu on a partition on my secondary HDD, sense then i have never used windows ( one week ), 
then i have formatted my windows  which is in the primary HDD.
Now when my computer restart it doesn't show my about wanting to start Ubuntu or windows it starts windows immediately.
PS: in my secondary HDD the partition which Ubuntu is installed on, i still see that it filled with data;it's not empty.

* one more question please; before i have installed Ubuntu i have created a partition ( 50GB ),
which i choose the HardDisk manager to make as "Linux Ext4"; then i have installed Ubuntu on!
is what i did right or wrong or it doesn't matter? Please Help in these two matters!


Can you tell us which system starts immediately, Windows or Ubuntu?
What you need to do is post a little more info.
Can you boot with the Ubuntu CD in live mode (try before installing mode)
It should recognise and configure your ethernet.

Post the output of:
sudo fdisk -l

---

### Post by DaYiM on 2011-05-30
Windows is the one that starts immediately.
What is live mode? i didn't tried it before;
i installed Ubuntu on the partition before trying it.
what is the "output of: sudo fdisk -|"?
thanks for your response.

---

### Post by DinoT1985 on 2011-05-30
grub2 was installed on your Windows HDD. When you formatted it was lost. grub2 is your Linux loader like Windows Boot Loader.

follow this

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

or if you want to use Windows Boot Loader.

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Scroll to "**[COLOR=#003366][B]Adding Ubuntu to the Windows Bootloader".**[/COLOR][/B]

---

### Post by DaYiM on 2011-05-30
thaaaaaanks alot,
i used the second link & it worked perfectly.

---

### Post by DinoT1985 on 2011-05-30
Glad to help. please mark the thread as solved :)

---

### Post by DaYiM on 2011-05-30
how? i tried to edit the first post, but couldn't change it.

---

### Post by lisati on 2011-05-30
> **DaYiM said:**
> how? i tried to edit the first post, but couldn't change it.

Use the "Thread tools" link near the top of the page: there should be an option "Mark thread as solved."

---

