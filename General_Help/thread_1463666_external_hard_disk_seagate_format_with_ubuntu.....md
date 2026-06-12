---
title: "external hard disk seagate format with ubuntu...."
date: 2010-04-27
forum: General Help
---

### Post by abhilashm86 on 2010-04-27
I've bought a segate 320GB extrenal usb  hard disk.....

1) What format should i do, i'll always use it with ubuntu only, few times on windows, will windows recognise ext3??

2) if i format my seagate hdd to ext3, can i set permissions of users, chmod permissions to files and directories?? will it work easily?

if its complicated, tell me procedure.....

3) how it should be mounted in order to work linux permissions, read and write?

thanks......


All i'm doing this is, i was fed up setting and playing with vfat anf ntfs on ubuntu, so i took new usb hdd, now i'll install lucid lynx on whole 80 GB on my computer.:guitar::lolflag:

---

### Post by varunendra on 2010-04-27
Hi Abhilash!
  Seems ur drive is new. Then why don't u just backup ur files that came  with HDD (500-600MB default backing up OEM program afaik) & do the  experiments yourself?
  
  As per my (limited) experience with my Seagate320GB usb drive:-
> **abhilashm86 said:**
> I've bought a segate 320GB extrenal usb  hard disk.....

1) What format should i do, i'll always use it with ubuntu only, few times on windows, will windows recognise ext3??Yes, (Windows WILL require external driver. You can get one [here]("http://www.fs-driver.org/download.html"). It's for ext2, but can mount ext3 also)

> **abhilashm86 said:**
> 2) if i format my seagate hdd to ext3, can i set permissions of users, chmod permissions to files and directories?? will it work easily?

if its complicated, tell me procedure.....Yes, (if tried under native setup of linux) Hope u won't need guidance

> **abhilashm86 said:**
> 3) how it should be mounted in order to work linux permissions, read and write?Since it is usb, all the partitions would be mounted automatically as soon as you connect it.
Changing permissions shouldn't be difficult. I f any problem occurs, just open terminal & type:
> sudo nautilus and you'll be the boss!

However, just a few suggestions:

[LIST=1]
[*]Keep atleast 1 small partition FAT32 to keep ur 3rd party ext3 driver & other stuff u may need for any windows pc just in case!
[*]Lucid is still beta, so watch ur step!
[/LIST]
You may find it interesting (keep partitions as per your needs):
> [http://ubuntuforums.org/showthread.php?t=1451172](http://ubuntuforums.org/showthread.php?t=1451172)

---

### Post by varunendra on 2010-04-27
Oops! I'm suggesting you! Didn't see your beans#-o

However, I still think it'd be a good idea to keep at least one small fat32 partition.
Also, ext3 WON'T BE DETECTED BY DEFAULT! You'll need the 3rd party driver.

---

### Post by Morbius1 on 2010-04-27
> 1) What format should i do, i'll always use it with ubuntu only, few times on windows, will windows recognise ext3??For best interoperability I would personally format it in a Windows filetype: FAT32 or NTFS - probably NTFS because FAT32 has a 4GB file size limit.

As for Windows recognizing a ext3 partition - No it will not. You can bolt on a filesystem driver on windows that will allow you to do that but you have to ask yourself if you really want windows to have read / write access to a linux filesystem.
> 2) if i format my seagate hdd to ext3, can i set permissions of users, chmod permissions to files and directories?? will it work easily?Yes and no. 
Yes. You can set the initial permissions of the mount point like this for example:

sudo chmod -R 0777 /media/Seagate

No. You will have to do that periodically in perpetuity depending on how you want to share the partition. The initial 777 chmod will allow Mary and John to both have access to the directory itself and will enable them to add to and delete from that directory. But when Mary saves the file it will save as owner=mary and permissions=0755. John will be able to read ("5") but only Mary will be able to write ("7") to that file. That may be what you want it to do, but maybe not. There's a way around that using BINDFS. [http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)

I'd have to think a bit on how BINDFS would work on an automounting external USB device but I think it would work. WIndows filetypes do not have this problem because they don't use ownership and permissions.
> 3) how it should be mounted in order to work linux permissions, read and write?Ext3 permissions are set after mount using chmod and chown
FAT32 or NTFS permissions are set up in fstab.

[COLOR=Blue]EDIT: [/COLOR]I should note that there is a problem in automounting external USB ntfs drives with permissions other than the user that turned it on. If you can assure that the device is on before you boot then that would eliminate the problem.

---

### Post by abhilashm86 on 2010-04-27
> **varunendra said:**
> Oops! I'm suggesting you! Didn't see your beans#-o

However, I still think it'd be a good idea to keep at least one small fat32 partition.


thats fine!! i was playing around new ext hard disk, so had few doubts!! 
learning and mastering ubuntu will never stop, there are tons to learn, thanks for reply......

[QUOTE=varunendra;9181341]
Also, ext3 WON'T BE DETECTED BY DEFAULT! You'll need the 3rd party driver.


yes i saw on net, i'll install other software for this.......

---

### Post by abhilashm86 on 2010-04-28
> **Morbius1 said:**
> 

[COLOR=Blue]EDIT: [/COLOR]I should note that there is a problem in automounting external USB ntfs drives with permissions other than the user that turned it on. If you can assure that the device is on before you boot then that would eliminate the problem.

thanks for those good points, i'm really comfortable with external usb, just foramtted to ext3, works like ace!!

---

