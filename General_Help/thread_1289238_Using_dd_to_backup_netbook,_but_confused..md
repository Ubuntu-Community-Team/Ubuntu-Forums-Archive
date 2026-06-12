---
title: "Using dd to backup netbook, but confused."
date: 2009-10-12
forum: General Help
---

### Post by Subban on 2009-10-12
I am wanting to backup my Acer Aspire One to an image file. I have booted from a live USB not from the internal SSD and then I used :

```
dd if=/dev/sda of=/media/Elements/backup.img
```

/dev/sda is the internal SSD, which I checked with **sudo fdisk -l**
/media/Elements is a separate USB 2.5" HD with plenty of space for a backup.

When dd completes and the in/out figures match, but my img file is only 4.0GB rather than the 16GB I epected from dd doing a bit for bit image. The internal SSD is 16GB and so I expected a 16GB file, or does it only bit for bit actual used space?

I tried to use **cmp** to check the image file, it didn't say the file was error free or anything, just:
"EOF /media/Elements/backup.img"

Does that mean it reached the EOF and no errors were reported?

---

### Post by Giblet5 on 2009-10-12
Verify that dd reads the entire SSD: ```
dd if=/dev/sda of=/dev/null bs=1M
```

You should see > 15000 in/out. If not, you need to ask yourself: "Where'd I get this '16G' SSD that only allows 4G to be read..."

How big any flash memory device appears is controlled by the SSD's controller. A person of low moral character can trick a 2G USB stick into looking exactly like a 16G stick. Fdisk will work for that whole 16G, but you won't succeed in writing AND reading back any more than 2G.

---

### Post by Subban on 2009-10-12
> **Giblet5 said:**
> Verify that dd reads the entire SSD: ```
dd if=/dev/sda of=/dev/null bs=1M
```

You should see > 15000 in/out. If not, you need to ask yourself: "Where'd I get this '16G' SSD that only allows 4G to be read..."

How big any flash memory device appears is controlled by the SSD's controller. A person of low moral character can trick a 2G USB stick into looking exactly like a 16G stick. Fdisk will work for that whole 16G, but you won't succeed in writing AND reading back any more than 2G.

I am about to pop out for a couple hours now but I will try adding the **bs=1M** as soon as I get back in.

The 16GB SSD is factory fitted in my Acer Aspire One, I am as certain as I can bet that it is a genuine 16GB not compressed.

Can I assume then that the dd image file should have been 16GB regardless of how empty or full the SSD is?

---

### Post by zer0x on 2009-10-12
I think the problem is that your target filesystem does not support files greater than 4GB, I assume its FAT32?

Yes, the image should be the size of your source block device, even if its totally blank :D

bs=1M should decrease the time it takes to read the image, the default bs on dd is 512bytes!

HTH

zer0x

---

### Post by Subban on 2009-10-12
> **zer0x said:**
> I think the problem is that your target filesystem does not support files greater than 4GB, I assume its FAT32?

zer0x

Ahhh of course, I must have had a senior moment to forget that, it is of course a fat32 external drive I am copying to. I shall dump it over the network to my main machine.... overnight ;)

Thank you to you both.

---

### Post by zer0x on 2009-10-12
It is one of those stupid limitations everyone tends to forget :D

Glad to have helped! :)

---

### Post by Giblet5 on 2009-10-12
> **zer0x said:**
> I think the problem is that your target filesystem does not support files greater than 4GB, I assume its FAT32?

Yes, the image should be the size of your source block device, even if its totally blank :D

bs=1M should decrease the time it takes to read the image, the default bs on dd is 512bytes!

HTH

zer0x


+1: didn't think of FAT target... That's probably the problem.

It won't increase it dramatically on an SSD.

The dd default is BLKSIZ from /usr/include/sys/param.h, but yeah, that's usually 512B.

Fastest is bs=64k on most mechanical drives and OCZ's SSD drives. Older drives do better with 32k.


What *I* do:
```
## Fill free space with zeroes...
cd /;dd if=/dev/zero of=zeroes.dat bs=64k;rm -f zeroes.dat

## Image the drive, compressing the easy stuff (like zeroes)
dd if=/dev/sda bs=64k | gzip -c1 > /media/MyBook/sda-image.gz
```

---

