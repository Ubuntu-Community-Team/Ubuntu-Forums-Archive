---
title: "No space left on device"
date: 2009-10-09
forum: General Help
---

### Post by wrxch on 2009-10-09
Hi to all. First a short intro about me. I am 31 y/o musician and I am a complete "virgin" to Linux/Ubuntu. :)
Now to the problem that I am having.
I have read on numerous websites including this forum about the solution that people found about the msg: No space left on device.
However, none of it seems to solve my problem of this kind. I have tried all the commands but probably i am simply lacking the basic info/knowledge.
I am writing this post right now using my windows again as Linux's tcp something in firefox crashed and the message with the df -h command output was gone without being sent. For whatever reason it might have been.
Shortly to put out the ouput of the command it looked like that

/dev/sda6 2.3gb 106mb (free) 2.2gb 96%

The rest all said 1.8gb and that its all free or in other words 0% are used.

I have tried getting into the /dev/sda6 folder but with no success.

I did notice however that after running the aircrack-ng program, at some point it started telling me the same msg while running it in the terminal. I did however manage to find the .cap files and deleted them but it only gave me 100mb of free space.

To be honest, I have no idea what I am really doing while typing the commands, but i did manage to install the ath9k drivers for my atheros card after 3 days of trying...
Any help or suggestions would be greatly appreciated. Any reading material that is suitable for complete beginners will be great as well.
Hope to hear from some of you soon

Thanks in advance

Daniel

---

### Post by Lars Noodén on 2009-10-09
We'll need the rest of the output from **df -h**.  While your at it, could you please post output from **mount** so we can make suggestions about what to move around?

/dev/sda6 will show up as /, /home, /var, /usr or some other mount point and would be access that way.

---

### Post by nothingspecial on 2009-10-09
This is a "bug" in the jaunty installer.

But as wrxch said, you need to post your partition table before someone can help.

```
sudo fdisk -l
```

Wouldn`t be a bad idea either. I assume that you are dual booting with windows. Do you have any free space in your windows partition. If so, defrag it a couple of times then boot your live cd.

Go system > administration > partition editor and increase your ubuntu partition into the free space in your windows partition.

But please please please back up anything you don`t want to loose. If you do this wrong you could wipe everything.

---

### Post by Lars Noodén on 2009-10-09
If you boot from the live cd that can let you use some basic tools:

[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

Later, if you want some advanced tools, then Finnix has them:
[http://www.finnix.org/](http://www.finnix.org/)

---

### Post by nothingspecial on 2009-10-09
> **wrxch said:**
> Hi to all. First a short intro about me. I am 31 y/o musician and I am a complete "virgin" to Linux/Ubuntu. :)



And from the home page of finnix

> Finnix is not intended for the average desktop user

I think the live cd and gparted will be just fine in this case.....


....although finnix looks interesting. :)

---

### Post by Lars Noodén on 2009-10-09
@nothingspecial : "**Later**, if you want some **advanced** tools, then Finnix has them"

---

### Post by nothingspecial on 2009-10-09
I am able to read thankyou

This is Ubuntu, not Gentoo

The op just wants his computer to work.

---

### Post by wrxch on 2009-10-09
Thank you for all your replies and suggestions. I'll do the commands in the terminal and post it either tonight or tomorrow.
:)
Wishing all a nice friday evening

Danny

---

### Post by wrxch on 2009-10-14
Hi again,
Sorry I didn't post at the time that I said I would.
Since then I have tried to install Kubuntu which I personally like more from the layout...
However, as soon as I've installed it, the space problem was there right away.
I have tried to boot from LiveCD but I couldn't increase the partition using the instructions above, because it simply wouldn't go higher than the size that it has at the moment...
Here is the output of df -h in Kubuntu which is not much different to the one that was in Ubuntu.

```
dvaiman@dvaiman-laptop:~$ df -h
Filesystem            Size           Used             Avail           Use%          Mounted on
/dev/sda8             2.3G            2.2G             35M             99%                   /
tmpfs                   1.8G               0                1.8G            0%               /lib/init/rw
varrun                  1.8G             104K            1.8G           1%               /var/run
varlock                 1.8G               0                1.8G           0%              /var/lock
udev                    1.8G              172K            1.8G           1%                  /dev
tmpfs                  1.8G               12K             1.8G           1%              /dev/shm
lrm                      1.8G              2.7M            1.8G            1%     /lib/modules/2.6.28-11-generic/volatile

```

And here is the sudo fdisk -l result

```
dvaiman@dvaiman-laptop:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x97646c29

   Device Boot      Start         End      Blocks             Id                 System
/dev/sda1               1           1530     12289693+     1c    Hidden W95 FAT32 (LBA)
/dev/sda2   *        1531       31930   244188000       7      HPFS/NTFS
/dev/sda3           31931       60801   231906307+    f       W95 Ext'd (LBA)
/dev/sda5           31931       51116   154111513+    7      HPFS/NTFS
/dev/sda6           60476       60779     2441848+     83     Linux
/dev/sda7           60780       60801      176683+      82     Linux swap / Solaris
/dev/sda8           60150       60453     2441848+     83     Linux
/dev/sda9           60454       60475      176683+      82     Linux swap / Solaris
/dev/sda10          51117       60149    72557541      83     Linux

Partition table entries are not in disk order

```
What I did try to do was to create a new partition on my windows D drive which has no real important info even if i would get lost. This was then made into /dev/sda10. I was hoping that by making some "free" partition using the LiveCD I would be able to increase the size of SDA6 (Ubuntu) or SDA8 (Kubuntu) but nothing happened and I just couldn't increase the size by pulling anything. To be honest I was trying to delete some data from the Ubuntu installation but it only ended up being completely broken and I can only get to the username/password logon screen as the keyboard and mouse aren't working. I guess I deleted something wrong ;). That is also one of the reasons I decided to try out Kubuntu. Now I don't even know how to delete Ubuntu without losing the bootloader.... So yeah, if any of you have any patience with me that would be great :)
I did manage to install my atheros 9285 on both Kubuntu and Ubuntu using some guides on the net :))) so i feel at least proud of that :)
Hoping to hear from some of you
Thanks again in advance.

