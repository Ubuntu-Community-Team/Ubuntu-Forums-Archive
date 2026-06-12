---
title: "Slow usb transfers"
date: 2006-04-23
forum: General Help
---

### Post by v4169sgr on 2006-04-23
Kubuntu breezy user, on Intel Coppermine with suspected USB1

I've noticed some issues with copying large numbers of files to a USB storage key. I have a 512MB model, and am copying typically 50-100 JPEGs at a shot to around 100 MB a time.

I've noticed that for total file transfers of about 40-50 MB everythig runs smoothly and quickly and I do not have any issues.

However for larger file transfers, after a while the following starts to happen:
1. Load average as monitored by 'top' increases to around 6, even though CPU activity remains only a few %;
2. File transfer rate goes right down, and sometimes becomes 'stalled', copying in 'bursts' around 30s to a minute apart;
3. After copying has apparently finished, load average remains very high, and a lot of disk activity seems to be taking place, with usb_storage and hald being active;
4. Pulling the key at this stage risks file system corruption [actually happened, had to use fsck on the key to correct the issue].

I do not notice similar issues on SuSe 9.1 on an AMD Duron with the same key. The uhci_usb module is being loaded by both kubuntu and SuSe.

I reproduced the issue by using Konqueror to transfer the files [lots of kio_file procs!], and by using cp -R, hence there is not a konq dependancy that I can see.

Is Kubuntu trying to be too clever here?

---

### Post by v4169sgr on 2006-04-24
Any clues? I'm wondering if Dapper has this issue too ...

---

### Post by sinkxdie on 2006-04-24
I have Dapper, and I don't have this issue at all. It might be your card.

---

