---
title: "dual boot"
date: 2011-01-11
forum: General Help
---

### Post by blakep2 on 2011-01-11
I have dual boot set up on my computer between ubuntu and windows xp.  I set up the ubuntu partition with 4gb mainly because I only use it for web browsing.  I have noticed that it says I have roughly 400MB left in the partition.  I have only downloaded ubuntu updates.  Is this abnormal.

---

### Post by pbpersson on 2011-01-11
That does sound like a very small hard drive for the year 2011!

---

### Post by blakep2 on 2011-01-11
Ok since there is nothing on the partition anyway is there a way I can install the ubuntu partition with say a 10GB partition without messing up the windows partition.

---

### Post by pbpersson on 2011-01-11
Assuming that you have one hard drive with two partitions (Windows and Ubuntu) and the Ubuntu partition is now 4 GB.....

When you are installing Ubuntu there is a way to shrink the NTFS Windows partition to make more room for Ubuntu but 

**BACKUP EVERYTHING ON YOUR MACHINE FIRST**

I have never used this feature myself

---

### Post by blakep2 on 2011-01-11
Ok so it should be similar to the original installation of ubuntu.  Do you know if there will be any problems with the os selector.

---

### Post by Dutch70 on 2011-01-11
> **blakep2 said:**
> Ok so it should be similar to the original installation of ubuntu.  Do you know if there will be any problems with the os selector.

There shouldn't be since you're installing the same version of Ubuntu, but you didn't say what version that was or which version of Grub you have. Is grub even what you use for a boot-loader? 

Use extreme caution when messing with your boot-loader and as someone else said, "Back up anything you don't want to lose."

---

### Post by blakep2 on 2011-01-11
yes exactly I don't know the version of GRUB but the version of ubuntu is 10.10.
I dont really want to mess with the boot-loader.  I am just wondering if I will have to with the new installation.

---

### Post by Dutch70 on 2011-01-11
> **blakep2 said:**
> yes exactly I don't know the version of GRUB but the version of ubuntu is 10.10.
I dont really want to mess with the boot-loader.  I am just wondering if I will have to with the new installation.

Karmic Koala onward uses grub2 so I don't see why it would change anything, and since you're doing a fresh install, It shouldn't.

You also may find this site helpful.
[[COLOR="Red"]***Click Here***[/COLOR]]("https://help.ubuntu.com/community/GrubHowto")

Someone else may have more info.

---

### Post by blakep2 on 2011-01-12
when I go to install ubuntu again.  How do write over the existing ubuntu installation.

Also is there any way to shrink the windows partition through the existing ubuntu installation.  I just want more space on the ubuntu partition.

---

### Post by Dutch70 on 2011-01-13
> **blakep2 said:**
> when I go to install ubuntu again.  How do write over the existing ubuntu installation.

Also is there any way to shrink the windows partition through the existing ubuntu installation.  I just want more space on the ubuntu partition.

No...Don't do that, windows does not like to be messed with from anything other than windoze. 

You just boot up your live cd/usb & install it, you don't have to worry about the existing install. It will overwrite it.

---

### Post by blakep2 on 2011-01-13
I guess I don't understand.  If windows doesn't like to be shrink-ed by anything but windows what is the ubuntu cd doing.  Also When I go to the install menu it shows the existing ubuntu partition.  What options should I select in the menu.
Install ubuntu along side other operating systems 
overwrite hard drive
Advanced Options


Also what do I do about linux swap?

---

### Post by blakep2 on 2011-01-13
double post (disregard this one)

---

### Post by wilee-nilee on 2011-01-13
We haven't really confirmed what type of install that you have; it sounds like a wubi to me. Boot the live Ubuntu cd to a try ubuntu=live session and go to system-admin-gparted and take a screenshot of it and post it.

---

