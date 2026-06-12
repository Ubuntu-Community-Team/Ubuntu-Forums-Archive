---
title: "It will not let me create folders on mounted drives"
date: 2009-07-05
forum: General Help
---

### Post by Ifaistos on 2009-07-05
I have just done a fresh install, of 9.04.
On this machine I also have two more HDs.
One with 120 GB and another one with 400 GB.

The first one (120GB) I formatted with ext4 and mounted at /home/120GB.
The second one (400GB) didn't formatted since it had data, and mounted it at /home/400GB.

When I tried to access the folder /home/120GB I saw that in properties it said that it was owned by root, and I couldn't change those properties.  It wouldn't allow me to create any folders there.  So I couldn't do anything with this HD.

On the other hand on the other HD (400GB NTFS) it said that it was owned by root and couldn't change the properties, BUT it allows me to create folders and generally delete, write, read.

Does anyone know why this has happened?
Can you point me to a resource explaining this?

Also, how can I fix that?  I want to have full access to the 120GB HD.

Thank you all in advance :-)

---

### Post by taurus on 2009-07-05
You can change the ownership of that /home/120GB from root to your login name so you can write to it anytime you want.  Assuming your login name is faistos, you would do something like

```
sudo chown -R faistos:faistos /home/120GB
ls -la /home
```

---

### Post by drs305 on 2009-07-05
> **Ifaistos said:**
> The second one (400GB) didn't formatted since it had data, and mounted it at /home/400GB.

On the other hand on the other HD (400GB NTFS) it said that it was owned by root and couldn't change the properties, BUT it allows me to create folders and generally delete, write, read.

Does anyone know why this has happened?
Can you point me to a resource explaining this?



As for the NTFS partition, permissions are set at mounting and cannot be changed after that mounting. The partition would, by default when mounted, owned by root, and allow users to r/w to it. To change this, you must change the mount options. You can also leave it as it is if you prefer and accept the limitations of its mounting that way.

In fstab, add the following line (gksudo gedit /etc/fstab):
```

UUID=XXXXX /home/400GB ntfs defaults,uid=1000,gid=1000,umask=022 0 0

```

Replace XXXXX with the UUID of the partition (check with "sudo blkid").
Assumes you are user 1000 (check with "id")
The "umask" entry gives you rwx, others rx. You can change that if desired. See the Permissions link.


You can also install "ntfs-config" and run it from System, Administration, NTFS Configuration Tool to automatically add the information to fstab.


Here is a link to understanding fstab:
[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

File Permissions:
[https://help.ubuntu.com/community/FilePermissions]("https://help.ubuntu.com/community/FilePermissions")

---

### Post by michy99 on 2009-07-05
I don't understand why you are mounting these drives in /home. The first level folders in /home should be the home folders of the different users. If you want these to be part of your /home, you should mount them as /home/yourusername/mountpoint/. Otherwise, you can mount them in /media or /mnt.

---

### Post by moster on 2009-07-05
go to mount folder in terminal which you have problem. Paste this.
sudo chmod -R 777 *

If you interested in why you cannot write by default go here.
[http://catcode.com/teachmod/]("http://catcode.com/teachmod/")

---

### Post by Ifaistos on 2009-07-05
Taurus it worked great :-)

Thank you all for your suggestions...

I believe though that if I did what michy said I wouldn't have any of thes problems... would I?

What I would like to know is this :

Can I do what michy says... that is mount the HDs at /home/myloginname/120GB and /home/myloginname/400GB without having to reinstall?

Any help would be greatly appreciated...

Thanks again...

---

### Post by drs305 on 2009-07-05
> **Ifaistos said:**
> Taurus it worked great :-)
Can I do what michy says... that is mount the HDs at /home/myloginname/120GB and /home/myloginname/400GB without having to reinstall?

Sure you can, as long as these are additional drives and not part of your system. (Even then you can, you may just have to tweak a few settings). 

You can mount the drives anywhere you wish. If they are mounted on /media you will see an icon on your desktop, but that is about the only difference. Traditionally internal drives are mounted in /mnt and removable drives in /media, but as I said, it really doesn't matter.

Just make the changes in fstab, if you have them listed there, then unmount and remount them. If you use the "sudo umount -a" command you will get some messages about the system being busy (which is ok), but it is the easiest way to remount all the partitions listed in fstab.

Create the mount points and make yourself the owner:
```

sudo mkdir /home/myloginname/120GB  /home/myloginname/400GB 
sudo chown -R myloginname: /home/myloginname/120GB  /home/myloginname/400GB 

```

Make the changes in fstab, then:
```

sudo umount -a
sudo mount -a

```
If you run the second command and nothing happens, it means fstab is correct and the partitions are correctly mounted.

---

### Post by Ifaistos on 2009-07-05
Problem solved !!

Thank you DRS305 :-)

what does the "-a" option does?  Unmounts all? and then mounts all?

I guess it unmounts only the HD that are not mounted on / or /home.. right?


Thank again :-)

---

### Post by drs305 on 2009-07-05
> **Ifaistos said:**
> Problem solved !!
Thank you DRS305 :-)
what does the "-a" option does?  Unmounts all? and then mounts all?
I guess it unmounts only the HD that are not mounted on / or /home.. right?
Thank again :-)

Yes, that is what the "-a" option does. That is why the system complains a bit with 'umount'. The command tries to unmount all mounted partitions, but of course it can't unmount the system partition so it reports that the device is busy and moves on to try to unmount the next one.

You can learn what a particular 'switch' does by opening a terminal and typing "man <commandname>". Most commands have a page that lists the command options and switches, with explantions of what they do.  Example:  man umount

---

### Post by Ifaistos on 2009-07-05
It is working great !!  I even shared it on the LAN, and my windows PC has full access to the 120GB file/HD... I love it !!

Thank you :drs305, moster, michy99, taurus.


ps. How can I declare this thread solved/closed?
How can I thank a person for helping me? I remember there was somewhere an option for that....

---

### Post by drs305 on 2009-07-05
> **Ifaistos said:**
> ps. How can I declare this thread solved/closed?
How can I thank a person for helping me? I remember there was somewhere an option for that....

There used to be but with the server upgrades the "solved" and 'thanks' buttons went away. One thing you can do is add a 'solved' tag to the thread. At the bottom right of the thread is an "Edit tag", then below the last post, in the middle, is an "Add tag" window. You can click on that and add a tag. Actually anyone can add a tag, but since you are the OP it's best if you do it.

Thanks are best made by helping someone else solve their problem.  :-)

---

