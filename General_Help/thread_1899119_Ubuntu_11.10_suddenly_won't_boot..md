---
title: "Ubuntu 11.10 suddenly won't boot."
date: 2011-12-22
forum: General Help
---

### Post by hiimcailin on 2011-12-22
I have been using Ubuntu 11.10 along side Windows 7 for several weeks with only small issues, (rare freeze ups, mouse randomly stops working until reboot) But today everything froze, I waited several minutes with no response from my computer and after I tried everything else I just had to do a hard shut down. After I turned my computer back on and chose Ubuntu I got a the GRUB screen. I typed "boot" and it came back "error not kernel found". The only other thing out of the ordinary that happened with the computer lately is Windows installing some updates, and I had installed Tor on each OS. 
Is there a way I can fix this aside from re-installing Ubuntu?
I searched through some other forums which said something about going into recovery mode from that screen, but I could not enter any command to get to recovery mode.

---

### Post by QIII on 2011-12-22
Just to clarify, because people often confuse the two:

Did you install Ubuntu "along side" Windows by creating a separate partition for Ubuntu and installing it there, or did you use Wubi to install Ubuntu while you had Windows running?

---

### Post by hiimcailin on 2011-12-22
I believe it is installed along side Windows. When I turn my computer on I get a message saying it has detected 2 operating systems and I can choose wither W7 or Ubuntu.

---

### Post by QIII on 2011-12-22
Could you please pop the Ubuntu LiveCD in and boot your computer?

When Ubuntu loads (it will take a while in a live session), go to the terminal and type

