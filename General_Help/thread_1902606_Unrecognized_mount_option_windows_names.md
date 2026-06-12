---
title: "Unrecognized mount option windows_names"
date: 2011-12-31
forum: General Help
---

### Post by t-a-s on 2011-12-31
Hi,

I recently got some help mounting an ntfs partition using fstab [here.]("http://ubuntuforums.org/showthread.php?p=11519761")

This was the line line I added to fstab to achieve it:

UUID=3012DCD612DCA1E0 /windows ntfs defaults,nls=utf8,umask=007,gid=46,windows_names 0 0

This worked perfectly until morning when I started up it said "unable to mount /windows" on start up.

When I look in dmesg it says "Unrecognized mount option windows_names"

I would applicate any help in getting this sorted.

---

### Post by Paddy Landau on 2011-12-31
Ubuntu sometimes cannot mount an NTFS partition if it had not been shut down cleanly.

Try booting into Windows; run check-disk on all NTFS partitions; restart into Ubuntu. Do you still have the problem?

---

### Post by Morbius1 on 2011-12-31
If that doesn't resolve the issue and since I use the "windows_names" option myself without issue my first guess is that somehow ntfs-3g got removed or corrupted somehow. Try installing it:
```
sudo apt-get install ntfs-3g
```Or reinstalling it:
```
 sudo apt-get --reinstall install ntfs-3g
```

---

### Post by Morbius1 on 2011-12-31
My apologies. The recommendation I gave above won't do diddly as I have just reproduced your symptoms.

11.10 has far too many fundamental packages that I rely on broken to be of any use to me but I do have it installed in VBox and thought I was up to date with the updates. I just did an update and it does in fact have a problem.

But it's a curious bug:

* When you boot you will get an error about the ntfs partition having serious errors ....

* When you tell it to skip it will not mount the partition

* But after you boot if you open up a terminal and tell it to do a check of fstab and mount all of the partitions that have not mounted by running the following command:
```
sudo mount -a
```It does mount the ntfs partition without errors indicating there is nothing wrong with the windows_names parameter.

This one will need investigating - it appears that the ntfs-3g "driver" is not loading at boot time or at least not in time but I'm not sure at the moment.

If you don't want to be annoyed with the error remove the windows_names parameter from fstab but just make sure you are carefull about file names saved to that partition because the windows_names option prevents you from saving it with a name Windows cannot recognize.

---

### Post by t-a-s on 2011-12-31
Hi,

Thanks for the replies, I completed a chkdsk and there were no errors, there was no "dirty" flag from Windows either.

I have reinstalled the ntfs-3g driver as Morbius1 initially suggested and it's back to normal! So it must have been corrupted somehow.

Just to clarify on start up it only said that there was an error mounting it not about the partition having serious errors. Also the error was also apparent when trying to manually mount in terminal.

Thank you for all your help.

---

### Post by Paddy Landau on 2011-12-31
I'm glad you managed to solve it. Well done to Morbius1 for suggesting a reinstallation.

Please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") to help others with the same problem.

---

