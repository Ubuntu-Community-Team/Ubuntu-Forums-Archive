---
title: "mount of root filesystem failed"
date: 2010-02-12
forum: General Help
---

### Post by nipunreddevil on 2010-02-12
i am not able to boot into ubuntu 9.10 which is installed within windows.it worked fine till yesterday when it showed some erratic behavior and now i am not able to boot.it says that a maintenance shell will be started.how can i rectify this error?

---

### Post by nipunreddevil on 2010-02-13
Now even the previous message is not appearing.Just caps lock key is continuosly turning on/off.
My Ubuntu is installed within windows in /dev/loop0

---

### Post by nipunreddevil on 2010-02-13
Is there any way i can get away without formatting my system.Please help.

---

### Post by amsterdamharu on 2010-02-13
Did you do an update? Maybe booting with the previous kernel will help. I have seen some problems with wubi install.

You might boot with the live cd and see if you're root.disk is corrupt:
[http://ubuntuforums.org/showthread.php?t=1396857#9](http://ubuntuforums.org/showthread.php?t=1396857#9)

If it is there us not much you can do about it though.

---

### Post by nipunreddevil on 2010-02-26
How can i recover my data?It is very critical.

---

### Post by amsterdamharu on 2010-02-26
Can you start the computer form the Ubuntu installation disk and run live mode? I think the menu entry is called try Ubuntu or something like that.

Then mount the big file on your windows drive and see if anyting goes wrong, copy and paste the following commands in a terminal in Ubuntu (running off the cd).```

sudo mkdir -p /media/WindowsXP
echo "Mounting NTFS Partition"
sudo mount -t ntfs /dev/sda1 /media/WindowsXP
sleep 1
sudo mkdir -p /media/root.disk
echo "Mounting Wubi Disk"
sudo mount -o loop /media/WindowsXP/ubuntu/disks/root.disk /media/root.disk
sleep 1
echo "Done :)"
gksu nautilus /media/root.disk

```Post any errors or warnings you might get, the terminal allows you to copy and paste what's in there.

---

### Post by nipunreddevil on 2010-02-26
i have windows Vista so shall i replace all XP with Vista in the code?

---

### Post by amsterdamharu on 2010-02-27
Sorry for the late reply, but no you don't need to replace xp with vista in the command.

/dev/sda1 means first harddisk first partitition. The a in sda is first harddisk the 1 in sda1 means first partititon so if windows is on the first harddisk first partition you don't need to change anything. It will not do anything with windows.

---

### Post by meierfra. on 2010-02-27
You might be hit a bug in Grub2.  For more  details  and how to fix it see:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by nipunreddevil on 2010-03-04
> **amsterdamharu said:**
> Can you start the computer form the Ubuntu installation disk and run live mode? I think the menu entry is called try Ubuntu or something like that.

Then mount the big file on your windows drive and see if anyting goes wrong, copy and paste the following commands in a terminal in Ubuntu (running off the cd).```


sudo mount -o loop /media/WindowsXP/ubuntu/disks/root.disk /media/root.disk


```Post any errors or warnings you might get, the terminal allows you to copy and paste what's in there.
I get an error at the quoted line.It says "No such file or directory"

Any hopes of recovering data?

---

### Post by nipunreddevil on 2010-03-04
BTW i am able to access extra.disk,home.disk,new.disk,root.disk,swap.disk which are there in my ubuntu folder in windows using the live cd.Will that be of any help?

---

### Post by jwbrase on 2010-03-04
> **nipunreddevil said:**
> I get an error at the quoted line.It says "No such file or directory"

Any hopes of recovering data?

Certainly. All the error means (so far) is that amsterdamharu guessed wrong about where the file we need is.

Directly before you type the line that gives the error, type the following command:

```
ls /media/WindowsXP
```

That should show you the list of top-level folders on your Windows drive. "ls" means "list" and tells the computer to list the files and folders in the specified folder. (Alternatively, if you want to do it graphically, you could use

```
nautilus /media/WindowsXP
```

to open up Nautilus to that folder, or boot into Windows (if it still boots), and use Windows Explorer, and post the list of folders on C:\ (or whatever drive Ubuntu is on)).

Post the list of folders you get (It should include things like "Documents and Settings", "Program Files", and "Windows").

If there is a folder "ubuntu", then type

```
ls /media/WindowsXP/ubuntu
```

(or browse the folder with Nautilus or Windows Explorer, and get the list of folders in "ubuntu").

If "ubuntu" has a folder "disks", do

```
ls /media/WindowsXP/ubuntu/disks
```

And post the names of any files in there to here. Compare the names of the folders and files you find to the command that gives the error. If there's something similar, but not exactly the same, to one of the names in bolded part of the command: "sudo mount -o loop /media/WindowsXP/**ubuntu/disks/root.disk** /media/root.disk", then replace that name in the command with the one you find.

For example, if you find a folder under "ubuntu" called "disk", then replace "ubuntu/disks/root.disk" with "ubuntu/disk/root.disk". Or if there's a file "root.disk" under "ubuntu", and no "disks" or "disk" folder at all, then replace "ubuntu/disks/root.disk" with "ubuntu/root.disk".

If there's no "ubuntu" folder, but there is a "Program Files" folder, try looking for it there:

```
ls "/media/WindowsXP/Program Files"
```

Another problem you may be encountering is capitalization errors: Make sure that the capitalization you're using in the "sudo mount -o ..." command is the same as you're getting from "ls". ls and nautilus should give you the capitalization you need, since Linux is case sensitive, Windows Explorer might not, since Windows isn't. You may just need to replace "ubuntu/disks/root.disk" with something like "Ubuntu/Disks/root.disk".

---

### Post by jhoney142 on 2010-03-04
Hi,
 there is the several ways to recovery data 
    1. from boot  CD's.
    2. Master and slave process (In this process the Hard disk will be connected to other system boot form that system you can recover the data)

---

### Post by jwbrase on 2010-03-04
> **nipunreddevil said:**
> BTW i am able to access extra.disk,home.disk,new.disk,root.disk,swap.disk which are there in my ubuntu folder in windows using the live cd.Will that be of any help?

OK: root.disk is directly under the "ubuntu" folder?

In that case:

```
sudo mount -o loop /media/WindowsXP/ubuntu/disks/root.disk /media/root.disk
```

should be:

```
sudo mount -o loop /media/WindowsXP/ubuntu/root.disk /media/root.disk
```

The "/media/WindowsXP/ubuntu/root.disk" part just tells it where to find "root.disk".

"/media/WindowsXP" is the name we've given to your Windows hard drive in Linux. (That's why it didn't matter if we called it "WindowsXP" or "Vista", since what we were doing was telling Linux what to call it).

So everything after "/media/WindowsXP" should be exactly the same as the path to the root.disk file.

EDIT: You'll definitely also want to mount home.disk and possibly extra.disk, depending what's on it. You don't need to mount swap.disk, and it might cause problems if you try (unsure, in any case, it doesn't have data on it). 

