---
title: "What's the best way to install on lots of computers?"
date: 2011-08-24
forum: General Help
---

### Post by artantaaa on 2011-08-24
Hello. I am a volunteer at a place that refurbishes computers and gives them away to those who can't afford one. I usually install Ubuntu on 4 computers at a time with the 10.04.3 alternate CD. We have limited table space and a 5 port switch. Installation takes 1-2 hours depending on how old the machine is, and then another 1-2 hours for updating and installing things like audio/video codecs, flash, java, gimp, etc. Recently, we have been experiencing a surge in donations and the room devoted to this project is now hard to move around in. I am now looking for a faster way of getting these machines out the door. 

We had 20 identical dells come in last week, and after I had finished the first four, I booted them from a live CD and used DD to clone drives for the rest of them. This saved a lot of time, but I have some concerns with this method. All of these computers go to different people, but if they were connected to the same network, would there be problems? Also, if I install one of these copied drives in a machine with different hardware, it seems to be okay, but I worry that it might not work as well as if I had installed directly on that system. What problems will I encounter using this same disc image for all of these computers? Is there a more efficient way to get Ubuntu installed and configured on these things?

---

### Post by stefangr1 on 2011-08-24
Using a PXE boot server and kickstart would make the install process very efficient, as human intervention would be largely reduced to changing the boot priority order of newly arrived systems.

It does, however, require an initial investment for plowing through some documentation and setting things up.

---

### Post by linkageless on 2011-08-24
I've used kickstart extensively for RedHat and it's clones, but not with anything else like Debian or Ubuntu. (I'm sure there's people working to make it work for Debian and Ubuntu thoug.)

Preseed is one way of building Debian systems repeatedly:
[http://wiki.debian.org/DebianInstaller/Preseed](http://wiki.debian.org/DebianInstaller/Preseed)

For my money though, a dd or rsyncs of a system works well for cloning. Issues to look out for are:
* clash of UUIDs and labels should the drives from such machines ever come together on the same system (not a problem if you fdisk, mkfs then rsync).
* clash of hostnames, can't imagine this to be that bad if these are workstations
* IP addresses should be DHCP, or change them each time if static (I'd go with DHCP if you can)
* udev rules for network interfaces (/etc/udev/rules.d/70-persistent-net.rules IIRC) will need removing or tweaking to match new MAC address(es) or you may end up with additional higher numbered eth* interfaces.
* ssh host keys ideally need re-creating (delete them from /etc/ssh/ssh_host* and do a dpkg-reconfigure openssh-server)
* consider replacing (or at least refreshing) all passwords given to login accounts (ideally you don't want /etc/shadow to be the same on every box)
* it's also nice to remove many of the old logs in /var/log/ and temp files in various places as they won't necessarily be relevant to the clone. This won't be a problem if you're cloning a freshly built system.

Slightly different hardware is not normally a problem. Most modern distros have loads of drivers as modules which helps to cope with changes of hardware fairly seamlessly. The worst issue (other than MAC addresses) I've encountered is different disk sizes when doing a dd, which is partly why I would normally rsync. Assuming your partitions aren't full, rsync is faster too.

for reference, rsync commandline I would use to clone root filesystem over network:

rsync -aHxz --stats --numeric-ids --delete root@sourcemachine:/ /mnt/target/

---

### Post by linkageless on 2011-08-24
Just found a useful pointer for preseeding natty:

[http://sshrootat.blogspot.com/2011/04/preseeding-ubuntu-natty-1104.html](http://sshrootat.blogspot.com/2011/04/preseeding-ubuntu-natty-1104.html)

Be aware that you will likely need to set up a PXE environment using dhcp and pxeboot. In your case, you may find cloning directly from a master copy faster than building machines over the network.

---

### Post by artantaaa on 2011-08-24
Thanks for the replies. I have already been reading about using clonezilla and a DRBL server to get the disc image onto the machines. Any type of network boot cloning system would definitely be better than physically moving the drives around if I was using the same disc image for every computer, but I will have to spend some time getting it set up.  Is kickstart any simpler than clonezilla? Are there other alternatives I should look into? For now, I'll stick with DD until I can get something else set up. All of those dells had 40 GB drives so I didn't have any trouble, but DD works as long as the target drive is the same size or larger
 than the source drive, right? I will have to try out Rsync, too. I didn't realize it worked over the network.

I also had another idea. Is there a way to create an install CD ( not a live CD) with all the updates and desired packages already included? It wouldn't go as fast as the cloning, but would cut the time spent on each computer in half, and the less experienced volunteers could benefit from it too.

---

### Post by linkageless on 2011-08-24
Your idea of creating an install cd is a fair one, but I've not seen anything like this that works without effort. In the past, we used something called mondo archive to create isos but it was more effort than using rsync or dd.

You're right that you should have no problem with dd as long as the drive is the same or larger, but unless you go at it with partitioning tools afterwards any spare space over your 40G will be wasted.

If you are concerned about your less experienced volunteers wiping out your original image with rsync, have the filesystems mounted read-only on a server and have them connect to a rsyncd on there.

Here's an example rsyncd.conf:
```
[roottemplate]
        path = /mnt/root-template/
        comment = read only copy of ubuntu template
        auth users = techuser
        secrets file = /etc/rsyncd.secret
        read only = true
        use chroot = true
        uid = 0
        gid = 0
```

Have a read of man rsyncd.conf for details on these and other options.

While I've not used it, Clonezilla appears to be a fancy way of doing a dd, while kickstart & preseed provide you a fresh system install based on a recipe. Technically, the latter is more appropriate in this case, but takes effort to set up and maintain also. If you use clonezilla, dd, rsync or any other cloning method, you should check the points listed in my first post.

---

### Post by Grenage on 2011-08-24
Rsync over multicast must be a viable option?  One machine sends, and many receive.

---

### Post by linkageless on 2011-08-24
> **Grenage said:**
> Rsync over multicast must be a viable option?  One machine sends, and many receive.

rsync is usually uses an ssh connection in the background, which can only be between a single client and a single server. If you're clever, you might be able to get something basic working over netcat and multicast - I've not tried.

Correction - Having had a quick look in the rsync man page, there does indeed seem to be reference to using multicast - have a look at the section entitled 'BATCH MODE'

---

### Post by linkageless on 2011-08-24
I'm reminded of this also:
[http://fai-project.org/](http://fai-project.org/)

Not used it myself, but it looks well worth considering as an alternative to preseed or kickstart.

---

### Post by Grenage on 2011-08-24
> **linkageless said:**
> rsync is usually uses an ssh connection in the background, which can only be between a single client and a single server. If you're clever, you might be able to get something basic working over netcat and multicast - I've not tried.

Correction - Having had a quick look in the rsync man page, there does indeed seem to be reference to using multicast - have a look at the section entitled 'BATCH MODE'

Aye; while I've never used it myself, I have seen it referenced.  There also seems to be at least one fork based on that one feature:

[http://freshmeat.net/projects/mrsync/](http://freshmeat.net/projects/mrsync/)

---

### Post by artantaaa on 2011-08-27
I found a program called remastersys that creates an installable live CD iso from your current installation. Mine was too large to fit on a CD, so I put it on a flash drive, and it works pretty well. I didn't want to use a Live CD because most of the machines I'm installing on are pentium4's with 512MB ram, but the flash drive doesn't take as long to load as an actual disc. I think Rsync will be what I use in the future though, after I've had a little more practice with it. Thanks for all of the advice.

---