### Post by presence1960 on 2011-01-13
If you have XP it is generally OK to shrink the windows partition from Ubuntu. BUT first from windows I would defrag XP once, twice is even better. Also from Control Panel I would turn off windows page file until after ubuntu is installed. Then boot to ubuntu or use the Live CD to shrink windows and create space. From the Live CD delete the ubuntu partition and use all unallocated space to install ubuntu onto by making an ext 4 partition for ubuntu. Then install to the ext 4 partition by choosing manual at the partitioning window of the installer.

If you want or need swap space I would create that along with the ext 4 partition.

---

### Post by blakep2 on 2011-01-13
> **wilee-nilee said:**
> We haven't really confirmed what type of install that you have; it sounds like a wubi to me. Boot the live Ubuntu cd to a try ubuntu=live session and go to system-admin-gparted and take a screenshot of it and post it.

[IMG]http://www.petermanweb.com/wp-content/uploads/2011/01/Screenshot.png[/IMG]

---

### Post by blakep2 on 2011-01-13
[IMG]http://www.petermanweb.com/wp-content/uploads/2011/01/Screenshot-1.png[/IMG]

---

### Post by presence1960 on 2011-01-13
You don't have a wubi installation, you have a true dual boot installation. You can defrag windows, turn off page file and then use the ubuntu Live CD to shrink sda1 by using gparted. Once sda1 is shrunk you can delete sda5 & sda6. Then you can delete the extended partition sda2. this will leave unallocated space to use to create an extended partition, and inside the extended partition 2 logical partitions- 1 ext4 for ubuntu and 1 linux-swap for swap. Then install to them using the manual method (choose partitions manually) at the partitioner window of the ubuntu Live CD installer.

---

### Post by blakep2 on 2011-01-13
How much space should I allocate for linux swap?  I don't fully understand what it is used for.

---

### Post by presence1960 on 2011-01-13
> **blakep2 said:**
> How much space should I allocate for linux swap?  I don't fully understand what it is used for.

If you want to hibernate then make swap = to installed RAM. I have 4 Gb RAM and hardly ever use suspend or hibernate but made swap 4 GB to be safe. Anything else is overkill.

---

### Post by blakep2 on 2011-01-13
Thanks so much for the help.  I think there is one more question.  What should the "space following" be set to.

---

### Post by blakep2 on 2011-01-13
also I am getting the message " NO root file system defined 
Please correct this from the partitioning menu"

What should I do?

---

