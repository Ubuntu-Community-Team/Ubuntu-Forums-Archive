---
title: "accessing USB stick from $ prompt"
date: 2010-10-20
forum: General Help
---

### Post by NutmegCT on 2010-10-20
Good morning.

I can't get beyond the $ prompt after moving from 10.04 to 10.10.  I'm still working on that.

But in the meantime, I want to copy my Home folder contents to a USB stick.

I assume I just use cp to copy files, but I don't know how to locate/map the USB stick.

At the $ prompt, how do I "see" the USB stick?  

Thanks.
Tom

---

### Post by Hippytaff on 2010-10-20
I think the path to the usb stick should be in media
 
```

cd /media

```
 
when your in media type ls to list the contents, should give you the name of the usb drive.
 
Then you can
 
```

cp /path/foldername /media/name_of_usb

```
 
but I'm not on my linux box to check

---

### Post by NutmegCT on 2010-10-20
Thanks.  I have the USB stick in the USB slot on the laptop, and a CD in the CD slot.

at $ on the laptop I type <cd /media>
<ls> shows cdrom and cdrom0

<cd /media/cdrom>

<ls> results in nothing

<cd /media/cdrom0>

<ls> results in nothing

Even tho' the CD has files, and the USB has files, <ls> shows nothing.  Isn't that saying the device isn't detected?

Thanks.
Tom

---

### Post by Hippytaff on 2010-10-20
I might have the wrong path...
 
try lsusb

---

### Post by NutmegCT on 2010-10-20
Thanks for hanging in there ...

I have no <lsusb> in the /media directory.

Not in etc either, or in the /cdrom directory.

Any idea where I should look to find the lsusb?

Tom

---

### Post by Hippytaff on 2010-10-20
> **NutmegCT said:**
> Thanks for hanging in there ...
 
I have no <lsusb> in the /media directory.
 
Not in etc either, or in the /cdrom directory.
 
Any idea where I should look to find the lsusb?
 
Tom
 
Sorry, my instructions were not clear. in the terminal type
 
```

lsusb

```
 
might want to try 
 
```

fdisk -l

```
in the termnial first, to show you the path of the usb drive, if it can bees seen :-)

---

### Post by NutmegCT on 2010-10-20
Thanks.  <lsusb> gives:

bus 003 device 001:  id 1d6b:0001 linus foundation 1.1 root hub
bos 001 device 002 id 0781:5406 sandisk corp. cruzer micro u3
bus 001 device 001 id id6b:0002 linus foundation 2.0 root hub
bus 004 device 001 id 1d6b:0001 linux foundation 1.1 root hub
bus 002 device 001` id 1d6b:0001 linux foundation 1.1 root hub

then back to the $ prompt

 fdisk -1 returns nothing - just the $ prompt again.

---

### Post by Hippytaff on 2010-10-20
> 
fdisk -1 returns nothing - just the $ prompt again.

 
should be fdisk -l (lowercase L), that looks like it might be 1 - one
 
Looks like it can see your usb drive anyway.
 
```

cd /media/usb

```
 
type the above and press TAB, the terminal might autocomplete the rest of the path - worth a try, but fdisk -l should give you the path :-)

---

### Post by NutmegCT on 2010-10-20
yep, it was fdisk - (lower case L)   
no result, just the $ prompt

 <cd /media/usb> gives:

no such file or directory

all that's in the /media directory is
cdrom cdrom0

---

### Post by Hippytaff on 2010-10-20
odd...can you see it on the desktop when it's plugged in, or in Places > Computer

---

### Post by Grenage on 2010-10-20
If you don't sudo fdisk, you won't get a listing:

```
sudo fdisk -l
```

---

### Post by NutmegCT on 2010-10-20
Remember - I have no desktop.  only the "terminal" with the $ prompt.  As the 10.04 to 10.10 upgrade failed, I can only boot to the $ prompt.

(still trying to be positive about all this ...)

---

### Post by NutmegCT on 2010-10-20
OK - sudo fdisk -l worked.

lists lots of info on hard drive partitions (/dev/sda1, sda2, sda5, sda6  
shows sdb1 device boot.

no info on the cdrom or usb, even tho' they show as devices in the boot screens.

---

### Post by Grenage on 2010-10-20
The USB drive 'should' show up as an sda device, I think!

---

### Post by Hippytaff on 2010-10-20
> **Grenage said:**
> The USB drive 'should' show up as an sda device, I think!
 
It should - maybe it needs mounting? though I thought this happened automatically
 
also, forgot you haven't gor a desktop :-s
 
try
```

cd /dev/sda/

```
then
```

ls

```

---

### Post by Grenage on 2010-10-20
I've used USB drives on Ubuntu server before, and I don't think they were automatically mounted.  I cannot be sure.

---

### Post by NutmegCT on 2010-10-20
Funny (not really ...) - if I could get the desktop back, I'd probably not need to worry about finding the USB from inside the terminal.

but it seems that 100s (1000s?) of people are having trouble with the 10,.04 to 10.10 migration, and the symptoms are all over the place.

If I can get my Home folder onto the USB, then I'll probably wipe the HD and try booting from the 10.04 live CD and starting over.

T.

---

### Post by Hippytaff on 2010-10-20
> **Grenage said:**
> I've used USB drives on Ubuntu server before, and I don't think they were automatically mounted. I cannot be sure.
 
maybe try mounting it first? [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)
 
I can;t understand why lsusb brings back the drive, but you cant navigate to it?

---

### Post by NutmegCT on 2010-10-20
Thanks.  <lsusb> shows the usb drive.  

bus 001 device 002:  id0781:5406 sandisk corp. cruzer micro u3

How do I use that information to mount the drive?

T.

---

### Post by Hippytaff on 2010-10-20
This might help [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

### Post by Grenage on 2010-10-20
Can you identify it in the fdisk listing?  For example, is it called sdb1 or sdc1?

---

### Post by NutmegCT on 2010-10-20
Sorry I wasn't clear.   In the fdisk listing I see:

/dev/sda1 start/end/blocks ID: c  System W95 fat32 lba
/dev/sda2 start/end/blocks ID 5 extended
/dev/sda5 start/end/blocks id 83 linux
/dev/sda6 start/end/blocks id 82 linux swap / solarix
/dev/sdb1 start/end/blocks id6 fat16

Is the sdb1 the usb drive?

---

### Post by Hippytaff on 2010-10-20
```

