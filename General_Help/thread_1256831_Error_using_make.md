---
title: "Error using make"
date: 2009-09-03
forum: General Help
---

### Post by Murdoc_of_puts on 2009-09-03
Hey guys, 
So I'm not sure what is going wrong here.  I was trying to install some driver mods following [this]("http://ubuntuforums.org/showthread.php?t=242556&page=11") guide.  Everything is going well and happy until I go to 'make' it.  Then this happens.
> Checking in /lib/modules/2.6.28-15-generic for ieee80211 components...                      
make -C /lib/modules/2.6.28-15-generic/build M=/home/murdoc/boobies/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'                      
/home/murdoc/boobies/ieee80211-1.2.18/Makefile:17:                                          
/home/murdoc/boobies/ieee80211-1.2.18/Makefile:18: WARNING: $SHELL not set to bash.         
/home/murdoc/boobies/ieee80211-1.2.18/Makefile:19: If you experience build errors, try      
/home/murdoc/boobies/ieee80211-1.2.18/Makefile:20: 'make SHELL=/bin/bash'.                  
/home/murdoc/boobies/ieee80211-1.2.18/Makefile:21:                                          
  CC [M]  /home/murdoc/boobies/ieee80211-1.2.18/ieee80211_module.o                          
  CC [M]  /home/murdoc/boobies/ieee80211-1.2.18/ieee80211_tx.o                              
  CC [M]  /home/murdoc/boobies/ieee80211-1.2.18/ieee80211_rx.o                              
  CC [M]  /home/murdoc/boobies/ieee80211-1.2.18/ieee80211_wx.o                              
/home/murdoc/boobies/ieee80211-1.2.18/ieee80211_wx.c: In function ‘ieee80211_translate_scan’:
/home/murdoc/boobies/ieee80211-1.2.18/ieee80211_wx.c:61: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/murdoc/boobies/ieee80211-1.2.18/ieee80211_wx.c:61: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/murdoc/boobies/ieee80211-1.2.18/ieee80211_wx.c:61: error: too few arguments to function ‘iwe_stream_add_event’                                    
/home/murdoc/boobies/ieee80211-1.2.18/ieee80211_wx.c: In function ‘ieee80211_wx_set_encodeext’:
/home/murdoc/boobies/ieee80211-1.2.18/ieee80211_wx.c:631: warning: format not a string literal and no format arguments
make[2]: *** [/home/murdoc/boobies/ieee80211-1.2.18/ieee80211_wx.o] Error 1
make[1]: *** [_module_/home/murdoc/boobies/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [modules] Error 2

 
I tried to leave in as much, But I did edit it.  It was mostly just repeating itself.  I don't really know what this means, so I don't know how to fix it. I tried the 'make SHELL=/bin/bash' . Please help.  I'm still learning, alot apearently.  Thank you in advance.

---

### Post by vedek on 2009-09-03
well it looks like some files arn't there so you might want to download them again.
also try typing ```
./configure
``` unless its file thats for ubuntu

---

### Post by wojox on 2009-09-03
When you open your terminal just type:

```
bash
```

Hit enter and go from there.

---

### Post by Murdoc_of_puts on 2009-09-03
no, I can see the file that it keeps getting stuck on.  Open it up and as far as I know it looks like a regular program.  ./configure gives me no such file directory. and running 'bash' at the start of the terminal and then trying to make the file doesn't result in any change.  What else do you guys have?

---

### Post by manaty on 2009-09-03
im having the exact same problem compiling the ieee80211-1.2.18 driver!

i kindof botched an installation of the intel pro injection patch and now cant get online (oops!) so im trying to reinstall the drivers using this guide: [http://ubuntuforums.org/showthread.php?t=387356](http://ubuntuforums.org/showthread.php?t=387356)

im running:
32 bit 9.04 
intel duo t5900 2.20 "hi-grade" laptop 

i cant connect to the internet on that machine atm, so any help would be greatly appreciated.  

much gratitude to the ubuntu community - you have saved my *** countless times before. thanks!

---

### Post by Murdoc_of_puts on 2009-09-05
Alright, I tried to do what he said in the above bump, and reinstalling the headers & wireless modules.  That went ok.  Then make asks me if I want to coment out some definitions, I said no.  Then if I want to strip some old symbols, I said yes (wouldn't let me continue otherwise).  Then I tried 'make install' and I got a similar answer to that of before.  What's going on here?

> CC [M]  /usr/src/ieee80211-1.2.18/ieee80211_module.o                          
  CC [M]  /usr/src/ieee80211-1.2.18/ieee80211_tx.o                              
  CC [M]  /usr/src/ieee80211-1.2.18/ieee80211_rx.o                              
  CC [M]  /usr/src/ieee80211-1.2.18/ieee80211_wx.o                              
/usr/src/ieee80211-1.2.18/ieee80211_wx.c: In function ‘ieee80211_translate_scan’:
/usr/src/ieee80211-1.2.18/ieee80211_wx.c:61: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/usr/src/ieee80211-1.2.18/ieee80211_wx.c:61: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/usr/src/ieee80211-1.2.18/ieee80211_wx.c:61: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/usr/src/ieee80211-1.2.18/ieee80211_wx.c:61: error: too few arguments to function ‘iwe_stream_add_event’                                    
/usr/src/ieee80211-1.2.18/ieee80211_wx.c:269: error: too few arguments to function ‘iwe_stream_add_point’
/usr/src/ieee80211-1.2.18/ieee80211_wx.c: In function ‘ieee80211_wx_set_encodeext’:
/usr/src/ieee80211-1.2.18/ieee80211_wx.c:631: warning: format not a string literal and no format arguments
make[2]: *** [/usr/src/ieee80211-1.2.18/ieee80211_wx.o] Error 1
make[1]: *** [_module_/usr/src/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [modules] Error 2


---

### Post by Murdoc_of_puts on 2009-09-09
Allright, I think I made some progress, but it's still r-tarded.  I looked at the install-which isn't the generic that I thought it would be.  It told me to enable certain modules.  I think all I had to do was remove the # in #define CONFIG_CRYPTO_MICHAEL_MIC module ?  Well, now I've got new errors as well as the old ones.  That's progress?  Here's the new ones.

> In file included from <command-line>:0:
./include/linux/autoconf.h:424:error: expected '=',',',':','asm' or '_atribute_' before 'CONFIG_CRYPTO_AES586_MODULE'
In file included from /usr/src/linux-headers-2.6.28-15-generic.arch/x86/include/asm/Paravirt.h:32

There's a couple of those, And more of the same as on above post.  PLease help. THanks in advance.

---

### Post by Ayuthia on 2009-09-09
The first set of error messages look like you are using the source that is for an older kernel.  You might want to search for a 2.6.28 patch for that source.

---

### Post by manaty on 2009-09-10
OK, 
so i tried booting up one of the earlier 9.04 kernels i had in my grub menu, (i cant remember which one, will post it on my next reboot) which seemed to do the trick - the driver compiled without a hitch! 

hope it works for you guys too

now for injection....

---

### Post by Murdoc_of_puts on 2009-09-11
All right, I think I solved the basic problem.  Building a house with a banana doesn't work. I didn't have build-essentials installed.which now 'make' works just like it's supposed to.   Any way thanks to Sambita for his great guide.  which is [here]("http://ubuntuforums.org/showthread.php?p=6934824#post6934824")

---

