---
title: "Can't enable TRIM support in 10.10"
date: 2011-01-13
forum: General Help
---

### Post by SkylinesSuck on 2011-01-13
I followed this tutorial  [http://lightrush.ndoytchev.com/random-1/howtoconfigureext4toenabletrimforssdsonubuntu](http://lightrush.ndoytchev.com/random-1/howtoconfigureext4toenabletrimforssdsonubuntu)  to enable my TRIM support and now my fstab looks like this:

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=c96b314c-24fe-4380-9992-fe47b9f55844 /               ext4    discard,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=bf21bb42-7bd6-458d-93ef-106e27e1d436 none            swap    sw              0       0but when I follow the second half of the tutorial [http://lightrush.ndoytchev.com/random-1/checkiftrimonext4isenabledandworking](http://lightrush.ndoytchev.com/random-1/checkiftrimonext4isenabledandworking)  to check and make sure it's working I don't get all zeros like I'm supposed.  I tried waiting a while like I saw in another tutorial as well and check it again.. Still random numbers and no zeros.  Am I doing something wrong in fstab?

---

### Post by SkylinesSuck on 2011-01-13
> root@Chris-Laptop:~# dd if=/dev/urandom of=tempfile count=100 bs=512k oflag=direct 
100+0 records in
100+0 records out
52428800 bytes (52 MB) copied, 7.16798 s, 7.3 MB/s
root@Chris-Laptop:~# hdparm --fibmap tempfile

tempfile:
 filesystem blocksize 4096, begins at LBA 2048; assuming 512 byte sectors.
 byte_offset  begin_LBA    end_LBA    sectors
           0   43058176   43060223       2048
     1048576   43192320   43194367       2048
     2097152   43235328   43239423       4096
     4194304   43460608   43554815      94208
root@Chris-Laptop:~# hdparm --read-sector 43058176 /dev/sda

/dev/sda:
reading sector 43058176: succeeded
88c3 1c9e c951 8d7a e29e 6d42 c020 0bb2
70d1 4a57 70f2 ad61 e50a ca0f 8578 db35
805d a95f bfe3 a142 75cb 9e7d 8a69 3b97
f48d 9aa8 fddc bd67 043b f291 8828 f1ad
7261 e2b3 e972 e1e4 2f6b ea21 29c9 1af5
3682 95b4 d1a8 d71a eff2 ff21 e6d8 06d3
ff7a d84a dbb4 aad4 e5fa 2797 7113 097c
c45e c2f6 941f 729f 68fd 5a1b a6b7 54a5
5113 afc3 106a a8e2 f33c f6af c7b1 6383
d82f 0ca1 6f8f 733b af93 19c5 4367 b626
1b32 19ec 6d06 20fc b3e9 c04f e0a7 a49d
13ab 5ef7 6b0f 9a6b 2978 8f5a 304e fb7c
e19c baac 8a5b 315c c822 cb20 a2bb 8b23
7067 481f aeec 6a88 4da7 42a4 2a0c 3d15
9ef7 f4b6 e795 b53e 658a ba99 10a7 805a
d538 f2fb 7a41 b748 a4dc a451 dab3 855c
16f9 b0a6 15ce 525a f966 ebdb 35f9 2f41
b367 f598 2881 9a95 49e1 b12d ac17 2815
c841 f19b 075e 0a71 a0bd 5ce7 1c9b e466
f2e1 e82c 72df 1d29 2a21 d553 8d4a afe2
fc79 c852 cab8 5f3f 1000 554e 0339 e50c
f51d faa4 82cb 50f9 e55f dc95 a714 3e75
c561 ad7f 09fd 065b 154f dd8d e11b feb7
12b0 5a4b f584 14fe 092d 033f 6759 4bae
a7cb b6da 8ef2 a023 d795 c29e db02 caf9
2402 694f 8124 be49 4d05 b4e5 f8db b709
9f79 1e51 daaf b742 b6df 0f88 d41d 1c94
0551 8c1a 3f01 8662 f3bc 11c2 a144 84e3
0128 9168 a666 4fd2 7550 c39e 6168 e818
faed 8c9c 4dd5 5d83 1aa9 86b8 67ec 8ded
b5d1 ff2b 1aed 41f8 a1a1 3cb6 bcc1 17dc
2d59 85bc 6ccb 0c46 252d 14b7 dcd9 d969
root@Chris-Laptop:~# rm tempfile
root@Chris-Laptop:~# sync
root@Chris-Laptop:~# hdparm --read-sector 43058176 /dev/sda

/dev/sda:
reading sector 43058176: succeeded
88c3 1c9e c951 8d7a e29e 6d42 c020 0bb2
70d1 4a57 70f2 ad61 e50a ca0f 8578 db35
805d a95f bfe3 a142 75cb 9e7d 8a69 3b97
f48d 9aa8 fddc bd67 043b f291 8828 f1ad
7261 e2b3 e972 e1e4 2f6b ea21 29c9 1af5
3682 95b4 d1a8 d71a eff2 ff21 e6d8 06d3
ff7a d84a dbb4 aad4 e5fa 2797 7113 097c
c45e c2f6 941f 729f 68fd 5a1b a6b7 54a5
5113 afc3 106a a8e2 f33c f6af c7b1 6383
d82f 0ca1 6f8f 733b af93 19c5 4367 b626
1b32 19ec 6d06 20fc b3e9 c04f e0a7 a49d
13ab 5ef7 6b0f 9a6b 2978 8f5a 304e fb7c
e19c baac 8a5b 315c c822 cb20 a2bb 8b23
7067 481f aeec 6a88 4da7 42a4 2a0c 3d15
9ef7 f4b6 e795 b53e 658a ba99 10a7 805a
d538 f2fb 7a41 b748 a4dc a451 dab3 855c
16f9 b0a6 15ce 525a f966 ebdb 35f9 2f41
b367 f598 2881 9a95 49e1 b12d ac17 2815
c841 f19b 075e 0a71 a0bd 5ce7 1c9b e466
f2e1 e82c 72df 1d29 2a21 d553 8d4a afe2
fc79 c852 cab8 5f3f 1000 554e 0339 e50c
f51d faa4 82cb 50f9 e55f dc95 a714 3e75
c561 ad7f 09fd 065b 154f dd8d e11b feb7
12b0 5a4b f584 14fe 092d 033f 6759 4bae
a7cb b6da 8ef2 a023 d795 c29e db02 caf9
2402 694f 8124 be49 4d05 b4e5 f8db b709
9f79 1e51 daaf b742 b6df 0f88 d41d 1c94
0551 8c1a 3f01 8662 f3bc 11c2 a144 84e3
0128 9168 a666 4fd2 7550 c39e 6168 e818
faed 8c9c 4dd5 5d83 1aa9 86b8 67ec 8ded
b5d1 ff2b 1aed 41f8 a1a1 3cb6 bcc1 17dc
2d59 85bc 6ccb 0c46 252d 14b7 dcd9 d969
root@Chris-Laptop:~# 


Here's the checking that doesn't go so well.

---

### Post by SkylinesSuck on 2011-01-15
bump for a little guidence

---

### Post by stackcheese on 2011-01-19
I'm having the same problem with 10.10 I've been able to get Trim to work on 10.04 with a Samsung drive, however, with 10.10 and  a Kingston SNV125-S2BD drive I'm getting the same problem you are.

what drive are you using?

---

### Post by SkylinesSuck on 2011-01-19
I've got a 64gb Kinston SNV4255-S2 drive firmware C09112a6.

I wonder since they are both Kinstons if the brand or firmware has something to do with it.  I'm going to look and see if there is a firmware update for it here in a sec.

---

### Post by SkylinesSuck on 2011-01-19
So after some searching, it appears Kinston (at least with my model) saw fit not to provide us an updated firmware.  Zero support for it.  Needless to say I won't be buying another Kinston drive.  I haven't given up on making it work with this drive though.  I've heard of some kind of manual trim support (sh.wipe or something like that.)  I wonder if that could be made to work, how helpful it is, and how often it would have to be run.

---

### Post by psusi on 2011-01-19
> **SkylinesSuck said:**
> So after some searching, it appears Kinston (at least with my model) saw fit not to provide us an updated firmware.  Zero support for it.  Needless to say I won't be buying another Kinston drive.  I haven't given up on making it work with this drive though.  I've heard of some kind of manual trim support (sh.wipe or something like that.)  I wonder if that could be made to work, how helpful it is, and how often it would have to be run.

If the drive doesn't support TRIM, then it doesn't support TRIM.  It does not know or care whether it is manual or automatic.

What you can do instead to avoid performance degradation, is to simply leave a bit of the drive unpartitioned so that you never use it.  Also doing a security erase with hdparm will completely wipe the drive and start fresh.

Also not all drives have deterministic TRIM behavior, so they won't necessarily return all zeros if it works.

---

### Post by libssd on 2011-01-19
For the record, I have seen the 32gb OCZ Vertex drive selling for $50-$90 over the past 9 months. Mine came with firmware 1.4, which did not support TRIM, but after updating to firmware 1.5, then 1.6, Nicolay's TRIM test returned all zeros. I've been quite pleased with this SSD, but in all honesty, I haven't noticed, or tested, any difference in performance before/after enabling TRIM. But, that's mainly because (if I understand correctly) TRIM only affects write speed, not read speed.

---

### Post by SkylinesSuck on 2011-01-19
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820139132](http://www.newegg.com/Product/Product.aspx?Item=N82E16820139132)

It has TRIM support according to every spec I can find.

---

### Post by psusi on 2011-01-19
> **libssd said:**
> But, that's mainly because (if I understand correctly) TRIM only affects write speed, not read speed.

Not only that, but without TRIM you only loose write speed after you have written to nearly every block on the disk.  I still have not bothered enabling it on my 64 gb vertex I got last March and it still works just as well as when I first got it.

---

### Post by libssd on 2011-01-20
> **psusi said:**
> Not only that, but without TRIM you only lose write speed after you have written to nearly every block on the disk.  I still have not bothered enabling it on my 64 gb vertex I got last March and it still works just as well as when I first got it.
If a drive already supports TRIM (virtually ubiquitous by now, I suspect), it's not much trouble, just adding one word, "discard" to /etc/fstab. In my case, considerable effort was required (including borrowing someone else's computer) to update the firmware, but I assume that was a good thing in general, as the release notes documented several fixes.

---

### Post by balak on 2011-03-03
Did you find a solution to your issue ? I also have a kingston drive (SNV125-S2/30GB) as my root drive and see the same issue while testing if TRIM works. 

In my case, I did check that the drive & firmware supports TRIM (hdparm -I). Also I have discards in the /etc/fstab file.

I guess I am still not clear if TRIM is enabled or not.

---

