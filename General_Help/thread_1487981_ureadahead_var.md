---
title: "ureadahead /var"
date: 2010-05-19
forum: General Help
---

### Post by bigbaraboom on 2010-05-19
According to:
[http://ubuntuforums.org/showthread.php?t=1423305&highlight=ureadahead+status]("http://ubuntuforums.org/showthread.php?t=1423305&highlight=ureadahead+status")

there is no long term solution for this issue. The "workaround" apparently is:
> OK, so you thought you were smart and installed Ubuntu with /var on its own partition so that way runaway log files can't take down your whole system. (wasn't this theory valid back when hard drives we measured in Megabytes?)

Well I am that smart guy and I got the readahead error.

Here is what I did to fix it. (it worked for me YMMV)

Boot to Ubuntu live CD

Mount /var partition and root partition from the Hard drive. (Just click the drive in Places to see the disks.)

Edit /etc/fstab on the hard drive root filesystem and comment out the line containing /var

Enter the /var partition on the root filesystem and rename the three existing directories appending ".old" (without quotes) to the end of the filename.

Copy the contents of the var partition to the /var folder of the root partition

Copy the contents of the three ".old" directories to their respective directories inside /var on the root partition.

Reboot.

Now in places you should see an unmounted disk which used to be the /var/ partition

Also you should not see the unreadahead error any more.


Correct me if I'm wrong, but what the above suggests is to copy contents of your /var partition over to the /var directory inside your / partition. This will result in the /var partition not being mounted at boot.
What will be the effects of mounting the /var partition after boot? Will the system use it instead of the /var directory which was used during boot? Any insight with answers or possible complications information is welcomed.

---

