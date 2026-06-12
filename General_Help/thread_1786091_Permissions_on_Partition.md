---
title: "Permissions on Partition"
date: 2011-06-19
forum: General Help
---

### Post by Pizarro on 2011-06-19
How do I change permissions from root to any user on my partition /dev/sda3 as I want all users to be able to read and write to it.

---

### Post by coffeecat on 2011-06-19
Where is it mounted, and what filesystem?

If it is a Linux filesystem, you can set permissions either by adding mount options in /etc/fstab, or chmodding the filesystem itself. If it is mounted:

```
sudo chmod 777 /media/mountpoint
```

Change mountpoint as appropriate. In that command you don't need the -R recursive option as you are chmodding the root of the filesystem itself. The changed permission will still work even if you mount the partition on another mountpoint.

---

### Post by Pizarro on 2011-06-19
so would the command be
sudo chmod 777 /media/dev/sda3

---

### Post by coffeecat on 2011-06-19
> **Pizarro said:**
> so would the command be
sudo chmod 777 /media/dev/sda3

/media/dev/sda3 seems an unlikely mountpoint, so I doubt it. Did you automount it from the Places menu, or Places left pane in Nautilus? If so, post the output of:

```
ls /media
```

---

### Post by vanadium on 2011-06-19
You can learn where your partition is mounted from the output of the command "mount".

---

### Post by Pizarro on 2011-06-19
From left plane in nautilus

output
martyn@martyn-natty:~$ ls /media
eb4922d9-af51-4b7b-96bf-dc91e50f58e1  floppy  floppy0
martyn@martyn-natty:~$

---

### Post by coffeecat on 2011-06-19
> **Pizarro said:**
> eb4922d9-af51-4b7b-96bf-dc91e50f58e1

If your sda3 partition is automounted from Places, this is the mountpoint. The long string is the UUID of the partition which is used to name a mountpoint when there is no partition label.

The command you need is:

```
sudo chmod 777 /media/eb4922d9-af51-4b7b-96bf-dc91e50f58e1
```You don't want to be typing all that out. :) You can use the terminal autocomplete feature. Type "sudo chmod 777 /media/eb" and then press the tab key and that will complete the string without errors. Now press enter.

---

### Post by Pizarro on 2011-06-19
Thanks I can now read and write to the drive. It does not seem to show a preview of jpegs or pdf files though. Also how do I change the permissions of the files already on the drive so I can read write delete them.

---

### Post by coffeecat on 2011-06-19
> **Pizarro said:**
> Thanks I can now read and write to the drive. It does not seem to show a preview of jpegs or pdf files though.

That's interesting. Perhaps it's because the files are not owned by you yet. I'd assumed this partition was empty of files, which is why I didn't complicate things. Sorry - that was an unwarranted assumption on my part. Did you copy the files to the partition with root privileges? 

> **Pizarro said:**
>  Also how do I change the permissions of the files already on the drive so I can read write delete them.

Assuming that all the files are yours, and not other users', we'll have to use the -R option after all, and chown. So:

```
sudo chown -R *yourusername*: /media/eb4922d9-af51-4b7b-96bf-dc91e50f58e1
```

Substitute your login name for *yourusername* and don't forget the trailing colon. That will set ownership of your files to your default group.

However - if some of the files are owned by users other than yourself, you will have to use a more fine-grained approach to chown-ing. Post back details if this is so. Also - check the rwx permissions of your files on that partition. If they were copied to the partition as root and have now been re-assigned to your ownership, it's worth checking this.

---

### Post by Pizarro on 2011-06-19
That has cured all access problems can read write and everything.
Still no preview for anything though just the grey/white checked icon with a clock on it.

Just turned machine off and on and everything works.

Thank-you for the help.

---

### Post by coffeecat on 2011-06-19
> **Pizarro said:**
> 
Still no preview for anything though just the grey/white checked icon with a clock on it.

That's odd. Just to show you it should work, the screenshot is part of a Nautilus window for a test folder on my Data partition, which has been chmod-ed and chown-ed very much the same way. I simply copied the jpeg (my previous avatar) and the pdf in to the folder and the previews appeared after a fraction of a second of what you're seeing showing.

Try:

Copy (not move) some selected files into a test folder. And/or... Double-click on some files to open them in the default application. What happens then?

---

### Post by Pizarro on 2011-06-19
I have turned the system off and on and all works perfectly.
Thank-you for the help.

---

