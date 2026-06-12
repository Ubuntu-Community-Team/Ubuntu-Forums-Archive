---
title: "Urgent, i cant install either ubuntu or windows!!!"
date: 2011-03-13
forum: General Help
---

### Post by myact720 on 2011-03-13
I am new here, if I have any question that u feel I am so stupid... Pls  pls dont laugh at me.. I am new completely!!!Thank you....[I edit this  thread by using Ubuntu on CD]

First,I would show my Laptop hardware information here first
DELL.  CPU i3 370M     Memory: 4 GB    Display card: ATI HD 5650    Hard Disk 500 GB....

The problem I meet being like this...

Yesterday, I had my Win7 clashed. in order to continue to work. I had to install a new system...

I dislike Ghost system but in the computer stores. Only the CD do they  have that is Ghost system.. At that time. I have an Ubuntu 10.10 CD.. I  decided to install an Ubuntu in order to work..

I inserted the CD .. I chose to install Ub beside Win7.. I chose to  install UB in D[All the format of my disk are NTFS]... After  installation finished, rebooted....

I can login Ub then...

After I got home. I wanted to format Disk C by using Win7 CD then I  could install Ub in Disk C...  Problem came.. Whether I insert Win7 or  XP... My CD-ROM doesn't recognise them,except Ubuntu 10.10, however  millions of time I have tried... 

Whatever, OK then,, if the laptop didn't want to do so, OK.. I decided to use Ubuntu to instead of using Windows.

