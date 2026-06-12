---
title: "weird problem after formatting a drive"
date: 2011-01-13
forum: General Help
---

### Post by quantumrider on 2011-01-13
Hi, I just formated an old HD using GParted to a single partition and formatted it to ext4 everything is fine but now when I try to paste and copy files to it I can't, I also can't create new directories on the drive, in properties in permissions it says the owner is root and it informs me that I am not the owner so I can't make changes... how can that be? I created the partition and formatted it, weird... what should I do? I can format it again I did that in fact already but the same results...

---

### Post by Smart Viking on 2011-01-13
Change the user to you.

```
sudo chown /whatever/file $USER
```

---

### Post by quantumrider on 2011-01-14
ok, I tried it... here is the result:

quantumrider@quantumrider-OptiPlex-755:~/Desktop$ sudo chown /dev/sdb1 $USER[sudo] password for quantumrider: 
chown: invalid user: `/dev/sdb1'
quantumrider@quantumrider-OptiPlex-755:~/Desktop$ sudo chown /dev/sdb1 $quantumrider
chown: missing operand after `/dev/sdb1'
Try `chown --help' for more information.
quantumrider@quantumrider-OptiPlex-755:~/Desktop$ 

where do I find my username? isn't that my login name? I used that... also, now when I clicked on properties for the drive and went to permissions tab it says only 'The permissions of "500 old" could not be determined' is there more to this problem?

---

### Post by tredegar on 2011-01-14
Where have you mounted the drive?
You need to **sudo chmod 777 /path/to/mountpoint** to allow everyone (including yourself) access to the drive.
If you only want access then
```
sudo chmod 770 /path/to/mountpoint
sudo chown quantumrider:quantumrider /path/to/mountpoint
```

---

### Post by quantumrider on 2011-01-14
I tried that, still no success, I'm attaching a screenshot from GParted, maybe there is something else wrong, although my main HD is also formatted with ext4 my boot disk

---

### Post by tredegar on 2011-01-14
May I repeat.....

_Where have you mounted the drive?_

**/dev/sdb1** is just a partition, it needs to be mounted somewhere

Eg:
```
sudo -i
mkdir /newdrive
chmod 777 /newdrive
mount  -t  ext4  /dev/sdb1  /newdrive
exit
```

Now you can use your new drive.

---

### Post by quantumrider on 2011-01-15
I tried that, still getting weird errors as to the ownership, I used kernelcheck a few days ago to install a newer kernel, could that cause my problems?

---

### Post by gordintoronto on 2011-01-15
The easy way to mount the drive is to go to Places and click on "466 GB Filesystem." (Or some other number which is in the same ball park.)

---

