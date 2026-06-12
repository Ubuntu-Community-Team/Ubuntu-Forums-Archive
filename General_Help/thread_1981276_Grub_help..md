---
title: "Grub help."
date: 2012-05-16
forum: General Help
---

### Post by MGebhart on 2012-05-16
Hi,&#8233;&#8233;

Ubuntu 12.04 amdx64

&#8233;&#8233;I got a wild hair and installed BURG. &#8233;&#8233;I would like to revert back to the way Ubuntu booted out-of-the-box.&#8233;&#8233;

I have 2 HDD. The main HDD runs Ubuntu 12.04 and owns the entire drive.&#8233;&#8233;The second drive has Windows 7 and owns the entire drive. I want to boot to this through the bios. (i have reasons for this)
&#8233;&#8233;
Can someone direct me to documentation to accomplish this or provide the steps.&#8233;&#8233;

Hope this makes sense.

Thanks a ton.

---

### Post by wilee-nilee on 2012-05-16
Just reload the mbr with grub, run

```
sudo fdisk -l
```To identify the HD running Ubuntu, then from that install run

```
sudo grub-install /dev/sdX
```The X is the sd**a** or sd**b** third letter on your HD identification is put there, no numbers after the first three letters.

If this makes no sense just post the fdisk output.
 
As suggested below run after loading.

```
sudo update-grub
```

---

### Post by drs305 on 2012-05-16
I just finished rewriting this community doc. 
[https://help.ubuntu.com/community/Grub2/Installing]("https://help.ubuntu.com/community/Grub2/Installing")

It covers a variety of considerations and if you want to totally reset GRUB you can go the purge/reinstall routine.

If what willee-nillee suggests is sufficient for you, you'll need to run "sudo update-grub" once you have grub reinstalled to generate the grub menu.

---

### Post by MGebhart on 2012-05-16
Excellent, thank you.

I guessing that if I want Ubuntu to bypass the menu choices then I need to set the timeout to 0.

Correct?

Thanks again.

---

### Post by wilee-nilee on 2012-05-16
> **MGebhart said:**
> Excellent, thank you.

I guessing that if I want Ubuntu to bypass the menu choices then I need to set the timeout to 0.

Correct?

Thanks again.

I would not set it to 0 unless you know you can bring up the menu with a shift key prompt still, you may need that recovery kernel access at some point, set to just above 0, say 1,2,3 depends on what the computer will work at.

You can set it to 0 then test it.

I run this to remove the memory test lines though.

```
 [FONT=Verdana, sans-serif][SIZE=1]sudo chmod -x /etc/grub.d/20_memtest86+[/SIZE][/FONT]
```                                  [FONT=Verdana, sans-serif][SIZE=1]That should remove both memtest entries. You can always bring them back by running the first command again with +x instead of the -x, and running update-grub again. [/SIZE][/FONT]

---

