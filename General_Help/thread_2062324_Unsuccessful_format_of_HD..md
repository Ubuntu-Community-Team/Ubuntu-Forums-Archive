---
title: "Unsuccessful format of HD."
date: 2012-09-24
forum: General Help
---

### Post by BlinkinCat on 2012-09-24
Hi all,

I fear I have made a mess of things. At present I dual boot with Windows 7 and Ubuntu.
Having made the decision that I wished to get rid of Windows altogether I read up on a few methods about how to go about it.
Considering myself technically challenged, I thought it would be an easier option to format the HD via Disk Utility on a live disk. However when I attempted to do this Disk Utility reported an error occurred while performing an operation etc etc .... The operation failed.
Have I ruined things entirely? or is there some way out of this mess?

Any help will be appreciated.

---

### Post by irv on 2012-09-24
> **BlinkinCat said:**
> Hi all,

I fear I have made a mess of things. At present I dual boot with Windows 7 and Ubuntu.
Having made the decision that I wished to get rid of Windows altogether I read up on a few methods about how to go about it.
Considering myself technically challenged, I thought it would be an easier option to format the HD via Disk Utility on a live disk. However when I attempted to do this Disk Utility reported an error occurred while performing an operation etc etc .... The operation failed.
Have I ruined things entirely? or is there some way out of this mess?

Any help will be appreciated.

Just boot with live CD/DVD or USB, do a fresh install and chose use the whole drive. It should format as part of the install.

---

### Post by BlinkinCat on 2012-09-24
Thanks very much irv - your're a champ.

I'll give it a go - thank you - :p

---

### Post by BlinkinCat on 2012-09-24
Looks like I have really cooked my goose this time - see gparted screenshot.
btw the windows partition appeared out of nowhere.

I suspect if I can't format the disk via live disk the installation may have had it.
Can anyone offer any suggestions?

Thank you.

---

### Post by GreatDanton on 2012-09-24
You can download live Gparted, which is (in my case) working better than Gparted included on Live cds. 

What do you mean I can't format HDD. Do you get any errors?

Regards.

---

### Post by BlinkinCat on 2012-09-24
Last message read -
error in forming the kernel about modifications to partition /dev/sda8 - device or resource busy. This means linux won't know about any changes you made to dev/sda8
until you reboot - so you shouldn't mount it in any way before rebooting.
Installation had stalled at that stage - when I cancelled data disappeared.

Screenshot is from a live version of gparted - it looks a complete mess - that is why I think I don't have much hope unless I can format drive - :confused:

---

### Post by Johnny3 on 2012-09-24
If you have a WD use their life guard to write 0 to the drive if not try this [http://www.youtube.com/watch?v=cpZwTaOHdT4](http://www.youtube.com/watch?v=cpZwTaOHdT4)
Good Luck and God Bless Johnny3 65++++

---

### Post by BlinkinCat on 2012-09-24
I attempted to install via "installer

---

### Post by BlinkinCat on 2012-09-24
I'm not real bright johnny3, I doubt if I could master that solution.

I thought if I deleted the ntfs partition and started again it might work.

What do you think?

Current screenshot -

---

### Post by BlinkinCat on 2012-09-24
I confirmed the pending operation on gparted which appeared to wipe the ntfs partition completely so maybe it will work - I can only hope so - :)

---

### Post by oldfred on 2012-09-24
What to all the errors say? Click on icons in gparted.

It sounds like Disk Utility messed with partition table. The one NTFS you had was the recovery not the main install.

You should not have to rewrite 0 to entire drive, just partition table. Only if you are sure you do not have anything to recover.

the MBR has two main parts. The boot code in the first 440 and the partition table after that.

Erase - Make double sure you have correct drive , This shows sdat.
sudo dd if=/dev/sda bs=512 count=1 | hexdump -C
Info on MBR
[http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm](http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm)
this puts zeros in sda. Make sure you type this exactly. I do not like to use dd as any typo can destroy something you do not mean to erase.
dd if=/dev/zero of=/dev/sda bs=512 count=1

---

### Post by BlinkinCat on 2012-09-24
First one -

ubuntu@ubuntu:~$ sudo dd if=/dev/sda1 bs=512 count=1 | hexdump -C
00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
1+0 records in
1+0 records out
*
512 bytes (512 B) copied, 0.0187443 s, 27.3 kB/s
00000200

---