```
sudo fdisk -l
```(that's an "ell" not a "one") and post back the results?

---

### Post by fdrake on 2011-12-22
to get to rescue mode:[https://help.ubuntu.com/community/Grub2#Last_Boot_Failed_or_Boot_into_Recovery_Mode](https://help.ubuntu.com/community/Grub2#Last_Boot_Failed_or_Boot_into_Recovery_Mode)

section "Command Line and Rescue Mode".
if you still have problem or you are confused, check the link in my signature ("Boot Script" and post here the results)

---

### Post by hiimcailin on 2011-12-22
I will have to use my work computer to make a cd tomorrow. Will post results then.

---

### Post by bcbc on 2011-12-23
> **hiimcailin said:**
> I have been using Ubuntu 11.10 along side Windows 7 for several weeks with only small issues, (rare freeze ups, mouse randomly stops working until reboot) But today everything froze, I waited several minutes with no response from my computer and after I tried everything else I just had to do a hard shut down. After I turned my computer back on and chose Ubuntu I got a the GRUB screen. I typed "boot" and it came back "error not kernel found". The only other thing out of the ordinary that happened with the computer lately is Windows installing some updates, and I had installed Tor on each OS. 
Is there a way I can fix this aside from re-installing Ubuntu?
I searched through some other forums which said something about going into recovery mode from that screen, but I could not enter any command to get to recovery mode.

Hard reboots will do that: [http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html)

Use Alt+SysRq R-E-I-S-U-B if it hangs.

---

### Post by hiimcailin on 2011-12-23
> **QIII said:**
> Could you please pop the Ubuntu LiveCD in and boot your computer?

When Ubuntu loads (it will take a while in a live session), go to the terminal and type

```
sudo fdisk -l
```(that's an "ell" not a "one") and post back the results?

Okay, was able to boot from the disk, it wanted to go through as a new install, but I just ran off the disk. When I entered the "sudo -l" into terminal I got "Matching Defaults entries for ubuntu on this host: env_reset   User ubuntu may run the following commands on this host: (ALL) NOPASSWD: ALL"

---

### Post by QIII on 2011-12-23
You didn't type the entire command.  Try again and see what happens.  We are going to go through what the other poster's script would do,  but this way we get a chance to stop and discuss so you get a chance to learn something worthwhile for later.

---

### Post by ItalyVillas on 2011-12-23
hi frnd

mya bee u uses pirated software or aur ur minght be ur motherboard getting problem if u receive any hardisk errer while ubuntu intalling...

---

### Post by QIII on 2011-12-23
Unfortunately, this may not be something either of us has time to go through step by step at this hour.

The script fdrake has in his signature will pull out a lot of data in a big dump that may not make any sense to you.  I had hoped we would have the time to pick it apart a little bit at a time and discuss what it all meant.

I hope whoever picks this thread up will do that.

Run the script and post the dump.

But if you would, ask whoever helps you to give you some understanding of what you are seeing so you know what to look for the next time you need to do it for yourself.  And you might be better able to help the next person.  I think it really sucks when someone looks at the report and says "Run this command" and you do -- without ever learning why the other guy knew what to run.

After you post the dump, would you take a look at two of the things that the script makes use of:

```
man fdisk
``````
man blkid
```The script goes in to a lot of other things besides these two and creates a really nicely summarized report.  But often the two I listed are often enough to light the bulb and let you see what you need to do.

---

### Post by hiimcailin on 2011-12-23
Okay, my mistake. Late nights can do that to a person. Anyways, here's the correct results.
And no, I did not install pirated software on my computer.

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x97804ced

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     3074047     1536000   27  Hidden NTFS WinRE
/dev/sda2         3074048   954376191   475651072    7  HPFS/NTFS/exFAT
/dev/sda3       954376192   976773119    11198464   17  Hidden HPFS/NTFS

```
I appreciate the assistance.

---

### Post by QIII on 2011-12-23
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total [COLOR=DarkGreen]976773168 [/COLOR]sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x97804ced

   Device Boot      Start         End      Blocks   Id  System
[COLOR=Blue]/dev/sda1   [/COLOR][COLOR=DarkGreen][COLOR=Navy][COLOR=Blue]*[/COLOR] [/COLOR]       2048[/COLOR]     3074047     1536000   27  [COLOR=Red]Hidden NTFS WinRE[/COLOR]
/dev/sda2         3074048   954376191   475651072    [COLOR=Red]7  HPFS/NTFS/exFAT[/COLOR]
/dev/sda3       954376192   [COLOR=DarkGreen]976773119[/COLOR]    11198464   [COLOR=Red]17  Hidden HPFS/NTFS[/COLOR]

```From this, I can deduce a couple of things.

1.  All the partitions on your drive are NTFS or other Windows-native file formats.  (See highlighted red.  NTFS is the general purpose file system, HPFS is High Performance File System.  That my be what Win 7 uses.  I'm not anything more than a casual Windows user and then only when necessary.  So I haven't kept up.)

2.  You do not have a dedicated Linux partition.

3. The first partition of your drive is set as the boot point (see the asterisk and blue)

4.  You aren't missing any partitions that may have been wiped out accidentally (see the numbers I highlighted in green).

So I think what you have done is a Wubi install.  Do you remember if you were in Windows and had to run some sort of a program in windows while it was running to install Ubuntu?

When you first start your computer, do you (or maybe did you) get something that looks like the image under the heading "How do I select whether to run Windows or Ubuntu?" at [https://wiki.ubuntu.com/WubiGuide?](https://wiki.ubuntu.com/WubiGuide?)

Can you boot into Windows?

---

### Post by hiimcailin on 2011-12-23
Yes, I get a screen like that and yes, I can boot Windows with no issues.

---

### Post by bcbc on 2011-12-23
Maybe my post ( [http://ubuntuforums.org/showpost.php?p=11558746&postcount=7](http://ubuntuforums.org/showpost.php?p=11558746&postcount=7) ) was a bit vague. So I'll repeat it:

With Wubi the most common problem for not booting is a missing root.disk or file corruption. If you review that blog page (or not) it recommends to:
1. run chkdsk
2. ensure the root.disk is there
3. try again

Sometimes a hard reboot will also corrupt the ext4 file system (within the root.disk). But that's a different fix.

---

### Post by hiimcailin on 2011-12-23
> **bcbc said:**
> Maybe my post ( [http://ubuntuforums.org/showpost.php?p=11558746&postcount=7](http://ubuntuforums.org/showpost.php?p=11558746&postcount=7) ) was a bit vague. So I'll repeat it:

With Wubi the most common problem for not booting is a missing root.disk or file corruption. If you review that blog page (or not) it recommends to:
1. run chkdsk
2. ensure the root.disk is there
3. try again

Sometimes a hard reboot will also corrupt the ext4 file system (within the root.disk). But that's a different fix.

Thanks for clarifying. I'm in the process of doing this. I ran chkdsk, which took about 5 hours, so I will try to post result tonight.

---

### Post by bcbc on 2011-12-24
> **hiimcailin said:**
> Thanks for clarifying. I'm in the process of doing this. I ran chkdsk, which took about 5 hours, so I will try to post result tonight.

That seems like a really long time for chkdsk. What sort of messages did it spit out?

---

### Post by hiimcailin on 2011-12-25
Nothing out of the ordinary, I've done the chkdsk before. The mail reason it took so long is the part where it was just checking the files. It said it was checking 310,000 files, so I image that would take a while.

In regards of finding the "found" file I was extremely unsuccessful. I opened command as admin and entered the commands, but I was continuously getting "Access is denied". I checked the admin profile and made sure the permissions were set properly. I opened god mode and made sure system was set to show all hidden files and give me full access. That was already set up. I went back to command and tried the same codes again with no success, I then tried the same codes with different files and got the same "Access is denied" even when I try to use the location of some picture files instead. So now I feel as if I am really doing something wrong here.

In addition, I had a previous version of my C drive backed up from before I had the issue. I tried to replace just the Ubuntu information from that back up, but I did not have permission to change those files.

Also, hope everyone is having a good Christmas, if that's your thing.

---

