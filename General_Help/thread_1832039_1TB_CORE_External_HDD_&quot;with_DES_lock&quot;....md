---
title: "1TB CORE External HDD &quot;with DES lock&quot;... will it work with Ubuntu?"
date: 2011-08-24
forum: General Help
---

### Post by t0p on 2011-08-24
I want to buy a new external USB hard disk drive, and my eye was drawn by the 1TB CORE External Desktop USB 2.0 Very appealing was the comment "Plug n Play  - no software to install".

But then I noticed the sentence: "Incudes DES lock - Protect all your important files."

This set the alarm bells ringing.  If the drive comes with a DES protection lock, is this likely to work with Ubuntu?  Or is it going to be a Windows-only thing, locking me out cos I don't use Windows?

Any ideas?  Cheers!

---

### Post by aeiah on 2011-08-24
these are often implemented in hardware and require software. it says 'no software to install' but that isnt the same as 'no software required'.

are you getting it from maplin? they dont seem to have any detailed specs for it - try asking a question on their site, they're usually pretty good for customer support.

---

### Post by t0p on 2011-08-24
Well, can anyone suggest an external USB HDD that *will* work with Ubuntu?  I currently use a Fujitsu Siemens 400GB HDD which works fine.  But I don't seem to be able to find any now.

Anything available from the electrical chain stores (ie Currys, PC World or Maplins) would be ideal.  I could just go into the stores and ask "Does this work with Ubuntu/Linux, but the blank stares I get from sales assistants at the mention of Ubuntu or Linux are just too disheartening.

---

### Post by t0p on 2011-08-24
Something that just occurred to me: suppose I get one of these drives with "DES encryption", and use gparted or whatever to format it ext4?  Will this ensure linux compatibility?

---

### Post by flipper T on 2011-08-24
have you looked here ?

[http://linuxhcl.com/browse/search+hard-drives?category=31](http://linuxhcl.com/browse/search+hard-drives?category=31)

---

### Post by tredegar on 2011-08-24
> suppose I get one of these drives with "DES encryption", and use gparted or whatever to format it ext4?
A word of warning: I have a 2GB USB flash "disk" that comes with DES encryption. Windows initially sees it as just a CD ROM, and loads the (Windows) software. Part of this seems to be responsible for making the (encrypted) partition appear on the device. Once the partition has become visible, it can be decrypted.

Linux sees this device as just a CD ROM with windows software. It does not see the encrypted partition at all. (A bit like those 3G mobile dongles that need **usb_modeswitch** to allow the creation of the modem device, which can only be configured once it has been created).

I have tried USB-sniffers and usb_modeswitch without success. I am sure that if I could just see the encrypted partition with **fdisk** or **gparted** then I could decrypt it (I have the key).

It does not work under wine either.

My advice: Just buy yourself a regular USB disk, without encrytion. Linux can do encrytion if you need it. My last purchase was a plain, ordinary, 1TB Seagate disk USB disk from Maplin. It "just works"

---

### Post by t0p on 2011-08-24
Well, I went to Maplin to have a look at their external HDDs, which all seemed to have the DES encryption thing going on.  Then I saw a 1 TB "Seagate Expansion External Drive" that had nothing on its packaging about DES or whatever.  So I bit the bullet and bought the damn thing.

So, Ubuntu sees the "Expansion" drive but won't let me do anything with it (I forgot to note down the precise error message, stupid me).  But I figured if I reformatted it to ext4 all would be well.  Which is what's happening: it's apparently "reformatting", and has been for the past 20 mins or so.

I have no experience of formatting anything as large as a 1 TB disk, so I don't know if this 20+ mins wait is normal.  What do you all thing?  My computer has a Pentium 4 1.6 GHz processor and 1 gig RAM.  Is such a lengthy reformat to be expected?  Or should I Cancel it and investigate other options.

Incidentally I am a victim of the world economic downturn and can't afford to just go out and buy another drive.  I've been saving up for ages to buy *this* one.

Anyone know what I can/should do?  Cheers.

---

### Post by tredegar on 2011-08-24
> I don't know if this 20+ mins wait is normal.
It's normal.
1TB is a **big** disk.
The bottleneck is the speed of USB2

Edit:
Once it has been formatted, you'll need to make it useable.
My external HDD is ext3, owner:group = root:root, permissions = 777
This works very well, everyone can use it, and I set my personal dirs on it to  permissions of 700 ( rwx------ ). This keeps my data "private".

So, once it is formatted, mount it.
Then
```
sudo chown root:root */path/to/mountpoint*
sudo chmod 777 */path/to/mountpoint*
```
Then you (and others) should find it easy to use.

If you give the partition a sensible label, it'll appear as such on your desktop. This is useful when you have several external USB disks. If you forgot to do this when you formatted it, you can do it now:

```
sudo tune2fs -L *MyLabel /dev/sdb1*
```

---

### Post by t0p on 2011-08-24
> **tredegar said:**
> It's normal.
1TB is a **big** disk.
The bottleneck is the speed of USB2

Edit:
Once it has been formatted, you'll need to make it useable.
My external HDD is ext3, owner:group = root:root, permissions = 777
This works very well, everyone can use it, and I set my personal dirs on it to  permissions of 700 ( rwx------ ). This keeps my data "private".

So, once it is formatted, mount it.
Then
```
sudo chown root:root */path/to/mountpoint*
sudo chmod 777 */path/to/mountpoint*
```Then you (and others) should find it easy to use.

If you give the partition a sensible label, it'll appear as such on your desktop. This is useful when you have several external USB disks. If you forgot to do this when you formatted it, you can do it now:

```
sudo tune2fs -L *MyLabel /dev/sdb1*
```

Thanks **tregegar**, and also thanks to everyone else who've responded to my pitiful wailing for help.  I've been using Ubuntu for so long, with everything just working, that I'd forgotten how awful it can be when a manufacturer refuses to give Linux any meaningful support.  Believe you me, things will have to change in a *biiig* way if I'm ever going to throw my money at that pack of wolves.

Sorry, wolves.  I know you're nothing like Seagate.  Just one of those old sayings, y'know?

Anyway, I'm sitting here now, with gparted chundering away in the background, presumably reformatting the drive to ext4.  I hope that works, as I have no more money for disk drives and I can't see Seagate giving me a refund just because I use Linux.

---

### Post by JKyleOKC on 2011-08-24
Figure to let it run for several more hours. When I formatted my 500-GB drive, installed internally, it took almost an hour to complete. The USB2 interface is at least 10 times slower than an internal connection, and your drive is twice as big, so your job may run overnight or even longer. Just be patient and it will eventually complete the task!

---

### Post by tredegar on 2011-08-24
> I can't see Seagate giving me a refund just because I use Linux.
It'll work.

And if it doesn't we'll *make it* work (as long as the disk does not have a hardware fault, in which case, you can take it back).

As JKyleOKC said, formatting may take some time .... ... .. .

Be patient.

---

### Post by t0p on 2011-08-24
Lovely!  After about 4 hours 30 mins gparted successfully reformatted the disk as ext4.  So now, after a little juggling with privileges (changing owner of the disk from root to t0p) I have successfully installed my 1TB external HDD.

Thanks to all who helped.  Much useful info was gleaned from members of these forums.

---

