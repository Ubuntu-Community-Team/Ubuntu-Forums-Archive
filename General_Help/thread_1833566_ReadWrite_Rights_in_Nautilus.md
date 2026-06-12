---
title: "Read/Write Rights in Nautilus"
date: 2011-08-26
forum: General Help
---

### Post by MaccyDG on 2011-08-26
Hello,

I'm having an odd problem in Nautilus, and I was wondering if someone could help me out, please.  I'm pretty new to Ubuntu, and Linux generally.  I don't think this will be difficult to solve for someone who knows more about Linux, but I can't figure it out myself.

In Nautilus, my Filesystem and a shared (with Windows) FAT32 partition have padlock icons on them.  I think this means that I only have opening access, and not read/write access.  Certainly, I can't change anything in either of these partitions.

Initially, everything had been fine with my new installation, but I wanted to set the FAT32 partition ("MYDOCUMENTS") to automount on boot.  I downloaded Storage Device Manager and altered the entry for MYDOCUMENTS by ticking the box "The file system is mounted at boot time", leaving all other options as their defaults.  The box "Mount filesystem in read-only mode" is unticked.  It was after installing and using Storage Device Manager that this problem started, I think.

I've been through a tutorial for how to use the program, but I can't find anything that looks like it'll help.  Does anyone here know how to solve this, preferably using GUI, rather than typing stuff?

Thanks for any help, and sorry if I'm being ignorant of something blindingly obvious!

Liam

---

### Post by nothingspecial on 2011-08-26
Hi you need to create a directory for it to mount to. Where do you want it? eg

```
mkdir /media/MYDOCUMENTS
```

Then you need to add an entry to /etc/fstab eg

```
UUID=52f4af4f-3560-434e-bba1-c6f15c369803 /media/MYDOCUMENTS   vfat   user,fmask=0111,dmask=0000   0   0
```

To find the uuid type ```
sudo blkid
```
Then type sudo mount -a

That will give read write access to all users.

---

### Post by raja.genupula on 2011-08-26
> **nothingspecial said:**
> Hi you need to create a directory for it to mount to. Where do you want it? eg

```
mkdir /media/MYDOCUMENTS
```Then you need to add an entry to /etc/fstab eg

```
UUID=52f4af4f-3560-434e-bba1-c6f15c369803 /media/MYDOCUMENTS   vfat   user,fmask=0111,dmask=0000   0   0
```To find the uuid type ```
sudo blkid
```Then type sudo mount -a

That will give read write access to all users.


was this thing applicable for usb storage ?

i have a nokia mobile .
when i trying to connect it in mass storage mode all the files in my card coming with lock symbol at top . i can copy from the memory card , but i cant able to write any thing to it .
i figure it out its  read & write option but i have done 
```
sudo chmod 777 label_name 
``` 
but Badluck , i didnt get it . 

thanks advance .

---

### Post by nothingspecial on 2011-08-26
It depends, for a phone that you only access once in a while, it would probably be easier to use ```
gksudo nautilus
``` to copy stuff as root.

Careful though. You can delete anything after issuing that command so once you are done with the phone make sure you close the file browser window.

---

### Post by raja.genupula on 2011-08-26
> **nothingspecial said:**
> It depends, for a phone that you only access once in a while, it would probably be easier to use ```
gksudo nautilus
``` to copy stuff as root.

Careful though. You can delete anything after issuing that command so once you are done with the phone make sure you close the file browser window.

aah thank you . i am gonna try it when i get back to my room .

---

### Post by MaccyDG on 2011-08-26
> **nothingspecial said:**
> 

```
UUID=52f4af4f-3560-434e-bba1-c6f15c369803 /media/MYDOCUMENTS   vfat   user,fmask=0111,dmask=0000   0   0
```That will give read write access to all users.

So how is fmask=0111,dmask=0000 different from rw?

And is there not a nice GUI for all this, that works, where we can just tick a box to say "I want this to be read/write/execute accessible by anyone?

Thanks for your help so far.

---

### Post by nothingspecial on 2011-08-26
> **MaccyDG said:**
> So how is fmask=0111,dmask=0000 different from rw?