To do that you'll need to repeat the following lines with "root.disk" replaced by "home.disk" and "extra.disk", to mount the respective file.

```
sudo mkdir -p /media/root.disk
echo "Mounting Wubi Disk"
sudo mount -o loop /media/WindowsXP/ubuntu/disks/root.disk /media/root.disk
```

The "gksu nautilus" at the end of what amsterdamharu told you to do just opens up root.disk in nautilus. To look in home.disk and extra.disk you can do the same command with them.

---

### Post by nipunreddevil on 2010-03-04
Ok..thanks a ton..I can now back up my data as i am able to access it.Still any way of preventing format??

---

### Post by jwbrase on 2010-03-04
> **nipunreddevil said:**
> Ok..thanks a ton..I can now back up my data as i am able to access it.Still any way of preventing format??

To know that we'd have to figure out exactly what's wrong.

And you wouldn't be "formatting" exactly, since it's a Wubi install. Rather, you'd just go back into Windows, uninstall it, and reinstall it. If you formatted, it would erase your entire Windows install, which, unless something's happened to it that you haven't said anything about, seems to be fine.

---

### Post by nipunreddevil on 2010-03-04
Another problem now.I have home.disk,new.disk,root.disk,swap.disk and extra.disk.All these contain my data but it's slightly outdated.Actually i had increased my wubi partition size long time back and it could be due to that.Any suggestions

---

### Post by jwbrase on 2010-03-04
> **nipunreddevil said:**
> Another problem now.I have home.disk,new.disk,root.disk,swap.disk and extra.disk.All these contain my data but it's slightly outdated.Actually i had increased my wubi partition size long time back and it could be due to that.Any suggestions

Swap.disk shouldn't contain any data. It's just a storage space in case Ubuntu runs out of RAM.

As to the other files, how far outdated is the data in them? Back to right before you started having problems? Back to a few weeks before that? A few months?

If you increased your Wubi partition size, extra.disk may contain the additional stuff (I'm not entirely sure how Wubi does things, but it's an educated guess based on the name "extra").

---

### Post by meierfra. on 2010-03-04
Let's have a closer look at your system:

Follow these i[nstructions]("http://bootinfoscript.sourceforge.net") to run the boot info script and post the RESULTS.txt

---

