---
title: "Need to install UBUNTU 32 bit on a 64 bit installation (I have 32-bit processor)"
date: 2012-09-21
forum: General Help
---

### Post by sandeepy02 on 2012-09-21
Hi,

  I am not much of techie, can barely do simple stuff. I cannot access internet from my laptop. I had installed ubuntu 64-bit 12.04 on my 32-bit laptop. However as expected there are dependency issues. I get upgrade requests in ubuntu, but I cannot download sizeable stuff on my laptop due to bandwidth issues.

  Now I need to revert back to Ubuntu 32-bit. Can I download Ubuntu 32-bit from net on to my pendrive, and then change my ubuntu 64 bit to ubuntu 32 bit?

  Is there an easy way to do that... or do i need to erase my current ubuntu install and install a new 32 bit???

Thanks

---

### Post by tienlbhoc on 2012-09-21
I think you need reinstall because packages in 32 and 64 are different

---

### Post by carl4926 on 2012-09-21
> do i need to erase my current ubuntu install and install a new 32 bit???Yes                  .

---

### Post by jwbrase on 2012-09-21
> **sandeepy02 said:**
> Hi,

  I am not much of techie, can barely do simple stuff. I cannot access internet from my laptop. I had installed ubuntu 64-bit 12.04 on my 32-bit laptop.

Before you reinstall: Are you *sure* your laptop is 32-bit? What did you do to find out that it's 32-bit? And are you *sure* you installed 64-bit Ubuntu?

It's completely impossible to even get the 64-bit Ubuntu install CD to boot on a 32-bit system, let alone install or run 64-bit Ubuntu, so either your laptop is 64-bit or you installed 32-bit Ubuntu, or both (it is possible to run 32-bit Ubuntu on a 64-bit laptop). So I don't think your Internet problems are caused by trying to run 64-bit Ubuntu on a 32-bit system, because you actually managed to install Ubuntu, which wouldn't happen in that case. Let's make sure of what your problem actually is before reinstalling.

---

### Post by prshah on 2012-09-21
> **sandeepy02 said:**
>  I am not much of techie, can barely do simple stuff. I cannot access internet from my laptop. I had installed ubuntu 64-bit 12.04 on my 32-bit laptop. However as expected there are dependency issues. I get upgrade requests in ubuntu, but I cannot download sizeable stuff on my laptop due to bandwidth issues.

  Now I need to revert back to Ubuntu 32-bit. Can I download Ubuntu 32-bit from net on to my pendrive, and then change my ubuntu 64 bit to ubuntu 32 bit?

  Is there an easy way to do that... or do i need to erase my current ubuntu install and install a new 32 bit???

Thanks

First off, as already mentioned, you cannot install 64 bit if only a 32 bit capable processor is used.

However, you CAN install 32bit even if you have a 64bit system, so you CAN use 32bit.

Secondly, it is unlikely that the problem you are facing is specifically due to 64 bit. I would suggest that you post about that problem + error messages + attempted solutions, rather than switch over to 32bit. The ONLY case that I have come across where 32-bit is justified over 64-bit is when using "softmodems" (aka linmodems, winmodems).

Third, until now, it was not possible to switch over without wiping and re-installing. However, from 12.04 onwards, ubuntu follows the Debian "multiarch" spec, and there are an EXPERIMENTAL method that will allow you to change a 32-bit to 64-bit and vice versa, WITHOUT need to re-install.

Note the EXPERIMENTAL: It is mentioned in "User stories" on the [Multiarch Spec on the Ubuntu wiki]("https://wiki.ubuntu.com/MultiarchSpec") but when I attempted it, "things went horribly wrong" (tm).

Further, it also requires a large amount of download, which you can probably circumvent with a live CD or alternate CD added to your existing software repos. Use the command apt-cdrom to add an existing CD/DVD to your repos.

If you are confused, I strongly suggest that you stick with 64 bit, and work to solve the issues you are facing.

If you want a quick turnaround, then probably the best option you have is to backup your data and re-install your OS.

If you can spare some time, and can manage the data download issue (for example, check on ebay for an "alternate" ubuntu CD), then I suggest you attempt the multiarch upgrade procedure, and fallback to a reinstall if it fails.

Please post back if you want more details.

---

### Post by drmrgd on 2012-09-21
As others have said, it is very unlikely that you installed 64-bit Ubuntu on a 32-bit CPU.  As well, I don't think your problems are due to the incorrect architecture either.  However, just to explicitly show what you're working with you can run the following two commands that will outline what you've set up:

```
sudo lscpu
```

```
uname -a
```

---

