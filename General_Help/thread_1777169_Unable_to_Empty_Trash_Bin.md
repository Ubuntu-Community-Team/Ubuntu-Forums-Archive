---
title: "Unable to Empty Trash Bin"
date: 2011-06-07
forum: General Help
---

### Post by jon64 on 2011-06-07
I'm running Ubuntu 10.04 and I'm having trouble emptying my trash bin. I've tried emptying the trash bin graphically but the items are still in there. I've also tried using nautilus to empty the trash but it didn't work either. I really need to free up some space because I'm down to 1.6 GBs of free space :(

---

### Post by iclestu on 2011-06-07
> **jon64 said:**
> I'm running Ubuntu 10.04 and I'm having trouble emptying my trash bin. I've tried emptying the trash bin graphically but the items are still in there. I've also tried using nautilus to empty the trash but it didn't work either. I really need to free up some space because I'm down to 1.6 GBs of free space :(

Dont know how to fix directly but if it is a single problematic file you could just restore it and then just

```
sudo rm /path/to/fileYouNeedRemoved
```bit of a crappy workaround tho....

---

### Post by seawolf167 on 2011-06-07
There are probably items in root's trash bin, type the following command to see root's trash bin, then simply delete the items there

```
gksudo nautilus /root/.local/share/Trash
```note that if you trash something on a flash drive but don't empty the trash before you remove the drive it will still display that something is in there

EDIT: changed /home/your_username to /root in the above command, wasn't thinking straight!

---

### Post by whatthefunk on 2011-06-07
The trash is located at ~/.local/share/Trash

You could go in through a terminal and manually delete things.

---

### Post by emarkay on 2011-06-07
When in doubt, reboot.  I see this often when I mound and unmount drives and all that...

---

### Post by seawolf167 on 2011-06-07
> **emarkay said:**
> When in doubt, reboot.  I see this often when I mound and unmount drives and all that...

You shouldn't need to reboot for anything but kernel updates and graphics card driver installations/updates. A simple log out/log or killing and restarting the appropriate service should do the trick. The trash file on the other hand wouldn't be affected by either of these things.

---

### Post by jon64 on 2011-06-07
> **whatthefunk said:**
> The trash is located at ~/.local/share/Trash

You could go in through a terminal and manually delete things.
When I go to ~/.local/share/Trash and do ls -l it says there isn't any files in there even though there should 20. I've tried right clicking the files in my trash bin and checking out where the location is but all it's giving me is trash:///

---

### Post by sisco311 on 2011-06-07
Your home trash is ~/.local/share/Trash, but you may have other trash directories  in the &#8220;top directories&#8221; of any of your extra partitions.

For example, if the partition is mounted in /media/data, the trash could be /media/data/.Trash or /media/data/.Trash-**uuid**.

---

### Post by jon64 on 2011-06-07
> **sisco311 said:**
> Your home trash is ~/.local/share/Trash, but you may have other trash directories  in the “top directories” of any of your extra partitions.

For example, if the partition is mounted in /media/data, the trash could be /media/data/.Trash or /media/data/.Trash-**uuid**.

Oh I see. All the files I would like to empty out of the trash was located in /mnt/storage1/ would I have to go to /mnt/storage1/.Trash to permanently delete the files?

---

### Post by jon64 on 2011-06-07
Just tried both /mnt/storage1/.Trash and /mnt/storage1/.Trash-uuid but the file/folder doesn't exist.

---

### Post by drs305 on 2011-06-07
Just to be clear, you would replace "-uuid" with your UUID. The first user is normally 1000, so the folder would be named .Trash-1000.

You can search your entire system (mounted partitions) for any Trash or .Trash folder with this command:```

sudo find / -type d -name *Trash* 
```

Here is the link to a Trash thread I wrote a while back that discusses some issues with the Ubuntu/Linux trash bins:
[http://ubuntuforums.org/showthread.php?t=898573]("http://ubuntuforums.org/showthread.php?t=898573")

---

### Post by whatthefunk on 2011-06-07
> **jon64 said:**
> When I go to ~/.local/share/Trash and do ls -l it says there isn't any files in there even though there should 20. I've tried right clicking the files in my trash bin and checking out where the location is but all it's giving me is trash:///

The actual files are in  ~/.local/share/Trash/files
Did you try looking there?

---

### Post by jon64 on 2011-06-07
> **drs305 said:**
> Just to be clear, you would replace "-uuid" with your UUID. The first user is normally 1000, so the folder would be named .Trash-1000.

You can search your entire system (mounted partitions) for any Trash or .Trash folder with this command:```

sudo find / -type d -name *Trash* 
```Here is the link to a Trash thread I wrote a while back that discusses some issues with the Ubuntu/Linux trash bins:
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
The search function was very useful and found four different trash locations. 
~/.local/share/Trash
/mnt/storage1/.Trash-0
/mnt/storage1/.Trash-1000
/root/.local/share/Trash

I was only able to go into two of the following trash locations. 
~/.local/share/Trash
/root/.local/share/Trash

The other two locations, I wasn't able to go to their locations because they didn't exist even though the search command found them.

---

### Post by jon64 on 2011-06-07
> **whatthefunk said:**
> The actual files are in  ~/.local/share/Trash/files
Did you try looking there?
That location didn't exist but if you meant ~/.local/share/Trash then there are no files located in this trash bin.

---

### Post by drs305 on 2011-06-07
> **jon64 said:**
> The search function was very useful and found four different trash locations. 
~/.local/share/Trash
/mnt/storage1/.Trash-0
/mnt/storage1/.Trash-1000
/root/.local/share/Trash

I was only able to go into two of the following trash locations. 
~/.local/share/Trash
/root/.local/share/Trash

The other two locations, I wasn't able to go to their locations because they didn't exist even though the search command found them.

See if you can access them with this command. Make sure hidden file viewing is enbabled in Nautilus preferences. When you delete the files, use SHIFT-DEL so they aren't moved to the Trash!

```
gksu nautilus /mnt/storage1/.Trash-0/files /mnt/storage1/.Trash-1000/files
```

---

### Post by jon64 on 2011-06-07
> **drs305 said:**
> See if you can access them with this command. Make sure hidden file viewing is enbabled in Nautilus preferences. When you delete the files, use SHIFT-DEL so they aren't moved to the Trash!

```
gksu nautilus /mnt/storage1/.Trash-0/files /mnt/storage1/.Trash-1000/files
```

Thank you!!!! I was just about to post a progress update on how I found out how to get into the trash locations that I wasn't able to enter before. I was successful in deleting all the files in /mnt/storage1/.Trash-1000/files and /mnt/storage1.Trash-1000/info but they would just get sent to /mnt/storage1/.Trash-0 and deleting the files again in Trash-0 would just replicate the files I deleted. Thanks again!!! I now have 40GB of free space instead of 1.6GB :D

---

