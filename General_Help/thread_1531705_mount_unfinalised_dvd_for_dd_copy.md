---
title: "mount unfinalised dvd for dd copy"
date: 2010-07-15
forum: General Help
---

### Post by RichLouth on 2010-07-15
Hello,

I have a dvd used as a mini-DVD for a camcorder. The disc is unable to be finalised for some unknown reason (I have it plugged in when I'm trying to finalise). I think the disc is corrupt in some way.

When I say finalised I don't mean iso or udf finalised. This is a dvd formatted with VOBs with the intention of being played back in a dvd player. I think this uses a different filesystem from iso and udf.

When in the camcorder I am able to see and play the videos. So I know that the video data itself is not corrupted.

I want to copy the disc to another disc in the hopes that the new disc can be finalised by the camcorder.

I've tried:
```
dd if=/dev/dvd of=~/test.img
```

but I get:
```
dd: reading `/dev/dvd': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.00375996 s, 0.0 kB/s
```

I've also tried dd_rescue but I get:
```
dd_rescue: (fatal): open "if=/dev/dvd" failed: No such file or directory
```

It looks to me that my computer "thinks" it is a blank disc because it isn't finalised for DVD playback. So I'm looking for a way to mount it as a dvd with vobs (not mount it iso or udf), whatever method is required for that. Hopefully then dd will work.

As a little extra info I've run:
```
dvd+rw-mediainfo /dev/dvd
```

And I get:
```
INQUIRY:                [ASUS    ][DRW-2014L1T     ][1.02]
GET [CURRENT] CONFIGURATION:
 Mounted Media:         11h, DVD-R Sequential
 Media ID:                 AML      
 Current Write Speed:   4.0x1385=5540KB/s
 Write Speed #0:        4.0x1385=5540KB/s
 Speed Descriptor#0:    00/713951 R@4.0x1385=5540KB/s W@4.0x1385=5540KB/s
READ DVD STRUCTURE[#10h]:
 Media Book Type:       00h, DVD-ROM book [revision 0]
 Legacy lead-out at:    714560*2KB=1463418880
READ DVD STRUCTURE[#0h]:
 Media Book Type:       25h, DVD-R book [revision 5]
 Last border-out at:    2045*2KB=4188160
READ DISC INFORMATION:
 Disc status:           appendable
 Number of Sessions:    1
 State of Last Session: incomplete
 "Next" Track:          1
 Number of Tracks:      5
READ TRACK INFORMATION[#1]:
 Track State:           reserved incremental
 Track Start Address:   0*2KB
 Next Writable Address: 0*2KB
 Free Blocks:           12272*2KB
 Track Size:            12272*2KB
READ TRACK INFORMATION[#2]:
 Track State:           complete incremental
 Track Start Address:   12288*2KB
 Free Blocks:           0*2KB
 Track Size:            256*2KB
 Last Recorded Address: 12543*2KB
READ TRACK INFORMATION[#3]:
 Track State:           complete incremental
 Track Start Address:   12560*2KB
 Free Blocks:           0*2KB
 Track Size:            665120*2KB
READ TRACK INFORMATION[#4]:
 Track State:           complete incremental
 Track Start Address:   677696*2KB
 Free Blocks:           0*2KB
 Track Size:            32*2KB
READ TRACK INFORMATION[#5]:
 Track State:           invisible incremental
 Track Start Address:   677744*2KB
 Next Writable Address: 677744*2KB
 Free Blocks:           36208*2KB
 Track Size:            36208*2KB
READ CAPACITY:          0*2048=0

```

So I can see that there are tracks on the DVD. These are what the camcorder is presumably able to read. And I'd like to get Linux reading them :)

I tried:
```
dd seek=25165824 count=524288 if=/dev/dvd of=/home/richard/test.img

```

i.e. seeking to track 2, counting sizeof track 2. With no luck:
```
dd: reading `/dev/dvd': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.00151712 s, 0.0 kB/s

```

Again, I think I need to mount it as a vob dvd.

Thanks to all

---

