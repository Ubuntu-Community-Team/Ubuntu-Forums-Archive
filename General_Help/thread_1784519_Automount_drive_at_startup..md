---
title: "Automount drive at startup."
date: 2011-06-17
forum: General Help
---

### Post by kanishkdudeja on 2011-06-17
How can i automount a drive at startup?

What changes do i need to make to the /etc/fstab file?

I am posting the screenshot of my gparted.

I want to automount /dev/sda2 whose label is "Home" and which is an ntfs partition. You can see it in the screenshot.

---

### Post by Wayne_V on 2011-06-17
follow the example in /etc/fstab:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

so, assuming you want it mounted as /home, add this to /etc/fstab

/dev/sda2   /home   ntfs   rw 1 1

You can check if the entry is OK with:

# mount -a -t ntfs

---

### Post by nomko on 2011-06-17
First:
open a terminal and type in: ```
blkid
```
If you don't get any output, type:```
sudo blkid
```, enter your password.
Post the output here.
 
Information about fstab can be found here: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
What is very interesting for you in your case is this: [https://help.ubuntu.com/community/Fstab#ntfs](https://help.ubuntu.com/community/Fstab#ntfs)
 
 
Best to do is mounting disc by their UUID code not by location or device. Ubuntu uses now, by default, the UUID nu8mbering of devices.

---

### Post by kanishkdudeja on 2011-06-17
```
kanishk@kanishk-Inspiron-1525:~$ sudo blkid
[sudo] password for kanishk: 
/dev/sda1: UUID="4a067711-5311-4f6a-8d3b-941b98149d4f" TYPE="ext4" 
/dev/sda2: LABEL="Home" UUID="42814B4813830A7F" TYPE="ntfs" 
/dev/sda3: UUID="0E2C2DCF2C2DB31F" TYPE="ntfs" 
/dev/sda5: UUID="8afe8594-0b96-4038-aa64-ad871549ed0d" TYPE="swap" 
/dev/ramzswap0: TYPE="swap" 

```

---

### Post by kukker32 on 2011-06-17
I'm automounting a folder on a client from a server with this



//10.129.16.89/svenson [COLOR=Red]<--- What to mount [/COLOR] /home/olga/Shared [COLOR=Red]<--- Where to mount[/COLOR] cifs exec,credentiels=/etc/cifspw 0 0[COLOR=Red] <--- Which file to use permissions from during mount[/COLOR], [COLOR=Red]only because i mount from a server[/COLOR]

---

### Post by ajgreeny on 2011-06-17
It will also be helpful to see the output of your current fstab with ```
cat /etc/fstab
``` however, you will not be able to use the entry given by Wayne_V as it is impossible to have an ntfs partition as your /home partition; it can be a data partition without problem, but /home must be of one of the standard linux filesystems, ext2, ext3, ext4, etc, or the necessary permissions are not possible.

---

### Post by nomko on 2011-06-17
Try this:
First install ntfs-3g. Open a terminal and type in:
```
sudo apt-get install ntfs-3g
```, enter en type in your password
 
open a terminal and type in: sudo gedit /etc/fstab
At the end of the file ente rthis line:
 
```
UUID=12102C02102CEB83  /media/Home  ntfs-3g  auto,users,uid=1000,gid=100,dmask=027,fmask=137,utf8  0  0

``` 
 
Save and close the file.
Then in the terminal type in: ```
sudo mkdir /media/Home
```
Then type in: ```
mount -a
```
 
This should work when you're rebooting your pc. If not, please let us know!

---

### Post by kanishkdudeja on 2011-06-17
okay thanks guys..:)

---

### Post by kanishkdudeja on 2011-06-17
@ajgreeny:

output of ```
cat /etc/fstab
```:

```
kanishk@kanishk-Inspiron-1525:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=4a067711-5311-4f6a-8d3b-941b98149d4f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8afe8594-0b96-4038-aa64-ad871549ed0d none            swap    sw              0       0


```

i just want the ntfs partition to be named as Home and i do not want it to be mounted directly under the root..i want to be mounted under the media directory..i used to manually mount it everytime after startup..now i just want it to get automounted..

@nomko: ntfs3g is already installed..can u please explain what does ```
auto,users,uid=1000,gid=100,dmask=027,fmask=137,utf8  0  0
``` signify?

@everybody:

earlier i added this to the fstab file:

```
/dev/sda2 /home ntfs
```

but after doing this all the files in my Home partition became executable..

---

### Post by nomko on 2011-06-17
> **kanishkdudeja said:**
> @nomko: ntfs3g is already installed..can u please explain what does ```
auto,users,uid=1000,gid=100,dmask=027,fmask=137,utf8  0  0
``` signify?
 
[https://help.ubuntu.com/community/Fstab#ntfs](https://help.ubuntu.com/community/Fstab#ntfs)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
 
Read this and you will find out.

---

### Post by kanishkdudeja on 2011-06-17
okay..thanks..:)

---

### Post by kanishkdudeja on 2011-06-17
i worked it out..its working perfectly now..thanks..:)

---

### Post by Morbius1 on 2011-06-17
> **kanishkdudeja said:**
> can u please explain what does ```
auto,users,uid=1000,gid=100,dmask=027,fmask=137,utf8  0  0
``` signify?

"auto" is in the defaults so it's redundant.
"users" won't do what you think it will do.
"uid=1000" will make you the owner of the mounted partition.
"gid=100" will make the group "users" which you probably ( and I'd bet the rest of the users on your machine ) aren't a member of.
[COLOR=Blue]*If you run the following command you will see what groups you are a member of:*[/COLOR]
```
id
```"dmask=027" represents the directory permissions you want to remove from the mounted partition. 
[COLOR=Blue]In this case the user has full permissions ( the first "0" ), group has write disabled ( the "2" ), and everyone else has no access ( the "7" ).[/COLOR]
"fmask=137" represents the file permissions you want to remove. 
[COLOR=Blue]In this case the owner can't execute the file ( the "1" ), group can't write or execute ( the "3" ), and everyone else can't do anything ( the "7" ).[/COLOR]

---

### Post by kanishkdudeja on 2011-06-17
okay..thanks a lot..i got it..:)

---

### Post by bioShark on 2011-06-25
Thanks guys.

The above solution helped me too.

---

