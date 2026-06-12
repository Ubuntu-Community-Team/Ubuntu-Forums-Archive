---
title: "Installing ubuntu killed my partitions"
date: 2012-04-15
forum: General Help
---

### Post by Skumleren on 2012-04-15
I am not sure if i did something wrong or if its a freak bug. I installed ubuntu at least 10 times before but now this happended:
 
I was installing ubuntu 10.04 on a fresh windows machine. I got to the choice about choosing how to partition, chose the top choice (Install side by side) like i always to. When i pressed next the computer blacked out and when it started up again, it said:
 
error: no such partition
grub rescue>
 
and nothing else. I went back into the setup and chose advanced partition options, and was shocked to see that there were no paritions left.
 
Never mind what the hell happened, i will fill out a bug report later. How do i repair this? Is it even possible. Please say it is, it was a brand new PC and i didnt even create the recovery discs yet:(

---

### Post by dictodude on 2012-04-15
I have a similar problem... Although your one can be fixed.

Have you got a windows cd??

---

### Post by Skumleren on 2012-04-15
I have an old xp cd, but this is a windows 7 machine. Will the xp work?

---

### Post by oldfred on 2012-04-15
Do you have more than one drive and are booting from an old install?

Best to post boot info script so we can suggest the best corrections. you can download this into your Ubuntu liveCD or USB or download a bootable repairCD.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by Skumleren on 2012-04-15
I only have one hard drive. There should be 3 partitions. When i use ls from the grub rescue, i see three partitions (With no recongisable names)
 
I am booting from a live USB with an ubuntu 10.04 install on it.
What is this boot info script of which you speak?

---

### Post by oldfred on 2012-04-15
If you download Boot Repair it lets you run the Boot info script. It may also fix system, but best to see what is where.

You can download script only directly.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

