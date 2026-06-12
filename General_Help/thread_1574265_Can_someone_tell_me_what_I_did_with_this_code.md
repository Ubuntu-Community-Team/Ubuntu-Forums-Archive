---
title: "Can someone tell me what I did with this code?"
date: 2010-09-14
forum: General Help
---

### Post by hortstu on 2010-09-14
```
mike@mike-laptop:~$ AndroidSDK/tools/adb shell rm /data/local/rights/mid.txt
mike@mike-laptop:~$ AndroidSDK/tools/adb shell ln -s /dev/mtd/mtd1 /data/local/rights/mid.txt
mike@mike-laptop:~$ AndroidSDK/tools/adb reboot

```

My htc evo phone is the device in question and I'm wondering what all this means in laymens terms.  Thanks

---

### Post by valbaca on 2010-09-14
> **hortstu said:**
> ```
mike@mike-laptop:~$ AndroidSDK/tools/adb shell rm /data/local/rights/mid.txt
mike@mike-laptop:~$ AndroidSDK/tools/adb shell ln -s /dev/mtd/mtd1 /data/local/rights/mid.txt
mike@mike-laptop:~$ AndroidSDK/tools/adb reboot

```My htc evo phone is the device in question and I'm wondering what all this means in laymens terms.  Thanks

```
mike@mike-laptop:~$ AndroidSDK/tools/adb shell rm /data/local/rights/mid.txt
```
This seems to use some sort of "fake" shell from the SDK to delete the '/data/local/rights/mid.txt' file
```
mike@mike-laptop:~$ AndroidSDK/tools/adb shell ln -s /dev/mtd/mtd1 /data/local/rights/mid.txt
```
This makes a shortcut **that goes to **'/dev/mtd/mtd1' where '/data/local/rights/mid.txt' used to be. in other words, when something reads 'mid.txt' it's **really** going to 'mtd1'
```
mike@mike-laptop:~$ AndroidSDK/tools/adb reboot
```
This last one is left as an exercise for the reader.

Hope I helped

---

### Post by hortstu on 2010-09-14
Valbaca Thanks alot!  I'm going to have more questions like this later.  really trying to grasp what I'm doing by applying it.  Thanks again.

---

