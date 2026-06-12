---
title: "Accessing Files Across Partitions"
date: 2012-06-30
forum: General Help
---

### Post by ltnewbie on 2012-06-30
I am trying to access files on two partitions from a third. The partitions that have the files on them are corrupted and inaccessible; I cannot even log in to them. They are both password protected, so when I try to use Nautilus to access files from them I am told I do not have permission. How do I access (or at the very least copy and paste) these files?

---

### Post by ubnewbie2 on 2012-06-30
What is the file system on the partitions?  

I hope you mean't that the operating system on those partitions is corrupted, because if the partition itself, or even the filesystem on the partition, is corrupted, you will need to hope it can be repaired.

---

### Post by oldfred on 2012-06-30
If when you say password protected you mean encrypted, then good backups are the only solution as none of the standard file recovery tools work (that is the purpose of encryption).

---

### Post by ltnewbie on 2012-06-30
Thank you both for your replies. Can either of you recommend a good backup device? I suspect the file systems aren't too far gone.

---

### Post by ubnewbie2 on 2012-06-30
> **ltnewbie said:**
> Thank you both for your replies. Can either of you recommend a good backup device? I suspect the file systems aren't too far gone.

I use an external USB drive that's attached to my ADSL router and shared. I tried quite a few backup programs, but, Deja Dup, that comes with Ubuntu now is surprisingly good, especially the single file restore functionality built into the file manager (Nautilus). I am also looking into using Ubuntu One for small backups.

How are you going to back them up if you can't access them?

---

### Post by ltnewbie on 2012-06-30
> How are you going to back them up if you can't access them?


I'd thought oldfred's post indicated I could back up files that I could not access:

> If when you say password protected you mean encrypted, then good backups are the only solution as none of the standard file recovery tools work (that is the purpose of encryption).

Unless he was referring to backups of the files taken before the problems occurred, in which case I may have just permanently lost a lot of valuable information.

---

### Post by ubnewbie2 on 2012-06-30
He meant backups taken while they were good.

The only thing left is to try some disk/partition/filesystem repair utilities.  I don't have much knowledge of what is best in this area.  Try googling around, or maybe someone here has some suggestions.

---

### Post by ubnewbie2 on 2012-06-30
double post - deleted

---

### Post by steeldriver on 2012-06-30
do you know for sure the filesytems are corrupted? by "password protected" do you mean they are actually encrypted, or just that you don't have the sudo password for your previous installs? have you tried simply running nautilus with root permissions?

```
gksudo nautilus
```

and then seeing if you can copy the files to your new installation

let's not jump the gun here

---

### Post by ubnewbie2 on 2012-06-30
> **steeldriver said:**
> do you know for sure the filesytems are corrupted? by "password protected" do you mean they are actually encrypted, or just that you don't have the sudo password for your previous installs? have you tried simply running nautilus with root permissions?

```
gksudo nautilus
```

and then seeing if you can copy the files to your new installation

let's not jump the gun here


He didn't answer my question about what the filesystems were.  Maybe they are Windows ntfs, not previous linux installs at all.

---

### Post by ltnewbie on 2012-06-30
Thank you both for your help. 

ubnewbie2, I will look into disk/partition/filesystem repair utilities. Unfortunately, all of the partitions are Linux.

steeldriver, I am afraid I do not understand the difference between actually encrypted and not having the sudo password.

EDIT: I tried using `gksudo nautilus` and found that I was able to access *some* of my old files. As I began to transfer them on to a flash drive, the computer crashed. When I rebooted and used the command again, the explorer no longer shows my two old partitions.

EDIT: I can once again use the explorer to go to the old partitions, but I still do not have permission to copy most of the files. In one of the folders there is a readme that says:

> THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
 "Access Your Private Data"

or

From the command line, run:
 ecryptfs-mount-private

When I try to use the command above, I get the response "ERROR: Encrypted private directory is not setup properly"

---

### Post by oldfred on 2012-06-30
I have not dealt with encrypted and do not know if the can be repaired outside the encryption. Sometimes only part is encrypted.

You can try this if nothing else.

#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors:
sudo e2fsck -f -y -v /dev/sdb1


And yes with encryption, I do mean backup before failure. Hard drives always fail, sometimes suddenly and others give some warnings. And corruption due to powerfailure or other sudden shutdown can cause problems. File checks can repair some issues, but encryption is intended to prevent any access. So once something is corrupted to not let you enter password it is gone.

---

### Post by oldfred on 2012-07-01
Some more info on encryption.

[https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)

---

