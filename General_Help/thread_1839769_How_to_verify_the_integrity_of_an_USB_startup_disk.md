---
title: "How to verify the integrity of an USB startup disk?"
date: 2011-09-06
forum: General Help
---

### Post by desire.linux on 2011-09-06
After you've burned an optical media, like a DVD, you can verify it on the command line by using the dd command in the terminal to check its integrity. You can also verify it on the first installation menu on the Ubuntu installer.

But I have not yet succeeded doing this on an USB startup disk made with an Ubuntu install iso. Is this possible?

---

### Post by j*tech on 2011-09-06
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Manual method should work for you...

---

### Post by desire.linux on 2011-09-07
It seems like this doesn't work on USB sticks, making it impossible to know for sure if your USB stick installer is 100% valid. This makes the USB startup disk creator useless.

---

### Post by e79 on 2011-09-07
> **desire.linux said:**
> It seems like this doesn't work on USB sticks, making it impossible to know for sure if your USB stick installer is 100% valid. This makes the USB startup disk creator useless.

Unless you downloaded a bad/corrupted ISO, which can be verified with j*tech's advices, and unless your USB is borken, which could be noticed when simply copying something to it, I don't think you would encounter much problems here. And I don't think the USB creator becomes useless just because you don't want to try your USB and see if it works ;)

---

### Post by desire.linux on 2011-09-07
The downloaded iso images are fine, tested with sha256sum. The sha256sum file is verified with gpg too.

The USB stick is fine too. When I copy large files to it, and test sha256sums of those files, it hasn't failed yet.

But if I use the startup disk creator, bundled with 10.04, and create an install "disk" on that USB stick, I can't verify its integrity. Testing the "disk" with the installer tells me that the "disk" is not an Ubuntu install "disk". Using the dd command always returns incorrect sha256sums, and these check sums changes if I change the block size option in the dd command as explained on the help page.

The installer on the USB stick from the iso is probably okay, but I always want to check if the installation media is okay before I do large installations. Especially if I'm going to test beta versions of Ubuntu and report bugs.

Are there any wizards in here with ideas to help me out?

---

### Post by e79 on 2011-09-07
I'm not sure what you mean by 'large installations'...I guess it means 'many machines'...Anyhow, I simply suggest you to boot up one machine and see how it goes...it if works correctly you can assume it will for other machines.

Unless someone else could pop in and have better advices...

---