sudo mkdir /media/external 

```
```

sudo mount -t vfat /dev/sdb1 /media/external -o uid=1000,gid=100,utf8,dmask=027,fmask=137 

```
```

sudo mount -t ntfs-3g /dev/sdb1 /media/external

```
 
Then cd to media/external or rather cp /home /media/external

---

### Post by NutmegCT on 2010-10-20
ok - i'm guessing that sdb1 is the usb, as it shows fat16

I used the link for mounting, created the /media/external directory, and followed the mount commands.

When I hit enter, I got a stream of informational stuff about how to use mount.  I didn't know if mount had actually done anything, so I tried:

<cd /media/external>

<ls>

just got the $ prompt; seemed that the <ls> showed no contents.  So I don't know if the usb is really mounted yet.

Also tried <dir> for the same /media/external directory, but still nothing shows.

T.

---

### Post by Hippytaff on 2010-10-20
```

sudo mount -t vfat16 /dev/sdb1 /media/external -o uid=1000,gid=100,utf8,dmask=027,fmask=137

```
 
try vfat16 instead?

---

### Post by NutmegCT on 2010-10-20
> **Hippytaff said:**
> ```

sudo mkdir /media/external 

```
```

sudo mount -t vfat /dev/sdb1 /media/external -o uid=1000,gid=100,utf8,dmask=027,fmask=137 

```
```

sudo mount -t ntfs-3g /dev/sdb1 /media/external

```
 
Then cd to media/external or rather cp /home /media/external

ok, did the above (didn't know about that last line until now).

result:  

NTFS signature is missing.
failed to mount /dev/sdb1
the device /dev/sdb1 doesn't seem to have a valid ntfs
maybe the wrong device is used?  or the whole disk insteaed of a partition (e.g. /dev/sda, not /dev/sda1)? or the other way around?"

(all the above is the result on the screen)

now back to $ prompt

---

### Post by NutmegCT on 2010-10-20
> **Hippytaff said:**
> ```

sudo mount -t vfat16 /dev/sdb1 /media/external -o uid=1000,gid=100,utf8,dmask=027,fmask=137

```
 
try vfat16 instead?

ok - tried vfat16 also.  same "info" result

---

### Post by Grenage on 2010-10-20
Just for fun, what does it say if you declare no options?

```
sudo mount /dev/sdb1 /media/external
```

---

### Post by NutmegCT on 2010-10-20
THAT WORKED!  NO OPTIONS

I then moved to the /media/external directory, and did a <ls> and saw all the USB files and folders.

Yeehaa!

OK - I've been at this for 8 hours yesterday and five hours this morning.  I'm taking a break.

Thank you for the help folks!

Tom

---

### Post by Grenage on 2010-10-20
Glad to hear you got there. :)

---

### Post by NutmegCT on 2010-10-20
well, minor detail.  looks like without the options, i don't have permission to create directories and files on the usb.  I'll try this afternoon to figure out how to do that.

Onward through the fog.

Tom

---

### Post by Hippytaff on 2010-10-20
You might be able to chown the usb at the mount point (Chown - change ownership) but thats a whole new path of discovery :-) have a break before we go there :-D
 
actually - surely you can just prefix the cp command with sudo
 
```

sudo cp /home /media/external

```

---

### Post by Grenage on 2010-10-20
That's an easy one, the mount point simply doesn't have the appropriate permissions.  Chown or chmod would allow you to own or set permissions; the following command would allow all users to do anything:

```
sudo chmod 777 /media/external
```

Or recursively:

```
sudo chmod -R 777 /media/external
```

Or to own as your user:

```
sudo chown username:username /media/external
```

---

### Post by NutmegCT on 2010-10-20
Gentlemen (?) -

it is DONE!

I changed permissions and got every single file and folder I needed from the nearly-defunct Ubuntu machine onto the usb drive.  Those files are now happily residing on my iBook.

Thanks again for all the advice and step by step instructions.

Question for you:  would you move to 10.10 yourselves?

My idea is currently to boot the dying Ubuntu machine from a utilities CD I have, then DOS fdisk the HD to one single 30G partition.

Then try (!) to boot from a 10.10 live CD and try to install and run.

If that fails, then DOS fdisk again, and try to boot and install from the current 10.04 live CD.

I actually like Ubuntu very much.  But the "law of unintended consequences" has been rearing its ugly head recently when I tried the 10.10 upgrade.

Any thoughts?

Tom

---

### Post by Grenage on 2010-10-20
Well I've installed 10.10 on several machines, with a couple of them being upgrades.  All are running fine, with minor glitches; so I might have stayed in 10.04, looking back.

---

### Post by Hippytaff on 2010-10-20
10.10 works fine for me and has from the offset, but if your having a few troubles with it it might be worth waiting until bugs are fixed and there are more fixes etc

Glad it all worked out - remember to mark the thread as solved in the forum tools so others can benefit from your hard work

---

