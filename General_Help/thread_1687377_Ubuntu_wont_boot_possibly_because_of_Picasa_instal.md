---
title: "Ubuntu wont boot possibly because of Picasa install"
date: 2011-02-13
forum: General Help
---

### Post by ifunky2 on 2011-02-13
I have an HP laptop. I had Ubuntu 9 running perfectly for months and now it won't boot at all. 
When I start the computer it begins with the BIOS screen (and option to enter startup/boot menu). Then, that's it! Black screen, no matter how long you wait. I am running Ubuntu live off of a USB stick so I know all my hardware is fine.

When it crapped out:
I was doing basic things such as I had Gedit, FireFox and Chrome (for emails) running. I wanted to do some image, batch edits and after googling a bit decided to install Picasa. The install seemed fine and I had Picasa up and running. All of a sudden a text file I wanted to edit with Gedit gave me an insufficient permissions error warning.
I do not remember exactly what I did from there but basically I closed out everything and shut down the computer, it hasn't booted since.

Any help, any ideas that would help me recover would be greatly appreciated. I really don't want to have to reinstall/reconfig my whole computer again. However I am not all that savvy with computers let alone Ubuntu, so if it's going to be a long, drawn out process trying to recover...

Thank you ahead for any ideas.

---

### Post by oldfred on 2011-02-13
From a liveCD lets run this to see if there is something obvious.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by ifunky2 on 2011-02-14
ubuntu@ubuntu:~4 sudo bash ~/Desktop/boot_info_script.sh
Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb
Searching sda1 for information...

~~~~~~~~~~~~~~~~~~~~

I ran this three times and each time it hangs there/only gets that far 
(once I waited 20 minutes) 

No more info, no txt file of results written to the same dir (Desktop)

---

### Post by oldfred on 2011-02-15
The script cannot read the drive/partition, so it has major errors. If windows NTFS run chkdsk on sda1. 

If a linux partition run

From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