The first time I installed UB,  I chose to install it in entire disk.. -  -!!! I did so,,, then all of my files were gone... Initially I had 4   partitions, but due to I chose the option "Erase and install in entire  disk, the partition became 1.. 
500GB... - -! [I know I am stupid, don't laugh at me.. I am new.. Thank you.]

Then I try to install again..

I went to the advanced option for partition, I did sth like this!

500 GB

I created a new primary partition, the format was EXT4, it is 50 GB    mount point  /
I created a new logical partition, the format was EXT4,it is 350 GB      mount point /home
I created a new logical partition, the format was EXT4,it is 100 GB      mount point /root

I chose to install the system at the first one.
The loader of what(forgot the description), I chose the third one(/root),,

Everything is OK ,,, but,, at the step Who are you..
I entered my name and password...
it showed "copying files" .. minutes later,,, about 80% finished...  it  showed "ready when you are..." then stopped... whatever how long u wait.... stop  here... .. 

I tried three times like this....

Now.. My question is.. 

1:Sometimes I have to deal with sth in Windows,, how can I have my  Windows back..to let this laptop recognise Windows installation CD...
2:Why it stopped there?? What's wrong with that??I want to learn and use Ubuntu.


[COLOR=Red]Thank you for you guys....   I am really urgent.. I got nothing to use.. Thank you.... Indeed.!!!![/COLOR]

---

### Post by ~Plue on 2011-03-13
dunno the answer to your first question but to the second one,
make sure you don't have any uppercase characters or spaces in the username field

btw, i wouldn't recommend the partition scheme you have chosen
a separate 100GB /root is completely unnecessary and would be better if you added that space to your /home
and 50GB for / is also too much. with around 15 GB, you could do pretty much whatever you want
(that if of course, if there isn't any special reason why choose to do as in your post)

---

### Post by oldfred on 2011-03-13
Your windows recovery disk is not an install disk that will let you install to a NTFS partition. It is just an image of your hard drive and will totally reformat drive and make it just like it was the day you purchased it. Or it erases everything.

Then if you want to dual boot, from windows shrink the windows partition. Then use gparted to make the partitions like you did before and install Ubuntu.

Dual Boot Win7 & Ubuntu
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)
Full Disk Install
[http://www.howtoforge.com/the-perfect-desktop-ubuntu-10.10-maverick-meerkat](http://www.howtoforge.com/the-perfect-desktop-ubuntu-10.10-maverick-meerkat)

After you have reconfigured windows to the way you want then a backup so you can just reinstall that may be a good idea.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by myact720 on 2011-03-13
> **~Plue said:**
> dunno the answer to your first question but to the second one,
make sure you don't have any uppercase characters or spaces in the username field

btw, i wouldn't recommend the partition scheme you have chosen
a separate 100GB /root is completely unnecessary and would be better if you added that space to your /home
and 50GB for / is also too much. with around 15 GB, you could do pretty much whatever you want
(that if of course, if there isn't any special reason why choose to do as in your post)


I am still new.. Nobody tells me how to install, I just read something online then do so.. so I dont know how to answer you...

could u tell me how to make my partition better..

I have 500 GB free space..

If u have 500 GB free space.. what will you do... also how to choose boot loader
Device for boot loader

thank you..

---

### Post by myact720 on 2011-03-13
> **~Plue said:**
> dunno the answer to your first question but to the second one,
make sure you don't have any uppercase characters or spaces in the username field

btw, i wouldn't recommend the partition scheme you have chosen
a separate 100GB /root is completely unnecessary and would be better if you added that space to your /home
and 50GB for / is also too much. with around 15 GB, you could do pretty much whatever you want
(that if of course, if there isn't any special reason why choose to do as in your post)


I am still new.. Nobody tells me how to install, I just read something online then do so.. so I dont know how to answer you...

could u tell me how to make my partition better..

I have 500 GB free space..

If u have 500 GB free space.. what will you do... also how to choose boot loader
Device for boot loader installation

the mount point i did,,, is it right??
/
/home
/root

I should choose which one to install my system... 
thank you..

---

### Post by ~Plue on 2011-03-13
> **myact720 said:**
> 
If u have 500 GB free space.. what will you do... also how to choose boot loader
Device for boot loader

assuming it's only ubuntu;
RAM size swap (if you don't want to hibernate or have more than 4gb ram, a little less would do)
15gb ext4 /   <--- where the system files would be
the rest as ext4 /home  <---- for your personal files
and the boot loader on /dev/sdX (your hard disk device, not a partition)
-(a separate /root is not really necessary)

but if you want to dual boot with windows, you would have to make some changes to that

you should see the links by oldfred, they'll explain it more clearly than i could

---

### Post by myact720 on 2011-03-13
> **~Plue said:**
> assuming it's only ubuntu;
RAM size swap (if you don't want to hibernate or have more than 4gb ram, a little less would do)
15gb ext4 /   <--- where the system files would be
the rest as ext4 /home  <---- for your personal files
and the boot loader on /dev/sdX (your hard disk device, not a partition)
-(a separate /root is not really necessary)
   
but if you want to dual boot with windows, you would have to make some changes to that

you should see the links by oldfred, they'll explain it more clearly than i could

I am doing it like below

20GB ext4 / (I choose to install system here)
470GB ext4 /home
No /root

Device loader
I choose my whole hard disk.. not like what i did before... I just chose a partitiion

I am sry for my ENglish. I am a chinese.. English is not that good.. 

Thank you ..if I proceed to meet problem.. I will reply u here. and if u r not online.. i will send u text msg here or if you can tell me ur Email... whether i succeed or not..

Thank you very much...

---

### Post by myact720 on 2011-03-13
> **~Plue said:**
> assuming it's only ubuntu;
RAM size swap (if you don't want to hibernate or have more than 4gb ram, a little less would do)
15gb ext4 /   <--- where the system files would be
the rest as ext4 /home  <---- for your personal files
and the boot loader on /dev/sdX (your hard disk device, not a partition)
-(a separate /root is not really necessary)

but if you want to dual boot with windows, you would have to make some changes to that

you should see the links by oldfred, they'll explain it more clearly than i could


It seems i got failure... 

it stopped there again...

---

### Post by Animal X on 2011-03-13
hi, it sounds like you've already destroyed whatever OS you had on there, if so then you are starting from scratch.

My recommendation:
get the ubuntu-livecd, it's gonna clean up your mess so you can start over
think about how you want to lay out your drive
you already said your open to ubuntu but you still need windows at times, so figure:
1 partition for windows(and its best if its first, but can be done other ways)
1 partition for ubuntu, 
and you may want to consider a third partition for your personal stuff
if your going to be going back and forth between OS's, not to mention it makes recovery so much easier later on.

the trick here is - do you have all the installation disks now? i mean for both windows and ubuntu?
if yes, then:
*open gparted on livecd, delete whatever mayhem is left on your disk and make a new partition(remember, you can have up to 4 partitions on a disk, so think of em as part1, part2, so on)
*make part1 @ about 30Gigs, dont install anything yet,  windows doesn't need more than 30 just to operate, i have installed vista into 16G(not healthy), but if it's just there for standby, you dont want to invest so much disk space into windows.
*before you make part2 think about part3, part3 will have ubuntu, you can get by with 20Gigs and have room for clutter, so when you make part2, your going to leave enough room for part3, but dont actually make part3, as ubuntu will install into unallocated space and it will automagically handle logical partitioning for you. 
*label part1 as "windows" or whatever you want so u can find it
*label part2 as "my_media" or "spacer" or whatever suits you
install windows, go into windows, may download EasyBCD (dont need it, just handy is all)
exit windows, shutdown, startup with livecd
install ubuntu into unallocated space, tweak and personalize as necessary

If you dont have the windows install disk then just make part1 and label it and go on without the windows installation, it's just that if you install windows later, you will have to redo the MBR, but easyBCD  fixes that well enough

---

### Post by Animal X on 2011-03-13
> **oldfred said:**
> Your windows recovery disk is not an install disk that will let you install to a NTFS partition. It is just an image of your hard drive and will totally reformat drive and make it just like it was the day you purchased it. Or it erases everything.[]("http://www.runtime.org/driveimage-xml.htm")


actually mine WAS an install disk, i still use it to this day, and it says recovery on it from cyberpower, and it really is just a striiped down windows installation without all the glitzy crapput on from factory, so its kinda nice.

---

### Post by Animal X on 2011-03-13
and don't pay for ghost when you can use the "dd" command in livecd to clone a drive image ;)

or download clonezilla

---

### Post by Animal X on 2011-03-13
> **myact720 said:**
> 
Now.. My question is.. 

2:Why it stopped there?? What's wrong with that??I want to learn and use Ubuntu.
[COLOR=Red][/COLOR]
once you get ubuntu installed, pop that other cd in there and open it up to see whats in it?

---

### Post by oldfred on 2011-03-13
In post #2 ~Plue mentioned Capitals or special characters. Name in Ubuntu has to be lower case. That is usually the problem.

Lots of detail on an install with graphics:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

---

