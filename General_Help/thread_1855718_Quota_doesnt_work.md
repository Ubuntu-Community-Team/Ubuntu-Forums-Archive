---
title: "Quota doesnt work"
date: 2011-10-06
forum: General Help
---

### Post by sadam20 on 2011-10-06
i`m trying to make Quota for a user but it doesnt work 
first> [B]test@test:~$sudo /etc/fstab
/dev/sdb1 /mnt/hd ext3 defaults,usrquota,grpquota 0 1 [/B]
then remounted sdb1 
check the quota off
>  ** test@test:~$sudo quotaoff /dev/sdb1**
 **test@test:~$sudo quotacheck -cug /dev/sdb1**
and ** test@test:~$sudo edquota -u test **
**/dev/sdb1 blocks   soft   hard   inods  soft   hard **
                                         **0                0         100          0            0           0**

then
>  ** test@test:~$sudo quotaon /dev/sdb1 **

but when i tried to do> ** test@test:~$ touch /mnt/hd/test.txt **

i get this 
> **testtouch: cannot touch '/mnt/hd/test.txt' : prermission denied**
tried to look at the repquota 
>   **test@test:~$sudo repquota  /dev/sdb1 **

i got only the root in the** repquota table **
**any help please** :(

---

### Post by flangemonkey on 2011-10-07
> i`m trying to make Quota for a user but it doesnt work 
 first test@test:~$sudo /etc/fstab

I'm guessing that should be along the lines of 

```

$sudo _editor_ /etc/fstb
add the line
/dev/sdb1 /mnt/hd ext3 defaults,usrquota,grpquota 0 1 

```

can you put your whole fstab here and the output of 

```

ls -lah /dev/disk/by-uuid/

```

You have then given us commands, but no output; is that correct?

> 
 then remounted sdb1 **expect no output**
 check the quota off  test@test:~$sudo quotaoff /dev/sdb1 **expect no output**
test@test:~$sudo quotacheck -cug /dev/sdb1 **expect output?**
 and  test@test:~$sudo edquota -u test 
/dev/sdb1 blocks soft hard inods soft hard 
0 0 100 0 0 0
 then  test@test:~$sudo quotaon /dev/sdb1 
 but when i tried to do test@test:~$ touch /mnt/hd/test.txt 
 i get this testtouch: cannot touch '/mnt/hd/test.txt' : prermission denied
 tried to loot at the repquota test@test:~$sudo repquota /dev/sdb1 
 i got only the root in the repquota table 
any help please 

please post output of 

```

(these with sdb1 mounted)
df -Th
ls -lah /mnt

```

Make sure you have both of these installed:
```

apt-get install quota quotatool

```

and also make sure you've completed any steps in this article:
[http://www.ubuntugeek.com/how-to-setup-disk-quotas-in-ubuntu.html]("http://www.ubuntugeek.com/how-to-setup-disk-quotas-in-ubuntu.html")

that should give us a start :)

---

### Post by sadam20 on 2011-10-07
**Really thanks flage for your concern.**
i got th quotatool too then i mad them along the lines as you sad and here the output
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=f57e87d0-e068-42fa-8101-288121201488 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=07382400-0b54-45ca-84dc-1a158c9b893c none            swap    sw              0       0
[B]/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1    /mnt/hard_drive    ext3    defaults,grpquota,usrquota 0     2[/B]
then i got ls -lah /dev/disk/by-uuid/

> total 0
drwxr-xr-x 2 root root 120 2011-10-07 00:48 .
drwxr-xr-x 5 root root 100 2011-10-07 00:48 ..
lrwxrwxrwx 1 root root  10 2011-10-07 00:49 07382400-0b54-45ca-84dc-1a158c9b893c -> ../../sda5
lrwxrwxrwx 1 root root  10 2011-10-07 00:49 1b56b60c-e669-4fcd-994a-c72913b2fa1e -> ../../sdb1
lrwxrwxrwx 1 root root  10 2011-10-07 00:49 e07adaea-4b38-4f7e-b6a6-67eb885ee261 -> ../../sdb2
lrwxrwxrwx 1 root root  10 2011-10-07 00:49 f57e87d0-e068-42fa-8101-288121201488 -> ../../sda1
and about the expect output yes you are correct 
output of **df -th**
> df: no file systems processed
and the output of   **ls -lah /mnt**

> total 16K
drwxr-xr-x  4 root root 4.0K 2011-10-06 16:19 .
drwxr-xr-x 23 root root 4.0K 2011-09-22 14:24 ..
drwxr-xr-x  3 root root 4.0K 2011-10-07 12:03 hard_drive
drwxr-xr-x  2 root root 4.0K 2011-09-22 14:26 hgfs


---

### Post by flangemonkey on 2011-10-07
hi, one of the pitfalls of people new to the terminal:

df -th is different from df -Th

the capital makes a difference...

