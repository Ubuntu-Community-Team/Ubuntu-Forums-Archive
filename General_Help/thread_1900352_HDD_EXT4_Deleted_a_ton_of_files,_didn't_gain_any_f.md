---
title: "HDD EXT4 Deleted a ton of files, didn't gain any free space, empty trash"
date: 2011-12-26
forum: General Help
---

### Post by Colonel_Ingus on 2011-12-26
[COLOR=black]So I was running 100% full on my only HDD.
I deleted a directory containing hundreds of thousands of files and more subdirectories that was over 200GB in size. It took forever, and my system overheated.

Now I'm back and the directories are gone, or appear to be, but the space wasn't made free. I'm still full up. The trash is empty, nothing in Lost+Found.

Any suggestions? Where did the files and directories go? Why didn't I gain any free space? How can I find those files and directories and actually delete them so I can free up the space they were consuming? 
[/COLOR]

---

### Post by mikewhatever on 2011-12-26
Perhaps the directory you deleted was on another partition, in other words, not the one that got full. You should provide a lot more info, along with the output of **df -h**.

---

### Post by Colonel_Ingus on 2011-12-26
> **mikewhatever said:**
> Perhaps the directory you deleted was on another partition, in other words, not the one that got full. You should provide a lot more info, along with the output of **df -h**.


I only have 1 partition.. minus the swap of course.
[FONT=Courier New]df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             577G  534G   14G  98% /
udev                  1.9G  4.0K  1.9G   1% /dev
tmpfs                 755M  1.2M  754M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  1.9G  1.6M  1.9G   1% /run/shm[/FONT]

---

### Post by techvish81 on 2011-12-26
> **Colonel_Ingus said:**
> I only have 1 partition.. minus the swap of course.
[FONT=Courier New]df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             577G  534G   14G  98% /
udev                  1.9G  4.0K  1.9G   1% /dev
tmpfs                 755M  1.2M  754M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  1.9G  1.6M  1.9G   1% /run/shm[/FONT]

You can see the size In properties of folders to verify what you may have not deleted by mistake.

---

### Post by Colonel_Ingus on 2011-12-26
> **techvish81 said:**
> You can see the size In properties of folders to verify what you may have not deleted by mistake.

Suggesting I move up another directory and delete that? 

The thing is, whether it says there's 200GB in there or not, I can't access it, I can't see it. I tried deleting it and now its somewhere in between... gone, but not making that space usable either.

---

### Post by mikewhatever on 2011-12-26
How exactly did you delete stuff (CLI, keyboard, which keys, as root/user), and why was it necessary to delete so much? What happened when the system overheated? Did the computer shut down before the deletion was finished?

You can look for what's taking all the space with **du**.

```
du -hs /* 2>/dev/null
```

That should print out the sizes of everything in /, but might take a long time, since you have a lot there.

---

### Post by Colonel_Ingus on 2011-12-26
> **mikewhatever said:**
> How exactly did you delete stuff (CLI, keyboard, which keys, as root/user), and why was it necessary to delete so much? What happened when the system overheated? Did the computer shut down before the deletion was finished?

You can look for what's taking all the space with **du**.

```
du -hs /* 2>/dev/null
```That should print out the sizes of everything in /, but might take a long time, since you have a lot there.

Deleted using Nautilus, regular user. 

I'm running that command now...

---

### Post by Colonel_Ingus on 2011-12-26
Used your command to list the size of all directories where I deleted the large directories... they're not listed, and no abnormal sizes. 

As I said, it appears they're lost in limbo somewhere...

---

### Post by mikewhatever on 2011-12-26
> **Colonel_Ingus said:**
> Deleted using Nautilus, regular user. 

I'm running that command now...

Go on, there are a few more questions. ...and don't forget to post the output of that command.

---

### Post by Colonel_Ingus on 2011-12-26
> **mikewhatever said:**
> Go on, there are a few more questions. ...and don't forget to post the output of that command.

/home says its 710G which is bigger than my drive.
Yet contents of /home doesn't add up to anywhere near that.

---

### Post by lswb on 2011-12-26
Have you checked the disk for errors? Either boot a live CD and fsck partition from the live CD environment, or you can "sudo touch /forcefsck" and then reboot.

---

### Post by Colonel_Ingus on 2011-12-27
The disk manager says my HDD has errors, ran fsck on a reboot, didn't fix my missing free space problem.

---

### Post by lswb on 2011-12-27
> **Colonel_Ingus said:**
> The disk manager says my HDD has errors, ran fsck on a reboot, didn't fix my missing free space problem.

Suggest you read up on the man page of fsck with attention to your particular partition type, then boot a live CD and run fsck from there. You may be prompted with some questions (usually needing just a yes or no answer.)

---

