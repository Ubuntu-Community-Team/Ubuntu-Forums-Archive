---
title: "connection issue"
date: 2010-07-20
forum: General Help
---

### Post by Rambit on 2010-07-20
Hi,
 
I recently installed ubuntu to my computer using wubi, how ever using ubuntu did not fix the connection problem I had with vista so I have 2 questions.
1 - does have ubuntu installed on windows make it run any differently to a boot disk?(such as windows errors carrying over)
 
2 - is there any way to make a boot disk from the files downloaded using wubi, or will they have to be downloaded again? (I have a very small data usage cap and will need to wait another month if this is the case)
 
Thanks in advance!
 
 
Rambit

---

### Post by bcbc on 2010-07-20
> **Rambit said:**
> Hi,
 
I recently installed ubuntu to my computer using wubi, how ever using ubuntu did not fix the connection problem I had with vista so I have 2 questions.
1 - does have ubuntu installed on windows make it run any differently to a boot disk?(such as windows errors carrying over)
 
2 - is there any way to make a boot disk from the files downloaded using wubi, or will they have to be downloaded again? (I have a very small data usage cap and will need to wait another month if this is the case)
 
Thanks in advance!
 
 
Rambit

wubi is booted completely separately from windows. It's installed under windows, and it's installed on a virtual disk under your windows file system, but it's not run under windows whatsoever.

So you shouldn't need a separate boot disk to fix your connection problems. Maybe provide more description about your hardware and the problems you are having.

---

### Post by Rambit on 2010-07-20
Wow thanks for the quick response.
 
Okay well the initial problem I have had with vista is the "local only" connection, which is a fairly common vista bug where you can't use the internet unless you reconnect.  How ever since I recently upgraded to mobile broadband from dial up, the problem although less frequent, no longer fixes from a simple reconnect - even a reboot doesn't fix it.  Some days it will work fine and others it wont at all.  It says the hardware is working fine, and the signal is more than sufficient so I assumed a new OS would fix the problem.  How ever even using Ubuntu it would say I am connected while the internet does not work at all.
 
But as a result of your reply i'm starting to think it may not be OS related if Ubuntu is running completely separate and still having the same problems.  Down side is I have no idea where to look now :(
 
 
Thanks again.

---

### Post by bcbc on 2010-07-20
> **Rambit said:**
> Wow thanks for the quick response.
 
Okay well the initial problem I have had with vista is the "local only" connection, which is a fairly common vista bug where you can't use the internet unless you reconnect.  How ever since I recently upgraded to mobile broadband from dial up, the problem although less frequent, no longer fixes from a simple reconnect - even a reboot doesn't fix it.  Some days it will work fine and others it wont at all.  It says the hardware is working fine, and the signal is more than sufficient so I assumed a new OS would fix the problem.  How ever even using Ubuntu it would say I am connected while the internet does not work at all.
 
But as a result of your reply i'm starting to think it may not be OS related if Ubuntu is running completely separate and still having the same problems.  Down side is I have no idea where to look now :(
 
 
Thanks again.
Try phoning your mobile broadband provider. They can help troubleshoot where the issue is.

---

### Post by 3rdalbum on 2010-07-20
> **Rambit said:**
> Hi,
 
I recently installed ubuntu to my computer using wubi, how ever using ubuntu did not fix the connection problem I had with vista so I have 2 questions.
1 - does have ubuntu installed on windows make it run any differently to a boot disk?(such as windows errors carrying over)

If Windows won't boot up, then Ubuntu won't be able to boot either due to the NTFS partition not being unmounted. Filesystem corruption on Windows' NTFS partition may also prevent Ubuntu from booting, because with Wubi, Ubuntu is installed to a file on the NTFS partition.

Problems with Windows' configuration, like the one you describe, will not carry over.
 
> 2 - is there any way to make a boot disk from the files downloaded using wubi, or will they have to be downloaded again? (I have a very small data usage cap and will need to wait another month if this is the case)

The ISO should be saved somewhere on the hard disk; do a search for ".iso" on your Windows side. You can then use any half-decent burning software and its "Burn image to disc" or "Burn ISO image" function to create an Ubuntu CD.

Also, for future reference, when you download the Ubuntu ISO it already contains a copy of Wubi. Next time you want a copy of Ubuntu, just download the ISO from the Ubuntu website, burn a disc from it, and then either boot up from it and install it properly, or run wubi.exe from the disc.

---

### Post by Rambit on 2010-07-21
> Try phoning your mobile broadband provider. They can help troubleshoot  where the issue is.
Okay thanks I will try that.

> The ISO should be saved somewhere on the hard disk; do a search for  ".iso" on your Windows side. You can then use any half-decent burning  software and its "Burn image to disc" or "Burn ISO image" function to  create an Ubuntu CD.
I have a 700mb file called "FUSE_HIDDEN0000000400000001 File (.fuse_hidden0000000400000001)" in C/ubuntu/install, however no .iso.  haven't managed to be able to do anything with the file though.

---

