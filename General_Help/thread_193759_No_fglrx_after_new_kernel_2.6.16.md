---
title: "No fglrx after new kernel 2.6.16"
date: 2006-06-10
forum: General Help
---

### Post by Piggah on 2006-06-10
hey everyone,

I've just compiled the 2.6.16 kernel, and I've been having trouble getting fglrx drivers to work with it. I'm still always getting the mesa information when checking fglrxinfo. 

I've tried installing fglrx-kernel-source, that doesnt work.

I've tried completely re-installing, also doesn't work. 

I've ran dpkg-reconfigure xserver-xorg, does not work. "fglrx" is also in the driver section in my xorg.conf

I made sure to restart and such after trying each thing, still always getting the mesa information. 

Any help is really appreciated. 

Thanks :)

---

### Post by cwaldbieser on 2006-06-10
[QUOTE=Piggah]hey everyone,

I've just compiled the 2.6.16 kernel, and I've been having trouble getting fglrx drivers to work with it. I'm still always getting the mesa information when checking fglrxinfo. 

I've tried installing fglrx-kernel-source, that doesnt work.

I've tried completely re-installing, also doesn't work. 

I've ran dpkg-reconfigure xserver-xorg, does not work. "fglrx" is also in the driver section in my xorg.conf

I made sure to restart and such after trying each thing, still always getting the mesa information. 

Any help is really appreciated. 

Thanks :)[/QUOTE]

Did you try running
```

$ sudo aticonfig --initial
$ sudo aticonfig --overlay -type=Xv

```
after you reconfigured the xserver?

---

### Post by Piggah on 2006-06-10
Yes, I ran both of those. Forgot to mention, sorry. 

Thanks :)

---

### Post by bollix47 on 2006-06-10
If you have an ATI card you could try:

[http://www.ubuntuforums.org/showpost.php?p=1108696&postcount=26](http://www.ubuntuforums.org/showpost.php?p=1108696&postcount=26)

---

### Post by Piggah on 2006-06-10
Ah, following the wiki linked to in that thread got it working straight away.

Link for anyone else who needs it: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

Thanks so much. :)

---

### Post by ehula on 2006-06-19
[QUOTE=Piggah]Ah, following the wiki linked to in that thread got it working straight away.

Link for anyone else who needs it: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

Thanks so much. :)[/QUOTE]
What exactly was it at this link that solved the issue for you. I have essentially done everything at this link when I installed the driver under the 2.6.15 kernel that ships with Dapper.

Any help would be greatly appreciated.

---

### Post by Piggah on 2006-06-19
Method 2 on that page worked for me..

If you're using the kernel from dapper, this way should work though: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by ehula on 2006-06-19
[QUOTE=Piggah]If you're using the kernel from dapper, this way should work though: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)[/QUOTE]
So, this would require a linux-restricted-modules-2.6.16 (or 2.6.17) which doesn't exist! Maybe the only way to do this is to use method 2, as you described, and manually build the packages from the ATI supplied driver.

Can anyone else corroborate this?

---

### Post by ehula on 2006-06-21
Bump.

---

