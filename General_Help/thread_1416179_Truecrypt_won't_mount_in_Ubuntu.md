---
title: "Truecrypt won't mount in Ubuntu"
date: 2010-02-25
forum: General Help
---

### Post by Kirboosy on 2010-02-25
Ok so here is the deal. I dual boot between Windows 7 (My school supplied me with a MSDNAA for free so I installed 7 for my Blackberry and gaming...) and Ubuntu 9.10. I have a 320 Gb. IDE Western Digital Scorpio Blue in a external enclosure. I am running TrueCrypt 6.3a on both Operating Systems.

Anyways, I have the entire 320 partition encrypted with Truecrypt using Serpent-Twofish-AES encryption. I was able to flip between operating systems flawlessly and mount the drive in TrueCrypt without any problems. However, last night the drive would not mount in Ubuntu. I just flipped back from a Windows gaming session and it would not mount. I figured Windows did something but I'm not certain...

I know its not my computer because I just tried it in my friends computer running Ubuntu 9.10 netbook remix and it still wouldn't mount.

If I try to Auto-Mount it comes up with "Incorrect password or no TrueCrypt volume found." If I try and manually mount it by selecting the drive it comes up with the error "No such drive location." (or something similar) even though I clicked right on the drive in the "Select Drive" menu. 

In Windows 7 it mounts flawlessly and I can access everything. Is there any way I can get this to work without having to take all the data off and re-encrypting it? I really don't want to do that because the drive is 96% full and its just a pain..

Thanks for all the help in advance. :D

---

### Post by bad.skipper on 2010-09-13
Hi,

I have the same problem. Auto-mount works nice in Windows XP but in Linux it fails.

According to the truecrypt documentation linux is fully supported:
[Linux (32-bit and 64-bit versions, kernel 2.4, 2.6 or compatible)]("http://www.truecrypt.org/docs/sys-encryption-supported-os")

So I have read this article about [truecrypt command line interface.]("http://polishlinux.org/howtos/truecrypt-howto/")

Now I have added two lines at the end of my profile file: $HOME/.profile (this is hidden file).

```
# Added as workaroung for TrueCrypt behaviour
truecrypt $/home/Alex/TC.archive>
```During system startup I am asked to provide TC password, and volume is mounted. This is workaround only, I am still looking for proper fix.


regards,

Bad Skipper.

---

### Post by muha123 on 2011-09-15
Hello! May be somebody still has this problem...

I've stumbled to the same.
Auto-mount button doesn't work for encrypted containers - it's written in tc's help. However I have found usefull info in user manual that helped me:

[I]A hidden volume can be mounted the same way as a standard TrueCrypt volume: Click Select File
or Select Device to select the outer/host volume (important: make sure the volume is not mounted).
Then click Mount, and enter the password for the hidden volume. Whether the hidden or the outer
volume will be mounted is determined by the entered password (i.e., when you enter the password
for the outer volume, then the outer volume will be mounted; when you enter the password for the
hidden volume, the hidden volume will be mounted).
[/I]

It has solved the issue (at least for me)... Good luck

---

