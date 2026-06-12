---
title: "Mount vs fstab - I'm getting a &quot;cannot determine permissions&quot; error"
date: 2010-07-10
forum: General Help
---

### Post by Jeffa on 2010-07-10
So I just did a fresh install of Lucid, and while I was at it decided to expand my RAID 5 Storage array. Everything seems to have gone fine and I've been able to format the array without an issue. When I reboot, the array automatically appears to mount. However, whenever I try to move a file to the array, I get an error saying I don't have the right permissions. If I right click on the array and go to the "Permissions" tab, I get an error saying the permissions can't be determined. 

If I run the mount command in a terminal, I can see the storage array listed, but if I open the /etc/fstab file, I don't see it listed there. So my question is two fold: 

I don't understand how the array is automounted if it is not in fstab

and:

how can I change the permissions so I can copy files to the array? 

Thanks in advance for any help!

---

### Post by Jeffa on 2010-07-11
Now I'm really confused. Here is my fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sda1 during installation
UUID=8cb71f57-d36c-419b-a952-2e0ce96e2ea1  /               ext4  errors=remount-ro         0  1  
# /home was on /dev/sda3 during installation
UUID=3c727201-9cf9-4401-bf8d-ba9d6ba3f82f  /home           ext4  defaults                  0  2  
# swap was on /dev/sda2 during installation
UUID=a9c4f8e2-7194-485c-84e3-04ad93f29672  none            swap  sw                        0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  
/dev/sdb1                                  /media/sdb1     ext4  users                     0  0  
```

the storage array is sdb1. So it's in my fstab file, but it still won't allow my to write to it unless I use the 'sudo' command. Do I not have one of the options set correctly? and why do the partitions on my boot drive list the UUID, but the storage array lists its device name as /dev/sdb1? 

I'm confused, and any help from the community would be greatly appreciated. 

Thanks!

---

### Post by bodhi.zazen on 2010-07-11
Did you try chown and chmod ?

```
sudo chown your_login:users /media/sdb1
sudo chmod 770 /media/sdb1
```

---

### Post by Pizack on 2010-07-11
show me what ```
ls -l
``` results in for /media/sdb1

If the owner is root, then you need to change it to your user name as such

```
sudo chown <username> /media/sdb1
```

Similar problem for me today.
edit: bodhi.zazen has better code than me, but we are saying the same thing basically.
edit2: [http://www.youtube.com/watch?v=g84P65hk28c](http://www.youtube.com/watch?v=g84P65hk28c) is a video walkthrough that may help you not only to do this, but understand the commands involved, which is very important.

---

### Post by bodhi.zazen on 2010-07-11
> **Pizack said:**
> edit: bodhi.zazen has better code than me, but we are saying the same thing basically.

Ah, but your command is "simple"

---

### Post by Jeffa on 2010-07-11
Awesome. That's got it. I used Pizack's code and it worked. I watched the video too. that was helpful, and it raised another question. I will be sharing this directory across my home network and accessing it through windows machines as well. I'm about ready to set up samba, but that video made me wonder if the group should be set to "users"? Right now, when i run the "ls -l" command the owner and the group are both listed as my user name. won't that prevent others from accessing it? 

Thanks again community!

---

### Post by Jeffa on 2010-07-11
Also, I've just noticed that while I can copy and delete files to the array, when I right click on the array, I don't have any "sharing options" and when I go to the "permissions" tab, it still says the permissions can't be determined. 

any thoughts on how to fix this? 

Thanks!

---

### Post by bodhi.zazen on 2010-07-11
> **Jeffa said:**
> Also, I've just noticed that while I can copy and delete files to the array, when I right click on the array, I don't have any "sharing options" and when I go to the "permissions" tab, it still says the permissions can't be determined. 

any thoughts on how to fix this? 

Thanks!

I suggest you read up first on Linux permissions and then on Samba.

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

Samba can be configured by either the graphical interface or the command line. Although everyone always wants a graphical interface, IMO Samba is easier to configure via the command line.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

If you run into something you do not understand, ask.

If you look up at the command I gave it is easier to share with my command. however, sharing on linux is not always so straight forward either.

---

### Post by Jeffa on 2010-07-11
Good information. Thanks! I'll read through it. 

I think I've figured it out though. While I couldn't see the permissions or enable sharing when I right clicked on the array in
Places>Computer>array, I could see the permissions and enable sharing when I right clicked on the folder at the mount point (media>sdb1). Then configured Samba and all appears to be working. 

Great work community!

---

