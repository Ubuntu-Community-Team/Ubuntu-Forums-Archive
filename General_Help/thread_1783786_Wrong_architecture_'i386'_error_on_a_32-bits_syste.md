---
title: "Wrong architecture 'i386' error on a 32-bits system"
date: 2011-06-16
forum: General Help
---

### Post by ElToro on 2011-06-16
Hi all,

I am having a rather odd problem on my Ubuntu 11.04 installation on a 32-bits Intel Core 2 Quad system. When I try to install packages that are not in the repositories, I keep getting the message " Wrong architecture 'i386' " in the Ubuntu Software Center. #-o

I have downloaded several packages for 32-bits systems and get the same error every time, for instance., with the Linux 32-bits Debian package for Teamviewer. :(

In addition to the PC, I have a laptop with an amd64, and I have transfered the pkglist from that machine to my PC to get the same environment. Could that cause any problems of the sort above?

Any help would be greatly appreciated...

---

### Post by steveneddy on 2011-06-16
That system is a 64 bit system - sounds like you have the 64 bit OS version installed.

Perform this command in terminal and post the output back in the forums:

```
uname -a
```

---

### Post by ElToro on 2011-06-16
> **steveneddy said:**
> That system is a 64 bit system - sounds like you have the 64 bit OS version installed.

Perform this command in terminal and post the output back in the forums:

```
uname -a
```

Thanks for the tip! Result:

Linux eric-MS-7360 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

I have managed to install the wrong system! That's just great... Ok, so now I have to start from scratch, right?

---

### Post by jerome1232 on 2011-06-16
> **ElToro said:**
> Thanks for the tip! Result:

Linux eric-MS-7360 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

I have managed to install the wrong system! That's just great... Ok, so now I have to start from scratch, right?

If by wrong system you mean you intended to install 32 bit then you'd be correct. However 64 bit os is the correct os for your cpu, as it is 64 bit. (You can't install a 64 bit os to a 32 bit cpu, it just won't boot)


If you are intent on installing 32 bit then yes you'd have to backup and reinstall.

---

### Post by ElToro on 2011-06-16
Apologies all around. I got confused because I was installing Ubuntu on various machines at a time, both 32 and 64-bits... :rolleyes:

This is a 64-bit machine with a 64-bits system. And from now on I'll download the right (64-bits) packages!

---

