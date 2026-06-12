---
title: "Intro, and in need of some help."
date: 2012-04-12
forum: General Help
---

### Post by tt8698 on 2012-04-12
Hi everyone.

A little bit of background, I'm relatively unfamiliar with knowing all that much about Linux commands on my own, however I've been dual booting Ubuntu on my laptop for the last two years.  So I do have some background with Ubuntu and following commands and processes for misc. activities. Recently I built my first official battlestation.  I have a total of 4 SSD/HDD's installed. I have windows booting off the SSD and mainly running the OS and a few programs. We'll say HDD(1) I have set up as a combo of storage and installed programs for Windows 7 Ultimate 64 bit. HDD(2) is dedicated entirely to Ubuntu (11.10 64 bit) ext3 with 8gb swap. HDD(3) is strictly a storage drive running a fat32 file system. 

First off I installed Ubuntu off of a usb stick; I've also never experienced so many issues with the installation, and how Ubuntu is performing but that’s a whole other story. During the process of formatting HDD(2) accidentally wiped HDD(1) without declaring a file system. I then correctly formatted HDD(2) and had to finish the install process. After installing Ubuntu I used gparition inside to recover the files, and I copied them to the desktop folder. I then went back and reformatted HDD(1) and made it an ntfs file system.

Now here comes the tricky part. After reformatting HDD(1), I went to go put all the files from the desktop folder onto HDD(1) however none of the files are in the folder and cannot be accessed by simply searching for them. I know the files are still on HDD(2) because when I use gparted to see the drives, the size of all the files are showing taking up space on HDD(2). 

I've tried using Gparted from a live cd to attempt to recover the files off HDD(2) and move them that way however, after running the long search for the files, and finding them, its showing as a fat32 files system, and getting an error for inconsistent file systems and not being able to recover the files, and start the whole tedious process over again. 

Is there anything that I may be doing wrong? Or how would I go about fixing the inconsistent file system errors? I've been doing searches all over and can't seem to find the answer that I'm looking for. Any help or advice would be greatly appreciated. Also if I posted this is the wrong place, I am sorry lol :p

---

### Post by riderplus on 2012-04-12
Hi,

Try using fsck to check for errors on that partition [https://help.ubuntu.com/community/SystemAdministration/Fsck](https://help.ubuntu.com/community/SystemAdministration/Fsck)
Also, bear in mind the principle [KISS]("https://en.wikipedia.org/wiki/KISS_principle") :p

---

### Post by Annernecrurgy on 2012-04-12
There are numberless distinct types of network hosts at one's disposal on the bazaar today. Choosing a fit provider depends on what type of site you require to obtain: recreation, blog, or ecommerce site. As a evolve, there are different flavors of web hosts. Some of the most normal website hosting types are: shared, unfastened, and dedicated hosting. Shared hosting is the most acclaimed web hosting organize [Hostgator Discount](http://hostgator1.info)  Shared website hosting permits more than ditty placement to be hosted on the unmodified server. Here, the web hosts afford the modus operandi supervision and the server maintenance. Benefits of a shared hosting neighbourhood are programming features, overweight bandwidth, and multiple e-mail whereabouts capability. Compared to free plans, shared web hosting allows a user to arrange their own concern name. [Hostgator Review](http://hostgator1.info)  Shared hosting is a conduct after a hosting company to tender affordable products and services to their clients while having more users on complete server and thus less high up costs. Independent hosting is the most vital web hosting service. Banners ads are clich‚d on this model of website hosting services. There are a few released web site hosting providers in presence today that accommodate tiptop options but that is the shut-out to the rule. Most free plans do not provide users with MySQL databases, multiple e-mail accounts, or the capacity to flood any scripting language. The strain of speciality one receives in this loose visualize of putting into play is typically a sub-domain or a directory. [Hostgator Discount](http://hostgator1.info)  Dedicated hosting is a good option for the treatment of someone who wants more storage and bandwidth and dominance over the server. The advantages of having dedicated hosting are: unlimited databases and email addresses as pretentiously as unlimited bandwidth. Also powerful to recall that there are two types of dedicated web hosting plans: managed and unmanaged. Managed hosting is hosting that is tranquillity controlled by means of the hosting company. In the unmanaged blank, the user is the server administrator, permitting the user the greatest amount of supervise and conformability [Hostgator Coupon](http://hostgator1.info)  It is a daunting test of strength to realize the best putting into play after your needs. Before all recollect that the function of the website chiefly determines the genus of web host. Then, the features, supporter, reliability, and rule decide the pricing of a hosting account.

---

