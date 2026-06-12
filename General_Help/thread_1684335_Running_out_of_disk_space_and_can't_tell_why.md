---
title: "Running out of disk space and can't tell why"
date: 2011-02-09
forum: General Help
---

### Post by Daanii on 2011-02-09
I'm a rank beginner with Linux, and just installed Ubuntu 10.10 on my laptop. I have only about 160 GB on my hard drive, with Windows as my main operating system. Since I have little space, I installed Ubuntu into an 8.6 GB partition. 

Now I keep getting messages that I'm running out of disk space. The disk usage analyzer shows that I have 6.5 GB total storage, with only 634.2 MB left open. But I can't tell what is using all the space. It seems to be used in my root folder, which I cannot access. 

Have I tried to cram Ubuntu into too little space? Or is there anything I can clean up to make the small space work? I don't need to do much on Ubuntu, since most work is done in Windows.

---

### Post by wilee-nilee on 2011-02-09
Check the trash, and run these two commands to clean out extras.
sudo apt-get autoremove
sudo apt-get autoclean.

Yes 8.6 gigs is kinda small, but if kept clean the system with a basic setup should be at the most 3 gigs.

---

### Post by matt_symes on 2011-02-09
Hi

Install Bleachbit.

```
sudo apt-get install bleachbit
```

That can be good to clean out your system.

If you are going to resize your partition backup the entire disc first.

Kind regards

---

### Post by Daanii on 2011-02-09
I'm embarrassed to say that it was the trash, and that I did not think to check it. That was overflowing. Emptying the trash freed up 2.5 GB. Running bleachbit freed up another 0.5 GB. So I am now at 2.9 GB, exactly as you predicted.

Thanks very much for the quick and helpful responses.

---

### Post by Primefalcon on 2011-02-09
Just wish to point out you already have a great tool installed to check what is using disk space.

just go to applications->accessories->Disk usage analyzer

---

