---
title: "really bad stuff: grub&gt; no filesystem found after extending partition in windows"
date: 2011-10-27
forum: General Help
---

### Post by JohannesJo on 2011-10-27
As I wanted to extend my linux partition, because space was getting sparse, I used the Easus Partition Manager under windows to free up more space (seemed reasonable to me to use a windows tool, which worked before for reducing the space of a windows partition. I planed to used gparted afterwards to extent the linux partition). Unfortunately something went really wrong and now my system wont boot any more telling me no filesystem found. 
```

error: unknown filesystem grub rescue >

```There seems to be hope for not loosing any data and there are suggestions on the Internet how to fix this, but i dont want to mess anything up, by using the wrong approach. I was hopeing a simple remount would work, but I thought it might be best to search for help first.

If I use fdisk -l in the terminal of a live-cd i get:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    20482047    10240000   27  Hidden NTFS WinRE
/dev/sda2   *    20482048   262116539   120817246    7  HPFS/NTFS/exFAT
/dev/sda3       323532800   625137663   150802432    7  HPFS/NTFS/exFAT
/dev/sda4       282585087   323532799    20473856+   f  W95 Ext'd (LBA)
/dev/sda5       282585088   306780159    12097536   83  Linux
/dev/sda6       306782208   315146239     4182016   82  Linux swap / Solaris
/dev/sda7       315158528   323532799     4187136   82  Linux swap / Solaris


```I suppose that the windows partition manager somehow created sda 4 (which before was sda 5 but im not quite sure about that) overlapping with all the linux partitions and made it something strange: W95 Ext'd (LBA).

I was hoping to do something like this:
```

sudo mount -t ext4 /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda5


```source: [http://www.linuxquestions.org/questions/linux-newbie-8/grub-error-unknown-filesystem-grub-rescue-781125/](http://www.linuxquestions.org/questions/linux-newbie-8/grub-error-unknown-filesystem-grub-rescue-781125/)

But really, i have no idea if this would mess things up further. I would really glad for any help. 

Edit:
Its might be worth noting that i really really hope not to loose any data, as I'm writing my thesis atm and of course it has been quite some time since the last backup and time is running out.  :-s

---

### Post by cryptotheslow on 2011-10-27
Your partitions are not overlapping.

Presuming it is a Windows 7 install then the partitions go like this:

/dev/sda1 - Primary partition - Some kind of system / manufacturer recovery partition.
/dev/sda2 - Primary partition - Win7 Boot partition.
/dev/sda3 - Primary partition - Win7 Main partition.
/dev/sda4 - Extended partition - container for holding Logical partitions.
/dev/sda5 - Logical partition - Ubuntu /
/dev/sda6 - Logical partition - Ubuntu swapspace
/dev/sda7 - Logical partition - Ubuntu swapspace


If you plan is to reinstall grub then you should be installing to sda not sda5 in most scenarios.

So:

```
sudo mount -t ext4 /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
```Please wait for someone else to confirm - this is just my view on it and I'm far from expert! :D

As for resizing - your partitions are not physically in order on the disk. This is not a problem - it would appear you created some space in between the end of sda2 and the start of sda4. Theoretically you should be able to use GParted move sda4 to the left (as it will appear on screen). Then increase the size of sda4 to the right (as it will appear on screen). Bear in mind that this will be a tediously slow process as all the data in 5, 6, 7 will be relocated. I strongly recommend taking backups of any files before proceeding there is a risk it could go badly wrong. Don't resize or move anything until you get both OS's booting fine again!

---

### Post by JohannesJo on 2011-10-27
thank you very much! its really good not to be alone in tough times like these =)  sda3 is the most important partition, as its the drive with all data stored (documents, pictures, mp3...).  i'm also wondering what i would be practically doing there... but more important than that is that it works of course.

---

### Post by JohannesJo on 2011-10-27
Another question: What would be the best way running the commands. Should I use a live-cd and boot ubuntu and enter the commands and a regular console or should i use Alt+strg + F1? maybe even boot something else or does it not matter?

---

### Post by xyzzyman on 2011-10-27
Wouldn't [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) work? I've used it a number of times (I just install it while in a live cd/usb session) after moving partitions around and my sda #'s change. If your fstab uses UUID's you're all set after that, but if it uses /dev/sda# then you will have to update for the new partition #'s.

---

### Post by cryptotheslow on 2011-10-27
Boot Repair would be an easy way to go as xyzzyman says - use a LiveCD and follow the instructions on the link provided.

If you choose to go the command line way - again from a LiveCD - either a regular Terminal or Ctrl-Alt-F1 will do just fine.

xyzzyman - why would the partitions changed? All that has been done is sda3 shrunk. That shouldn't change the sdaNN - I also don't think UUID changes on a size change either - my fstab uses UUID and I've resized partitions a few times and not had to touch fstab due to it.

---

### Post by JohannesJo on 2011-10-27
boot repair tells me: "Please use this software in a 64bits session" .

dam what to do?

---

### Post by JohannesJo on 2011-10-27
It is said here ([http://ubuntuforums.org/showthread.php?p=10871917#post10871917](http://ubuntuforums.org/showthread.php?p=10871917#post10871917)) that i need to run it from a 64 environment if i want to repair one, but as far i know, i installed a 32 bit ubuntu. i also think my system is not even capable of running in 64 bit mode. anyone maybe got an alternative suggestion to boot-repair?

---

### Post by drs305 on 2011-10-27
```
grep --color=always ' lm ' /proc/cpuinfo
```
If you get a colored "lm", you have a 64-bit machine.
```
file `which bash`
```
If you see "64-bit" or "x86-64" you are running a 64-bit version. Note those are not straight quotes, use the one at the upper left of most keyboards.

If you can't get Boot Repair to run, please boot the LiveCD and download/run the Boot Info Script. Post the contents of RESULTS.txt between 'code' tags, which you can generate with the # icon in the post's menubar.

The script will show us the status of your boot files and help us troubleshoot your issues. You can get to the script's download page by clicking the "BIS" link in my signature line.

---

### Post by JohannesJo on 2011-10-27
Thank you all very much! After spending hours trying to get boot-repair to cooperate and coming to the believe that it is anyway not doing much more than that I simply used cryptotheslow suggestion.

```
sudo mount -t ext4 /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
```

---

### Post by critin on 2011-10-29
> **cryptotheslow said:**
> 

xyzzyman - why would the partitions changed? All that has been done is sda3 shrunk. That shouldn't change the sdaNN - I also don't think UUID changes on a size change either - my fstab uses UUID and I've resized partitions a few times and not had to touch fstab due to it.

The OP stated that his partition numbers have changed.  I believe xyzzyman was giving examples of when to use boot repair.  :)

---

