---
title: "Unsuable Partition"
date: 2009-12-01
forum: General Help
---

### Post by earfer on 2009-12-01
Hey everyone, yes i know that this question has popped up many many times. But i would like to be sure about it.

I have a Vista computer installed now. I "Shrinked" my "D:" so that i can have room for Ubuntu 9.10. But when i go up to step 5. It says that the partition is "Unusable" 

Everytime i click on it and then click "Forward". It says...

```
No root file system is defined
Please correct this from the partitioning
```I really dont know what to do. Also i had a rea around and it said that maxium of...partitions is 4? and yes i do have 4. But if thats the problem then how do i merge them together.

```
/dev/sda
  /dev/sda1 [NTFS]
  /dev/sda2 [NTFS]
  /dev/sda3 [NTFS]
  unusable  -
  /dev/sda4 [NTFS]
```_Summery:_
i) Why cant i use the partition.
ii) If the 4 partition i the problem how do i merge one together?

Thanks in advance~~

---

### Post by ibuclaw on 2009-12-01
You cannot "merge" filesystems.

What do you have in the contents of each filesystem?
What you can do instead is backup the data in one or two of the already existing filesystems, then delete and create an [Extended Partition]("https://help.ubuntu.com/community/HowtoPartition/ExtendedPartition") in their place to hold many logical filesystems.

Regards
Iain

---

### Post by earfer on 2009-12-01
> **tinivole said:**
> You cannot "merge" filesystems.

What do you have in the contents of each filesystem?
What you can do instead is backup the data in one or two of the already existing filesystems, then delete and create an [Extended Partition]("https://help.ubuntu.com/community/HowtoPartition/ExtendedPartition") in their place to hold many logical filesystems.

Regards
Iain

Thank you for the reply. But what do you mean by..."What do you have in the contents of each filesystem?" do mean what i have in each and every drive? if that is so. then there are 2 drive that i dont know of that is...sda 1 and sda 4.

sda 2 is my C: drive primary and sda 3 is my D: drive.
Plz explain further....

---

### Post by ibuclaw on 2009-12-02
> **earfer said:**
> Thank you for the reply. But what do you mean by..."What do you have in the contents of each filesystem?" do mean what i have in each and every drive? if that is so. then there are 2 drive that i dont know of that is...sda 1 and sda 4.

sda 2 is my C: drive primary and sda 3 is my D: drive.
Plz explain further....

I meant directory listings.

OK, so sda1 is unknown (possible recovery partition for Vista).
sda2 is C: (If I recall correctly, that is the system partition).
sda3 is D: (So you keep all your music/data in there?)

What files are kept inside sda4 then?
If empty, delete it and create an Extended partition - with an Ext4 and Swap partition inside.

So your partition structure will now look like this:
```

/dev/sda
  /dev/sda1 [NTFS]
  /dev/sda2 [NTFS]
  /dev/sda3 [NTFS]
  /dev/sda4 [Extended] {
    /dev/sda5 [EXT4]
    /dev/sda6 [SWAP]
  }

``` 
You can do that in gparted, have a look at the [Basic Guide to Partitioning.]("https://help.ubuntu.com/community/HowtoPartition")

Once sorted, when asked how in the Ubuntu installer, select "Advanced" and then set the Ext4 partition as the root filesystem **/**

Regards
Iain

---

### Post by earfer on 2009-12-03
> **tinivole said:**
> I meant directory listings.

OK, so sda1 is unknown (possible recovery partition for Vista).
sda2 is C: (If I recall correctly, that is the system partition).
sda3 is D: (So you keep all your music/data in there?)

What files are kept inside sda4 then?
If empty, delete it and create an Extended partition - with an Ext4 and Swap partition inside.

So your partition structure will now look like this:
```

/dev/sda
  /dev/sda1 [NTFS]
  /dev/sda2 [NTFS]
  /dev/sda3 [NTFS]
  /dev/sda4 [Extended] {
    /dev/sda5 [EXT4]
    /dev/sda6 [SWAP]
  }

``` 
You can do that in gparted, have a look at the [Basic Guide to Partitioning.]("https://help.ubuntu.com/community/HowtoPartition")

Once sorted, when asked how in the Ubuntu installer, select "Advanced" and then set the Ext4 partition as the root filesystem **/**

Regards
Iain

Ahh...

- Sda 1 is "Eisa Configuration" (like you said might be recovery)
- Sda 2 is my C: "Primary, Has Vista, Everything"
- Sda 3 is my D: "Wanting to shrink it and use the partition made to be ubuntu. but cant because i cant format it. it turns dynamic and drive doesnt support dynamic for some reason..." (Primary before then i stupidly made it Logical cant make it primary again T__T)

- Sda 4 is "Eisa Configuration" (Yep same as Sda 1)

---

### Post by ibuclaw on 2009-12-03
> **earfer said:**
> Ahh...

- Sda 1 is "Eisa Configuration" (like you said might be recovery)
- Sda 2 is my C: "Primary, Has Vista, Everything"
- Sda 3 is my D: "Wanting to shrink it and use the partition made to be ubuntu. but cant because i cant format it. it turns dynamic and drive doesnt support dynamic for some reason..." (Primary before then i stupidly made it Logical cant make it primary again T__T)

- Sda 4 is "Eisa Configuration" (Yep same as Sda 1)

Interesting ...

Was that the structure of the filesystem when you bought the Laptop/Desktop ?

---

### Post by Grey Seal on 2009-12-03
My current OS is FS 2.0.0.6 which will not download GNU library files, so I am unable to upgrade. 

I have tried to partition and download new OS but cannot create enough room in the new partition. The Kate files are most important. Will Ubuntu erase all? Am I better off copying the Kate docs and browsers bookmarks and simply starting over?

Thanks,
GS

---

### Post by earfer on 2009-12-03
> **tinivole said:**
> Interesting ...

Was that the structure of the filesystem when you bought the Laptop/Desktop ?

Yeh it was all like that when i brought it.

Its not the same as other systems ive seen. so yeh working about is kinda hard..

---

