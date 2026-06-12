---
title: "Hard Drive Help"
date: 2011-03-15
forum: General Help
---

### Post by Don Ju4n on 2011-03-15
HEy everyone:)

I've been messing around with my Windoze PC all morning, since it got a pc virus. I have a live cd and im trying to run the anti virus from ubuntu to scan my hard drive.... But what do you know, I cant mount my hard drive! It is being recognized in Disk Utility but in places nothing is showing up. I can't install ubuntu because its my work comp so im forced to work with the live cd. Im running the 64 bit. Thanks, please someone :)

---

### Post by lithopsian on 2011-03-15
Not enough info.  What error do you get mounting the drive?

---

### Post by ChipOManiac on 2011-03-15
Click On The Hyperlink like text next to "Mount Point:" that should open up the file manager to the mounted harddrive...

---

### Post by Don Ju4n on 2011-03-15
> **lithopsian said:**
> Not enough info.  What error do you get mounting the drive?

I didnt get an error. No hard drive shows up so that I can mount. In other words, no hard drive to moiunt means no error

---

### Post by ChipOManiac on 2011-03-15
> **Don Ju4n said:**
> I didnt get an error. No hard drive shows up so that I can mount. In other words, no hard drive to moiunt means no error

You mentioned previously that "Disk Utility" recognizes the Hard Drive, if so you can mount it through the application by simply clicking on the partition and clicking "Mount". :D

---

### Post by blueridgedog on 2011-03-15
Please post the output of the following when run in a terminal:

```
sudo fdisk -l
```

and

```
mount
```

---

### Post by Don Ju4n on 2011-03-15
> **ChipOManiac said:**
> You mentioned previously that "Disk Utility" recognizes the Hard Drive, if so you can mount it through the application by simply clicking on the partition and clicking "Mount". :D

Mount is not an option in Disk Utility. I only get format, SMART data, Benchmark, Format edit or delete. Might it be because im running the live cd and im not installed?

---

### Post by ChipOManiac on 2011-03-15
> **Don Ju4n said:**
> Mount is not an option in Disk Utility. I only get format, SMART data, Benchmark, Format edit or delete. Might it be because im running the live cd and im not installed?
Hmm... Not Sure... I was able to mount all my drives with the Disk Utility... Is Disk Utility able to identify the File System? or is it already mounted (in which case there is "unmount" instead of "mount")?

---

### Post by Don Ju4n on 2011-03-15
> **ChipOManiac said:**
> Hmm... Not Sure... I was able to mount all my drives with the Disk Utility... Is Disk Utility able to identify the File System? or is it already mounted (in which case there is "unmount" instead of "mount")?

Hold on, i cant do further testing atm, since I was using the 64 bit and now changed over to the 32 bit just to see if it recognized my hd. My last resort is going to be installing ubuntu (hopefully IT doesn't kill me about it) :lolflag:

---