Danny

ps. what does sudo stand for?? just out of curiosity

---

### Post by wrxch on 2009-10-15
Hi again,
Well, after some more hardcore reading, I finally found a way to solve the problem and reinstall Ubuntu that is now working much better as it has not the size problems :). Also Kubuntu installation got more space now. I have used the guide that I did find on repartitioning Ubuntu. A very interesting post was made by one of the users of this forums. Unfortunately the bookmark to that post is on my Kubuntu installation :).
Anyways, 2 very important things that I as a new user had no idea about was that you can set the partition size from the graphical menu upon the installation itself. There is the option (right under the option to install manually) to just slide the selector to the needed size of the partition for Ubuntu. However, I didn't realise it and left it at the original 2.5gb. Also, in order to repartition anything, using gparted from LiveCD, the partition that you would like to make bigger, has to be "touching" the partition that you are going to make smaller. Meaning it has to be next to each other. Again something I had no idea about and was just surprised to see (as I mentioned in my previous post) that although I have created another 70gb partition, I couldn't change anything on the ones that I actually needed.
I will login under Kubuntu at some point soon and will post the links. 
Meanwhile thanks for all your comments. I will now try to continue learning on how to use Linux :D. Especially the installation of programs and hardwares is something I am really unfamiliar with.
Wishing all a nice upcoming weekend.

Danny

---

### Post by Lars Noodén on 2009-10-15
@ wrxch  (aka Danny) : glad you found a solution.  Sometimes it takes a few tries to guess the right partition sizes because the space needs to be distributed based on what you are doing.   I guess at the minimum there should almost always be a separate /home

> **wrxch said:**
> 

ps. what does sudo stand for?? just out of curiosity

[sudo](http://xkcd.com/149/) is a tool that allows you to grant additional limited privileges to groups of users without giving away the whole farm.  

The principle involved is 'least privilege'.  

Here is a snippet from sudo configuration (/etc/sudoers) which allows any user in the group 'autofsusers' to run the script '/etc/init.d/autofs' as root without a password but only if used with the options start, stop,  restart, reload, status, getmounts, active, and no other options:

```

%autofsusers ALL=(ALL) NOPASSWD: /etc/init.d/autofs start, \
   /etc/init.d/autofs stop, /etc/init.d/autofs restart, \
   /etc/init.d/autofs reload, /etc/init.d/autofs status, \
   /etc/init.d/autofs getmounts, /etc/init.d/autofs active

```

The example above can be written more elegantly, but I think this way might be most clear.

This example allows any user in the group webmeisters to start, restart, check the status, or reload the server configuration, but not to stop it or do anything else.  The user's own password must be entered to run the script.  

```

%webmeisters ALL=(ALL) PASSWD: /etc/init.d/apache2 start, \
   /etc/init.d/apache2 restart, /etc/init.d/apache2 reload, \
   /etc/init.d/apache2 status

```

sudo is in particular very useful when helping new people share system administration.  If it's only you using the machine, but you find yourself constantly logging in as root to do the exact same thing again and again, a sudo entry might make life easier and safer.

---

### Post by wrxch on 2009-10-24
Thank you very much for your explanations :)
Sorry my reply took so long but I am pretty much on the way since my last post and didn't have much time to logon.
Thanks again
Danny

---

### Post by phillw on 2009-10-24
> **wrxch said:**
> Hi to all. First a short intro about me. I am 31 y/o musician and I am a complete "virgin" to Linux/Ubuntu. :)
Now to the problem that I am having.
I have read on numerous websites including this forum about the solution that people found about the msg: No space left on device.
However, none of it seems to solve my problem of this kind. I have tried all the commands but probably i am simply lacking the basic info/knowledge.
I am writing this post right now using my windows again as Linux's tcp something in firefox crashed and the message with the df -h command output was gone without being sent. For whatever reason it might have been.
Shortly to put out the ouput of the command it looked like that

/dev/sda6 2.3gb 106mb (free) 2.2gb 96%

The rest all said 1.8gb and that its all free or in other words 0% are used.

I have tried getting into the /dev/sda6 folder but with no success.

I did notice however that after running the aircrack-ng program, at some point it started telling me the same msg while running it in the terminal. I did however manage to find the .cap files and deleted them but it only gave me 100mb of free space.

To be honest, I have no idea what I am really doing while typing the commands, but i did manage to install the ath9k drivers for my atheros card after 3 days of trying...
Any help or suggestions would be greatly appreciated. Any reading material that is suitable for complete beginners will be great as well.
Hope to hear from some of you soon

Thanks in advance

Daniel


I am adding this just for those caught up in 2.3Gb hell.

[http://ubuntuforums.org/archive/index.php/t-1219270.html](http://ubuntuforums.org/archive/index.php/t-1219270.html)

It's too easy to just accept what the system says, instead of telling it that you need more then the minimum - like 10Gb ...

Regards,

Phill.

---

