---
title: "Ripping CDs faster?"
date: 2011-03-26
forum: General Help
---

### Post by linuxuser12345 on 2011-03-26
Hey, I am using Ubuntu 10.10 64-Bit Desktop Edition, and I am looking for a faster way to rip CDs, without having to resort to Windows. I try to rip a CD, but it takes 20+ minutes just to get the files copied, then another 5 or so minutes to burn the cd!

I have a new SATA interface CD/DVD burner, so I know it is not the hardware.
Can somebody please help me with this problem?? Thanks! :)

---

### Post by linuxuser12345 on 2011-03-26
Can anyone help me? Thanks

---

### Post by wanderingarticfox on 2011-03-26
What are the speeds of your CD/RW or DVD/RW; also I'm not really you want to rip any faster than Rhythm-Box does if you want quality that is:guitar:  You can look at Brasero Disc burner  for your write speed options. You say you have a new SATA optical drive; did you check the BIOS settings?

---

### Post by linuxuser12345 on 2011-03-26
No, I haven't checked the BIOS setting, but when I go to rip a CD, I tell it to use the maximum speed possible.

When I try to rip a CD on a friend's Windows 7 PC, it rips them MUCH faster.

---

### Post by AlphaLexman on 2011-03-26
Depending on the program you are using, some (most) Linux CD rippers create a .wav file (lossless) and then convert it to a lossy format (.ogg or .mp3). Windows Media Player will rip straight to lossy format, that's why it's faster.

---

### Post by Spyderkid on 2011-03-26
The best one for CD's and DVD's which i have found are as folows:

>[CD's] Asunder CD ripper (takes about 5mins per album)
>[DVD's] OGMrip (10-15mins per 30 mins of film)

---

### Post by linuxuser12345 on 2011-03-26
Is there a way I can get those speeds in Brasero?

---

### Post by newbuntuxx on 2011-03-26
How fast is it on windows?

Don't know if this is faster, but you can try the dd command to copy the cd/dvd to an iso. I always use it for create ISOs from DVDs/CDs

First, insert the DVD, then unmount it:

```
sudo umount /dev/sr0
```

Then create a directory in your home directory, call it: ripped

```
cd ~
mkdir ripped
cd ripped

```

Then start ripping:
```
sudo dd if=/dev/sr0 of=dvd.iso bs=4096
```

This takes 3 - 5 mins for a cd, 10 mins for a dvd. You can then use whatever software you like to burn the image (k3b or brasero)

---

