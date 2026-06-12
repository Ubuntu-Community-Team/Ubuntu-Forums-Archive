---
title: "Boot problem &quot;init crypto disk&quot;"
date: 2010-01-29
forum: General Help
---

### Post by BigBuntu on 2010-01-29
[FONT=monospace]I am trying to help a friend with a serios need. His laptop was rebooted and when it loads then it stops after the white ubuntu logo (Karmic version) in a black screen with the message in the top left corner:

init crypto disk..

He is desperate to get his information out from the "home folder" and there is denied access to this when booting the system via CD. So I was thinking there might be a pass through "safe mode". How do we make a copy of his home folder and access this information from safe mode.(He is pretty f... if he doesnt get this work out fast)

My linux /ubuntu level i on a starter/user level so if you have some great ideas please spell them for me. Thanks 

ooh yes I HAVE looked through other treads, but there have not been a geek good enough to solve the "init crypto disk" problem so others with the same problem was able boot normally. 


[/FONT]

---

### Post by BigBuntu on 2010-02-01
Okay..
We think to have "solved" the issue. The data on the labtop was not recovered  - while an error from updating the ATI driver resulted in a crypting of all data. This is the conclusion after the same thing happened after 2 crashes (when installing the ATI driver) on a otherwise clean ubuntu installation.

I also tried to update my old T40 IBM labtop with the same shitty driver - but at that time was my data  still intact after the crash. So I guess I was lucky that I have an old and less advanced labtop compare to my friends equipment. 

So to all of you that have ATI hardware on your labtops - do not use this driver "ATI binary X.Org driver" - or if you decide to take the chance have a BACKUP ready before optimizing your ubuntu.

I hope this helps some of you....

---

### Post by ben2talk on 2010-05-02
This issue is not solved - and I have no ATI driver. My problem came after choosing to do an upgrade; actually I'd forgotten that my Home was encrypted. I've had no trouble in recovering it previously, and I saved a couple of files with information about the keys.

I'm going to try this set of instructions to mount the encrypted partition from a CD:

# Mount the partition with the encrypted home directory:
ubuntu@ubuntu$ sudo mount /dev/sda1 /mnt

# Establish a proper chroot environment:
ubuntu@ubuntu$ sudo mount -o bind /dev /mnt/dev
ubuntu@ubuntu$ sudo mount -o bind /dev/shm /mnt/dev/shm
ubuntu@ubuntu$ sudo mount -o bind /proc /mnt/proc
ubuntu@ubuntu$ sudo mount -o bind /sys /mnt/sys
ubuntu@ubuntu$ sudo chroot /mnt

# Become the user (ben, or 'foo') who's data needs recovering:

root@ubuntu$ su – foo
foo@ubuntu$ ecryptfs-add-passphrase --fnek
Passphrase:
<Enter the recorded passphrase>
#Cryptoben ????
# aa0717aec350d9cf6480645a23a94025
# the passphrase
# 9e1ba670bc0514495188b8fcadc37f3f

#Mount the Encrypted Home Directory and access the data:
foo@ubuntu$ ecryptfs-mount-private
foo@ubuntu$ cd $HOME
foo@ubuntu$ ls -alF

Though I'm not sure it will work, and Im' not sure I'll find my way back to this thread when I'm done - but unless someone adds a report that this problem really is solved, then it should be marked accordingly... not solved.

Surely a backup would have been better (and I did keep backups of most of my important files on a separate storage partition...) but this is not a solution to this problem.

---

