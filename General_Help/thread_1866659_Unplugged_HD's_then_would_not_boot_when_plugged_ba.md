---
title: "Unplugged HD's then would not boot when plugged back in"
date: 2011-10-21
forum: General Help
---

### Post by Oldhacker on 2011-10-21
Running Ubuntu 11.04 64 bit, I unwisely unplugged two of my physical HD's one by one and then restarted to try to determine which one had the OS (I have three physical HD's)

After unplugging the first one, it restarted normally, so I knew that the OS was not there. After re-plugging that one, I unplugged the second one and then it would not restart at all.

Then I plugged them all in again, and now it would not boot.
I checked each power and signal plug for correct insertion but it would not boot. Then, I inserted my System Rescue Disk and selected "boot from first HD" and it booted normally. However, without the System Rescue Disk inserted and making the selection of "boot from first HD" it refuses to boot.

Where can I look to find what is amiss?

Thanks,

---

### Post by dcstar on 2011-10-22
> **Oldhacker said:**
> Running Ubuntu 11.04 64 bit, I unwisely unplugged two of my physical HD's one by one and then restarted to try to determine which one had the OS (I have three physical HD's)

After unplugging the first one, it restarted normally, so I knew that the OS was not there. After re-plugging that one, I unplugged the second one and then it would not restart at all.

Then I plugged them all in again, and now it would not boot.
I checked each power and signal plug for correct insertion but it would not boot. Then, I inserted my System Rescue Disk and selected "boot from first HD" and it booted normally. However, without the System Rescue Disk inserted and making the selection of "boot from first HD" it refuses to boot.

Where can I look to find what is amiss?


Firstly check the Boot sequence in your BIOS.

---

### Post by Oldhacker on 2011-10-22
Good try, but the boot sequence was correct in the BIOS.
One thing that I did attempt after that was to compare the mtab files with those in /etc and the mtab in a very recent backup.
They were not identical, so I renamed mtab to mtabold and restored the mtab from the backup. It did not help. :-(

I compared the fstab files in /etc with the fstab in the backup and they were identical. 

Back to the drawing board ---

---

### Post by dcstar on 2011-10-22
> **Oldhacker said:**
> Good try, but the boot sequence was correct in the BIOS.
One thing that I did attempt after that was to compare the mtab files with those in /etc and the mtab in a very recent backup.
They were not identical, so I renamed mtab to mtabold and restored the mtab from the backup. It did not help. :-(

I compared the fstab files in /etc with the fstab in the backup and they were identical. 

Back to the drawing board ---

Boot using the method that works and then:

```
sudo dpkg-reconfigure grub-pc
```
and reinstall the boot loader on the disk that you actually want to use as the boot drive.

---

### Post by Oldhacker on 2011-10-23
This morning, I was all set to continue my troubleshooting when I discovered that it would not even reach the BIOS booting stage using the Ubuntu 11.10 CD in the CD drive. This gave me a clue: I took out the BIOS battery, and tested it on my battery tester and it showed in the yellow zone.

Off to Wal Mart, purchased a new 2032, put it in prepared to just see if it would boot the BIOS and the whole Ubuntu 11.10 just booted up normally with no further manipulations on my part!

The moral of the story is to always look for the simple things first. 

Many thanks to all who have volunteered good suggestions.

---

