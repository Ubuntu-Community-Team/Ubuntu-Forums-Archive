---
title: "Using cut/paste in Ubuntu 11.10"
date: 2011-11-01
forum: General Help
---

### Post by Panawe on 2011-11-01
I can't seem to be able to use cut and paste in 11.10! Either right clicking or using edit menu.

---

### Post by 2F4U on 2011-11-01
What applications are involved, i.e. what is source and destination? Is it just plain text?

---

### Post by Jaybyrrd on 2011-11-01
Also, when you switched from Natty to Oneiric, did you upgrade or do a clean install?

---

### Post by Panawe on 2011-11-01
> **Jaybyrrd said:**
> Also, when you switched from Natty to Oneiric, did you upgrade or do a clean install?

Upgrade.

I tried to cot (& copy) a file from Home to another (internal) HD.

---

### Post by Gatemaze on 2011-11-01
Can you see the cut/paste on the right menu and they are inactive? If yes then you don't have write permissions in these folders.

---

### Post by Panawe on 2011-11-01
> **Gatemaze said:**
> Can you see the cut/paste on the right menu and they are inactive? If yes then you don't have write permissions in these folders.

When copying or cutting the right click copy/cut option is live but the paste button is greyed out when I come to paste (and have moved to a different drive).

Why wouldn't I have write permission? It's never happened before?

Thanks.

---

### Post by dave0109 on 2011-11-01
It will depend upon the permissions of the destination location.  If you open a terminal window, then do the following:-

```
id
```
This will tell you what your user and group IDs are.

```
cd /path/to/destination/directory
ls -lad .
```
This will tell you which permissions are set on the directory that you are trying to paste into.

For example:-
```
$ id
uid=1000(dave0109) gid=1000(dave0109) groups=4(adm),20(dialout)....
$ cd /usr/local
$ ls -lad
drwxr-xr-x 12 root root 4096 2011-08-08 22:39 .
```
Don't know if you understand the permissions, but if you are not the owner (as indicated by first 'root' above) or in the group (as indicated by second 'root' above), then it's the last 3 characters on the left that determine the permissions that apply to you, and you need to see a 'w' as the second character in the group of 3.  Here we can see a '-', which means no write permission.

Alternatively for this part you can use Nautilus, right click on the directory and look at the permissions.  You can see if you have write permission in there.

As to why - that depends on many factors.  By default, and for good reason, you don't have permission to write files everywhere.

---

### Post by Panawe on 2011-11-01
> **dave0109 said:**
> It will depend upon the permissions of the destination location.  If you open a terminal window, then do the following:-

```
id
```This will tell you what your user and group IDs are.

```
cd /path/to/destination/directory
ls -lad .
```This will tell you which permissions are set on the directory that you are trying to paste into.

For example:-
```
$ id
uid=1000(dave0109) gid=1000(dave0109) groups=4(adm),20(dialout)....
$ cd /usr/local
$ ls -lad
drwxr-xr-x 12 root root 4096 2011-08-08 22:39 .
```Don't know if you understand the permissions, but if you are not the owner (as indicated by first 'root' above) or in the group (as indicated by second 'root' above), then it's the last 3 characters on the left that determine the permissions that apply to you, and you need to see a 'w' as the second character in the group of 3.  Here we can see a '-', which means no write permission.

Alternatively for this part you can use Nautilus, right click on the directory and look at the permissions.  You can see if you have write permission in there.

As to why - that depends on many factors.  By default, and for good reason, you don't have permission to write files everywhere.

Here goes...

phil@panawe:~$ cd /media/StoreWin
phil@panawe:/media/StoreWin$ ls -lad .
dr-x------ 1 phil phil 16384 2011-10-30 00:45 .

I'm beginning to regret the upgrade!

---

### Post by Panawe on 2011-11-02
So I suppose I need to change my user privileges? I have just noticed that when I log it sayd "Guest Session" - this needs to upgraded to user or something?

---

### Post by dave0109 on 2011-11-02
> **Panawe said:**
> Here goes...

phil@panawe:~$ cd /media/StoreWin
phil@panawe:/media/StoreWin$ ls -lad .
dr-x------ 1 phil phil 16384 2011-10-30 00:45 .

I'm beginning to regret the upgrade!

OK, so the permissions show that you do not have write permission.  The 'd' indicates that it's a directory, this we know already.  The next 3 characters show the permissions for the user 'phil'.  You have read ('r') and execute ('x') permissions.  You do not have write ('w') permissions.

So, what is StoreWin?  Is this a removable disk?  E.g. a USB stick, portable hard drive, or a Windows partition that you are mounting using the 'Places' menu, for example.

It may well be your user permissions.  Go to the Users & Groups menu option in the System, Administration menu to see what access rights are assigned to the user 'phil'.

---

### Post by Panawe on 2011-11-02
Okay, I've done that and promoted myself to "administrator" and here's the Terminal result...

phil@panawe:~$ cd /media/StoreWin
bash: cd: /media/StoreWin: No such file or directory
phil@panawe:~$ ls-lad
ls-lad: command not found
phil@panawe:~$ ls -lad
drwxr-xr-x 99 phil phil 344064 2011-11-02 07:52 .
phil@panawe:~$ id
uid=1000(phil) gid=1000(phil) groups=1000(phil),4(adm),20(dialout),24(cdrom),46(plugdev),111(lpadmin),119(admin),122(sambashare)

