---
title: "True Encryption?"
date: 2011-04-16
forum: General Help
---

### Post by buntuser2 on 2011-04-16
I have just installed Ubuntu 10.10 with full disk encryption using the alternate CD. I selected "Guided encrypted LVM" and it used my whole hard drive for the encrypted installation.

If I install a DOS utility to view files on my hard drive, will the utility show the ubuntu files as encrypted, or show the regular files?

Someone told me the files will still be visible.

---

### Post by Keypel on 2011-04-16
> **buntuser2 said:**
> I have just installed Ubuntu 10.10 with full disk encryption using the alternate CD. I selected "Guided encrypted LVM" and it used my whole hard drive for the encrypted installation.

If I install a DOS utility to view files on my hard drive, will the utility show the ubuntu files as encrypted, or show the regular files?

Someone told me the files will still be visible.

 I do believe the Guided encrypted LVM does provide true disk encryption except for the boot partition. I'm pretty sure the boot partition is left unencrypted. It would allow an attacker to know you are running linux but not much beyond that. The rest should be encrypted and no files would show but, I think you may want to be aware of something called a cold boot attack, just youtube for it.

[http://www.youtube.com/watch?v=NDHIv1xJF0E](http://www.youtube.com/watch?v=NDHIv1xJF0E)

The above clip is using Windows for demonstration but this is not an attack on Windows but rather the memory in ram itself. As far as I know, PC and Laptop vendors are not coming up with solutions yet.

note: ignore the part about "windows bit locker". That part wouldn't apply to you but the rest is VERY relevant.

Also, for more bad news, this isn't the only attack, there is also your firewire port, which is just as easy to exploit as the cold boot. Both attacks are very easy to pull off and leaves encryption useless.

---

### Post by buntuser2 on 2011-04-16
thanks keypel and yes I think you are right it is true encryption I just read an article about it.

I'm trying to find a utility that will let me browse files on my hard drive now. If anyone knows of a free utility that I can burn as an ISO image to a disk and boot from, then view files on my hard drive please reply with the name.

I will post back here with the results of the test.

---

### Post by Keypel on 2011-04-16
> **buntuser2 said:**
> thanks keypel and yes I think you are right it is true encryption I just read an article about it.

I'm trying to find a utility that will let me browse files on my hard drive now. If anyone knows of a free utility that I can burn as an ISO image to a disk and boot from, then view files on my hard drive please reply with the name.

I will post back here with the results of the test.

I'm not quite sure what you mean. Once you enter the phasphrase during the boot up processes, the encryption key is stored in ram and files are encrypted and decrypted on the fly. The process is completely transparent to the user. In other works, after you enter the phassphrase, everything works and looks like a regular unencrypted system. It's not until the system is shut down that the files become inaccessible.

I'm sorry, I'm just not quite sure what you are trying to do.

If your going to run a live CD as your OS I would recommended you encrypt your hdd (or IMHO a TC encrypted file container is better) with TC (truecrypt) instead of the Guided encrypted LVM.

If your using two physical hdd's, (One hdd for your OS and one for encrypted files) I would recommend Guided encrypted LVM for your OS hdd and one truecrypt file container on the other hdd. Like I said, I'm just not exactly sure what you are trying to do.

---

