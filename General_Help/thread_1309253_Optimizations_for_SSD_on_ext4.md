---
title: "Optimizations for SSD on ext4"
date: 2009-11-01
forum: General Help
---

### Post by kentcb on 2009-11-01
Hi there,

My setup:
[LIST]
[*]Ubuntu 9.10
[*]ext4
[*]160GB Intel X25-M Gen II SSD
[/LIST]

I'm wondering whether 9.10 is optimal out of the box for SSDs, or whether I should modify configuration to reduce writes etc.

Can anyone comment on this?

Thanks,
Kent

---

### Post by goofee on 2009-11-01
You have to optimize. I did this with my OCZ Vertex. Once done though it's blazingly fast!

I used this guide, most should work with your Intel:

[http://www.ocztechnologyforum.com/forum/showthread.php?t=54379](http://www.ocztechnologyforum.com/forum/showthread.php?t=54379)

---

### Post by andrewabc on 2009-11-01
I have 60gb ocz vertex. All I did was align it to 512kb. I assume intel has same size.

Do the swap disable (not disable but make kernel not use swap much) thing assuming you rarely run out of ram to prevent it from writing to swap unless you absolutely run out of ram. Ubuntu rarely writes to swap for me before ever tweaking it anyways.

Do you have a hard drive attached as well? Make sure all your downloads and data (music/video) go there to have less writes on SSD. Keep SSD mostly for OS+programs+daily used files.

---

### Post by apocalypse80 on 2009-11-01
For trim get hdparm 9.27 [_from this ppa_]("https://launchpad.net/~bdrung/+archive/ppa") and use the contained "wiper" - the ocz thread contains more details.
It works for intel drives too, however I'm not sure if it will work without the (withdrawn) intel trim-enabled firmware.

To verify that you're achieving optimal performance you can run a very quick benchmark.
Install iozone3 and run the following

```
apocalypse@nikos-laptop:~$ iozone -I -a -s 16M -r 4 -i 0 -i 2

.......

                                                 random  random
   KB  reclen   write rewrite    read    reread    read   write
16384       4   54584   59750                     18619   59767
```

The interesting number is the last one, 4k random writes.
On a trimmed and aligned intel G2 it will be ~55MB/s, fail on either count and it will be much lower.

If you're nervous about ssd wear from writes you can monitor the use of the ssd using iotop and iostat (contained in sysstat).

Oh and keep in mind that some of the proposed optimizations for ssds are targeting netbook ssds (slooooooow).
As a result most will have little to no effect on a g2's performance.
Align, trim, maybe use noatime and you're golden.

---

### Post by andrewabc on 2009-11-01
You need TRIM enabled firmware in order to use TRIM.

My output of your iozone command:

```
	Run began: Sun Nov  1 12:02:42 2009

	O_DIRECT feature enabled
	Auto Mode
	File size set to 16384 KB
	Record Size 4 KB
	Command line used: iozone -I -a -s 16M -r 4 -i 0 -i 2
	Output is in Kbytes/sec
	Time Resolution = 0.000001 seconds.
	Processor cache size set to 1024 Kbytes.
	Processor cache line size set to 32 bytes.
	File stride size set to 17 * record size.
                                                            random  random    bkwd   record   stride                                   
              KB  reclen   write rewrite    read    reread    read   write    read  rewrite     read   fwrite frewrite   fread  freread
           16384       4   44632   42865                     24719   11304                                                          

iozone test complete.
                                                         

```

Dunno if those are good numbers. My random read is a bit higher, but random write is much lower than yours.
OCZ vertex 60gb firmware 1.3
I can't update firmware to garbage collection because my computer doesn't support changing to IDE mode. So have to hook it up to a friends computer.

---

### Post by apocalypse80 on 2009-11-01
> **andrewabc said:**
> Dunno if those are good numbers.

If you can't find comparable iozone numbers from other vertex users, you can try looking at (much easier to find) results from the windows benchmark crystaldiskmark.
Iozone and crystal agree pretty much completely for me (see attachment), including the difference they saw from trim (both went from ~35MB/s to ~55MB/s 4k random writes).

As for trim, I did what was proposed in the karmic-trim thread.
Installed hdparm 9.27, edited the wiper script to remove the verification question and created a daily cron job for it.
It's triggered once so far and all seems fine.
But I do have that withdrawn firmware.

---

### Post by andrewabc on 2009-11-01
Those programs don't run in ubuntu :P
I've ran them on my winxp hard drive before.

I have winxp installed on my hard drive, but winxp doesn't even recognize linux filesystems (on hard drive) let alone my SSD.

I do expect your intel 160gb to be much faster than my 60gb vertex. Every benchmark/review shows it (especially 4kb random write). If I had a 120gb vertex my numbers would be improved a bit.

---

### Post by apocalypse80 on 2009-11-01
> **andrewabc said:**
> Those programs don't run in ubuntu :P

Well yeah, but it's *much* easier to google for their results.
In my case I verified my diskmark (ntfs) vs that of other intel g2 users (ntfs) vs my iozone (ext4) - they all agree, which is good.
Looking for iozone results from other g2 users proved futile.

You can just skip one step and compare your iozone with the diskmark of other vertex users.
For the full comparison something like "iozone -I -a -s 100M -r 4 -r 512 -r 8192 -i 0 -i 1 -i 2" should work.

EDIT: some fast googling gave this for a 60GB vertex - [http://www.hardforums.com/showpost.php?p=1034828358&postcount=11](http://www.hardforums.com/showpost.php?p=1034828358&postcount=11)

---

### Post by andrewabc on 2009-11-01
[OCZ Vertex SATA 2.0 60GB SSD](http://www.phoronix.com/scan.php?page=article&item=ocz_vertex_ssd&num=4)
Phoronix uses iozone to benchmark. But no simple read/write and 4kb read/write.

4kb in crystaldisk from google:
[http://www.cdrinfo.com/Sections/Reviews/Print.aspx?ArticleId=25610](http://www.cdrinfo.com/Sections/Reviews/Print.aspx?ArticleId=25610)
Near bottom of article.

Thanks for the google search.
So my 4kb speeds are around the same. Probably differences due to software/filesystem/OS etc.

---

