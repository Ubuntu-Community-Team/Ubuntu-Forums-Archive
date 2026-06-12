---
title: "Fixing Hard drive"
date: 2012-06-24
forum: General Help
---

### Post by sdpagent on 2012-06-24
I was performing a shred on an external usb hard drive and was about 50% the way through the second run when the machine cut out.
Ever since, I have not been able to see the drive in gparted. However in the disk utility it shows up as /dev/sdd (gparted shows drives for sdc and then goes straight to sde).

The disk utility has the option to format drive and to format volume. For some reason neither of these work and I get an error:
Error calling fsync(2) on /dev/sdd Input/Output error.

Has anyone got some useful tips? I get the feeling I just killed it, though the smart data tool still works and it states that the drive is healthy...

I wish i could unscrew the thing and stick it in my machine, but unfortunately it looks like one solid piece (WD 2tb elements)

Stu

---

### Post by jmfal on 2012-06-24
Welcome to Ubuntu

Does that have a power supply, maybe it is going bad, or is gone already.

---

### Post by sdpagent on 2012-06-24
It has to be plugged into the mains yes. 

I read another forum where the guy stated that he fixed it by using windows disk management. I tried that and it gave me an error stating that the drive is 'write protected'...

---

### Post by jmfal on 2012-06-24
If you have an  XP disc you can try and format it  and then stop before it starts to install

 Are you going to use it for storage or put  a os on it

---

### Post by nipunshakya on 2012-06-24
Try to format the drive in linux via terminal... see the link below for details...
[http://www.ehow.com/how_1000631_hard-drive-linux.html](http://www.ehow.com/how_1000631_hard-drive-linux.html)

Goodluck

---

### Post by oklokl on 2012-06-24
fdisk-l error occurs
 mbr can only be used to

2tb.. -> GPT


# view.. Normal operation
sudo parted -l

Usage..  Please use the Google search.
# badblocks test..
man badblocks

# testdisk -> Find lost partitions
man testdisk

# How to erase the partition clean.
man dcfldd
man dc3dd   # sudo apt-get install dc3dd dcfldd  # (If there is no way to install)




# parted Usage (erase) 
# Precautions
 # Data is erased.

sudo parted /dev/sdXy
p #view
h  #(help)
mktable
gpt
0
-1
q

sudo mkfs.ext4 -L "test123" /dev/sdXy

# or
sudo mkfs.ntfs -f /dev/sdXy

---

### Post by HermanAB on 2012-06-25
Howdy,

A couple things:
a. There is a secure erase utility built into the drive controller of all modern disk drives (since the previous century).  It can be activated with 'hdparm'.  It is better than shred since it can write everywhere, including between tracks and in damaged sectors.
b. Shred writes pseudo random data to the disk.  This can confuse partition editors, which may think that some random string is meaningful.  To 'repair' the disk, Zero the first 1MB or so using Data Definition:
dd if=/dev/zero of=/dev/sdd bs=1024 count=1000

---

### Post by sdpagent on 2012-06-25
Thank you all for your responses! its great to see such an active community.

Can I just state that I did try running secure erase before doing this shred, but could not run the hdpaarm commands due to an input/output error, im guessing because this is usb external? It does state that the hard drive supports it though, and setting the password etc did work on it.

none of the fdisk commands would work but the mkfs command is currently in progress (for whole device not partitioning this is ok though as I only want to use it for storage), fingers crossed will let you know if it works! 

Thanks guys!

---

### Post by sdpagent on 2012-06-25
When I tried to format to ntfs, it would refuse as it gave me:
```
/dev/sdd is entire device, not just one partition.
Refusing to make a filesystem here!
```

I have been unable to run any partitioning tools so far. I am formatting it to ext3 now.

---

### Post by sdpagent on 2012-06-25
Ok so mkfs isn't magically fixing the drive (still not recognized).

I tried running 
```
dd if=/dev/zero of=/dev/sdd bs=1024 count=1000
```
as suggested before, but i get the following error:

```
dd: writing `/dev/sdd': Input/output error
1+0 records in
0+0 records out
0 bytes (0 B) copied, 0.00159173 s, 0.0 kB/s
```

---

### Post by oklokl on 2012-06-25
# First
```
sudo parted -l
```Partition
 When you create your ...
/dev/sdd not..
/dev/sdd1 ok..

```
sudo mkfs.ext4 -L "test1234" /dev/sdd1
```First ...   sudo parted   -> Using
 Wipe using.
and...       To build gpt.

Create the next partition.
```
sudo parted /dev/sdd
```Mkfs.ext4 last afternoon.

You received this program iso ...
 could be used in a cd ..
 dc3dd With dcfldd easy even for beginners are available. 
 Is recommended.
[http://partedmagic.com/](http://partedmagic.com/)

In some cases, the
dd may be needed by low-level format.
Can take advantage of an error during complex

It takes a long time running.         HDD sata2~sata3 PC
Connect directly to the pc.
If you cancel in the middle will die HDD.
Warning
dd..  The risk is too great.
Do not use as much as possible.

---

### Post by rubylaser on 2012-06-25
> **oklokl said:**
> 
If you cancel in the middle will die HDD.
Warning
dd..  The risk is too great.
Do not use as much as possible.

I'm not sure what this means.  dd will not kill a hard drive.  You may risk overwriting data if you don't know what you are doing, but you certainly won't kill it.

To the OP, although you say the disk passes a smart test, can you run a long test on it and then post the results back her?  This sounds like a bad controller, USB cable, or disk more than a filesystem issue (hardware).  Please run this from the terminal

```
smartctl -t long /dev/sdd
```

^ this will take a while to complete.  Once it's done, can you run this and paste the output back here? Thanks.

```
smartctl -a /dev/sdd
```

Also, all WD enclosures can be opened.  If this is the same model as yours, [here's how you take it apart]("http://www.youtube.com/watch?v=iwGHiMaIxD8"). Their enclosures all pop together.

---

