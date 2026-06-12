---
title: "Need to edit Linux files from Windows 7"
date: 2012-05-10
forum: General Help
---

### Post by CyrusHeick on 2012-05-10
I was playing around with my Ubuntu partition on my laptop (using it for learning purposes) and I accidentally renamed my bin folder. Now I can't get Ubuntu to boot, but if I could just rename it from Windows, I'm pretty sure it would all be okay again. Is there any way to edit files and directories from Windows? I got DiskInternals Linux Reader but it's "safe" and won't let me edit files.

---

### Post by idoitprone on 2012-05-10
> **CyrusHeick said:**
> I was playing around with my Ubuntu partition on my laptop (using it for learning purposes) and I accidentally renamed my bin folder. Now I can't get Ubuntu to boot, but if I could just rename it from Windows, I'm pretty sure it would all be okay again. Is there any way to edit files and directories from Windows? I got DiskInternals Linux Reader but it's "safe" and won't let me edit files.


[http://www.ext2fsd.com/?page_id=2](http://www.ext2fsd.com/?page_id=2)

support ext 2/3/4

i never tested it so this is just is suggestion

---

### Post by jerome1232 on 2012-05-10
> **CyrusHeick said:**
> I was playing around with my Ubuntu partition on my laptop (using it for learning purposes) and I accidentally renamed my bin folder. Now I can't get Ubuntu to boot, but if I could just rename it from Windows, I'm pretty sure it would all be okay again. Is there any way to edit files and directories from Windows? I got DiskInternals Linux Reader but it's "safe" and won't let me edit files.

Just boot an Ubuntu live cd, and do it from there. You can read ext4 from Windows, but you can't write to ext4 from Windows.

---

### Post by kelvin spratt on 2012-05-10
Use the parted magic live cd it runs as root either burn to disc or put on a stick

---

### Post by nizamibilal1064 on 2012-05-10
> **CyrusHeick said:**
> I was playing around with my Ubuntu partition on my laptop (using it for learning purposes) and I accidentally renamed my bin folder. Now I can't get Ubuntu to boot, but if I could just rename it from Windows, I'm pretty sure it would all be okay again. Is there any way to edit files and directories from Windows? I got DiskInternals Linux Reader but it's "safe" and won't let me edit files.
I am not very sure how to fix this ..but i think you can access files across the os using virtual machine applications,,,

---

### Post by jim_24601 on 2012-05-10
If you can get a root shell up by adding the kernel option "init=/path/to/where/bin/used/to/be/sh", you should be able to put /bin back from the command line.

---

### Post by 3rdalbum on 2012-05-10
> **jim_24601 said:**
> If you can get a root shell up by adding the kernel option "init=/path/to/where/bin/used/to/be/sh", you should be able to put /bin back from the command line.

Yes, that may work. Jim's explanation wasn't easy to follow so you're probably still a bit lost. So, if you renamed 'bin' to 'xyz', you'd bring up GRUB and edit the grub line to include the argument:

```
init=/xyz/sh
```

Then at the command line, run these commands:

```
mv /xyz /bin
reboot
```

I've actually never had to do anything with GRUB 2; so I can't advise on how to get to the part where you edit the kernel options. Sorry.

Alternatively, you can edit it in a root file browser from the Ubuntu live CD. I assume you know how to get to a root file browser as you probably used one to do the renaming in the first place :-)

---

### Post by CyrusHeick on 2012-05-13
Thanks guys, I used the live cd to access my file system, and am happy to report that my OS is running like I never did anything completely boneheaded to it in the first place.

---

