---
title: "Need help in mounting other partition"
date: 2009-08-30
forum: General Help
---

### Post by DougieFresh4U on 2009-08-30
Some reason my internet is borked for my Jaunty partition (sda6).Here is the thread I started about internet drama w/Jaunty.
[http://ubuntuforums.org/showthread.php?t=1253449](http://ubuntuforums.org/showthread.php?t=1253449)
 I would like to mount that partition from one of my other partition as I am running a multi-boot machine.
Would some one please provide the codes for me to mount so I can run updates on my Jaunty and possibly reinstall network manager. I ran a code in terminal 2 days ago and it spat out something about network is disabled.
Thanks

---

### Post by DougieFresh4U on 2009-09-02
Still have not solve the issue.
Any ideas would be great!

---

### Post by drs305 on 2009-09-02
> **DougieFresh4U said:**
> Some reason my internet is borked for my Jaunty partition (sda6).Here is the thread I started about internet drama w/Jaunty.
[http://ubuntuforums.org/showthread.php?t=1253449](http://ubuntuforums.org/showthread.php?t=1253449)

The link takes us to the identical thread with no new information!  ;-)

---

### Post by DougieFresh4U on 2009-09-02
> **drs305 said:**
> The link takes us to the identical thread with no new information!  ;-)
Sorry, I don't have any new info.I will mention that when I plug in wireless, it's not even seeing that.
I would like to mount my Jaunty partition (sda6) through my Karmic install and some how update Jaunty. Don't know why networking is 'disabled' And I do not know how to enable it. Internet was working and suddenly it just quit. My other 3 partition have working ethernet.

---

### Post by drs305 on 2009-09-02
For a simple mount of an ext3 partition:

Make sure you own the mount point. I will use the example of /mnt/data:
```

sudo mkdir /mnt/data
sudo chown -R *yourusername:* /mnt/data

```
Example:
sudo chown -R doug: /mnt/data

```

sudo mount /dev/sda6 /path/mountpoint

```
Example:
sudo mount /dev/sda6 /mnt/data

---

### Post by DougieFresh4U on 2009-09-02
> **drs305 said:**
> For a simple mount of an ext3 partition:

Make sure you own the mount point. I will use the example of /mnt/data:
```

sudo mkdir /mnt/data
sudo chown -R *yourusername:* /mnt/data

```
Example:
sudo chown -R doug: /mnt/data

```

sudo mount /dev/sda6 /path/mountpoint

```
Example:
sudo mount /dev/sda6 /mnt/data
Thanks for your assistance, but sorry, I am not a dummy but I still do not understand what you are saying. I want to mount 'sda6' from my Karmic (sda88) install..
To be honest, I actually want to know what is wrong with my networking for Jaunty (sda6). I needs to be 'enable' and I have tried all the menu entry's pertaining to networking. I am at a loss. 
Guess I could leave that partition alone and it will be used for the next release (10.04) for testing

---

### Post by drs305 on 2009-09-02
> **DougieFresh4U said:**
> Thanks for your assistance, but sorry, I am not a dummy but I still do not understand what you are saying. I want to mount 'sda6' from my Karmic (sda88) install..
Perhaps I don't understand what you are asking. You want to be able to see the contents of your Jaunty/sda6 install while running Karmic?

To view the contents, the sda6 partition must be mounted on a folder. If you run the mount command in a terminal it will place the sda6 contents in the /mnt/data folder. You can navigate to it with nautilus to see the contents. 

For instance, if you want to see the contents of your Jaunty boot partition, you would navigate to /mnt/data/boot after you mounted sda6.

> 
To be honest, I actually want to know what is wrong with my networking for Jaunty (sda6). I needs to be 'enable' and I have tried all the menu entry's pertaining to networking. I am at a loss. 


There is a networking Ubuntu forum. If you provide the proper details in that forum with a descriptive title you may be able to solve your networking problem.

---

### Post by DougieFresh4U on 2009-09-02
> **drs305 said:**
> Perhaps I don't understand what you are asking. You want to be able to see the contents of your Jaunty/sda6 install while running Karmic?

To view the contents, the sda6 partition must be mounted on a folder. If you run the mount command in a terminal it will place the sda6 contents in the /mnt/data folder. You can navigate to it with nautilus to see the contents. 

For instance, if you want to see the contents of your Jaunty boot partition, you would navigate to /mnt/data/boot after you mounted sda6.



There is a networking Ubuntu forum. If you provide the proper details in that forum with a descriptive title you may be able to solve your networking problem.
Thanks for your patients.
I know there is a way to mount 'sda6' and run an update for said partition. I just don't know the exact codes.

---

### Post by drs305 on 2009-09-02
> **DougieFresh4U said:**
> Thanks for your patients.
I know there is a way to mount 'sda6' and run an update for said partition. I just don't know the exact codes.

Sorry I'm not giving you the information you need to fix your problem.

What you may be thinking is chroot'ing into a system, and I don't know if you can solve your problem by this method. To do it from the Jaunty LiveCD, where you may be able to get your network to work, you would do it like this. I can give you the basics of how to get it set up, but not how to fix your networking issue:

Boot the LiveCD to the Desktop. Hopefully you can establish a connection to your network.

Run these commands to mount your existing Jaunty installation:
```

sudo mount /dev/sda6    /mnt
sudo mount --bind /dev  /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys  /mnt/sys
sudo chroot /mnt

```

Commands you run would now be executed on your actual Jaunty partition.

---

### Post by DougieFresh4U on 2009-09-02
> **drs305 said:**
> Sorry I'm not giving you the information you need to fix your problem.

What you may be thinking is chroot'ing into a system, and I don't know if you can solve your problem by this method. To do it from the Jaunty LiveCD, where you may be able to get your network to work, you would do it like this. I can give you the basics of how to get it set up, but not how to fix your networking issue:

Boot the LiveCD to the Desktop. Hopefully you can establish a connection to your network.

Run these commands to mount your existing Jaunty installation:
```

sudo mount /dev/sda6    /mnt
sudo mount --bind /dev  /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys  /mnt/sys
sudo chroot /mnt

```

Commands you run would now be executed on your actual Jaunty partition.
Thanks for the codes. Will give it a try.
Will also post in 'Networking'

---

