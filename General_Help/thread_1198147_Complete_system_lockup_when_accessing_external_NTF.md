---
title: "Complete system lockup when accessing external NTFS drive too often"
date: 2009-06-27
forum: General Help
---

### Post by /home/marc/ on 2009-06-27
Hello Ubuntufolks! I'm having a really big problem with accessing my external hard drive under Ubuntu 9.04 (Kernel: 2.6.28-13). Mounting it with ntfs-3g (ntfs-3g 2009.2.1) works *most of the time* and reading/writing files to/from the HDD also works quite well.

**But**, somewhat curiously, my system locks up completely as soon as I perform access-heavy tasks like creating thumbnails for folders with >2500 images or even when importing my music library into Rythmbox, Banshee or Amarok (inclusive "or"). Additionally, it sometimes crashes when mounting the partition *after* a previously occurred crash.

I do understand that reading *a lot* if files also requires *a lot* of work by the OS, but I have never had this problem with any other distribution of Linux or even Windows. It worked perfectly under Windows XP SP3 and distributions like Arch Linux, Sidux and Fedora. I really don't know why this error occurs and I would really appreciate any helpful input on the issue, because I'd love to continue using this, up until now, very enjoyable version of Ubuntu, but if I can't access my files under normal circumstances I will probably have to revert back to another distribution/OS.

What I tried to solve the problem with is mounting the partition with noatime and nodiratime, which did not help at all. But that was just a guess. And guessing is all I can do because I don't get any kind of error informing me about anything that is happening during a crash. The only thing close to an error-message is looking at the output in a TTY while scanning files in Rythmbox. Unfortunately I don't know how to save this output and I haven't yet found it in any of the logs in /var/log/. If anybody can tell me how to retrieve the error message I would be more than happy to provide you with the information in the message. As far as I can remember there were a lot of entries containing the string "irq" and one with the word "async". What's weird is that it seems to only happen in graphical applications, because when I recursively chowned every file on the HDD from a terminal my system didn't lock up.

Also, the system freezes *completely*. SysReq + REISUB doesn't work either.

(By the way, the drive is 1Tb in size and contains around ~530Gb of data. It was encrypted with TrueCrypt, but I reformatted the drive without an encryption to test if this issue is caused by TrueCrypt. But it wasn't. It still happens under the unencrypted NTFS partition.)

---

