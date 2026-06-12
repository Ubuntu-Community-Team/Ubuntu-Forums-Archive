---
title: "Help, I think I ruined my computer"
date: 2011-02-06
forum: General Help
---

### Post by hijiz on 2011-02-06
Please Help. I had a problem with my computer so i had to take out the battery while the computer was running. now when I turn the computer on it gives me the following options;
> Ubuntu, with Linux 2.6.35-26-generic
Ubuntu, with Linux 2.6.35-26-generic (recovery mode)
Ubuntu, with Linux 2.6.35-25-generic
Ubuntu, with Linux 2.6.35-25-generic (recovery mode)
Ubuntu, with Linux 2.6.35-24-generic
Ubuntu, with Linux 2.6.35-24-generic (recovery mode)
Ubuntu, with Linux 2.6.35-23-generic
Ubuntu, with Linux 2.6.35-23-generic (recovery mode)
Ubuntu, with Linux 2.6.35-22-generic
Ubuntu, with Linux 2.6.35-22-generic (recovery mode)
Ubuntu, with Linux 2.6.32-25-generic
Ubuntu, with Linux 2.6.32-25-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
And when i select one of the Ubuntu options, some code apears followed by the statement (initramfs):confused: i dont know what to do.

---

### Post by Habitual on 2011-02-06
try this thread:
[http://ubuntuforums.org/showthread.php?t=422523](http://ubuntuforums.org/showthread.php?t=422523)

---

### Post by wojox on 2011-02-06
Will it let you boot into recovery mode?

What is the exact message?

---

### Post by Rubi1200 on 2011-02-06
If you are unable to boot the kernel or recovery options, run the boot info script and post it here please:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by hijiz on 2011-02-06
Will this make me lose any of my information?
and how do i download the scripts?

---

### Post by csikose on 2011-02-06
I did try yesterday the same, had exactly the same problem, but was unable to find out the partition name and I lost all my business data I had on my company laptop

---

### Post by coffeecat on 2011-02-06
> **hijiz said:**
> Will this make me lose any of my information?

No.

> **hijiz said:**
>  and how do i download the scripts?

You need to be connected to the internet while in the live session. Simply open firefox, got to the link Rubi1200 gave you and follow the directions.

> **hijiz said:**
> And when i select one of the Ubuntu options, some code apears followed by the statement (initramfs)

Which option? Have you tried more than one? If the first -26-generic gives you the initramfs error, simply try the -25-generic one, or the -24-generic one and so on.

---

### Post by hijiz on 2011-02-06
> Which option? Have you tried more than one? If the first -26-generic gives you the initramfs error, simply try the -25-generic one, or the -24-generic one and so
Yes ive tried ALL of them.

---

### Post by 3rdalbum on 2011-02-06
It would really help to know the exact error message, and what you were doing when you took the battery out (for instance, if you were installing updates when the computer lost power that might suggest one particular course of action).

---

