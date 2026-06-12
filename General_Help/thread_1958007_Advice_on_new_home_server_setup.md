---
title: "Advice on new home server setup"
date: 2012-04-13
forum: General Help
---

### Post by NertSkull on 2012-04-13
So, I've decided to centralize all my files and was hoping for some advice from the community.  This is what I'm looking to do.

I have a desktop I'm not using.  Its a phenom II X2, 8 gigs of ram.  I want to make it my file server.

I have a small (160gb) hard drive I was hoping to install a base operating system on.  I always do full disk encryption, so I can easily do that for the OS.

Then I have two hard drives (700GB and 640GB) I wanted to put in and set up in a RAID 1 configuration.  These I wanted to be my "data" drives for all my personal files.

Then I have two other drives (1TB and 1.5TB) I want to put in just as drives.  No RAID, just things I have my movies and music on.  I'm not worried so much about backup there.

Obviously I'll have the OS encrypted.  I would really like my "data" drives to be encrypted as well.  Often I've gone with truecrypt to do that, but I don't know how that works with RAID.  I've never set up a RAID system before.

So, here are my questions.

1. Can I full disk encrypt a RAID1 configuration?

2. What do I use to configure the RAID?  I know linux can do it.  But most of the tutorials I see are for mirroring the OS.  I don't really need that, I just need my data drive mirrored.  I don't know even know what the program/commands are to set that up.  I'm pretty sure I'm not buying stuff to do hardware RAID, so can someone give me some pointers on how to set this up?  With encryption?

3. Am I totally missing the boat on something? Should I be doing this differently?

4. I know RAIDs mirror the drive.  So if I have a 700GB and 640GB drive I'm mirroring, will I lose the extra 60GB from the one drive?  Or will that become a new/separate partition?

5. Maybe this will come with the previous question, but do I still use Ext4 for my RAID system? Or are there better partition tables?

6. On a different note (maybe I need a new thread).  I've always used NFS to share files between my linux computers.  Is that my best option?  Or should I look into FreeNAS or something else?  I don't necessarily need windows access, I'm 100% on linux.

7. From what I can tell, mdadm appears to be the program to use to setup a RAID.  Is this true?  Is it the best way?  Is it the only way?  Is there a better way?

Thanks everyone for helping someone totally new to the RAID world.

---

### Post by abyrne on 2012-04-13
I'm not a RAID expert, so I'm not sure 1-5, but for question 6:
> I've always used NFS to share files between my linux computers. Is that my best option? Or should I look into FreeNAS or something else? I don't necessarily need windows access, I'm 100% on linux
I was going to suggest Samba until you mentioned that you don't necessarily need Windows access. Since you seem to be quite interested in security, I would suggest SFTP. But if you're looking for something with compatibility and zero-config on the client-side, I'd still go with Samba.

---

### Post by NertSkull on 2012-04-13
So, I guess I should mention that this will all be access on my LAN.  Any coming in from the outside I would do using SSH/SCP.

So, that being the case, does SFTP or Samba offer any advantages over NFS?  I've always assumed Samba was primarily just to play nice with windows.  But with zero windows machines on my home network, would it still be the better choice over NFS?  I'm currently using NFS and just mount the drives in fstab.  Is that the same in samba?

---

### Post by gordintoronto on 2012-04-13
The desktop system is far more powerful than you need, but if it's spare, you might as well use it.

I suggest you install Ubuntu Desktop, not Ubuntu Server. Desktop can do everything Server can do, and it's a lot easier to manage. It consumes slightly more resources, but that's not an issue for you.

My preference is backup, not RAID, and no encryption. In my opinion, those are technologies which can break, and I like simple. 

I *think* you should be able to encrypt a RAID1 setup just as easily as a single drive. In most cases, people set up RAID1 with drives which are the same size, but it should work with different size drives, you'll just be wasting a bit of space on the larger drive.

Obviously, first you would set up the RAID, then the encryption.

The 160 GB drive for your OS is about 30 times as large as you need, but if that's what you have available, go for it!

From what I have read, NFS performs better than Samba, but takes more effort to set up.

---

### Post by NertSkull on 2012-05-01
So it works pretty smoothly.

I ended up going with a desktop version for my "server".  The raid setup was incredibly easy.  And once it was setup it just gave me a partition in /dev/md0p1.  I then encrypted that partition using truecrypt and mounted it.  It works great.  It also is set up to send me an email if one of the raid drives fails.  And I have duplicity backing up encrypted backups to another drive.  Which I then RSYNC to an off-site computer.

The 160g hard drive is definitely more than I need, but it wasn't doing anything else.

NFS is working well, but not as well as I would have liked.  If I transfer one large file (like an HD movie that is 10GB) I get very close to my gigabit network speeds.  I get speeds upwards of 900 Mb/sec (I seem to fall around 80-105 MB/s on average with large files).

But if I transfer hundreds or thousands of really small files, it only hits around 25-40 MB/s if that.  Which is a bit annoying to have it take just as long to transfer a few hundred megabytes of many small files as it takes to transfer a few gigabytes of one file.  But I need to look more into optimizing NFS and maybe make a different thread to try and speed that up.

As it is, everything seems to be working quite well thus far.

---

### Post by LewisTM on 2012-05-01
The slow performance for small files if probably due to the machine having to allocate many nodes while doing encryption/decryption of the filesystem on the fly.
See [http://superuser.com/questions/397252/ecryptfs-and-many-many-small-files-bad-performance](http://superuser.com/questions/397252/ecryptfs-and-many-many-small-files-bad-performance)

---

### Post by zero2xiii on 2012-05-01
> **LewisTM said:**
> The slow performance for small files if probably due to the machine having to allocate many nodes while doing encryption/decryption of the filesystem on the fly.
See [http://superuser.com/questions/397252/ecryptfs-and-many-many-small-files-bad-performance](http://superuser.com/questions/397252/ecryptfs-and-many-many-small-files-bad-performance)

+1 for this.

I have also noted speed (network related) degration on encrypted drives/folders. Haven't tested this extensively, but hardware encryption seemed faster the last time I used it compared to software encryption.

This could possibly be sped up somewhat using a RAID 0 config instead of RAID 1.. Remember RAID 1 performs at the slower speed between the drives being RAID. So this might also be a bottleneck issue, albeight I highly doubt it. Reading one file from 2 drives is quicker than reading a 100 from 2...

Combining encryption, with RAID will even just make the problem worse.

But yea, remember, adding any form of overhead, will decrease performance.

Try plying with the MTU of the network. INCREASING this MIGHT help with the smaller files being transfered somewhat faster, but this is only a guess.

Cherz

---

