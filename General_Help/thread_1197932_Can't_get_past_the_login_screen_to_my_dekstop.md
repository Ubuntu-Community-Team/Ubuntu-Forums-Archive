---
title: "Can't get past the login screen to my dekstop"
date: 2009-06-26
forum: General Help
---

### Post by Sashamaru on 2009-06-26
I put the name and pass and nothing happens...... i installed wubi 9.04 and had many problems mostly of my ATI drivers.... so i installed 8.10 and it has the same problem........ the problem is that every time i install ubuntu and download all the programs and drivers for some reboots everything is ok... but then after 2-3 days when i try to login again i can't get past the prompt... it asks for password and name and that's all........ what should i do??? i can't uninstall and install ubuntu every time i want to access them.... plz help me 
(i am using XP and Ubuntu 8.10 in the same partition..... don't know if that got anyhting to do with  my problem)

---

### Post by siryuhan on 2009-06-26
Can you elaborate a bit more? What do you mean "it asks for password and name and that's all?" Do you mean it rejects your password, or that it accepts it but then freezes? Does the screen change at all? Is there any indication of loading?

---

### Post by Sashamaru on 2009-06-26
it accepts it...... then it comes up with some information about last login and etc. and after that there is only this:
sasha@ubuntu:~$
i don't know if i typed it correctly but you get the idea.... i can write the commands no problem but i can't get to the dektop.... i tried "startx" but nothing happened...

---

### Post by Yvan300 on 2009-06-26
Maybe the problem is the wubi install itself, from my experience, when i installed ubuntu through wubi for others i got problems, so maybe it is wubi and you would have to install ubuntu from a live cd.

---

### Post by Sashamaru on 2009-06-26
> **Yvan300 said:**
> Maybe the problem is the wubi install itself, from my experience, when i installed ubuntu through wubi for others i got problems, so maybe it is wubi and you would have to install ubuntu from a live cd.

this means that i need to delete my windows?? or i can have both?? because if i have both what's the difference between wubi and ubuntu from a live cd???

---

### Post by siryuhan on 2009-06-26
> **Sashamaru said:**
> it accepts it...... then it comes up with some information about last login and etc. and after that there is only this:
sasha@ubuntu:~$
i don't know if i typed it correctly but you get the idea.... i can write the commands no problem but i can't get to the dektop.... i tried "startx" but nothing happened...

Do you get an error? Or does bash accept the command and then just give you another prompt $ ?

---

### Post by Sashamaru on 2009-06-26
> **siryuhan said:**
> Do you get an error? Or does bash accept the command and then just give you another prompt $ ?
 in the startx i get some errors......
can i install ubuntu from live cd into the windows xp partition??? i mean can i have both???

---

### Post by philcamlin on 2009-06-26
are you dropping to prompt?

---

### Post by Sashamaru on 2009-06-26
> **philcamlin said:**
> are you dropping to prompt?

yes....

---

### Post by siryuhan on 2009-06-26
> **Sashamaru said:**
> in the startx i get some errors......
can i install ubuntu from live cd into the windows xp partition??? i mean can i have both???

Can you give me a cat /etc/X11/xorg.conf?

---

### Post by philcamlin on 2009-06-26
click ctrl alt f2 

if that fails sudo apt-get install ubuntu-desktop :popcorn:

---

### Post by Sashamaru on 2009-06-26
> **siryuhan said:**
> Can you give me a cat /etc/X11/xorg.conf?

"command not found"
and i even tried "cat /var/log/Xorg.0.log|grep 'EE'"   but nothing again....

---

### Post by Sashamaru on 2009-06-26
> **philcamlin said:**
> click ctrl alt f2 

if that fails sudo apt-get install ubuntu-desktop :popcorn:

nothing man.... the issue here is that this happened to me every time i installed ubuntu.... so every time i just uninstalled.... one time i remember using "sudo cp /root/xorg.conf.new /etc/X11/xorg. conf" nad then "startx" and it worked.. but that was on 9.04..... but that didn't work this time... so now i'm thinking of installing the live cd like said before.... but i need some info on the procedure

---

### Post by siryuhan on 2009-06-26
Try sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by Sashamaru on 2009-06-26
sorry guys for the hustle but i uninstalled..... i must do another install except wubi.... i can't have this happening every time.....

---

### Post by sailthesea on 2009-06-26
> **Sashamaru said:**
> this means that i need to delete my windows?? or i can have both?? because if i have both what's the difference between wubi and ubuntu from a live cd???

 You can have both but to answer these questions first 
The difference betaeen wubi and ubuntu livecd is :
Wubi installs ubuntu in virtual disk within your xp partition
Ubuntu livecd runs ubuntu as a live session from the cd you do not "mount" or run anything on the hard drive itself meaning you can edit the drives partitions
 This enables you to create a dual boot with xp and ubuntu giving the two their own disk space or you can have them share a third file partition for data 
Your problem with login is almost certainly due to fact that your wubi install is getting squeezed especially if you still use xp a lot

---

### Post by Sashamaru on 2009-06-26
> **siryuhan said:**
> Try sudo dpkg-reconfigure -phigh xserver-xorg

i tried that before....... again nothing...... i have been "lurking" these forums for weeks and tried almost everything......

---

### Post by Sashamaru on 2009-06-26
> **sailthesea said:**
> You can have both but to answer these questions first 
The difference betaeen wubi and ubuntu livecd is :
Wubi installs ubuntu in virtual disk within your xp partition
Ubuntu livecd runs ubuntu as a live session from the cd you do not "mount" or run anything on the hard drive itself meaning you can edit the drives partitions
 This enables you to create a dual boot with xp and ubuntu giving the two their own disk space or you can have them share a third file partition for data 
Your problem with login is almost certainly due to fact that your wubi install is getting squeezed especially if you still use xp a lot

i use xp almost every hour :P because i had that problem with ubuntu..... 
so i have 2 HDDs (each one has 1 Terra)..... the one has been partitioned 150gb (for windows) and the rest for data... and the other one is exclusively for data... so my question is how do i handle it?? when you mean live cd that means that it doesn't save the data and preferences into the hard drive???

---

### Post by sailthesea on 2009-06-26
Just to add 
You may as well try a dual boot now 
There is plenty of help on that in the forums
In a nutshell BurnLiveCD>clear out/Fdisk/defrag XP>Boot LiveCD>Create partitions CAREFULLY!>Install Ubuntu>Fix Grub>GO
Good luck!

---

### Post by sailthesea on 2009-06-26
> **Sashamaru said:**
> i use xp almost every hour :P because i had that problem with ubuntu..... 
so i have 2 HDDs (each one has 1 Terra)..... the one has been partitioned 150gb (for windows) and the rest for data... and the other one is exclusively for data... so my question is how do i handle it?? when you mean live cd that means that it doesn't save the data and preferences into the hard drive???

No it doesnt It is a guest session when you turn the computer off it is unchanged
 You have LOOOOAAADS of room! You could divide your first HDD for the 2 OS and use the other for data Setting up a dual boot is tricky so make sure you are sure of what you are doing
 If you back everthing up and take care you will come to no harm Just read and don't rush that how things get broke for good!

---

### Post by Sashamaru on 2009-06-26
> **sailthesea said:**
> No it doesnt It is a guest session when you turn the computer off it is unchanged
 You have LOOOOAAADS of room! You could divide your first HDD for the 2 OS and use the other for data Setting up a dual boot is tricky so make sure you are sure of what you are doing
 If you back everthing up and take care you will come to no harm Just read and don't rush that how things get broke for good!

well the first time i installed wubi i accidentally quickformated my 2nd HDD :D.....
but to divide the first HDD for 2 OS means i should format my HDD.... i haven't got any room to back up so i can't do that..... or you mean divide my 150 partition for the 2 OS??? also could you make it more detailed "In a nutshell BurnLiveCD>clear out/Fdisk/defrag XP>Boot LiveCD>Create partitions CAREFULLY!>Install Ubuntu>Fix Grub>GO"???? :D

---

### Post by sailthesea on 2009-06-26
OK The first thing you need is a LiveCD of the Ubuntu you want 
Do you have one? Make one in windows if not 
Go here
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Hardy has Long Term Support but Ive had no problems with Jaunty so far Intrepid was a a bit buggy
 If your second HDD has nothing much on it you can install directly onto it but you will have to see how your Livecd session reads it and get advice 
Get burning:P

---

### Post by Sashamaru on 2009-06-26
> **sailthesea said:**
> OK The first thing you need is a LiveCD of the Ubuntu you want 
Do you have one? Make one in windows if not 
Go here
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Hardy has Long Term Support but Ive had no problems with Jaunty so far Intrepid was a a bit buggy
 If your second HDD has nothing much on it you can install directly onto it but you will have to see how your Livecd session reads it and get advice 
Get burning:P

 well i have already the image ubuntu-8.10-desktop-i386 but i don't know if that can be a live cd...... isn't that any good?? and i'm downloading now Ubuntu 8.04 LTS Desktop from the link you gave me...... i won't download Jaunty because of the ATI :D
the other HDD is full......  150 gb isn't enough for 2 OS?? and also aren't there going to be any problems if there are 2 OS in one partition??? 
****

---

### Post by Sashamaru on 2009-06-26
if i don't understand something just yell at me :D

---

### Post by sailthesea on 2009-06-26
> **Sashamaru said:**
> well i have already the image ubuntu-8.10-desktop-i386 but i don't know if that can be a live cd...... isn't that any good?? and i'm downloading now Ubuntu 8.04 LTS Desktop from the link you gave me...... i won't download Jaunty because of the ATI :D
the other HDD is full......  150 gb isn't enough for 2 OS?? and also aren't there going to be any problems if there are 2 OS in one partition??? 
****

 You need to burn the image to CD once its downloaded just follow the instructions on the link 150GB should be enough for 2 OS but you you will need to do some serious defragging in windows Try 3plus passes on all drives then fdisk to be sure After that boot the liveCD and see how things go
 You cant have two OS in one partition thats why you must create another for ubuntu it will make one and install itself there from the cd if you want

---

### Post by Sashamaru on 2009-06-26
> **sailthesea said:**
> You need to burn the image to CD once its downloaded just follow the instructions on the link 150GB should be enough for 2 OS but you you will need to do some serious defragging in windows Try 3plus passes on all drives then fdisk to be sure After that boot the liveCD and see how things go

"Try 3plus passes on all drives then fdisk to be sure"  what exactly is that?? and which instructions?? sorry for asking you too much but i want to do it right with every detail and it seems that i don't know too much :D
also one more question..... why do i need the space if i'll be running a live cd???
also which one should i burn?? 8.04 or 8.10???

---

### Post by raymondh on 2009-06-26
Hope these links serve you well as reference/guides.

[http://members.iinet.net.au/~herman546/p17.html](http://members.iinet.net.au/~herman546/p17.html)
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Good luck.

---

### Post by Sashamaru on 2009-06-26
> **raymondhenson said:**
> Hope these links serve you well as reference/guides.

[http://members.iinet.net.au/~herman546/p17.html]("http://members.iinet.net.au/%7Eherman546/p17.html")
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Good luck.

thnx.... i will post in some hours with my progress cause here now it's 6 in the morning 
thnx everyone :D

---

### Post by sailthesea on 2009-06-26
OK Wll get back its 0349 here ZZzz

---

### Post by Sashamaru on 2009-06-27
ok... so i downloaded the iso..... 8.04... chekced it, burned it and tested it....... i used the live session to use partition editor in ubuntu and i made a partition of 30 gb for ubuntu which i left unallocated...... but in the installer it doesn't seem to be able to use that partition..... so i have a screen for you, from XP to see where i am now........ 
[IMG]http://i157.photobucket.com/albums/t50/MetriMetrix/partttt.jpg[/IMG]

---

### Post by raymondh on 2009-06-27
> **Sashamaru said:**
> ok... so i downloaded the iso..... 8.04... chekced it, burned it and tested it....... i used the live session to use partition editor in ubuntu and i made a partition of 30 gb for ubuntu which i left unallocated...... but in the installer it doesn't seem to be able to use that partition..... so i have a screen for you, from XP to see where i am now........ 
[IMG]http://i157.photobucket.com/albums/t50/MetriMetrix/partttt.jpg[/IMG]

There is a 4-max partition limit per drive, whether primary or extended.  Ubuntu requires 2 partitions (root and SWAP) unless you decide you don't want the SWAP.  As it stands with your screenshot, and a standard install with SWAP, you'll exceed the 4-max rule hence the installer hesitation.

You could forego SWAP thus choosing MANUAL install, pointing it to the unallocated and setting root (/) and the format you wish to use (ext3 or ext4).  Foregoing SWAP is no issue if you have enough RAM to hibernate/suspend.

Another option is to break down the unalllocated and use the advatages of an EXTENDED partition.  You can do so using gparted or any partitioning editor you wish.... I will use gparted.

Remember .... do this only on the partition you wish to work on.  Be careful not to reformat the windows, NTSF partition as you will lose it. Also ... back up any file you do not wish to lose.  It may happen.

1.  Right click on the windows partition to unmount ... 
2.  Left Click on the unallocated, go to **PARTITION** menu and select **NEW**.  Make **EXTENDED** and let it use all **free space**. Click **APPLY** to make the extended partition.
3.  Now, click inside the newly created extended partition .. we will make 2 logical partitions.

3a.  Make a **SWAP** partition, about 1.5GB, and format as **SWAP FILE SYSTEM**
3b.  The next partition, format as **EXT3**, use **remaining space**.  This is where we will put root (/) later on.

Remember to review before applying.

Once partitions are made, quit and close gparted.

Continue with the install CD.  When you get to the partitioning stage, step 4, I think,

1. Choose **Manual** install
2. Select the SWAP partition you created, click on **EDIT** (bottom box) and set it to **USE** and **SWAP** type.
3.  Select the root partition > **EDIT** > **USE** and **EXT3** and  "**/**" type

Continue with the install.

Good luck.

---

### Post by Sashamaru on 2009-06-27
> **raymondhenson said:**
> There is a 4-max partition limit per drive, whether primary or extended.  Ubuntu requires 2 partitions (root and SWAP) unless you decide you don't want the SWAP.  As it stands with your screenshot, and a standard install with SWAP, you'll exceed the 4-max rule hence the installer hesitation.

You could forego SWAP thus choosing MANUAL install, pointing it to the unallocated and setting root (/) and the format you wish to use (ext3 or ext4).  Foregoing SWAP is no issue if you have enough RAM to hibernate/suspend.

Another option is to break down the unalllocated and use the advatages of an EXTENDED partition.  You can do so using gparted or any partitioning editor you wish.... I will use gparted.

Remember .... do this only on the partition you wish to work on.  Be careful not to reformat the windows, NTSF partition as you will lose it. Also ... back up any file you do not wish to lose.  It may happen.

1.  Right click on the windows partition to unmount ... 
2.  Left Click on the unallocated, go to **PARTITION** menu and select **NEW**.  Make **EXTENDED** and let it use all **free space**. Click **APPLY** to make the extended partition.
3.  Now, click inside the newly created extended partition .. we will make 2 logical partitions.

3a.  Make a **SWAP** partition, about 1.5GB, and format as **SWAP FILE SYSTEM**
3b.  The next partition, format as **EXT3**, use **remaining space**.  This is where we will put root (/) later on.

Remember to review before applying.

Once partitions are made, quit and close gparted.

Continue with the install CD.  When you get to the partitioning stage, step 4, I think,

1. Choose **Manual** install
2. Select the SWAP partition you created, click on **EDIT** (bottom box) and set it to **USE** and **SWAP** type.
3.  Select the root partition > **EDIT** > **USE** and **EXT3** and  "**/**" type

Continue with the install.

Good luck.

i have already 3 partitions so by making another one for SWAP i will have 4 so i am on the limit..... but i have to ask.... what does SWAP exactly do???and what do i gain if i will make the SWAP partition instead of choosing MANUAL install, pointing it to the unallocated and setting root (/) and the format i wish to use (ext3 or ext4). and which one should i use?? ext3 or ext4???

---

### Post by raymondh on 2009-06-27
[http://www.linux.com/news/software/applications/8208-all-about-linux-swap-space](http://www.linux.com/news/software/applications/8208-all-about-linux-swap-space)
[http://www.cyberciti.biz/tips/linux-swap-space.html](http://www.cyberciti.biz/tips/linux-swap-space.html)
[http://kerneltrap.org/node/3202](http://kerneltrap.org/node/3202)

As you will gather from those links ... swap is helpful in conditions such as low RAM and/or if you hibernate/suspend to RAM a lot.

If you wish to forego (not use) SWAP, you will just have to point the installer (use MANUAL) to the empty space, set root (/) and the format.

As for EXT3 or EXT4. EXT 3 is tested and stable.  The new thing is EXT4 which is faster.  Again, it is new. If you are using 8.04, I suggest you just use EXT3 .... unless you want to really try EXT4.  

Here is the wiki for ext4

[http://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4](http://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4)

Some reading materials for you:

[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by Sashamaru on 2009-06-27
> **raymondhenson said:**
> [http://www.linux.com/news/software/applications/8208-all-about-linux-swap-space](http://www.linux.com/news/software/applications/8208-all-about-linux-swap-space)
[http://www.cyberciti.biz/tips/linux-swap-space.html](http://www.cyberciti.biz/tips/linux-swap-space.html)
[http://kerneltrap.org/node/3202](http://kerneltrap.org/node/3202)

As you will gather from those links ... swap is helpful in conditions such as low RAM and/or if you hibernate/suspend to RAM a lot.

If you wish to forego (not use) SWAP, you will just have to point the installer (use MANUAL) to the empty space, set root (/) and the format.

As for EXT3 or EXT4. EXT 3 is tested and stable.  The new thing is EXT4 which is faster.  Again, it is new. If you are using 8.04, I suggest you just use EXT3 .... unless you want to really try EXT4.  

Here is the wiki for ext4

[http://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4](http://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4)

Some reading materials for you:

[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")

thnx man. i'll just go ahead and try the manual way 
also thnx for the links.... learning a lot from them :D

---

### Post by Sashamaru on 2009-06-27
encountered a problem...... yous said to set root....... but there isn't an option for root.... i took a screen for you to see my options.......
[IMG]http://i157.photobucket.com/albums/t50/MetriMetrix/DSC00752.jpg[/IMG]

---

### Post by raymondh on 2009-06-27
> **Sashamaru said:**
> encountered a problem...... yous said to set root....... but there isn't an option for root.... i took a screen for you to see my options.......
[IMG]http://i157.photobucket.com/albums/t50/MetriMetrix/DSC00752.jpg[/IMG]

root is /

---

### Post by raymondh on 2009-06-27
the slash (/) is known as root

---

### Post by Sashamaru on 2009-06-27
> **raymondhenson said:**
> the slash (/) is known as root

ok..... :D
i did it....... i have installed ubuntu successfully without losing any data.... thnk you kind sir..... you and the others that helped me.......

---

### Post by raymondh on 2009-06-27
> **Sashamaru said:**
> ok..... :D
i did it....... i have installed ubuntu successfully without losing any data.... thnk you kind sir..... you and the others that helped me.......

You are most welcome, Sir.  Now on to tweaking :)

Happy Ubuntu-ing.

---

### Post by Yvan300 on 2009-06-27
Hmmmm, it way be an xorg problem. If that is so then there is a chance that the problem will persist when you install ubuntu from a live cd. Try running the live cd and tell us what happens. If it works then most likely the problem is wubi.

For a guide to having ubuntu and xp at the same time follow this.............. well i can't remember right now, but it is a very good guide that i used myself. When i remember i will post.

---

### Post by Sashamaru on 2009-06-27
> **Yvan300 said:**
> Hmmmm, it way be an xorg problem. If that is so then there is a chance that the problem will persist when you install ubuntu from a live cd. Try running the live cd and tell us what happens. If it works then most likely the problem is wubi.

For a guide to having ubuntu and xp at the same time follow this.............. well i can't remember right now, but it is a very good guide that i used myself. When i remember i will post.

ok thnx.... if the problem persists i will come back... asta la vista baby:D

---

