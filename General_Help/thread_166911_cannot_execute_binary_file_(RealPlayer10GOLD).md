---
title: "cannot execute binary file (RealPlayer10GOLD)"
date: 2006-04-27
forum: General Help
---

### Post by 1002285 on 2006-04-27
I downloaded RealPlayer, but cannot install it. I get the answer "cannot execute binary file".
At first I thought it might have been a download problem and downloaded it again - but this changed nothing.
When I wrote "chmod a+x RealPlayer10GOLD.bin" in the terminal to make it executable (as the installation instructions suggested" - no answer at all. Why might that be?

---

### Post by kaamos on 2006-04-27
if 
```

chmod +x RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin

```
doesn't work, I'd say that the binary is corrupt or for a different architecture etc..

---

### Post by cjmartinez on 2006-04-27
i had gone through the same issue and found out that the latest version tha that i could install was realplayer 8, i actually had to download it thru synaptic.  you should be able to find it by just searching for realplayer in the synaptic search.

---

### Post by hajk on 2006-04-27
Where did you get your executable? I just recently downloaded RealPlayer10 from the Helix DNA site, taking care to choose the version suited to my architecture (32-bit amd-smp kernel): realplay-10.1.0.1892-linux-2.2-libc6-gcc32-i586.bin.
I installed it (with sudo) to /usr/local/lib/RealPlayer, it plays just fine. So, just check that you pick the right version to download.

---

### Post by Jagot on 2006-04-27
You may want to just get the .deb from here:

[https://wiki.ubuntu.com/RestrictedFormats#head-848295cba1b3591a4b4a0dbea5844fd5d2894b6b](https://wiki.ubuntu.com/RestrictedFormats#head-848295cba1b3591a4b4a0dbea5844fd5d2894b6b)

Would be much easier.

---

### Post by cjmartinez on 2006-04-27
i might not have the correct package, but if memory serves me right i tried to download the .deb file "realplayer_10.0.6-0.0_i386.deb" and the main prob i was having was with the libstdc++5 package that you need to run the insall. when i search for it with apt-get it says it is an invalid function and cant find it.  is this lib for use with all ubuntu versions or does it not exist in breezy repositories?  also this is probably a waste of a question but it seems that i cant install it into my root or user bin folder since it says that i dont have permissions.  if i try and install using sudo, it just never creates itself, insall says its finished but realplayer bin doesnt exist in bin folder.  any suggestions?

---

### Post by Jagot on 2006-04-27
[QUOTE=cjmartinez]i might not have the correct package, but if memory serves me right i tried to download the .deb file "realplayer_10.0.6-0.0_i386.deb" and the main prob i was having was with the libstdc++5 package that you need to run the insall. when i search for it with apt-get it says it is an invalid function and cant find it.  is this lib for use with all ubuntu versions or does it not exist in breezy repositories?[/QUOTE]


libstdc++5 is in the main respoitory:

[http://packages.ubuntu.com/breezy/base/libstdc++5](http://packages.ubuntu.com/breezy/base/libstdc++5)

Providing your sources.list is intact then you should have no problem in obtaining it.

---

### Post by cjmartinez on 2006-04-27
you know what, actually i was wrong, i was able to get libstdc++5, but the realplayer install is asking for libstdc++5.so.3, actually i might be wrong on the file name, im leaving work right now, will be home in about 20 min and will get you the exact name of the lib it asks for, by the way, thanks for the help Jagot, and thanks for bringing up the topic nameless user -1002285

---

### Post by cjmartinez on 2006-04-27
GOT IT!:D   Looks like i was just off by a little on something because i ran:   
*apt-get libstdc++5 *
then unpacked it and installed, afterwards i just specified the directory the bin file was in and installed RealPlayer 10 Gold with ease.  good feeling, dont know why i needed it so bad but i think after failing the first few times it became more of a "competition between man and machine" LOL  anyway thanks all!  and thanks for the link jagot

---