### Post by BlinkinCat on 2012-09-24
2nd one  -
ubuntu@ubuntu:~$ dd if=/dev/zero of=/dev/sda bs=512 count=1
dd: opening `/dev/sda': Permission denied
ubuntu@ubuntu:~$

---

### Post by oldfred on 2012-09-24
I left out sudo. I run a lot of commands and then it comes back permission denied, so then I know I forgot the sudo.

try:
sudo dd if=/dev/zero of=/dev/sda bs=512 count=1

Then gparted should show it as a blank drive.

---

### Post by BlinkinCat on 2012-09-24
Should I put sudo in front of that command?

---

### Post by oldfred on 2012-09-24
Forgot it when I redid command, now fixed in previous post. Or yes add sudo.

---

### Post by BlinkinCat on 2012-09-24
ubuntu@ubuntu:~$ sudo dd if=/dev/zero of=/dev/sda bs=512 count=1
1+0 records in
1+0 records out
512 bytes (512 B) copied, 3.1213e-05 s, 16.4 MB/s

Thanks very much for all of your help Fred -

---

### Post by BlinkinCat on 2012-09-24
Sorry Fred, I've been daydreaming

This is gparted now -

Can I assume that is a straight forward install from here?

---

### Post by pakguru on 2012-09-24
I had similar problems recently when trying to format a hard drive using 'Disk Utility' in Ubuntu. In desperation I used my WinXP OS disc to to format the drive, as happens in the first stages of the WinXP installation. After this formatting I aborted the subsequent steps of WinXP installation. The Disk Utility was then able to do its stuff and enable a subsequent successful install of Ubuntu 10.04 (-I still use Lucid as I can't get on with Unity).
 I have also used this method with a Windows 98 disc when partitioning/formatting have not worked in Disk Utility. Worth a try!

---

### Post by oldfred on 2012-09-24
You should just be able to install. Note that we have seen issues with very large / (root) partitions on large drives. Best to keep / smaller.

The default install of use entire hard drive only creates / (root) and swap. I generally prefer smaller / or system partition whether Linux or Windows and separate data partition(s). A separate /home is a good way to start.

But to control partitions you have to use manual install and chose partition size, format and what to mount it as / , /home, swap etc.
For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by BlinkinCat on 2012-09-24
Hi oldfred and pakguru,

Well I have successfully installed - from what you say I hope I haven't overdone the partition sizes. Oh well, I guess I may find out.
I have a large /home partition - I hope that is O.K.

I will now be in the process of installing the files I wanted plus installing gnome shell which is my current favorite. I just wish to express my gratitude to you oldfred for helping me out - I really thought my installation was doomed - My knowledge will never reach 10% of yours. You have helped so many in these forums - Thank you - :P

BlinkinCat

---

### Post by oldfred on 2012-09-24
Glad it worked. :)

If you find /home is too large you can shrink it and create more partitions. Some choices might be to have a separate partition of 25GB just to install another operating system or next version of Ubuntu to see if you like it. That way you do not interfere with your good working install. Also data, backup or other partitions may be choices.

---

### Post by BlinkinCat on 2012-09-26
Hi oldfred,

As you can see some of my partitions may be over-large, but I was not really sure about the correct sizes. My /home will be used up a lot with movies and music, so I am quite happy having it fairly large.
Although I don't envisage it at this stage, you never know, I may have a desire to try another distro in the future.
I decided to have a go at shrinking /home to give me a bit more spare room. 

1. Do the partitions appear reasonable?

2. Is there any problem with the extended partion overlapping the unallocated space?

3. Should/could I shrink the extended partition?

4. Is there anything else I should do?

Thanks once again oldfred for all of your help.

Cheers - :p

---

### Post by oldfred on 2012-09-26
I typically do not create the other system folders as separate partitions. I did that 15 years ago with RedHat but that was more a server install with a gui to use as a desktop. Server installs may need separate partitions to isolate certain tasks, but desktops do not normally.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

You have used all 4 primary partitions, so you need to expand your extended to include all the unallocated at the end of the drive. You will only be able to create new logical partitions inside the extended.

If using multiple Linux installs you may want data in a data partition not /home. You can share /home partition but only if a different user. That to me defeats the advantage and I put all data into shared data partition and keep /home small. My /home became so small that I now include it in my / partition of 25GB. My /home is about 2GB and most of that is .wine for my Windows Picasa.

---

### Post by BlinkinCat on 2012-09-26
Hi oldfred,

Ah gee, looks like I blew it again. I thought I was doing the right thing installing the partitions that way. I could start again but that may prove to be more difficult for me to do. Although I may if you think it will be best. My question then would be should I simply install over the top with a minimal number of partitions?
Which partitions should I choose if I decide to go down that path?
I generally create 4 users to take advantage of different bookmarks for various topics.
Would I need to format? although an error occurred when I tried to do that with disk utility last time.
I trust you don't mind guiding me further - :(

Edit: I think I will go ahead and resize the extended partition for now and check back later to see if you have added any comments on the points I have made above. Right now I would love to install with /, boot, swap and /home but would need guidance about how best to go about that.

I trust you have a great day oldfred - :P

---

### Post by BlinkinCat on 2012-09-26
Hi if you're there oldfred,

At present I am in live disk attempting to enlarge extended partition however I have a problem. After selecting sda4 in gparted the information for sda4 reads Status busy, at least one logical partition is mounted. As a result I am unable to select resize as an option. 

Do you have any ideas?

Edit - I have checked each logical partition and none show as mounted.

---

### Post by oldfred on 2012-09-26
You have to use liveCD/USB to edit partitions, and even liveCD likes to mount swap to speed things up. But then gparted cannot edit anything in your extended partition as any partition mounted in extended mounts the extended partition also. Click on swap and right click swap-off to unmount swap. Then from liveCD you can edit extended partition or create more.

I used Ubuntu with just the / (root) and swap on one drive. And Windows and a NTFS shared data partition on another drive. Both were 160GB. I think I had it that way for 3 or 4 years, until I got a new larger 640GB drive and then went berserk with 25GB / partitions. I still have every install since then and some experiment installs. I am about out to room on that drive and will have to finally houseclean.

Or how you partition now may not be what you want in several years. Change is normal. :) But as long as you have room you can work with what you have.

---

### Post by BlinkinCat on 2012-09-26
Thanks oldfred,

I will give that a go - you really must be thinking of me as a bit of a pain in the neck by now.

Many thanks oldfred - :p

---

### Post by BlinkinCat on 2012-09-26
Hi oldfred,

A final post for this thread - :p

As you new it would, right click on swap off did the trick. Although the installation may be a little cumbersome, I think I will keep it as is for now. I tend to get a little overwhelmed with all of the documentation that is around. At least I have learnt a little more which is a good thing. It is my intention at this stage to stick with gnome shell and unity for 12.04. Maybe things will change in the future. Thanks again oldfred for all of your time and patience. I will bookmark this thread for future reference.

Kind regards,
BlinkinCat - ):P

---

### Post by oldfred on 2012-09-26
You are Welcome. :)

---