And is there not a nice GUI for all this, that works, where we can just tick a box to say "I want this to be read/write/execute accessible by anyone?

Thanks for your help so far. 

Because vfat (as fstab and the mount command specify fat32) is not a native linux file system and does not support linux file permissions. You have to use dmask and fmask to do it when the file system is mounted.

On a linux only system you wouldn't use a fat32 partition, but I can understand why you would want to in a dual boot with windows.

There probably is a nice gui somewhere in the software centre for you tick boxes with but I don't know of it.

---

### Post by nothingspecial on 2011-08-26
Sorry for double post :P

If you open a terminal and post the output of

```
sudo blkid
```

and tell me where you would like the file system to mount (where in your system eg your home folder or /media), I (or someone else) can give you something to copy and paste.

---

### Post by MaccyDG on 2011-08-26
Done it, thank you!  And thanks for the explanation in your earlier post.

My FAT32 is now mounting nicely, but my file system still has the padlock icon on it.  I'm perplexed by this, cos I hadn't changed any options on that partition before I got the padlock.  This is what my fstab looks like:
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid     0  0  
# / was on /dev/sda3 during installation
UUID=7fa91f34-b43c-47ca-b12f-3cece1001644  /            ext3  errors=remount-ro       0  1  
# swap was on /dev/sda4 during installation
UUID=09dc6fd8-f045-45bf-bbb2-261f2cf24f37  none         swap  sw                      0  0  
UUID=D6D6-D3C6                             /media/sda2  vfat  user,fmask=0111,dmask=0000   0  0  
```I tried changing the ext3 options to ```
default,errors=remount-ro
```, but when I rebooted, Ubuntu said there was an error mounting it, so I took it out again.  Any ideas?!

---

### Post by nothingspecial on 2011-08-26
I had missread your first post. Up till now I was unaware that your file system had the lock on it as well as the fat partition.

Your fstab looks fine to me except that / should be ext4 not ext3. Did you manually partition at install?

I don't mean that fstab should read ext4 necessarily, just that it should if your / partition is ext4. Which it should be unless you did _not_ do a standard Ubuntu install.

It maybe that this "file system manager" has changed your fstab and that the ext3 option is causing the "errors" which is causing it to remount read only, as specified.

This is all a complete guess, but I shall think more on it.

---

### Post by nothingspecial on 2011-08-26
Double post again sorry,


but it is worth pointing out that you should always make a backup of fstab before you mess with it.

although thinking about it, your back up is right here in this thread I suppose.

---

### Post by MaccyDG on 2011-08-26
Thanks for the reminder - I have been making backups, although when stuff's gone wrong so far, I've just booted into a different install of Ubuntu on a USB key and altered any changes back to what they were from there.

I did do a manual install, yeah - I'd already made my partitions, so I wanted to tell Ubuntu where to install to, and where to use as swap.  I chose ext3 cos I thought I'd read somewhere that ext4 wasn't amazingly stable yet.  Is it worth reinstalling to get the improved features of ext4?

But anyway, the ext3 is correct in this case.

---

### Post by MaccyDG on 2011-08-29
*bump*

Does anyone have any ideas about this?  I'm pretty sure the filesystem is OK, cos the disk check doesn't show any problems.

---

### Post by MaccyDG on 2011-09-05
*Last bump, before I give up on this*

Does anyone have any ideas what might be causing me this problem?

To recap: ext3 / partition shows a padlock symbol in Nautilus: read-only access unless I sudo every time I want to change anything on that partition, which is annoying.

The fsck doesn't throw up any disk errors (at least, it finishes without saying anything, so I assume that means there are no errors).

If you think you've got an idea as to why this might be, I'd be very grateful to hear from you.

Cheers,

Liam

---

### Post by MaccyDG on 2011-09-06
OK, so it turns out that although I can't change stuff within the Root partition generally, I can change stuff in the Home folder, which is what matters, really.  So all OK!

---

### Post by nothingspecial on 2011-09-06
That's how it is supposed to be. If you really need to change stuff there, take note of my sig, you can hit Alt-F2 and type ```
gksudo nautilus
```

---

