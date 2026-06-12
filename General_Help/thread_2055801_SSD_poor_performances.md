---
title: "SSD poor performances"
date: 2012-09-10
forum: General Help
---

### Post by Trompette83 on 2012-09-10
Hello,

I have a new PC (Asrock 970 Extreme4, FX-8120, 8GB RAM, SSD Samsung 840 128GB) with Ubuntu 12.04.
I did the following:
Mounting partitions with the options noatime and discard
Minimise writes with tpmfs in RAM
Enable Automatic TRIM => Tested OK
Change I/O Scheduler => Tested OK
Change swappiness

SSD firmware is up-to-date
M/B firmware is up-to-date

Now I test the SSD performance according to 
[https://wiki.archlinux.org/index.php/SSD_Benchmarking]("https://wiki.archlinux.org/index.php/SSD_Benchmarking")

My results are:
> sudo hdparm -Tt /dev/sda
/dev/sda:
 Timing cached reads:   9036 MB in  2.00 seconds = **4521.54 MB/sec**
 Timing buffered disk reads: 1420 MB in  3.00 seconds = **473.13 MB/sec**

> dd if=tempfile of=/dev/null bs=1M count=1024
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB) copied, 0.208829 s, **5.1 GB/s**

In the benchmark and other SDD tests, performances are much better:
> # hdparm -Tt /dev/sda
Timing cached reads:   22130 MB in  2.00 seconds = **11080.54 MB/sec**
Timing buffered disk reads: 1500 MB in  3.00 seconds = **499.38 MB/sec**
> # dd if=tempfile of=/dev/null bs=1M count=1024
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB) copied, 0.119695 s, **9.0 GB/s**

Any idea why I have these so poor performances?
Many thanks.

---

### Post by Cheesemill on 2012-09-10
What makes you think that you have poor performance?

It all looks good to me.

---

### Post by Trompette83 on 2012-09-10
With hdparm
Timing cached reads: 9036 MB in 2.00 seconds = 4521.54 MB/sec
compared to
Timing cached reads: 22130 MB in 2.00 seconds = 11080.54 MB/sec

with dd
1073741824 bytes (1.1 GB) copied, 0.208829 s, 5.1 GB/s
compared to
1073741824 bytes (1.1 GB) copied, 0.119695 s, 9.0 GB/s

This is about half speed

---

### Post by shreepads on 2012-09-10
First have you done the partition alignment correctly and turned off journalling, assuming you have used ext4 (see [https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives))

Next have you run the benchmark 4-5 times as recommended. Does the System Monitor report paged memory being used or not?

Third, I assume you're refering to the benchmarks posted on the Arch wiki for the Samsung 830 (not 840)... Without knowing the specs of the system used to create that benchmark not really possible to compare the two..

Lastly, these are measures of sequential read access, which isn't IMHO the point of getting a SSD...

---

### Post by Trompette83 on 2012-09-10
1a - When installing I had to use gparted as palimpsest gave me the error for aligment. So aligment is good.

1b - fstab
# / was on /dev/sda1 during installation
UUID=59d33dc7-4511-44f4-918a-1bbdb71580b4 / ext4 noatime,discard,errors=remount-ro 0 1
# /home was on /dev/sda3 during installation
UUID=0c91a5c5-ed6e-4853-9545-c4f0f03aa081 /home ext4 noatime,discard,defaults 0 2

Next-a - I run hdparm and dd lot of time, results are almost the same

Next-b - System Monitor shows 1.2 GiB (15.3%) of 7.8 GiB
I don't know how to see paged memory.
BTW, why I have only 7.8 GiB as lshw see 8 GiB.

3 - Typo Samsung 830
Connected to a SATA3. This is half the speed and looks a huge gap for me.
Is there other benchmak programs in UBUNTU?
Where can I compare?

---

### Post by Statia on 2012-09-10
I think you are believing the speeds the manufacturer advertises with too much.
I have an SSD too, it's advertised with reads of 550MB/sec, I am quite content to get around 400MB/sec.

---

### Post by Trompette83 on 2012-09-10
Could you try
sudo hdparm -Tt /dev/sda
and
dd as describe in the link
To clear the cache you will have instead to write
sudo sync; echo 3 | sudo tee /proc/sys/vm/drop_caches

Let me know

---

### Post by Statia on 2012-09-10
My SSD is a Corsair Force GT 60GB. Corsair claims reads up to 555 MB/s.