the ls -lah /dev/disk/by-uuid 
shows us that there is only one mount entry for sdb1, this is good

pop back the df -Th and we'll see where to go from there, cos I'm a little flummoxed so far :)

---

### Post by sadam20 on 2011-10-07
sorry for that mistake :D i recorrect it  and i got this
 > 
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext4    6.9G  2.4G  4.2G  37% /
none      devtmpfs    242M  660K  241M   1% /dev
none         tmpfs    248M  168K  248M   1% /dev/shm
none         tmpfs    248M  104K  248M   1% /var/run
none         tmpfs    248M     0  248M   0% /var/lock
/dev/sdb1     ext4     19G  172M   18G   1% /mnt/hard_drive


but when i try to start from the beginning i got this message 
> 
test@test~:$sudo quotacheck -cugv /dev/sdb1

quotacheck: Your kernel probably supports journaled quota but you are not using it. Consider switching to journaled quota to avoid running quotacheck after an unclean shutdown.
quotacheck: Scanning /dev/sdb1 [/mnt/hard_drive] quotacheck: Checked 2 directories and 2 files

i dont know i`m goinn to be crazy ](*,)

---

### Post by sadam20 on 2011-10-07
i solved the journal porblem using the journalled quota but stilll have the same problem user **test** cant write into the **/mnt/hd** and **permissioned denied **

---

### Post by flangemonkey on 2011-10-07
sb1 is formatted ext4 (as shown by df -Th)
whereas in fstab you mount it as ext3, this shouldn't affect the write permissions however, but change your fstab to ext4 for /mnt/sdb1

there's a useful guide in 
[http://www.yolinux.com/TUTORIALS/LinuxTutorialQuotas.html]("http://www.yolinux.com/TUTORIALS/LinuxTutorialQuotas.html")

seems to indicate the line in fstab should read: 

```
UUID=1b56b60c-e669-4fcd-994a-c72913b2fa1e /mnt/hard_drive ext4 defaults,grpquota,usrquota 1 1
```

lemme know if I've been any help? :)

---

### Post by sadam20 on 2011-10-07
yes i know i changed it to ext4, i said that this may solve the problem, i made this steps on fedora and ubuntu and still have the same ouput. Sorry flage for annoying and thanks for your help :)

---

### Post by flangemonkey on 2011-10-08
ah; one more thing....

should've seen this earlier...

> 

and the output of ls -lah /mnt

 total 16K
 drwxr-xr-x 4 root root 4.0K 2011-10-06 16:19 .
 drwxr-xr-x 23 root root 4.0K 2011-09-22 14:24 ..
 drwxr-xr-x 3 root root 4.0K 2011-10-07 12:03 hard_drive


d rwx r-x r-x shows 
d - directory
rwx - owner can read/write/execute contents
r-x - group can read / execute contents
r-x - everyone else can read / execute contents

may I recommend adding write support by group to /mnt/hard_drive

in terminal type 

```

sudo chmod 775 /mnt/hard_drive
_OR_
sudo chmod 770 /mnt/hard_drive

```

The differences are whether you want *anyone* on the system to be able to write /mnt/hard_drive (775) or just people in the correct group, or the owner (770)

that should be the only thing left :)

(if it doesn't work will you try ```
sudo chmod 777 /mnt/hard_drive
``` for testing pls)

for security purposes, I recommend that you try the commands in order 770, 775, 777... :)

---

### Post by sadam20 on 2011-10-08
I think that you are the best one i have ever known throught my life :guitar:
thnks flange, thanks so much mate =D>

and sorry for annoying you but i have two questions please if you wanna answer them i will be so grateful  :
first i just studied the permissions and when you said change them i made it and it succed but how can this be i changed the permissions for group to rwx but it`s the **root group** how it affected on the** test** user that i made ??

second question : i understood the labels for** edquota -u spider** but the number i dont know how to put them 
> 
User            blocks    soft    hard   
test                0        0          0       
and i check my block size and it`s **4096**

say that i wanna limit 10Mb for the** test** user how can this be ??  

and rally thanks man

---

### Post by flangemonkey on 2011-10-08
could've sworn I posted another reply... :/

anyway, the gist was

see [_this book (LINK)_]('http://books.google.co.uk/books?id=IZqg3kQzpEMC&pg=PA143&lpg=PA143&dq=set+quota+size+terminal+ubuntu&source=bl&ots=_0nheOd6OY&sig=8F4AspUtichmI-U6BFO2w7UvqYM&hl=en&ei=6WaQTvvLII7z-gbHxI3tCg&sa=X&oi=book_result&ct=result&resnum=1&ved=0CB0Q6AEwAA#v=onepage&q&f=false')
 and the block size of 4k would give you 2560 blocks per 10MB...

the book link should help you set up aquota.group and aquota.user and get them to register with repquota and edquota; good luck :)

---