So it looks like it's done. I don't recall whether I had administrator privileges before the upgrade but I could certainly cut/paste to places.


Thanks

---

### Post by Panawe on 2011-11-02
> **dave0109 said:**
> OK, so the permissions show that you do not have write permission.  The 'd' indicates that it's a directory, this we know already.  The next 3 characters show the permissions for the user 'phil'.  You have read ('r') and execute ('x') permissions.  You do not have write ('w') permissions.

So, what is StoreWin?  Is this a removable disk?  E.g. a USB stick, portable hard drive, or a Windows partition that you are mounting using the 'Places' menu, for example.

It may well be your user permissions.  Go to the Users & Groups menu option in the System, Administration menu to see what access rights are assigned to the user 'phil'.

Nope, wrong again - can't paste to "StoreWin" (internal hard drive). Here's the Terminal stuff...

phil@panawe:/media/StoreWin$ ls -lad
dr-x------ 1 phil phil 16384 2011-10-30 00:45 .
phil@panawe:/media/StoreWin$ id
uid=1000(phil) gid=1000(phil) groups=1000(phil),4(adm),20(dialout),24(cdrom),46(plugdev),111(lpadmin),119(admin),122(sambashare)

I'll logging out and in again.

Phil

---

### Post by Panawe on 2011-11-03
Any ideas why I don't have permission to write to internal hard drive? I have given myself "administrator privileges.

Phil

---

### Post by Gatemaze on 2011-11-03
Yup you don't have write permissions. Is this a dynamically mounted drive like a usb pen or another partition on your hard drive. If the latter post your /etc/fstab, there must be somtething wrong with the mask... as you have read and execute permissions but not write.

---

### Post by westie457 on 2011-11-03
> **Panawe said:**
> So I suppose I need to change my user privileges? I have just noticed that when I log it sayd "Guest Session" - this needs to upgraded to user or something?

Have you corrected this to log in as 'admin', the person who set everything up?
Once you log in with your ID default permissions for the main account should apply.

---

### Post by Panawe on 2011-11-03
Here it is...

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=0dc6003c-74d4-4382-9c6f-002877b280d6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=fbcadba6-5823-4484-876f-1c8df1bb7d3f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

All goobledegook to me!

When I log in it says "Guest Session" which seems wrong but I've gone into Users/Groups and given myself admin privileges!

Thanks,

Phil

---

### Post by Gatemaze on 2011-11-03
> **Panawe said:**
> Any ideas why I don't have permission to write to internal hard drive? I have given myself "administrator privileges.

Phil

Administrator privileges have nothing to do with the permissions. OK a very short intro to linux filesystem permissions. For every file you have three types of permissions: (r)ead, (w)rite, e(x)ecute, for three types of ownership: user, group, all. Hence the nonuplet which for full permissions will be: rwxrwxrwx. Eg. two users: phil and mac with groups phil and mac. phil is also a member of group mac. Let's say you have the following files:

user  group  all filename   user  group
rwx   rwx    --- a.txt      mac   mac
rwx   ---    --- b.txt      mac   mac
rwx   rwx    --- c.txt      phil  phil

a.txt: both phil and mac can read/write/execute
b.txt: only mac can read/write/execute
c.txt: only phil can read/write/execute

Hope this helps.

---

### Post by Gatemaze on 2011-11-03
Hold on a min. Guest session? OK. Where does it say guest session? OK.

1. Which version of ubuntu are you using?
2. Once you login can you please give the output of id again?
3. If you login as your normal user and it is in guest session mode then maybe when you login can you please check the session you are logging in? Maybe there is something like guest session for a particular user? This relates to question 1, as in my 10.04 there is no such thing unless i login as guest or swittch to guest session.

---

### Post by Gatemaze on 2011-11-03
Regarding your fstab, sorry but it does not give more info. It only shows that your internal drive/partition winstore is mounted dynamically. Me I prefer having them mounted from fstab and make a bookmark in nautilus, as I hate seeing them on my desktop since they are internal and I can also control the permissions and mounting options.

---

### Post by Panawe on 2011-11-03
It says Guest Session below the logon box when ubuntu (11.10 - regretting it already!) loads.

Thanks,

Phil

---

### Post by Panawe on 2011-11-03
Here it is...

phil@panawe:~$ id
uid=1000(phil) gid=1000(phil) groups=1000(phil),4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),29(audio),30(dip),44(video),46(plugdev),104(fuse),111(lpadmin),119(admin),122(sambashare),130(scanner)

---

### Post by Panawe on 2011-11-03
Update...

I've just realised it only happens with my Windows-formatted drive. I have partitioned drives and the Linux partition I can write to all right!

Is this a clue?

Thanks,

Phil

---

### Post by Gatemaze on 2011-11-04
> **Panawe said:**
> Update...

I've just realised it only happens with my Windows-formatted drive. I have partitioned drives and the Linux partition I can write to all right!

Is this a clue?

Thanks,

Phil

I think it is the way they are dynamically mounted. I don't know how to resolve this automatically, but if you really want to have write access on them, you can do so through fstab. If you want to let me know and tell me what filesystem they are (fat32, ntfs) and I can send you my fstab line.

---