### Post by blakep2 on 2011-01-13
Can anyone help me with
[http://ubuntuforums.org/showthread.php?p=10353621#post10353621](http://ubuntuforums.org/showthread.php?p=10353621#post10353621)

---

### Post by Quackers on 2011-01-13
To correct that last message you need to set a mount point of / for the root partition.

---

### Post by blakep2 on 2011-01-13
how do I do that?

---

### Post by Quackers on 2011-01-13
In the partitioning stage. You set up the partition type, size etc. The mount point is in that window where you set these details.

---

### Post by Quackers on 2011-01-13
Please don't cross post. Look at your other thread.

---

### Post by s.fox on 2011-01-13
Please do not create multiple threads for the same problem.  Thank you.

Threads Merged.

---

### Post by blakep2 on 2011-01-13
I do not see that anywhere.  I just set up the partition in Gparted.  I don not see anything about mountpoint

---

### Post by Quackers on 2011-01-13
You set the mount point in the manual partitioning stage in the installer - not gparted.

---

### Post by blakep2 on 2011-01-13
OK I have gotten to the manual partitioning stage and I don't see where there is anything to do with mount points

---

### Post by Quackers on 2011-01-13
Did you select the manual partitioning option?

---

### Post by blakep2 on 2011-01-13
yes I set up the partition with ex4 with gparted.

I noticed when I right clicked it gave the option to change then I selected "use as" it was previously selected as "do not use this partition" do I need to change it to something else?

---

### Post by Dutch70 on 2011-01-13
Take a pic of the manual partitioning stage and "attach" it to your post with the "paper clip" in the toolbar, so we're not going off memory of 10.10's installer. Use a regular camera if you have to.

I used this site to do my install & it worked great. Should answer a lot of questions for you, even though it's old.
[**[COLOR="Red"]_Psycocats_[/COLOR]**]("http://www.psychocats.net/ubuntu/partitioning")


Also, swap is similar to a page file in windows.

---

### Post by blakep2 on 2011-01-13
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=181007&stc=1&d=1294965202[/IMG]

---

### Post by blakep2 on 2011-01-13
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=181008&stc=1&d=1294965333[/IMG]

---

### Post by Quackers on 2011-01-13
Yes, I know you set up the partitions in gparted.
Now you have to tell the installer what mount points you want to use. In the manual partitioning screen double click on the partition you want to use as /root and select  /  as the mount point. If the partition is already ext4 and the right size (which it should be) you can leave those if you wish (but not if it says "do not use" as default).
Then do the same for /home partition, if you have chosen to make a separate /home partition . For that one choose /home for the mount point (from the drop down menu).
You can have a look at the swap partition but it usually looks after itself.

---

### Post by weedeater64 on 2011-01-13
> **blakep2 said:**
> yes I set up the partition with ex4 with gparted.

I noticed when I right clicked it gave the option to change then I selected "use as" it was previously selected as "do not use this partition" do I need to change it to something else?


That's the part they are talking about, there is a drop down menu when you click there with options for where to mount...

---

### Post by blakep2 on 2011-01-13
What should I select for the "use as" drop down menu.

---

### Post by blakep2 on 2011-01-13
I see the options for mounting now but they are greyed out until I select something besides "do not use this partition".

---

### Post by Quackers on 2011-01-13
You may as well choose ext4 for the /root partition then the / mount point, then tick the format box too.
Check the swap partition too. I think there is a swap type to choose.

---

### Post by weedeater64 on 2011-01-13
> **presence1960 said:**
> If you have XP it is generally OK to shrink the windows partition from Ubuntu. BUT first from windows I would defrag XP once, twice is even better. Also from Control Panel I would turn off windows page file until after ubuntu is installed. Then boot to ubuntu or use the Live CD to shrink windows and create space. From the Live CD delete the ubuntu partition and use all unallocated space to install ubuntu onto by making an ext 4 partition for ubuntu. Then install to the ext 4 partition by choosing manual at the partitioning window of the installer.

If you want or need swap space I would create that along with the ext 4 partition.


Careful with that!! I don't about the windows he is using, but I just went through a bit of hell because of selecting ext4. My Debian 2.26 was unable to mount and read the ext4 partition.

**So You'll want to make sure that your version of window can read ext4, before using that...**

Unless you don't care about reading your Ubuntu files from your windows partition, if that be the case, go ahead..

---

### Post by blakep2 on 2011-01-13
Ok the install started.  Thanks for the help guys.  I will mark it as solved once the install finishes.

Thanks again

---

### Post by blakep2 on 2011-01-13
Alright I am using windows xp professional.  So The only problem that resulted in your situation was that windows wasnt able to read the files?

---

### Post by presence1960 on 2011-01-13
> **weedeater64 said:**
> Careful with that!! I don't about the windows he is using, but I just went through a bit of hell because of selecting ext4. My Debian 2.26 was unable to mount and read the ext4 partition.

**So You'll want to make sure that your version of window can read ext4, before using that...**

Unless you don't care about reading your Ubuntu files from your windows partition, if that be the case, go ahead..

Windows can not read ext3 or ext4 natively. There is a software for reading ext3 files, but as far as I know nothing for ext4 yet.

As far as linux goes ext3 can not read/write to ext4, but ext4 can read/write to ext3.

When sharing files across multiple OSs it is best to create a partition in a filesystem that all OSs can read such as NTFS.

---

### Post by blakep2 on 2011-01-13
so whats the deal with ex2.  I saw that there as well

---

### Post by Quackers on 2011-01-13
They are just different file system types. Some are for older systems. All shapes and sizes available :wink:

---

### Post by blakep2 on 2011-01-13
So if I would have selected partitions the easy way on a fresh install of ubuntu what file system is used?

---

