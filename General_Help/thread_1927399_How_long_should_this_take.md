---
title: "How long should this take?"
date: 2012-02-17
forum: General Help
---

### Post by Rafterman414 on 2012-02-17
FIRST OFF DO NOT USE THIS COMMAND YOU WILL LOSE DATA!
I am erasing data on a hard drive that I will be giving to a friend and I am using a live Xubuntu 11.10 CD to execute the following command:```
dd if=/dev/zero of=/dev/sdx bs=1M
```  DO NOT USE THIS COMMAND, YOU WILL LOSE DATA! I do not want to get accused of trying to damage people's systems, you have been warned.

Anyway my question is I am trying to do this on a 700GB 7200 RPM SATA Internal HDD. I don't know the other specs of the drive, however does anyone have a rough estimate of how long I should expect this to take? It's been about 2 hours now and it is still going. Thanks.

---

### Post by jayshomebrew on 2012-02-18
I think this depends on a lot of things, but with my average computer it took me 12-14hrs for a 500GB drive.

---

### Post by yetiman64 on 2012-02-18
If your sata BIOS settings are set to use "native ide" then it may take a very long time. I set mine here to "AHCI" to get full speed sata access.

With the BIOS settings at optimum, a 500 GB drive takes me about 5 hours to erase with shred (also just doing the one zeroing pass like you are doing with dd, so should be roughly similar timing). jayshomebrew's estimate sounds about right for a 500 GB sata set up as "native ide" (much slower drive access and writing).

Unless you specifically set up (or had someone set the machine up for you) with optimal drive access in mind, I would suggest the 12-14 hour guess previously mentioned is a reasonable starting figure (more, even as much as 18-20 hours, as your drive is 700 GB).

---

### Post by Rafterman414 on 2012-02-18
Well I went to bed and let it do its thing and here is how long everything took, here is the output of the command.
```
ubuntu@ubuntu:/dev$ sudo dd if=/dev/zero of=/dev/sda bs=1M
dd: writing `/dev/sda': No space left on device
715405+0 records in
715404+0 records out
750156374016 bytes (750 GB) copied, 11677.8 s, 64.2 MB/s

```

I was incorrect in thinking that it was 700 GB it was really 750 GB

---