```
# hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   11604 MB in  2.00 seconds = 5805.31 MB/sec
 Timing buffered disk reads: 710 MB in  3.01 seconds = 236.06 MB/sec

``````
root@quokka:/# dd if=/dev/zero of=tempfile bs=1M count=1024 conv=fdatasync,notrunc
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB) copied, 4.26096 s, 252 MB/s
root@quokka:/# sync
root@quokka:/# echo 3 > /proc/sys/vm/drop_caches
root@quokka:/# dd if=tempfile of=/dev/null bs=1M count=1024
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB) copied, 4.24495 s, 253 MB/s
root@quokka:/# dd if=tempfile of=/dev/null bs=1M count=1024
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB) copied, 0.168984 s, 6.4 GB/s

```

---

### Post by Trompette83 on 2012-09-10
It looks close to mine.
I don't knon how they can have this high speed.

Thank you for the test anyway.

Do you have an answer for the 7.8 GiB RAM?

---

### Post by Statia on 2012-09-10
> **Trompette83 said:**
> It looks close to mine.
I don't knon how they can have this high speed.

Do you have an answer for the 7.8 GiB RAM?

They probably run their benchmarks in highly optimised conditions on the fastest hardware available, getting results that are far distant from real world use.

As for your RAM, probably your BIOS reserving some memory for hardware, I wouldn't worry about it.
Same on my system with 8GB RAM:

```
$free -m
             total       used       free     shared    buffers     cached
Mem:          7968       2027       5941          0         35        662
-/+ buffers/cache:       1329       6639
Swap:         7812          0       7812
```

---

### Post by Trompette83 on 2012-09-10
Thank for this answer.

I found this [link]("http://www.unix.com/unix-dummies-questions-answers/163209-difference-between-buffered-disk-reads-cached-reads.html") very informative on hdparm.

In fact the "Timing cached reads" (hdparm -T) are not a SSD value but a Linux buffer speed value.

Good to know!

---

### Post by Cheesemill on 2012-09-10
> **Trompette83 said:**
> Thank for this answer.

I found this [link]("http://www.unix.com/unix-dummies-questions-answers/163209-difference-between-buffered-disk-reads-cached-reads.html") very informative on hdparm.

In fact the "Timing cached reads" (hdparm -T) are not a SSD value but a Linux buffer speed value.

Good to know!
Indeed.

That's why I though there was nothing wrong with your original read speeds of 473MB/s and 499MB/s. Those are some very good speeds.

---

### Post by dcstar on 2012-09-11
> **Trompette83 said:**
> Thank for this answer.

I found this [link]("http://www.unix.com/unix-dummies-questions-answers/163209-difference-between-buffered-disk-reads-cached-reads.html") very informative on hdparm.

In fact the "Timing cached reads" (hdparm -T) are not a SSD value but a Linux buffer speed value.

Good to know!

If you no longer have a "problem", then Mark The Thread.

---

### Post by enjoy10 on 2013-04-08
@[**[COLOR=#000000]Trompette83[/COLOR]**]("http://ubuntuforums.org/member.php?u=347275")
[COLOR=#000000][/COLOR]
[COLOR=#000000]"Enable Automatic TRIM => Tested OK"
is it meaning you did this test ? [https://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking](https://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking)
[/COLOR]
thanks

---

### Post by stilllife on 2013-04-15
I would like continue this thread because I have a issue that seems worse to me. I have the same SSD Samsung 840 Pro but hdparm gives me only a read speed of 269MB when I thought to get around 400-500. 

I tried 3 times different partitions with no luck and I put 1MB of space at the beginning of the disk. I also added noatime and trim support but I still have to test if trim works. I checked the SATA version and it seems that the disk is properly using a SATA III connector but I am still not sure because I see multiple SATA controllers, one of them seems to be limited to SATA 3Gbp (but I hope is the CD driver)

Then if this can be a SSD firmware issue I would like to know how to update on linux since I tried the Samsung .iso but is not bootable

Anyone could please lead me to the correct troubleshooting procedure? thanks a lot

---

### Post by stilllife on 2013-04-16
Solved!! The problem was the SATA cable, to much twisted to fit in the motherboard. Relaxing the cable brings me the speed of 540MB
To check if you have this problem a good place was 
sudo dmesg | grep -iE '(ata|ahci)'
there I found an error that disappears with a good cable
Hope this helps

---

