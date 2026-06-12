---
title: "EXT3 or EXT4 File System."
date: 2009-11-01
forum: General Help
---

### Post by yo2boy on 2009-11-01
Hello. I upgraded my Ubuntu 9.04 installation to the FINAL 9.10 version as I've already tested the beta and the RC.

Now, my question:

How do I check if I'm using the EXT3 File System or EXT4? Because, when I'm booting my computer, it says something about EXT3.

-- EDIT --

If I'm using the EXT3, how do I change it so that I use the EXT4?  (Like I said, I'm using 9.10)

---

### Post by exploder on 2009-11-01
I do not think that the upgrade changes the file system. You are most likely on ext3.

---

### Post by yo2boy on 2009-11-01
How can I be sure that I'm using EXT3? And, how do I change it to EXT4 then? :(

---

### Post by kaibob on 2009-11-01
To check whether you have ext4, you can use the disk utility that comes with 9.10. It's in the Administration submenu.

---

### Post by yo2boy on 2009-11-01
How do I change it to ext4??

---

### Post by ranch hand on 2009-11-01
Install from the LiveCD.

---

### Post by akand074 on 2009-11-01
There is a way to change it to an ext4 without reformatting the drive, but you need a live CD of Jaunty or higher.

Boot into the live CD

Go to *System->Partition Editor*. This will show all the partition in your hard disk. Record down the filesystem ID of the partition that you want to convert to ext4. (should be something like /dev/sda1) the one that is currently ext3.


Close the Partition Editor. Open a terminal, type the following:
  [COLOR=#C20CB9]**sudo**[/COLOR] tune2fs [COLOR=#660033]-O[/COLOR] extents,uninit_bg,dir_index [COLOR=#000000]**/**[/COLOR]dev[COLOR=#000000]**/**[/COLOR]XXXX

  Replace XXXX by the filesystem ID that you have recorded just now.
 Once that is done, type the following to fixed your partition:
  [COLOR=#C20CB9]**sudo**[/COLOR] fsck [COLOR=#660033]-pf[/COLOR] [COLOR=#000000]**/**[/COLOR]dev[COLOR=#000000]**/**[/COLOR]XXXX

  Don&#8217;t forget to replace XXXX with your filesystem ID.
 **Mount your filesystem**
  [COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**mount**[/COLOR] [COLOR=#660033]-t[/COLOR] ext4 [COLOR=#000000]**/**[/COLOR]dev[COLOR=#000000]**/**[/COLOR]XXXX [COLOR=#000000]**/**[/COLOR]mnt

  Open the fstab file:
  gksu gedit [COLOR=#000000]**/**[/COLOR]mnt[COLOR=#000000]**/**[/COLOR]etc[COLOR=#000000]**/**[/COLOR]fstab

and change the ext3 entry to ext4. Save and exit.

[IMG]http://images.maketecheasier.com/2009/04/edit-fstab.jpg[/IMG]

Back to the terminal, we need to reinstall the grub bootloader.
  [COLOR=#C20CB9]**sudo**[/COLOR] grub-install [COLOR=#000000]**/**[/COLOR]dev[COLOR=#000000]**/**[/COLOR]XXX

  This time, replace the XXX by the filesystem without the number. For example, *sudo grub-install /dev/sda*
 Close the terminal and restart the computer. Reboot into ubuntu 9.04.
 In the terminal, type
  [COLOR=#C20CB9]**df**[/COLOR] [COLOR=#660033]-T[/COLOR]

  You should see your filesystem mounted as ext4 now. 



I just pasted the instructions here for you, original source is:



[http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21](http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21)
[URL="http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21"]
[/URL]

---

### Post by zzzBrett on 2009-11-01
Make sure you have a backup of your partition before attempting to upgrade it to ext4!

---

### Post by ranch hand on 2009-11-01
> **zzzbrett said:**
> make sure you have a backup of your partition before attempting to upgrade it to ext4!
+572

---

### Post by falconindy on 2009-11-01
Converting an existing file system from ext3 to ext4 only enables the features that Ext4 provides over ext3. The conversion will **not** add these new features to any of the existing data (such as defining blocks with extents). In other words, you're not going to see a performance gain on a file system that doesn't get a lot of rewriting done on it.

Also, if you don't understand the above, you probably don't need ext4. Even as a fresh format, there's not much of a performance gain to be had.

---

### Post by Mzwo on 2009-11-02
sorry for the hijack, but can you not just use gparted to change from ext3 to ext4? 

Mzwo

---

### Post by kaibob on 2009-11-02
> **Mzwo said:**
> sorry for the hijack, but can you not just use gparted to change from ext3 to ext4? 

Mzwo

You can but it deletes the the contents of the partition.

---

### Post by ranch hand on 2009-11-02
> **kaibob said:**
> You can but it deletes the the contents of the partition.
+1
I keep hearing this and wonder "what part of format do they not understand?"

---

### Post by Zoot7 on 2009-11-02
@yo2boy

If I were you I'd stick to ext3 for simplicity's sake. To get the full advantage of ext4 you'll have to do a clean format.

---

### Post by yo2boy on 2009-11-04
> **Zoot7 said:**
> @yo2boy

If I were you I'd stick to ext3 for simplicity's sake. To get the full advantage of ext4 you'll have to do a clean format.

Yeah.. I'll do a clean format instead.

---

### Post by ranch hand on 2009-11-04
> **yo2boy said:**
> yeah.. I'll do a clean format instead.
+1

---

