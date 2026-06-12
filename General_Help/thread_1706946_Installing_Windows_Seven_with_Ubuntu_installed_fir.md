---
title: "Installing Windows Seven with Ubuntu installed first."
date: 2011-03-14
forum: General Help
---

### Post by Mr. ViC on 2011-03-14
Ok, so, I'm having problems when installing Seven with Ubuntu installed first.

I did everything right I guess, I booted with Gparted Live CD and created a partition for Windows Seven:

[img]http://uppix.net/3/5/4/8e6f6ddfc4efa6a6b609b8d04f2b4.png[/img]

(the nfts one there)

And when trying to install, this damn error pops up:

```
Setup was unable to create a new system partition or locate an existing system partition. See the Setup log files for more information.
```

Then I tried to SHIFT+F10 and do the diskpart, then select the partition but when trying to activate it it pops up another error.

Kind of desperate here.

Any help please?

---

### Post by ajgreeny on 2011-03-14
You can't install Windows of any sort into a logical partition, I'm afraid, which is the main problem with your sda7.  I can not help any further with Windows as I stopped using it a while ago, but I thought Windows 7 needed more than one partition to install; perhaps I am wrong about that.

---

### Post by Mr. ViC on 2011-03-14
Thanks for your reply.

So I have to create a new primary partition?

---

### Post by Mr. ViC on 2011-03-14
Ok, I got it working now!

Glad you told me to create that, just created a primary partition it with GParted and Windows 7 is installing.

Thank you so much! :D

---

### Post by Jerry N on 2011-03-14
You do need a new primary partition for Win 7.  And you need only one partition for Win 7.  Possible exception:  I have never installed Win 7 from an OEM disk so I don't know if an OEM install requires more than one partition or not.  

I don't understand your present partitioning scheme.  You can have 4 primary partitions, or 3 primary and one extended.  Why are you trying to put everything in an extended partition?

After you get Win 7 installed, you will have to reinstall grub and there are numerous threads covering this on the Absolute Beginner and General Help forums.

Jerry

---

### Post by eddier on 2011-03-14
I was interested to see you have Linux "/" installed on one 235GB partition.

You only need about 10GB for "/" at most,all your personal files and configuration files are best kept on a separate "Home" partition (225GB ?) (equivalent to "My Documents" in windows).That way if your Linux OS goes West,you can reinstall the "/" partition without reformatting your "Home" partition.That way all your "stuff" and settings can be retained.:)

Apologies if i,m barking up the wrong tree.

eddie

---

