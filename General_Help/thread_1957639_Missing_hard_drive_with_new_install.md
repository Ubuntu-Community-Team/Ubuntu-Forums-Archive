---
title: "Missing hard drive with new install"
date: 2012-04-12
forum: General Help
---

### Post by axxicE on 2012-04-12
I decided I wanted to try Ubuntu out and have come across a problem with my 2nd hard drive. My windows 7 is installed on my SSD which is my main drive. But I use a mechanical hard drive for installing programs to. I installed Ubuntu on the HDD, after resizing the partition and making 2 new partitions for the root & swap for linux. When the master boot question popped up at the end of install I told it to install to the SSD instead of the HDD so I could dual boot through the grub. When it was all done the pc restarted, but now when I restart there is no grub or option for Ubuntu, just goes automatically to windows, and inside windows (the real problem) I have no second drive, just my SSD. I need to access the files on the older drive and dont believe I formatted over the drive itself. Thanks for the help!

---

### Post by oldfred on 2012-04-13
Welcome to the forums.

We need you to run the bootinfo script which documents your entire boot configuration. You can download Boot Repair into your Ubuntu liveCD/USB or download it as a liveCD of its own.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

Or:
You can directly download and run script from Ubuntu or liveCD. post results.txt inside code tags (# on message edit panel).

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by axxicE on 2012-04-13
I found that I have erased my data and theres no going back now. I have one more problem, if you dont mind. I partitioned the remainder of my hard drive to add onto the memory I could use with Ubuntu, but ubuntu isnt installed on the partition. Is there a way to re-partition it so I could use it with windows because I use windows 50% of the time and would need the space back to download my old data. Thanks for the quick reply earlier!

---

### Post by oldfred on 2012-04-13
Is it a separate partition, do you have any data in it to save first?

If an empty partition just use gparted and reformat to NTFS. Then you can store data from both Ubuntu & Windows in that partition.

You will want to mount the NTFS partition in Ubuntu to use it.

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by axxicE on 2012-04-13
It is a separate partition and the partition is empty, however the hard drive as a whole is not empty. Can you format a partition and not an entire drive?

---

### Post by oldfred on 2012-04-13
Sure, just be careful on which partition.

---

### Post by axxicE on 2012-04-14
Worked awesome, thanks! Used Gparted to reformat partition.

---

