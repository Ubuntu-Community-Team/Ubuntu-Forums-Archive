---
title: "GParted :   Copy–Paste Partitions"
date: 2010-08-27
forum: General Help
---

### Post by Dmal on 2010-08-27
Hi guys,
   
      I have a 'Lucid Lynx' amd64 installation (**root** & **home**  both logical partitions) and I am very happy with it ... so happy that I would like to test 'Maverick Meerkat'  ... but without interfering with my already stable system. I decided I had to replicate my actual system to a couple of different partitions (in the same HD) and upgrade to Ubuntu 10.10 from there to test the Meerkat ... and that's what I did :
   
           
           -   Using Windows Vista **Diskpart** utility (all my HD partitions had been created from Vista ... I just wanted to keep
              homogeneous)  I created two new logical partitions (20GiB  & 20GiB  exactly the same size as the original partitions) .
   
           -   From an **external** Ubuntu on a **Pendrive** using **Gparted** ( v 0.6.2 ) I copied the original **home** partition and pasted to
              the new home partition  ...  and before doing the same with the original **root** partition I started checking some things ...
   
   
       Well, the two previous steps using Diskpart & Gparted  ended properly. Everything seemed to be perfect and ... before continuing the proccess I just had to enter 10 minutes to my original Ubuntu installation to check some mails. I logged into my original Ubuntu and before checking the mails, couldn't resist to enter GParted to see the running proccess from there ... AND A PROBLEM CAME UP ...
   
       My original Ubuntu was actually a **mixed** Ubuntu, I mean ... my mounted running partitions were the original root and the new (just pasted) home partition. After digging a bit I found out that when I copied-pasted my original home partition into the new created home partition, besides the data inside the partition, it was also copied the **label** and the **UUID** !!!!!   ... so that in the same HD I had two partitions (original home & new home) with the **same UUID** (Universal Unique Identifier) . That's why the new home partition was mounted ... it had the same UUID than original home partition and while my  **/etc/fstab**  dataset points to these identificators instead of  /dev/sd*  it will not be possible to differenciate both partitions using UUID.
   
       I logged out my original Ubuntu and went back to the Ubuntu on my Pendrive ... I started Gparted and changed the new home partition **label** ... but I couldn't change the **UUID**. Still from the Pendrive, when I mount the original home partition I can map it at Nautilus and reach all the files there ... but  I can see an exclamation mark at Gparted saying “Impossible to find the mount point”. **That's the situation ...  one HD with two different logical partitions having the same UUID .     :(** 
   
   
       I am not an advanced user at all ... so I would like to know your opinion about that.
   
       Is this a BUG from Gparted or it is just an expected behaviour ?
   
   
       Thank you.

---

### Post by oldfred on 2010-08-27
If you are doing a backup where you want it to work without changes you have to have the same UUIDs as those are in fstab and grub. So I think it has to be expected that it will copy.

 Change UUID uuidgen tune2fs
[http://ubuntuforums.org/showthread.php?t=561080](http://ubuntuforums.org/showthread.php?t=561080)

You can use uuidgen to create a new uuid and tune2fs to change a partitions UUID. For details see man tune2fs or man uuidgen.

I have 3 versions of Ubuntu last install 9.10, current 10.04 and 10.10. But I have them each in 20-25GB system partitions and have all my data in a separate /data partition. My /home only has about 1GB of data now and I can copy it over if I want or not. But I mount all my data in each install, so I have the same data.

---

### Post by Dmal on 2010-08-27
It worked PERFECT ...  Thank you very much.
 

   While it is the first time I am cloning partitions I wonder if instead of using Gparted copy-paste operations (and post adjustment) , maybe using Clonezilla would have provide me a more straightforward solution ...
 

   Either case, the problem is SOLVED ... Thank you again.

---

### Post by oldfred on 2010-08-27
Glad you got it working.

I prefer to just install as a new install. I copy ISO to USB and use grub to loop mount it. From USB to new partition takes about 9 minutes on my system which is about 3 years old dual processor. It takes longer to install all the updates and then I have a long list of apps that I install so it is about an hour total to get to a full install.

---

