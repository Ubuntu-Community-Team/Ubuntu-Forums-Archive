---
title: "home directory read only"
date: 2009-09-27
forum: General Help
---

### Post by Mikael P. on 2009-09-27
Hello,
for some reason ubuntu decided that my home directory should be read only. I am not sure but it seems to kick in a few minutes after I start the OS.
Most folders in documents and pictures show up empty when I try and browse them. This goes away if I restart but then other folders become empty instead.
Thunderbird and Firefix both become sad as they can't write to the HD. But luckily Opera works so I can write this.

So I guess it's time for backup... But if it's not my hardware that is taking it's last breaths, what could it be?

---

### Post by aysiu on 2009-09-27
Well, there are three possibilities here: [list=1][*]Somehow you've managed to change ownership of the home directory to root[*]Your /home directory is on a separate partition and you didn't put in the correct /etc/fstab entry[*]Your /home directory is on a separate partition and that partition is somehow physically corrupted and so mounted as a read-only filesystem[/list] If it's #3, there's not much you can do. If it's #2, you should post your /etc/fstab entry here.

If you don't have /home on its own partition or drive, then it's probably #1, in which case you can boot into recovery mode (it's the second boot option--press Escape during bootup if you don't see a boot menu), drop to the root shell, and type in (unfortunately pasting won't work in this scenario, as it's a fullscreen terminal): ```
chown -R *username:username* /home/*username*
exit
``` where *username* is your actual username.

---

### Post by Mikael P. on 2009-09-27
Well, I have done nothing to the system as far as I know.
The only thing I can think of is that I accepted the latest updates.

How do I go about checking if a partition is corrupted? And yes, my /home is on it's own partition.

(and thanks for replying!)

---

### Post by sisco311 on 2009-09-27
> **Mikael P. said:**
> Well, I have done nothing to the system so as far as I know I have changed no ownerships.
The only thing is that I accepted the latest updates.

How do I go about checking if a partition is corrupted? And yes, my /home is on it's own partition.

(and thanks for replying!)

You can force a check on reboot by setting the mount count to 30+:
```
sudo tune2fs -C 40 /dev/sdXY
sudo reboot
```
replace /dev/sdXY with the actual name of your /home partition.

---

### Post by Mikael P. on 2009-09-27
Cool. Can I do that if I boot into safe mode?

---

### Post by sisco311 on 2009-09-27
> **Mikael P. said:**
> Cool. Can I do that if I boot into safe mode?

It doesn't really matters, the check will run after the system reboots.


From the Recovery Mode you can run a manual check:
```

sudo umount /dev/sdXY
sudo e2fsck -C**0** -f -p -v /dev/sdXY

```

NOTE: that's a 0 (zero) in the command,** not** an uppercase o.

The first command unmounts the partition.
The second one is the actual check.

[COLOR="Red"]WARNING!!!  Running e2fsck on a mounted filesystem may cause **SEVERE** filesystem damage.[/COLOR]

---

### Post by Mikael P. on 2009-09-27
I did a manual check. Not really sure if it reported any bad news. This is part of what I could suspect being such:
7252 non contiguous files (6.2%)
103 non contiguous directories (0.1%)
0 bad blocks
3 large files

Did this command that I ran in recovery mode automatically repair any errors it found?

Thanks for the help so far!

---

### Post by StuartN on 2009-09-27
If you are happy enough on the command line, then use **cd** (with no options) to move to your home directory and then "ls -l" and you should see something like this:

```
drwxr-xr-x  8 mikael mikael  4096 2009-09-27 12:55 Desktop
drwxr-xr-x 19 mikael mikael  4096 2009-09-27 13:22 Documents
lrwxrwxrwx  1 mikael mikael    26 2008-11-28 17:31 Examples -> /usr/share/example-content
```

i.e. the top level directories in your home belong to user mikael, group mikael and are drwxr-xr-x (directory with user read-write-execute, group read-execute and world read-execute). If you **cd Desktop** and **ls -l** again then you should see similar ownership and permissions there.

And just check **whoami**, which should match the prompt in Terminal.

---

### Post by Mikael P. on 2009-09-27
For added info, I did try this:
```

sudo tune2fs -C 40 /dev/sdXY
sudo reboot

```
While logged in on my normal account. But that command seemed to want to write to some file, so it did not work. My windows got greyed out and stopped responding. After a while it gave me access again.
But no automatic check when rebooting.

For the ls -l giving correct info I assume that I have to be logged in as myself and not being in su mode?

---

