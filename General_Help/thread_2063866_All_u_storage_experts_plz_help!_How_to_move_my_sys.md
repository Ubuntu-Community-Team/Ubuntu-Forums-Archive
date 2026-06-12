---
title: "All u storage experts plz help! How to move my system to a new RAID array"
date: 2012-09-28
forum: General Help
---

### Post by latebeat on 2012-09-28
Hi guys,

I have the following problem. I bought a second ssd for my computer and I'm planning to do a RAID-0 array using my motherboard's built-in raid adapter. 
On that hard drive I have a windows system and some other partitions apart from Ubuntu. Now, I'm not a storage expert but if I use dd to do a bit-by-bit image of the current state of my system and then add the 2nd disk, create the array can I dd back the image (and then expand the file systems etc)?

*If it was just a simple upgrade and I was copying over again to a single hard disk I know it would work.* **However, will it work with a RAID array? **That's what I'm asking basically because I know we have different cluster sizes, raid stripes etc.. ?

what do you think?!

thanks

---

### Post by latebeat on 2012-10-02
I guess I thought since had a dd image I had nothing to lose in trying different scenarios and figuring out which would work. 
You were right and it is a soft/fakeRAID. However, since I'm using 2 ssd drives in a laptop (sony vaio z) so I am hoping that I wont be experiencing any hw failures and also it's a core i7 so system resources is not an issue either. Also, I wanted a fakeraid over Linux raid due to the fact that I'm dual booting windows 7.

So I started by creating the fakeraid array in bios, booting linux in a live cd and restoring the dd image onto the fakeraid device. To my surprise, everything worked right away. Even windows 7 booted with no problems. However, performance was suffering due to the fact that the 128kb stripe size introduced a misalignment to the partitions. I googled a bit and was unable to find a solution that didn't include re installing everything. 

So in the end (and unfortunately) this is what I had to do to realign the partitions with the filesystem and the raid array and the ssd block size. I used an online [calculator]("http://www.techpowerup.com/articles/other/157") to check everything was ok. Also I went with a GPT partition table and have no problems with grub2.
So far I've only reinstalled my main os (linux) and the performance is noticeably faster. I haven't been able to re install windows yet to check if that's true there also. 

again, thank you for the reply. 

Hope someone else finds this useful!

regards,

a

---

