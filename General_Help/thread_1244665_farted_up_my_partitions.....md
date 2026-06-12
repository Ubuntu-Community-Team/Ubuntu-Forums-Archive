---
title: "farted up my partitions...."
date: 2009-08-19
forum: General Help
---

### Post by blur xc on 2009-08-19
Hey, I recently repartitioned my drive-  I should have 4 partitions, Vista, Ubuntu, Home, and Swap...  But, somehow I ended up with 5- one 10gb blank, unformatted partition.  I don't know how I managed to do that, but is it fixable?  I mean, it's only 10gb, and I probably will never fill this drive up (it's not used for mass storage, that's what the external drive(s) are for)...

It just irks me when I do an fdisk -l

Thanks,
BM

---

### Post by running_rabbit07 on 2009-08-19
Can you give me a screenshot with GParted running? 

Basically, you will just need to boot the LiveCD and use the partition editor to expand one of the partitions that is beside the unallocated space.

---

### Post by blur xc on 2009-08-19
> **running_rabbit07 said:**
> Can you give me a screenshot with GParted running? 

Basically, you will just need to boot the LiveCD and use the partition editor to expand one of the partitions that is beside the unallocated space.

Yeah, I'm not home right now, but I understand what you are saying...

I need to get the live cd in anyway.  I made the home partition, but have not yet moved my home folders over.  I guess I'm just a little lazy...


Thanks,
BM

---

### Post by running_rabbit07 on 2009-08-19
If you look at this screenshot, if I wanted to make that unallocated section into one of the partitions, I could click on sda6 or sda7 and resize it to fill the gap. That easy.

---

### Post by running_rabbit07 on 2009-08-19
> **blur xc said:**
> Yeah, I'm not home right now, but I understand what you are saying...

I need to get the live cd in anyway.  I made the home partition, but have not yet moved my home folders over.  I guess I'm just a little lazy...


Thanks,
BM

I know that feeling. If you are going to resize an NTFS partition, you can do it within Windows while it is running.

Either way, if you want to post that shot to get advice on it, we don't mind helping.

---

### Post by blur xc on 2009-08-19
> **running_rabbit07 said:**
> I know that feeling. If you are going to resize an NTFS partition, you can do it within Windows while it is running.

Either way, if you want to post that shot to get advice on it, we don't mind helping.

A'ight- here's the screenie...  

I looks like I should be able to pull my home partition over and make it 10gb bigger...

Thanks,
BM

---

### Post by running_rabbit07 on 2009-08-19
> **blur xc said:**
> A'ight- here's the screenie...  

I looks like I should be able to pull my home partition over and make it 10gb bigger...

Thanks,
BM

Yeah, that would be best. I doubt you would really want almost 20 gigs of swap.

---

### Post by blur xc on 2009-08-24
Thanks for all the help- I finally got around to doing this over the weekend, as well as moving my home folders over to sda3.

The partition fixing was successful;  I had issues w/ home folder move, but that's a topic for another thread.

BM

---

