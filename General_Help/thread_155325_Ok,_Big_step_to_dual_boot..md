---
title: "Ok, Big step to dual boot."
date: 2006-04-04
forum: General Help
---

### Post by Irish_Mob on 2006-04-04
Ok I'am thinking of putting Ubuntu on to my main comp along with XP. I have an HP. NOw if I do this. Would it lagg my system? (Proubally not). Umm, just my main consern is doint it right I guess.

---

### Post by Fffan on 2006-04-04
I did it no problem doing it myself for the first time, but as for shared partitions/swap partitions, dont ask me... I still have no idea how to compile...

Anyway, won't lag your system anymore than a few DVD files

---

### Post by RRS on 2006-04-04
[Here's]("http://users.bigpond.net.au/hermanzone/index.htm") an excellent site for installation instructions.

I'd suggest creating a Fat32 partition (Instructions in above link) during the install to use for sharing files between Windows and Ubuntu.

With a dual boot set-up only one operating system is running at a time so there should be no "lag" or slowdowns, in fact you'll find most things to be quicker in Linux then in Windows.

Welcome aboard.

---

### Post by Irish_Mob on 2006-04-05
Awsome thanks. Ok I think Ill read up on it this week and do it on Friday :) But one more question. Would it void any warrintys I have on my computer?

---

### Post by crazy_fox on 2006-04-05
Some quick tips, just so you know.

You will need at least two partitions on your system. This will not slow down your system at all, but you wont be able to use the linux partition from your win XP.

If u install windows after you install linux, Windows will overwrite your boot sector (the place on the harddrive, telling your computer where to start) , and although linux will still be on your hardrive, u wont be able to boot it..


Those are some quick tips so that you know ;)

---

### Post by az on 2006-04-05
[QUOTE=Irish_Mob]Awsome thanks. Ok I think Ill read up on it this week and do it on Friday :) ?[/QUOTE]

I live for the weekend.

[QUOTE=Irish_Mob]
But one more question. Would it void any warrintys I have on my computer?[/QUOTE]

Good question.

I'm certain it won't.

However, check your EULA.  I recently bought a Dell and I spent 2.5 hours reading all the licences (Some FUD being spread says that free-libre software licencing is complicated - WRONG!)  The only glitch was that the windows recovery solution they provided was to write an image to a "hidden" partition.  Now that works just fine unless you start playing around with your partition table.

If I ever wanted to resell that box, the buyer may want windows, so it would be nice to have a way to reinstall it (I did pay for it, although the computer would have been more expensive *without* on os)

Playing around with your partition table is in no way prohibited.  That is normal use of your computer.  It will not dammage your drive nor void the warranty - It may bork your partition table and force you to have to recover your data - which is why putting the recovery image on a partition instead of a seperate cd is not a good idea.

I phoned the vendor and they immediately sent me a reinstallation CD - which is a proper option.  

I still find it important to point out that a lot of people are under the impression that it is "against the rules" to install or run free-libre software.  That is completely false.

---

### Post by Irish_Mob on 2006-04-05
Ok cool. So if I do screw up I can call HP and get a new windows CD?

---

### Post by az on 2006-04-05
[QUOTE=Irish_Mob]Ok cool. So if I do screw up I can call HP and get a new windows CD?[/QUOTE]
You would have to ask them.  Did you get one when you got your computer?

---

### Post by OneBuntu on 2006-04-05
[QUOTE=crazy_fox]You will need at least two partitions on your system. This will not slow down your system at all, but you wont be able to use the linux partition from your win XP.

If u install windows after you install linux, Windows will overwrite your boot sector (the place on the harddrive, telling your computer where to start) , and although linux will still be on your hardrive, u wont be able to boot it,..[/QUOTE]

Good advice, except you can install Windows after Linux.

Read about it here: [http://linux.coconia.net/addingXP.htm](http://linux.coconia.net/addingXP.htm)

---

### Post by OneBuntu on 2006-04-05
This is interesting:

After, the installation (of Windows XP) you will be left to search for, and install, such items as video drivers for you video card. Although, the installation provides a small number of utilities, games, etc, you still have to install and configure the bulk of your software. 
 
 So, you now have the difficult task of reinstalling and customizing, Microsoft Office, all of your third party software, such as, Adobe Reader, Photoshop, Virus protection, your printer drivers, etc, etc. This all takes a lot of time and effort, especially if you happen to have lost the disk that came with your printer that included the printer drivers. Even worse, you often find that the disk that came with your printer does not have the necessary Windows XP/2000 drivers. 
 
 So, reestablishing a Windows system is a royal pain in the ***. In contrast, if you are satisfied with only partially accelerated video drivers, reestablishing a Novelle SuSE 10.0, is pretty much all done in 30 or 40 minutes. However, if, for example, you have an ATI video card and wish to install the fully accelerated ATI drivers, this may take you forever, as the installation seems to have been deliberately sabotaged. 
 
 On occasions, getting Windows back to the way it was, has taken all day (and sometimes longer). When people tell you how easy Windows is to install, they as lying by omission, as they omit to tell you that the install is just the beginning of reestablishing a Windows system. 
 
[http://linux.coconia.net/addingXP.htm](http://linux.coconia.net/addingXP.htm)

---

### Post by OneBuntu on 2006-04-06
[QUOTE=Irish_Mob]Ok I'am thinking of putting Ubuntu on to my main comp along with XP. I have an HP. NOw if I do this. Would it lagg my system? (Proubally not). Umm, just my main consern is doint it right I guess.[/QUOTE]
And you can use NTFS-FUSE to read/write to windows XP

[http://linux.coconia.net/suse/ntfs.htm](http://linux.coconia.net/suse/ntfs.htm)

---

### Post by mcwtlg on 2006-04-06
[QUOTE=crazy_fox]Some quick tips, just so you know.

You will need at least two partitions on your system. This will not slow down your system at all, but you wont be able to use the linux partition from your win XP.
[/QUOTE]

I do not think this is 100% true.  I downloaded and intalled an app that allows read and writing to ext2 and ext3 file systems.  The bad news is that all permissions are lost, so anyone on the PC can alter the files.

I did a dual boot on system that has 2 HD with 4 total partitions.  The first HD has both WinXP and Ubuntu 5.10 (Windows has been on that partition for over 2 years).  The partition Ubuntu was later installed on was sitting empty waiting for a job (I was considering BeOS, but I thought Linux would be better) to do.

The install went well, actually flawless.  I just told it to use the empty partition and away it went.  My only "hitch" was the largest of the two remaining partitions was NTFS and I could not get Ubuntu to read/write it until FUSE was installed.

This process was not bad at all.  I was a little nervous since I am not too strong on Linux, but Ubuntu made it very easy.  Easy Breezy :)

---

### Post by OneBuntu on 2006-04-06
"The bad news is that all permissions are lost, so anyone on the PC can alter the files."

So it is the same as windows then.

---

